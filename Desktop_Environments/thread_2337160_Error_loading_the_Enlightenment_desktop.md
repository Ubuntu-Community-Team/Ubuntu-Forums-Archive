---
title: "Error loading the Enlightenment desktop"
date: 2016-09-15
forum: Desktop Environments
---

### Post by MOGuy78 on 2016-09-15
Hi everyone!  I have been trying out different GUI's that are lighter than the regular Gnome and KDE desktop environments.  I was trying out one called
Enlightenment, but I've been having errors trying to load it.  Here's a summary of what's going on.


The first thing I did was install X.org to be able to use a basic GUI environment, which installed with no problem.

> sudo apt-get install xorg

I then followed the installation method described in the official website of the Enlightenment window manager:
[https://www.enlightenment.org/distros/ubuntu-start](https://www.enlightenment.org/distros/ubuntu-start)

and I tried to use the latest stable version.

> sudo add-apt-repository pp:niko2040/e19
> sudo apt-get update
> sudo apt-get install enlightenment
> sudo apt-get install terminology

Both of the needed files seemed to install correctly as well.

My problems seemed to start when I tried to load the GUI itself.  First I tried to start it simply by typing in the name of the GUI,
> enlightenment

but received the following message:

[ATTACH=CONFIG]271188[/ATTACH]

I then tried to follow the instructions given on the screen and typed:
> enlightenment_start

but then received the error:

[ATTACH=CONFIG]271189[/ATTACH]


After both of these options failed, I tried to just use the 'startx' command, where hopefully the window manager would start up automatically after the
x-session loaded, as some of the others I had tried out had, but all that loaded was the base graphical environment without loading the installed
window manager.

[ATTACH=CONFIG]271190[/ATTACH]


Can anyone tell me what I'm doing wrong, and if I may have missed a step?  What can I do to correct it?  Thanks!

---

### Post by ajgreeny on 2016-09-15
How did you install the base Ubuntu system on which you have added enlightenment, and what version is it?

You use a new DE such as enlightenment not by running commands like you have but by choosing it from the login window of whatever display-manager you have, (eg lightdm, gdm, etc etc.), so logout from wherever you are now, and at the login window look for the cog icon (usually a cog) and if you click on that you may find an entry for enlightenment.  If you don't get a login screen you may need to install one.

I have only ever used that enlightenment on a test install of Bodhi Linux and did not like the way it worked, even though it was very lightweight, so I have no idea how it will present itself in the login window of an ubuntu system.

---

### Post by Frogs Hair on 2016-09-15
You have to select the enlightenment session from the login screen. Click the icon on the top right of the box where you enter the password.

---

### Post by MOGuy78 on 2016-09-16
Thanks for the reply.  I am running an Ubuntu Server 14.04, so it did not come with a GUI installed.  I set it up to use as a media server, and although I have a fairly good understanding of the CLI, I'm trying to find a lightweight gui to use for certain apps; namely for changing system settings and other system-wide needs.  I'm trying out different lightweight distros to see which one I'm most comfortable with, as well as best suits my needs.
I had looked at the Bodhi Linux version of Enlightenment, as well as puppy linux, but they are complete desktop versions.  I'll only be using the GUI for certain things, the rest of the time just using the CLI.

As of right now, since I'm trying out different ones and not sure which GUI I'll end up using, I'm only installing them using Virtualbox.

---

### Post by Frogs Hair on 2016-09-16
I've only run Enlightenment as a second desktop from PPA . There is a script for building E19 and a link for 22 here on the forum though I haven't used it. [https://ubuntuforums.org/showthread.php?t=2203190&page=4](https://ubuntuforums.org/showthread.php?t=2203190&page=4)

---

### Post by MOGuy78 on 2016-09-20
I think I'm just going to go with Lxde.  More people are using it, so I can find a lot more information online about it.  It also worked just fine right after I installed it from the CLI.  Thanks for helping with my questions about Enlightenment.

---

