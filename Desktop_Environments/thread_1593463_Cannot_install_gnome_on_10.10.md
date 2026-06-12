---
title: "Cannot install gnome on 10.10"
date: 2010-10-11
forum: Desktop Environments
---

### Post by neeemtom on 2010-10-11
Hi,

I have an old Ubuntu instance, if I remember egzactly it was originally Ubuntu 08 10, I always upgraded it, now it is 10 10. I have a problem, the gnome damaged when I upgraded  to 9 10 from 09 04.
Finally I removed gnome and tried to reinstall it, I tried it several times on  9 10, 10 4 and now on 10 10 too.
I started synaptic, marked package gnome to install as any other package.

Installing gnome:
gnome:
 Depends: epiphany-extensions but it is not going to be installed

Ok, no problem, let's install it first
installing epiphany-extensions:
it removes swfdec-mozilla
it is done, after it I tried to install gnome again

gnome:
 Depends: swfdec-mozilla but it is not going to be installed

Than I install swfdec-mozilla, it removes epiphany-browser and eiphany_extensions, the circle is full.

How can I solve this problem?

Help me please guys! 

SzG

---

### Post by ankspo71 on 2010-10-11
Hi,
Here is what I see when I run the command **sudo apt-get install -s gnome**
> sudo apt-get install -s gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages

It shows there is a dependency problem while installing the "gnome" desktop in Ubuntu 10.10 at this time. You can try opening Synaptic Package Manager, then go to the menu -> Edit > Fix Broken Packages. This might help fix any problems with the dependencies. It didn't fix it for me though. Like you said, swfdec-mozilla can be installed, but swfdec-mozilla (or the dependencies that swfdec-mozilla uses) is probably the wrong versions and the correct versions that "gnome" and "Epiphany" needs are not available right now.

However, right now I can install the "ubuntu-desktop" package in Ubuntu/Kubuntu 10.10 without problems. ubuntu-desktop is the gnome desktop, but it includes Ubuntu's improvements, Ubuntu's preferred packages, Ubuntu's own packages (Ubuntu one, Ubuntu Music Store, Ubuntu Software Center, etc), and Ubuntu's artwork. So try installing "ubuntu-desktop" in Synaptic Package Manager. If it is already installed, mark it for to be reinstalled and click apply. 

Or you can wait a few days to see if the gnome package can be installed at a later time.

Hope this helps.

---

### Post by neeemtom on 2010-10-11
Hi,

First of all thanks for your fast answer!
The package "ubuntu-desktop" is already installled, I tried to reinstall it, but it didint helped me. I installed ubunto netbook too, it is now on, buty seems broken too, I guess it is an modified gnome. The effect is similar, I can choose gnome desktop or netbook at gdm login, it seems starting, but not gnome starts, it is like an e16 based gnome like something.

SzG

---

### Post by ankspo71 on 2010-10-11
Hi,
Can you post a screenshot of what you see when you try logging into Gnome?

Do you have e-16 or openbox or any other desktops installed? 

Do you get a Gnome desktop, but the window borders look like e16 or openbox? This could be because Gnome is starting as gnome-openbox-session or e16-gnome-session. Try using this command in the terminal to temporarily fix the window borders to see if it helps.
```
metacity --replace
```  

Do you get a Gnome desktop but it has no themes applied? This could be because gnome-settings-daemon is failing to start with Gnome. I saw a fix for this about a month ago, I'll see if I can find it. But to see if this is the problem you can open a terminal and use this command to see if it will temporarily fix it
```
gnome-settings-daemon
```

If all you see is a e16 desktop or something similar, then there could be an error in your Gnome sessions choices.

---

### Post by neeemtom on 2010-10-11
Hi,

Something like You mentioned, picture here: [http://bit.ly/b8W6sP](http://bit.ly/b8W6sP)
I tried what You said:


szg@ubuntu:~$ sudo metacity --replace
Window manager warning: Screen 0 on display ":0.0" already has a window manager
szg@ubuntu:~$ sudo gnome-settings-daemon

** (gnome-settings-daemon:14586): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:14586): WARNING **: Could not acquire name


