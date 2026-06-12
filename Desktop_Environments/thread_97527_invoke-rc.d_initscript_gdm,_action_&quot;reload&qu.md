---
title: "invoke-rc.d: initscript gdm, action &quot;reload&quot; failed."
date: 2005-12-01
forum: Desktop Environments
---

### Post by veloct on 2005-12-01
I've noticed this has been posted several times with no answer.  Here's what happened.

I got home and since KDE 3.5 was released I manually changed my /etc/apt/sources.list and included the source line from the Kubuntu site. I did the usual:

*sudo apt-get update*
*sudo apt-get upgrade* (it upgraded a couple of packages)
*sudo apt-get install kubuntu-desktop*

When asked which display manager to use I figured why not try KDM, so I chose it. I log out of Gnome/Ubuntu back to the login screen.  I Start KDE (I select 'just for this session') and it's running fine so I log out.  I try to log into GNOME and it shows me the splash screen and it hangs,  I reboot.  Same thing.  I open a failsafe terminal and start synaptic and remove all of kubuntu (including config files) and reinstall gdm for good measure.  I start and login into Gnome and nothing, it hangs.  I drop down to a terminal and make sure to purge kdm if it wasn't, it was all gone.  I type the following: 'sudo dpkg-reconfigure gdm' and I get the following error after it tells me is ok.

**invoke-rc.d: initscript gdm, action "reload" failed.**

I tried removing it and installing xdm and i can only get to a terminal, gnome will not start even in recovery mode.  I tried with KDM also and gnome will not start.  I even tried reinstalling gdm and nothing, I still get the same thing.

**invoke-rc.d: initscript gdm, action "reload" failed.**

Can anybody help?  I am assuming it's a gdm problem because I can get to a login screen without issue so I know X is working and if I go to terminal I can start any program I have installed. 

I tried to install xubuntu-desktop and it starts but once I try to go to settings all the panels disappear and it locks up.  I'm at the end of what I can think off and I don't want to reinstall after all the work I've put into getting my desktop working how I like it.

---

### Post by veloct on 2005-12-01
<bump>

---

### Post by chandru on 2005-12-01
I am having the same problems as well.

gdm crashes as soon as the mouse cursor appears. The X server seems ok as I can run kde or twm.

All gtk application seem to segfault when started from the console. The errror messages don't seem to be consistent for the applications.

gnome terminal crashes with gtk_accel_label_set_accel_closure:assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL` failed

rhythmbox crases with couldn't connect to session bus: unable to determine the address of the message bus.

So for now I seem to be stuck with kde, which is a problem because most of my email is in evolution.

---

### Post by veloct on 2005-12-01
I am going to try a few things tonite when I get home but if that doesn't work then I'll install kubuntu and I guess I'll be stuck with it.  I haven't been able to find anyone that's knows anything about this.  It's very frustrating.

---

### Post by veloct on 2005-12-01
<bump>

---

### Post by almahtar on 2006-02-06
I'm getting some of these problems too.  GDM loaded fine, but when I go to log into Gnome it gives me the "your session ended in less than 10 seconds, you likely have an installation problem, try the failsafe session" type message.  It then tries to return to GDM but the box hangs: blank screen, no response to keyboard or mouse, no hard disk activity.  The caps lock light doesn't even work.

So I powered down, and after many many different things I tried rm -r .gconf .gconf2 .gnome* (I miss my old settings!), and now I can get into Gnome, but if I log out and it tries to go back to GDM it hangs the same way as before.

So I switched to KDM.  KDM will get me into gnome or KDE just fine, but when I log out of gnome the system hangs still, and when I log out of KDE it boots me to the terminal.

I tried dpkg-reconfigure gdm, and got the same "invoke-rc.d: initscript gdm, action "reload" failed." message.

I am seriously bummed.

---

### Post by gosh on 2006-09-21
Anyone of you solved this already?
I have the same problem.

---

### Post by Predatornica on 2007-09-03
I've had the same problem.
I've run invoke-rc.d gdm -force-reload  (I don't remember exactly - I think smth. like that). 
There were written that invoke-rc.d failed, but when after that I ran dpkg-reconfigure gdm I had gdm selected instead of kde. So, I've rebooted. 
Now everything is ok.

---

