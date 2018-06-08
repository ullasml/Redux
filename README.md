
# Why Redux? #

* The major problem with the non redux like state of affairs is that there's no dedicated, central, place to store and retrieve states. 

* The state is spread out all over your app. Often we find ourselves in situations where state is mutable, and where multiple actors in our system need to be addressed in case state changes.  

* We have multiple solutions for these problems, such as Singletons, KVO, Bindings, Notifications, Closures, Delegation, and more.  

* Apps built using such a non redux like implementation often end up with a lot of complexity around state management and propagation.  

* We need to use callbacks, delegations, Key-Value-Observation and notifications to pass information around in our apps and to ensure that all the relevant views have the latest state.  
		 		
* However this often ends up in spaghetti code

# Benefits Of Redux #

**Predictability of outcome **: There is always one source of truth, the store, with no confusion about how to sync the current state with actions and other parts of the application.

**Maintainability**: Having a predictable outcome and strict structure makes the code easier to maintain.

**Organization**: Redux is stricter about how code should be organized, which makes code more consistent and easier for a team to work with.

**Ease of testing **:The first rule of writing testable code is to write small functions that do only one thing and that are independent. Redux’s code is mostly functions that are just that: small, pure and isolated.

# Summary #

* You get a clearer, declarative code blocks with this structure. Your actions describe every single way the state of the application can be changed. If you follow the pattern well, there is no function that performs any side effect, there’s no other place where someone could inject a piece of code that is hard to track down — there’s just these list of actions. It doesn’t matter how many there are and they clearly describe which mutations can happen.

* If you want to see how these actions are responded to, you go into exactly one place and that are the reducers. That way you end up with predictable and explicit state. If I were to ask you what is the state of your app at this moment in time, you would have no idea. With this architecture, you actually have one data structure that you can print out to the console and you can see exactly what the current application state is.

* Furthermore, with explicit application state and actions that describe the changes, our program now has a shape. Now, if I bring on a new developer on my team and they want to see what are the existing features, they take a look at the application state, the reducers, and the actions, and they don’t have to dive into hundreds of view controllers to see what is going on.


# What is Redux? #

 It is a ****Unidirectional state management paradigm****. It is surprisingly simple, and therefore even more surprisingly powerful.

![Alt Text](https://raw.githubusercontent.com/pluralsight/guides/master/images/f685aa1c-99d2-44aa-b705-99267c16bd4b.com-optimize)

## **State** ##

* State does not exist anywhere but one single store. 

* Views and view controllers do not manage their own state — they only ask the store to update (via actions), and they deterministically update their interface whenever state has changed to visually represent it.

## **Action** ##

* They are, fundamentally, requests to update state.

* In a nutshell, actions are events with/without data  intending to perform an task.

* When they are dispatched to the store, the reducer is called to take in the prior state and the action, and it spits out a new state. 

* The store then replaces its state with the new state and updates subscribers — views / view controllers.

## **Reducer** ##

* Reducer — a pure function that is given an old state and an action, and it returns a new state that’ll replace the old one in the store. 

* The reducer is literally just a pure function, making unit testing a breeze. 

* It can be broken down into sub-reducers to tidy code per sub-state.

* It **contains no asynchronous or external calls**, and has no side effects.

## **Store** ##

Store — contains the state, receives actions, uses the Reducer to replace the state, and fires off the new state to subscribed views.This makes Redux very simple, predictable and easy to reason about.

## **Subscribers** ##

* Subscribers/Views/ViewControllers — subscribe to the store to receive new state when it’s updated. 

* Views/ViewControllers simply visualize state exactly as it’s received from the store. 

* They don’t manage their own state in any capacity.

## **Action Creators/Sagas** ##

* They are the middleware library that handles side effects in your redux app.

* you can test your asynchronous flows easily and your actions stay pure. 

* They are dispatched and can run asynchronous code that eventually may dispatch an action.



