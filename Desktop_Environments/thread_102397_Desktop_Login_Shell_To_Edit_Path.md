---
title: "Desktop Login Shell To Edit Path"
date: 2005-12-11
forum: Desktop Environments
---

### Post by pilaftank on 2005-12-11
What user modifiable startup script runs at login on Ubuntu?

Details -
1: From my simple testing, apparently it's not **~/.bash_profile**, **~/.bashrc**, **~/.profile**, or **~/.login** (although **~/.bashrc** does get run when launching a terminal).
2: Needs to work at login for the desktop (terminal stuff is not applicable in this situation).
3: User has no "root" privileges and we can assume a plain vanilla, fresh install.

The reason for this question is that I'm creating instructions for regular desktop users (no root privileges) to download Java (just the JRE) from Sun, untar it, and then add a symbolic link to "java" in their **~/bin** directory.  So, I also need to tell my users how to add **~/bin** to their PATH.  After all that, the users can create a "Launcher" on their desktop to conveniently launch my application.

---

### Post by pilaftank on 2005-12-12
I've been investigating using one of the X startup scripts.  The **~/.xsession** and **~/.xinitrc** scrips have potential.  However, the **~/.xsession** and **~/.xinitrc** scripts are responsible for launching the desktop itself, and creating one of those scripts overrides the default X11 startup script.  In other words, it's very easy to ***crash*** your desktop (which I accidentally did myself).

Details --> [Setting up .xinitrc/.xsession](http://fluxbox.sourceforge.net/docbook/en/html/app-setup.html) 

Creating a **~/.xsession** or **~/.xinitrc** script is kind of the Windows equivalent of editing the Registry.  Is there an X startup script that is not so dangerous and would be an appropriate place for regular desktop users to modify their PATH setting.

---

### Post by pilaftank on 2005-12-18
I think the lack of replies is because there actually is no answer.  It's just not possible.  I also tested the files **~/.gtkrc**, **~/.gtkrc.mine**, **~/.dtprofile**, **~/.dtlogin**, **~/.login**, **~/.xsetup**, **~/.Xsetup**, **~/.Xstartup**, and **~/.xstartup**.  It seems that the only way an Ubuntu desktop user can modify the PATH is to be root.

Desktop applications targeted for business and personal usage should not require root to install or setup.  Maybe future versions of Ubuntu will be more accommodating to non-techie users.

---

### Post by cwaldbieser on 2005-12-19
[QUOTE=pilaftank]I think the lack of replies is because there actually is no answer.  It's just not possible.  I also tested the files **~/.gtkrc**, **~/.gtkrc.mine**, **~/.dtprofile**, **~/.dtlogin**, **~/.login**, **~/.xsetup**, **~/.Xsetup**, **~/.Xstartup**, and **~/.xstartup**.  It seems that the only way an Ubuntu desktop user can modify the PATH is to be root.

Desktop applications targeted for business and personal usage should not require root to install or setup.  Maybe future versions of Ubuntu will be more accommodating to non-techie users.[/QUOTE]
You should be able to simply put it in you ~/.bashrc.  Something like:
```

export PATH=$PATH:~/bin

```
.bashrc gets sourced every time you start a bash shell or subshell.  I am not sure why it did not seem to work as you indicate in your first post.  Maybe if you explained exactly what you tried we could figure it out.

---

### Post by pilaftank on 2005-12-19
The operative word here is: *desktop*.  The **~/.bashrc** script does get run when launching a terminal, but it does *not* apply to the *desktop*.  It's easy enough to test yourself: Just add the line **date >> log** to **~/.bashrc** and you'll find out that the **log** file is *not* created when you login using the standard *desktop* login.

---

### Post by cwaldbieser on 2005-12-19
[QUOTE=pilaftank]The operative word here is: *desktop*.  The **~/.bashrc** script does get run when launching a terminal, but it does *not* apply to the *desktop*.  It's easy enough to test yourself: Just add the line **date >> log** to **~/.bashrc** and you'll find out that the **log** file is *not* created when you login using the standard *desktop* login.[/QUOTE]
That may be true, but to create your desktop shortcut, using ~/.bashrc will work fine.

I have an executable program that is located in my ~/bin directory.  This folder is *not* in my PATH by default.  I add ~/bin to my PATH in my ~/.bashrc.  I create a shortcut that is simply the name of the command (without the full path).  I click it and it runs.

Also, for Kubuntu users, any script placed in ~/.kde/Autostart is run when the user logs in.

---

### Post by pilaftank on 2005-12-19
I'm a little confused on the use of the word *shortcut*.  Do you mean you create a *launcher* that runs your **~/.bashrc** script and then you manually run that launcher *before* you use any another launcher that relies on the updated PATH?  Or are you talking about a symbolic link?

---

### Post by anatole on 2005-12-19
gdm's handling of startup scripts is stupid imho, in fact i was lazy to try to understand it, so i wrote an .xsession file, thats easier. you can try reading this documentation however.. (section three, initialization scripts)

[http://www.gnome.org/projects/gdm/docs/gdmtalk.pdf](http://www.gnome.org/projects/gdm/docs/gdmtalk.pdf)

---

### Post by cwaldbieser on 2005-12-19
[QUOTE=pilaftank]I'm a little confused on the use of the word *shortcut*.  Do you mean you create a *launcher* that runs your **~/.bashrc** script and then you manually run that launcher *before* you use any another launcher that relies on the updated PATH?  Or are you talking about a symbolic link?[/QUOTE]
I simply mean a launcher that runs the command.  In this case, the command is a game I installed in my ~/bin directory called "lost-labyrinth".  My desktop launcher simply has "lost-labyrinth" as the command (without the full PATH).

---

### Post by pilaftank on 2005-12-19
But the launcher won't know to look in the **~/bin** directory because **~/.bashrc** has not yet run (and therefore **~/bin** is not in the PATH).

---

### Post by khc on 2005-12-20
~/.gnomerc if you use GNOME.

---

### Post by pilaftank on 2005-12-20
[QUOTE=khc]~/.gnomerc if you use GNOME.[/QUOTE]

That's it!  I just tested it, and it works.  Finally!  Thanks.

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=pilaftank]But the launcher won't know to look in the **~/bin** directory because **~/.bashrc** has not yet run (and therefore **~/bin** is not in the PATH).[/QUOTE]
I looked into this and it seems the executable being called by my launcher was a bash script, so I guess that explains why the ~/.bashrc was being sourced.

---

