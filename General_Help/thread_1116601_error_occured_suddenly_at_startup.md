---
title: "error occured suddenly at startup"
date: 2009-04-05
forum: General Help
---

### Post by cooltarlee on 2009-04-05
an error occured suddenly at start up . the  error is " an error occured while loading or saving configuration information for update-notifier. some of your configuration settings may not work properly".

DETAILS FOR ERROR:-
failed to construct configuration server .some possible causes are that you need to evolve tcp/ip networking for orbit or you have stale nfs locks due to a system crash. details1- could not send message to gconf deamon. message did not recieve a reply.
(timeout by message bus).

what should i do now to solve this problem. now i can see just a black screen. please tell me an appropriate solution

---

### Post by infallible on 2009-04-07
I came across your thread while searching for the solution to a similar problem, and thought I would share what I've learned (or at least my theory.) 

The system crashed, and gconf didn't close out properly. It has a function that locks critical files, etc for the use of the individual user. The crash caused them to remain locked, and therefore inaccessible.  ctrl-alt-1 brings up a terminal, ctrl-alt-7 brings up  a gnome (windowed) session. To remedy this, try typing ```
 mv ~/.gconfd/saved_state saved_state.old

``` into your terminal and reboot, or perhaps its only necessary to ctrl-alt-backspace and log in again.   It was either this that fixed it, or "dpkg-reconfigure gconf<tab><tab>" and reconfiguring everything that started with gconf. either way, these steps allowed me to log in again.

best of luck,
Pete

---

