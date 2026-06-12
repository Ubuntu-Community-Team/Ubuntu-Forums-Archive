---
title: "Scrolling Focus follows mouse"
date: 2012-11-13
forum: Desktop Environments
---

### Post by rich6031 on 2012-11-13
I have linux experience, but I'm new to xubuntu.  I'm running 12.04 and have run apt-get update, so everything should be up to date. My problem is that I've gone into Window Manager and set my Focus Model to "Click to focus" however when I move the mouse off of any window the mouse wheel stops scrolling the window with focus. In fact it will scroll which ever window the mouse is over. My focus isn't changing. The window that had focus still has focus, I just lose the ability to use the mouse wheel to scroll the window with focus.  Is there a setting somewhere to change this?

---

### Post by rai4shu2 on 2012-11-13
Change it to "Focus follows mouse". What you are describing is the normal behavior as designed.

---

### Post by rich6031 on 2012-11-19
I knew I was explaining this wrong. I do not want focus to follow mouse. I WANT focus on click. I have my settings set to focus on click. The problem is that when I move the mouse away from the window that I have clicked on (and therefore should have the focus) the mouse scroll wheel no longer scrolls the contents of the window.

---

### Post by rich6031 on 2012-11-19
Here, I posted a link to an image of my problem in action. The left window shows my settings which are "Click to Focus" then I clicked on Firefox on the far right and cleared out the location bar to prepare to type in it. I then moved my mouse over the middle window (chrome). When I type my typing shows up in firefox's location bar. This is correct "click to focus" behavior. However, when I use the mouse wheel to scroll the contents of the window it scrolls chrome. This is not "click to focus" behavior.
[http://i.imgur.com/sSbdw.png](http://i.imgur.com/sSbdw.png)

---

### Post by rai4shu2 on 2012-11-19
I understand, but what you're describing is how Windows works. Windows isn't Linux.

---

### Post by rich6031 on 2012-11-19
As a unix developer, I don't actually use windows. I assure you I do understand that linux isn't windows. 

My concern is the focus settings aren't configured the way I like them, and a joy of using an open source system like linux is that almost everything is configurable. I was wondering if there was any way to configure Xubuntu to send scroll events to the window with focus. 

You've communicated that you don't know of a way, thank you for responding. If someone else does know of a way to configure scroll events to go to the window with focus, I hope they will post on this thread.

---

### Post by rai4shu2 on 2012-11-20
I don't think xfwm can do what you want. Maybe try some other window manager (like KDE or Openbox). I do know that one of the Window Manager Tweaks (in Accessibility) is "Raise windows when any mouse button is pressed" which will also give the window your mouse is over the focus if you use the third button. It isn't what you want, but I think that's as much as xfwm does.

---

