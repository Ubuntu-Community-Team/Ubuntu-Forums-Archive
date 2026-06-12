---
title: "Remote desktop FROM windows. Possible?"
date: 2006-05-24
forum: Desktop Environments
---

### Post by motionsiren on 2006-05-24
I use a windows notebook and would *love* to remote desktop into my ubuntu desktop machine. is there any quick way to acheive this? i see that it's pretty straight forward when it's linux to linux, er well X to X as it's all setup for that, but it'd really be valuable to be able to get to my gnome desktop.

thx.

---

### Post by aysiu on 2006-05-24
Go to System > Preferences > Remote Desktop

Allow viewing and control, require a password but no approval.

Then go to Applications > Accessories > Terminal and type ```
ifconfig
``` Find out what your IP address is and then go to Windows and launch TightVNC Viewer (Best Compression) and type in your IP address and password.

---

### Post by motionsiren on 2006-05-24
thank you very much, exactly what i was hoping. although, what service on the ubuntu box needs to run in order to connect?

---

### Post by aysiu on 2006-05-24
[QUOTE=motionsiren]thank you very much, exactly what i was hoping. although, what service on the ubuntu box needs to run in order to connect?[/QUOTE] It's the Remote Desktop application. The actual process is called *vino-server*, but you don't need to know that to get it to work.

---

### Post by gumbald on 2006-05-24
You need to be logged in on the Ubuntu machine... I've found FreeNX to be more useful :) and quicker. I only now use VNC when I'm on my LAN, as I'm normally logged in. VNC is much slower over the internet...

Does that make sense?

---

### Post by jones_jj on 2006-05-25
> Go to System > Preferences > Remote Desktop

Allow viewing and control, require a password but no approval.

Then go to Applications > Accessories > Terminal and type
Code:

ifconfig

Find out what your IP address is and then go to Windows and launch TightVNC Viewer (Best Compression) and type in your IP address and password.

In order to get this working do you need to have a VNC server installed and running on Ubuntu?  Also couldn't you just use Remote Desktop/Terminal Services Client from Windows to connect back to Ubuntu?

---

### Post by aysiu on 2006-05-25
[QUOTE=jones_jj]In order to get this working do you need to have a VNC server installed and running on Ubuntu?[/quote] When you go to System > Preferences > Remote Desktop and check the option to share your desktop, you're turnining on the VNC server in Ubuntu.  > Also couldn't you just use Remote Desktop/Terminal Services Client from Windows to connect back to Ubuntu? I don't know. I guess. I've had good luck using TightVNC to connect, but there are probably several viable options.

---

### Post by gumbald on 2006-05-25
RDP is a Windows thing, equivalent of FreeNX emulating the X Window System. You can only use RDP *into* a compatible Windows host, XP Pro and 2003 Server I think.

---

### Post by harisund on 2006-05-25
You do have a couple of options.

To begin with, RDP is a Windows only protocol. Not compatible with Unices. So you can't use the terminal services client to login to a Linux machine. 

Next, VNC is a good idea. You will have to enable VNC on your machine by the method Aysiu mentioned earlier in the thread. VNC is not extremely fast though, and you will have to leave your Linux machine logged in first. 

The other option you have is X forwarding through SSH. While you might not be able to get your Gnome desktop per se, you can still run the GUI applications. For this though  you will need X/Cygwin installed. You can try out a live X/Cygwin version developed by Indiana university. This is my preferred method, because I don't really want my entire Gnome desktop, but only the apps. 

That apart, there is also XDMCP which is not quite secure, but would require X/Cygwin on your Windows machine again.

---

### Post by jones_jj on 2006-05-25
[QUOTE=aysiu]When you go to System > Preferences > Remote Desktop and check the option to share your desktop, you're turnining on the VNC server in Ubuntu.   I don't know. I guess. I've had good luck using TightVNC to connect, but there are probably several viable options.[/QUOTE]

So you do have to install the VNC server through Synaptec or apt-get?  I do not have a VNC server running at all on my Ubuntu server so when I go to ** System -> Preferences ** there is no Remote Desktop in the menu at all.

---

### Post by aysiu on 2006-05-25
[QUOTE=jones_jj]So you do have to install the VNC server through Synaptec or apt-get?  I do not have a VNC server running at all on my Ubuntu server so when I go to ** System -> Preferences ** there is no Remote Desktop in the menu at all.[/QUOTE] It's supposed to be in the default Ubuntu installation. You shouldn't have to install something separately to have that in your preferences. You are using Gnome, right?

Check it out:
[http://packages.ubuntu.com/breezy/base/ubuntu-desktop](http://packages.ubuntu.com/breezy/base/ubuntu-desktop)

The regular *ubuntu-desktop* (default metapackage) for Breezy includes *vino*.

---

### Post by AndyOB on 2006-05-26
on a similar topic, I am trying to find out if it is possible to login via VNC (I use tight VNC and default remote desktop settings in Ubuntu).

i.e. If I'm not logged in locally and my machine shows the login page, can i remotely connect with VNC by tweaking settings somewhere!?

---

### Post by ElijahLofgren on 2006-05-26
[QUOTE=motionsiren]I use a windows notebook and would *love* to remote desktop into my ubuntu desktop machine. is there any quick way to acheive this? i see that it's pretty straight forward when it's linux to linux, er well X to X as it's all setup for that, but it'd really be valuable to be able to get to my gnome desktop.
thx.[/QUOTE]
The absolute best way that I have found is to use FreeNX (it's FAST!). I followed this tutorial today:
[Installing FreeNX server on Kubuntu Dapper Drake Flight 6](http://www.ubuntuforums.org/showthread.php?p=917050#post917050)
After setting it up, I was able to login to my Ubuntu Dapper Drake box from a Windows 98 PC. :D

---

### Post by Lord Illidan on 2006-05-26
I just tried out VNC. Very nice. A little slow though...but very easy to do.

---

