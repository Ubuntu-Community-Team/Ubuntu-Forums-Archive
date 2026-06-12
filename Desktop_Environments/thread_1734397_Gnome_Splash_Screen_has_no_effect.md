---
title: "Gnome Splash Screen has no effect"
date: 2011-04-20
forum: Desktop Environments
---

### Post by dredmal on 2011-04-20
I installed the Gnome Splash Screen application to change my login splash screen to the same background as my desktop.

After using the program and applying my changes, and rebooting nothing happened. I still have the pink default image in the background instead of the image I chose.

I did not have any luck using a search engine to solve this issue.

I'm using Ubuntu 10.10 with an Nvidia graphics card.

This is my first attempt at linux support of any kind and I hope I am in the right place and using an acceptable format. 

thanks

---

### Post by Frogs Hair on 2011-04-20
Hi and Welcome

Many of the applications for changing splash screens in Ubuntu no longer work with newer versions. What application did you use ?

---

### Post by dredmal on 2011-04-20
I'm using gnome-splashscreen-manager 0.2 (didn't realize it was a beta when i downloaded it from Ubuntu Software Center)

I assume I'll have to use the terminal to do it. I'll start looking now. Would you have any advice or a link on what to do?

thanks

---

### Post by Krytarik on 2011-04-20
The app you installed is meant to change the Gnome Splash, a little window that appears *after* logging in to a Gnome session, those isn't enabled by default (anymore).

It seems like you want to change the appearance of the login screen (GDM), therefore please see my earlier post:
[http://ubuntuforums.org/showthread.php?p=10468340#post10468340](http://ubuntuforums.org/showthread.php?p=10468340#post10468340)

Greetings.

---

### Post by dredmal on 2011-04-20
Yes i want to change the background image of the screen where I input my password to login to my desktop. I understand you said it can't be done. I really hope I'm not stuck with that pink background.

I followed the link you provided where you said it can't be done. But just below there is [this link]("http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html") that says it can be done.

I followed the instructions and that link and it didn't work. 

I'm confused now. Am I really stuck with this pink background when I reach the login prompt?

---

### Post by Krytarik on 2011-04-20
I didn't say *at all* that it can't be done!

It's just that some people want to apply login themes that were build for previous versions of GDM, when it was possible to change its look very much more than just through the "Appearance" settings. I've done it myself with an earlier version of Ubuntu (Gutsy 7.10).

So, just follow my instructions at the upper part of my post, and you will achieve what you want. The level of customizibility is still enough for me.

---

### Post by dredmal on 2011-04-20
I started to follow the post you linked. Here is the first instruction.

- copy "/usr/share/applications/gnome-appearance-properties.desktop" into "/usr/share/gdm/autostart/LoginWindow"

I navigated my filesystem to the /usr/share/applications/ folder but I can not find anything called 'gnome-appearance-properties.desktop'

Any help?

---

### Post by dredmal on 2011-04-20
Solved: I followed the 'detailed commands' on your post and got it to work. That is exactly what I wanted.

Thanks for the help.

---

### Post by Krytarik on 2011-04-20
You're welcome!

---

