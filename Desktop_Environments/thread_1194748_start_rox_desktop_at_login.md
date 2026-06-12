---
title: "start rox desktop at login"
date: 2009-06-23
forum: Desktop Environments
---

### Post by user sam on 2009-06-23
Well, hello again. A while back I posted about setting up Ubuntu on a slow old computer(128mb ram, 633MHz processor and an addiction to its original operating system). Well, youll be pleased to know that it works just dandy with icewm and rox-filer(for desktop icons). My problem is with rox. You can get a desktop by typing rox -S in a command prompt. I would be very happy if I could start it automatically at login. It just makes for something a little more familiar to us ex windows and mac users. So, if you know what im talking about, please help.

---

### Post by Brandon Williams on 2009-06-23
How are you starting icewm? I assume it's with either a .xsession or a .xinitrc file. Post the contents of that file and we can tell you what needs to be modified.

I expect that the file will end up looking something like this:
```
#!/bin/sh
rox -S &
icewm
```
That's just a guess about the command to start icewm.

---

### Post by user sam on 2009-06-23
where would I find these files? the only files by that name look nothing like that.:confused:

---

### Post by Mark76 on 2009-06-23
ROX desktop has its own session manager ([here]("http://roscidus.com/desktop/ROX-Session")).  Install zeroinstall injector from the repos, then run it and drag the 0install link to the window that pops up. It'll cache the program and its dependencies (there are two). Go into /usr/share/applications and click on the zeroinstall-manage-desktop file, then click on the run button next to the entry for ROX-Session (which should be the only one) and click on Set Up Rox. Choose Set Up for  User or Add to Login (the latter requires you to set up a root password first. Open a terminal and type sudo passwd. It'll prompt you to input a new passwd for root (note: this is not the same as your sudo password). Create one and then retype it when it asks).

When you've set up ROX-Session do as it says and then when you log back in you'll either be running ROX-Session by default (the first option), or it'll be one of the session choices alongside Gnome and whatever else.  When it starts it'll ask you if you want to download OroboROX. Say no and then type icewm into the CLI box that appears.  It should then remember your choice of window manager until you change it.

---

### Post by kerry_s on 2009-06-23
> **user sam said:**
> where would I find these files? the only files by that name look nothing like that.:confused:

icewm-session uses a startup file, you may need to create it.
[http://www.icewm.org/FAQ/IceWM-FAQ-4.html](http://www.icewm.org/FAQ/IceWM-FAQ-4.html)

---

### Post by user sam on 2009-06-23
Okay, im really confused now. There isnt a way to run a program at login? Cant I just get the command rox -S to run at login?

---

### Post by kerry_s on 2009-06-23
> **user sam said:**
> Okay, im really confused now. There isnt a way to run a program at login? Cant I just get the command rox -S to run at login?

yes there is, just create the startup file like the icewm says to do & it will start with icewm.

i'm going to assume since your using light programs, you'll probably be using leafpad as your editor.

**leafpad ~/.icewm/startup**
put:
[B]#!/bin/sh
rox -S &[/B]

now make it executable> **chmod +x ~/.icewm/startup**

thats it should start with icewm from then on.

---

### Post by user sam on 2009-06-23
Alright. I got it. I created a .xprofile file in my home directory and it says

#! /usr/bin/sh
rox -S &
icewm
exit

or something like that. the exit at the end seems to have fixed a problem where i had to logout twice. Thanks! 
Oh, and my default text editor is actually nano. I should probably get leafpad though. nano is easier to use sudo with in my opinion. fewer letters.

---

### Post by kerry_s on 2009-06-23
alright, whatever works for you.
remember, graphical programs use "gksudo", so it would be:
gksudo leafpad
gksudo rox
etc...

you know you can save more resources, not using icons & backgrounds. a simple file manager is "gpe-filemanager", it doesn't do hidden folders/files but you can use "mc" in the terminal for that.

i did a build on a ibmt20 with 128mb ram(120mb -vid), i used the lightest of everything else since the main program would be the web browser(used epiphany).

---

### Post by Brandon Williams on 2009-06-23
I don't think you want to do this in ~/.xprofile, which tends to be applied very early in session setup and is sourced, not executed, so that other session startup activity can continue. That's probably why you have to log out twice.

Did you try putting it in ~/.icewm/startup, as suggested above?

---

### Post by user sam on 2009-06-24
OK, that works too. I didn't understand at first. The thing works like a charm now! Thanks.

---

### Post by kerry_s on 2009-06-24
yeah, you might want to read through that icewm manual when you have time, it will help you get the most out of icewm. icewm has a lot of features that you can take advantage of, to make working with it smoother & faster.

---

### Post by kristan2000 on 2009-06-28
Here you'll find news, software, themes, tutorials, hints and tips. However, these pages are not static. Anyone can post comments attached to any page. You can request an account which allows you to create your own pages. If you receive Developer status you can edit existing pages.
 You can get back to this page at any time by clicking on the Home Page link in the page header. 
 If this web-site is too slow, please try the sf.net project page instead.
==============================================
[wasserbett](http://www.wasserbettenhilfe.com)
[taxi from toronto airport to toronto](http://www.torontoairportcab.com/html/services.htm)

---

### Post by Mark76 on 2009-06-28
Erm.

Isn't that from the ROX Desktop site? :?

---

### Post by yanom on 2009-06-29
> **kerry_s said:**
> but you can use "mc" in the terminal for that.

midnight commander is AwSoMe!!!!

---

