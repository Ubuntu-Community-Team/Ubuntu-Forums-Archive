---
title: "How to switch between Gnome shell and Unity?"
date: 2011-11-06
forum: Desktop Environments
---

### Post by jasoncruz98 on 2011-11-06
I have installed Ubuntu 11.10 on my USB. 

I want to use both Gnome shell and Unity.

So, how do I switch between them freely without anything bad happening to my files or open windows?

---

### Post by Randy Schilling on 2011-11-06
I installed U10.10 but the login screen 
(where you choose which user account to log into)
does not include the usual options.
These are language, keyboard, and most importantly, session.
The session is where you choose your desktop.
I get just two choices, ubuntu and ubuntu 2D,
even though all the files of the Gnome environment  
are installed on my system.  

Would you please tell me
how to setup the Gnome GUI as one of my desktop options?

I tried Unity, its got some goo ideas, but I'd
like to go with the familiar Gnome desktop.

Thanks for your help and regards. Randy

---

### Post by Copper Bezel on 2011-11-06
Gnome Shell isn't installed by default, so make sure you have the package gnome-shell installed. Then, at the login screen, click the cog icon next to the password field to select the session.

I don't know how to change the language and keyboard settings from the LDM login window, but they don't have any effect on your actual session (unlike the old GDM.)

You can't switch between the two within a session, however. jasoncruz98, you'll need to save your work and log out to get to a different login session, because it's not just one process running the whole interface; there are a lot of little things they handle differently beyond just the window manager. You can run gnome-shell --replace or unity --replace from Alt+F2, but bad things *are* likely to happen.

---

### Post by 3Miro on 2011-11-06
Windows Managers like Compiz, Metacity, Open Box etc, work on one standard. Gnome-shell uses the Mutter WM, which is a different standard. In the past, you could switch between Compiz and Metacity "on the fly", however, the only way to switch between Compiz (Unity) and Gnome-shell is to logout then login.

---

### Post by Randy Schilling on 2011-11-06
Thanks very much for you help.
As far as I'm concerned, the problem is solved.
Thanks again and regards - Randy

---