Regards,

SzG

---

### Post by ankspo71 on 2010-10-11
Hi Again,
Sorry it took me a while to come back. I originally had ubuntu-desktop and ubuntu-netbook installed, but I wanted to install e16 and openbox to see if I can reproduce the problem you are having. Well, I tried logging into e16, then e16-gnome and then back to Ubuntu Desktop, and now I am having a very similar problem of e16 taking over my gnome desktop like you. I just removed e16 but metacity (the window manager for gnome) does not start anymore. My conclusion is that there is a bug somewhere in here and it must have been overlooked during the 10.10 testing releases, or maybe it is something that is still being worked on.

Do you have a way to backup your important data to a cd or usb drive? If so, then it might be easier to make backups, then download a new copy of Ubuntu 10.04 or 10.10, burn it to a cd, and then install it so that it replaces your existing Ubuntu. I wouldn't recommend installing e16 or other desktops until we know it is safe to do so though. I'm going to try to find a solution to this problem tonight though.

If you don't have a way to backup files for a new install of Ubuntu, I'm going to keep trying to figure out how to get back to a normal Gnome desktop and I will be filing a bug report tonight for sure. I'll reply back here with any news.

---

### Post by ankspo71 on 2010-10-11
Hi again,
Try this:
```
sudo apt-get remove e16
sudo apt-get autoremove
```

Now if you don't have any window borders, try this:
```
sudo update-alternatives --config x-window-manager
```
(choose metacity)

Now restart, or log out and log back in. 

---Part 2---

If you still don't have any window borders for your applications, try this:
```
metacity --replace  
```
(sudo isn't necessary)
Your window borders should appear correctly now.

If that works, go to System > Preferences > Startup Applications and create a new entry for metacity --replace. 
```
Name = Metacity  
Command = metacity --replace
```

Now restart your computer and see if that Startup Application entry works. This will be only a temporary solution.

---Part 3---

IF (only if), you have a problem with indicator-appmenu like I am (it is like a global menu) automatically appearing on your panel of your "Ubuntu Desktop" session, and covering your menus, try this:
```
sudo apt-get remove indicator-appmenu
sudo apt-get autoremove
```

Now restart, or log out and log in and the appmenu problem should be gone. I'll be back in a bit :)

---

### Post by ankspo71 on 2010-10-11
Edited:
Hi,
Here's an update. I restarted my computer 4 times already (now 5 times) and my Ubuntu Desktop returned to its normal desktop every time so far. :P So the above solution works for me.

But of course, now that I removed "indicator-appmenu" my Ubuntu Netbook desktop isn't going to work as it should anymore. I also removed "mutter" to rid myself of the extra window manager thinking that removing it might help the appmenu problem. You don't have to remove these items if they are not causing you any problems.

---

### Post by ankspo71 on 2010-10-12
Hi,
I made a comment at the bug report located here:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/616763](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/616763)

If you decide you want to keep e16 as a desktop, the first poster had a fix to stop Gnome (ubuntu-desktop) from from using e16 as a window manager.
The poster said:
> 
the only way I could find to reverse this was to manually edit a line in ~/.gconf/desktop/gnome/session/required_components/%gconf.xml to read "metacity" instead of "e16".

The same poster also said:
> In fact, this has disabled all my 3D effects like true transparency, so I may have to edit that file again to read "compiz" or something, quite a mess when I have to reverse unwanted changes to my default settings in this manner.

and then the poster said in another comment:
> Just a quick note - the lack of 3D effects were solved simply by going into System > Preferences > Appearance > Visual Effects and turning them back on.

---

### Post by neeemtom on 2010-10-12
Thank You, it helped a lot, metacity --replace was the final solution. I still have problems with compiz, but the gnome already works. After work I will fight for compiz. :-)

---

