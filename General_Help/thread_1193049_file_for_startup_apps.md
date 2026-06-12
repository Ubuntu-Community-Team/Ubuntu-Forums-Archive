---
title: "file for startup apps"
date: 2009-06-21
forum: General Help
---

### Post by cong06 on 2009-06-21
I was messing around with making my computer more efficient, and tried disabling a bunch of the start up programs.
I could go back in and reformat the whole computer, but what I'd like to do is find the file and edit it to fix the problem.

Where are the start up applications stored in ubuntu? I've heard of ~/.gnomerc but in my 9.04 install, that file is empty (even after making changes).

---

### Post by dyess002 on 2009-06-21
What is the problem Cong06, you didn't give us the problem you are having.
I have ( start-up Application ) in system/preference/start up application and that will let me choose which one starts up when I boot up.

---

### Post by cong06 on 2009-06-21
yeah, I was hoping for information about where the data is actually stored.

Right now when I open my computer...well, a critical application for the gui isn't loading. My desktop shows up (nautilus) but program that decorates the windows is missing.

So if I know where the file is I have the potential to fix the error I caused through command line.

---

### Post by drs305 on 2009-06-21
Applications you have chosen to autostart via Preferences > Startup Applications are found in ~/.config/autostart

If you are looking for system applications, they are often located in /etc/init.d with the startup links in the /etc/rcX.d folders (X being a number).

If you know the name of the app specifically you want to tweak we can probably give you the exact location.

If you need to start or restart *compiz*, which has window decoration capabilities, you can try:
```

compiz --replace &

```

---

### Post by blueridgedog on 2009-06-21
Well, I find that in modern Linux systems there are two types of startup applications.  There are the traditional system applicatoins then there are user applications started by the window manager.  

As far as the traditional applications go, there are two locations.  I pass them on not for editing purposes, but so you know they are there:

1.  When booting all files in /ect/init.d/rc.local are run.  This is the equivillant to the DOS autoexec.bat file system, but if you are under 30, you don't know what that it is and it seems like silly reference.

2.  In /etc you will find various directories named /ect/rcn.d where n is a number from 0 to 6.  These numbers represent the different Linux run levels.  The default Ubuntu run level is 2, so if you look inside /etc/rc2.d you will see symbolic links back to files in /etc/init.d.  Files with a capital S are run when the system starts to that run level, others are not.

For more reading, browse some of these:

