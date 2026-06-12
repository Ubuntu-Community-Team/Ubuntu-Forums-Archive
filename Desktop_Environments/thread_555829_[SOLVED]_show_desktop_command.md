---
title: "[SOLVED] show desktop command"
date: 2007-09-20
forum: Desktop Environments
---

### Post by HokeyFry on 2007-09-20
what is the terminal command to run the show desktop program for xubunxu?

i know the shortcut is ctrl+alt+D, and i know theres a button, but i need to know what i would type in a terminal to run it

---

### Post by swisscow on 2007-09-20
don't know about showing the desktop but you can do 

```
cd Desktop

ls
```

to list contents of the desktop - but you probably know that anyway. Will watch this thread and learn myself

---

### Post by Wolki on 2007-09-20
There isn't really one - showing the desktop is a built-in of the window manager, not an executable.

But don't worry though, most window managers (including the ones in xfce and gnome) adhere to a standard interface, the EWMH/NetWM specification. This allows programs that remote-control their functionality. And fortunately, someone already has written one called "wmctrl". Install it from the repos.

Then, you can switch 'show desktop' on with "wmctrl -k on" and off with "wmctrl -k off".

wmctrl also has a lot of other functionality, take a look at its manpage to find out more.

---

### Post by HokeyFry on 2007-09-21
thanks, that really helps

just out of curiosity though, does this mean there's no way to activate the "Show Desktop" button that you can enable in the panel from the terminal?

---

### Post by Wolki on 2007-09-21
> **HokeyFry said:**
> thanks, that really helps

just out of curiosity though, does this mean there's no way to activate the "Show Desktop" button that you can enable in the panel from the terminal?

I'm not an XFCE expert, so I'll answer this from the gnome viewpoint, but yes, there's no way to activate the show desktop button from the terminal, similar to how there's no command to activate the menu from the terminal, or cycle tabs in firefox from the terminal - simply because these actions are not programs, but functions in a program (which you could surely bind to commands, but this would become very messy - command line and graphical interfaces are quite different, and trying to map one fully to the other doesn't make sense).

But since the show desktop button and wmctrl do nothing but send messages to the window manager (or read the state from there), you shouldn't be able to note any difference - at least on my machine, executing "wmctrl -k on" will cause the show desktop button to appear pressed, and should in all other respects work like the button. 

If the wmctrl solution is good enough for you, would you mark this thread as solved?

---

### Post by HokeyFry on 2007-09-21
yeah wmctrl does solve my problem thanks

---

### Post by poojac20 on 2008-01-15
Just to add, why one may want to do this from console. 

I use AWN, which allows me to set launchers on my dock or use inbuilt applets. For some reason, it doesn't allow me to change icons of applets. So, although they have provided an applet to "show desktop", i want my own launcher (Their icon is purple!)

To have my own launcher, i need "a command" to show desktop. As I can see from this thread, it cannot be done through one command with no persistence/memory. At the minimum, the command needs to remember its toggle status in order to supply on|off params correctly. So, I am writing a small shell-script that remembers the last status. 

Thanks for the information.wmctrl is kind of a cool tool.

---

### Post by chochem on 2008-02-20
> **Wolki said:**
> I'm not an XFCE expert, so I'll answer this from the gnome viewpoint, but yes, there's no way to activate the show desktop button from the terminal, similar to how there's no command to activate the menu from the terminal, or cycle tabs in firefox from the terminal - simply because these actions are not programs, but functions in a program (which you could surely bind to commands, but this would become very messy - command line and graphical interfaces are quite different, and trying to map one fully to the other doesn't make sense).


Uhm I'm just an enthusiastic Xfce user (no expert) but - just to set the record straight - that really is nothing more than your opinion. And wrong as far as Xfce goes. Most 'actions' related to the Xfce components (Xfwm, the window manager; Xfdesktop, the desktop manager; xfce4-panel, the panel; etc.) can be controlled simply by passing arguments to the program. Which does make a lot of sense, since you can then put them into scripts, tie them to bits that the programmers didn't think of etc. (this feature provided me with a workaround to an otherwise intractable problem only just yesterday!) In short customize your system to your taste. Isn't that what Linux is about?

Anyway, just my little rant. wmctrl is an excellent little tool :)

---

### Post by Wolki on 2008-02-20
> **chochem said:**
> Uhm I'm just an enthusiastic Xfce user (no expert) but - just to set the record straight - that really is nothing more than your opinion. And wrong as far as Xfce goes. Most 'actions' related to the Xfce components (Xfwm, the window manager; Xfdesktop, the desktop manager; xfce4-panel, the panel; etc.) can be controlled simply by passing arguments to the program. Which does make a lot of sense, since you can then put them into scripts, tie them to bits that the programmers didn't think of etc. (this feature provided me with a workaround to an otherwise intractable problem only just yesterday!) In short customize your system to your taste. Isn't that what Linux is about?

Of course it's my opinion - I posted it, and I have no normative powers that allow me to declare ultimate truths :) But I'm quite sure that not all functions of each interface component are bound to shell commands (I've just taken a look at xfwm4, and its options seem to be rather few...).

If your point is that it's good if functions of a program are available via a shell command where it makes sense, then you're certainly right (though i usually prefer dbus interfaces instead, since they are often easier to use from scripting languages and potentially faster, shell wrappers around that dbus interface can be written afterwards). But I didn't argue against that.

---

### Post by chochem on 2008-02-21
> **Wolki said:**
> Of course it's my opinion - I posted it, and I have no normative powers that allow me to declare ultimate truths :)

You just made me loose faith in the whole concept of 'ask some guy on the internet' ;) Okay, I'm sorry if I read your post in a way it wasn't intended.

> **Wolki said:**
> though i usually prefer dbus interfaces instead, since they are often easier to use from scripting languages and potentially faster, shell wrappers around that dbus interface can be written afterwards

Uhm I'm out of my depth here. What are dbus interfaces and how would one go about doing something like that?

---

### Post by Wolki on 2008-02-21
> **chochem said:**
> You just made me loose faith in the whole concept of 'ask some guy on the internet' ;) Okay, I'm sorry if I read your post in a way it wasn't intended.


Ah, I seem to have a habit of writing in such a way that I can be easily misunderstood... >_<

> Uhm I'm out of my depth here. What are dbus interfaces and how would one go about doing something like that?

Basically it's a inter-process communication system, so that program A can send a signal and receive information from program B. More info is on the wikipedia page: 
[http://en.wikipedia.org/wiki/D-Bus](http://en.wikipedia.org/wiki/D-Bus)

---