[http://www.google.com/search?q=linux+run+levels&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=linux+run+levels&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Note that Ubuntu/Debian defaults to run level 2 and uses a GUI at that point which is contrary to most Linux configurations.

The window manager also starts applications when the user logs in, running these applications as the user, not as system level applications.  The gnome applications you configure to run at start are setup as files in the directory /home/USER/.config/autostart.

Edited on 2009-June-26 to add additional information:

CAtKiller reported that System Gnome applications also start based upon the entries in /etc/xdg/autostart/ and if you use the gui to disable them, a negating entry is placed in your /home/USER/.config/autostart directory.

And finally, the applications can be started via entries in the files /home/USER/.bashrc and /home/USER/.bash_profile.

So, there are the applications started via the system initialization process (init.d), the applications started by the window manager /etc/xdg/autostart and /home/USER/.config/autostart and the normal shell profile files (.bash*).

---

### Post by CatKiller on 2009-06-21
> **blueridgedog said:**
> I have not been able to find the plethora of included gnome start up applications as a text file, but perhaps someone else can shed dome light on them.

They are also .desktop files. They can be found at /etc/xdg/autostart/.

---

### Post by blueridgedog on 2009-06-21
> **CatKiller said:**
> They are also .desktop files. They can be found at /etc/xdg/autostart/.

Where then is the "checked" or "unchecked" state stored?

---

### Post by CatKiller on 2009-06-21
> **blueridgedog said:**
> Where then is the "checked" or "unchecked" state stored?

In ~/.config/autostart. Each user that deselects one of the system applications gets a launcher for the same application in their Home directory with X-GNOME-Autostart-enabled=false set.

---

### Post by blueridgedog on 2009-06-21
> **CatKiller said:**
> In ~/.config/autostart. Each user that deselects one of the system applications gets a launcher for the same application in their Home directory with X-GNOME-Autostart-enabled=false set.

Excellent.  I was on the verge of figuring that out based on the items in my autostart directory.

Philosophically:
-Why have four sources of starting applications on boot (more if you count the multiple run levels and local rc files)?  rc.local rcn.d autostart in /etc and autostart in ~/
-If the answer to the above is "to give different users a way to configure user level start applications" then why build the user level application launching code on top of/into the window manager rather than using historical shell tools such as .bashrc .bash_profile?  Why build a new structure that will need to be managed per each window manager?

---

### Post by CatKiller on 2009-06-21
> **blueridgedog said:**
> Philosophically:
-Why have four sources of starting applications on boot (more if you count the multiple run levels and local rc files)?

Come on, you already know the answer to this; backwards-compatibility.

In the crusty past, where graphical tools to do many things were neither available nor desirable, there was one way of doing things. There may even have been two ways of doing things, but they probably were both configured by editing a text file somewhere. The distributions wanted to cater to both ways, so they put in support for both ways.

Then a graphical system was developed. They were able to start things with the graphical environment, so they did. The distributions wanted to cater to users of this new graphical environment, so they put in support for the new way. But some users were still using the old ways, so they didn't take out support for the old ways.

Then a desktop environment was developed. They were able to start things with the desktop environment, so they did. The distributions wanted to cater to users of this new desktop environment, so they put in support for the new way. But some users were still using the old ways, so they didn't take out support for the old ways.

Then a different desktop environment was developed. They were able to start things with the desktop environment, so they did. The distributions wanted to cater to users of this new desktop environment, so they put in support for the new way. But some users were still using the old ways, so they didn't take out support for the old ways.

At some point there was probably a desire to consolidate all the ways of doing things, so a new method was developed. But some users were still using the old ways, so they didn't take out support for the old methods.

Rinse and repeat.

---

### Post by blueridgedog on 2009-06-21
It would appear to me that the graphical tools could add entries to the text files versus creating files of their own.  I still manage my systems with /etc/rcn.d, rc.local and .bash_profile.  

It scares me to think that certain applications and processes are starting to be dependent on the window manager so that the system isn't fully booted at a non-gui run level.  The result is that things running by the OS independent of the user (/etc/rcn.d for Debian like things) are starting to be called "services" and user programs are called applications that run under sessions.  

This is too "windows like" and is getting away from the simplicity of the window manager being separate from the OS.

---

### Post by CatKiller on 2009-06-21
There's not necessarily anything wrong with doing things the same as Windows does them. There are quite a few things that are done the same amongst any number of desktop environments, and there's no benefit to doing things differently just for the sake of being different. Doing things **better**, of course, is an entirely different concern.

Any attempt to unify the different start-up mechanisms runs the risk of fragmenting the community and exacerbating the problem further. But hopefully the endeavours of the Upstart project and the freedesktop people will make the situation better rather than worse.

---

### Post by cong06 on 2009-06-22
Well, thanks for the discussion and the help. It helped me learn a bit about Ubuntu, even if it didn't quite solve the problem.
I might have to just reformat.

Running ```

compiz --replace &

```
Did help some, but for some reason I can't figure out the app that's not loading. I could run it each time on startup to fix the problem, but I'm also missing the panels..

Basically to make a long story short, I'm scrapping and reformatting. It's not worth it, I don't quite have enough time to learn more about the issue I'm having. Thanks for the help in any-case...I wish I had enough time to learn about what I disabled so I don't accidentally do it again...

---

### Post by blueridgedog on 2009-06-22
Well, I think we covered most of the ways in which things start and stop in Ubuntu and Linux, so if you can't find the item you disabled, it may be that is not the issue.

---

### Post by loomsen on 2009-06-25
> **cong06 said:**
> I don't quite have enough time

sudo adduser MyNewUser

log in, BAM! Just like it is after a fresh install (well, including apps you might have installed)

Bummer you don't have the time, blueridgedog really explained everything nicely and comprehensive. 18 hrs (from you initial post) should actually be enough to become rcS.d pro...

However, now you know why sudoing without knowing what you do can mess things up (if you don't know how to fix them)
Rather get a permission denied and rerun a command afterwards, than running a supercow powered command when there's not even a fly to impress.

---

### Post by cong06 on 2009-06-26
sudoing without knowing what I was doing?

I knew what I was doing...I was installing my apps.

Oh well. my laptop's working nicely now, as you probably noticed in my [other thread]("http://ubuntuforums.org/showthread.php?p=7519036#post7519036").

---

