---
title: "odd problem with beryl"
date: 2006-12-14
forum: Desktop Environments
---

### Post by thelinux_guy on 2006-12-14
I successfully installed beryl and was happy with the results,it looked sooooooo good on my desktop,then a couple days later,I was in Emerald theme manager configuring my title-bars when I logged out,logged back in,and went to the Beryl settings manager,it froze,then it un-froze,but was half-functional,then my desktop slowly  died (I had to reboot into a recovery CD to delete the Beryl files to make sure that it would not start next time i logged in)then i booted back into Ubuntu and logged it,beryl wasn't running,which was good at the moment,I went to synaptic to uninstall beryl and re-install it,it installed and when i typed in a root terminal "beryl-manager",it started and had no problems what-so-ever,then i found out that you could have it ran automaticlly when you log in. that sounded good to me so i went to "sessions" in Gnome,and typed beryl-manager as a startup program,logged out,and then logged back in,but then it was back,Beryl was half functional as it was,and crashed my desktop,making me have to use the recovery CD once again,My desktop is back to normal,and im using beryl,but running it from terminal,not automatically

What I want to know is how to completely remove beryl and its configuration files (so there is no trace left on my PC) Any help would be appreciated,I posted this in the Beryl forums,but got no reply...

---

### Post by thelinux_guy on 2006-12-15
anyone?

---

### Post by d3v1ant_0n3 on 2006-12-15
sudo aptitude purge <package name> will completely remove a program and it's config files.

For Beryl, the packages are:

beryl
beryl-core
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-settings
emerald

I'm not quite sure what you meant with 'half-functional' - is it just slow? Or are certan plugins causing you problems? I find using water and blurfx plugins gives me all sorts of issues and slow down.

---

### Post by thelinux_guy on 2006-12-15
> **d3v1ant_0n3 said:**
> sudo aptitude purge <package name> will completely remove a program and it's config files.

For Beryl, the packages are:

beryl
beryl-core
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-settings
emerald

I'm not quite sure what you meant with 'half-functional' - is it just slow? Or are certan plugins causing you problems? I find using water and blurfx plugins gives me all sorts of issues and slow down.

thank you so much,ill try this imedeantly ,and what I mean by "half-functional" is that the program is non-responsive,but is not frozen like what can happen with apps in windows, this means it  would effect my desktop as well,meaning I could only move the mouse courser ,and not start apps,delete stuff,or even logout or shutdown the computer

thanks for the help!

---

### Post by thelinux_guy on 2006-12-15
ok,I fixed the problem,beryl is running properly,and even better that before,for all the people who have this same problem,do this:
   
            Go to beryl settings manager,look for the 'screenshot' plugin. DISABLE IT! its very unstable,has memory leaks,and can cause your desktop to crash

            If you cant get to the settings manager,go to synaptic (system-administration-synaptic package manager) and uninstall beryl,as well as all of its componates.after that,go to settings,look for the files tab,click "clear cache",then restart your PC,after that,you should be fine,if the problem persist once you re-install beryl,set metacity as your windows manager,then go to beryl settings manager,go to screenshot plugin and disable it,then you should be fine...



-jason

---

### Post by DJ-Power on 2006-12-20
Thanks for the tip I was having the exact same problem.
Regards
DJP :)

---

### Post by broughcut on 2006-12-30
this just happened to me...

I'm having odd sound probs since Edgy upgrade and used Synaptic to remove all packages with "alsa" in the title in order to do a reinstall (which hasn't helped the sound issues). Well, this wasn't very sensible... perhaps I stupidly deleted something used by X as when I rebooted there was no graphical desktop. 

But I had to reboot because I was trying to do a screen capture with Beryl while Synaptic worked in the bg and the desktop became totally unresponsive.

I reinstalled the alsa packages I had removed but it still wouldn't boot into the graphical desktop--so I'm going to blame this one on Beryl!

Fixed using:
> 
sudo aptitude update && sudo aptitude install ubuntu-desktop

--my thanks to aysiu, found that in a recent "X won't start" thread.

I noticed several hacked-up screencaps on the desktop. Restarted Beryl, and it started screen capping again at random and the desktop froze up. Unless there is a terminal open to kill X with "/etc/init.d/gdm stop" you're stuck as menus and windows don't respond.

Removing Beryl and reinstalling doesn't fix the problem, which is how I found this thread. Time to purge the config files and try again. 8)

---

### Post by broughcut on 2006-12-30
removing linux-sound-base will also remove ubuntu-desktop, so that's what happened there...

But the desktop freezing up was down to Beryl. I've not had any probs since I reinstalled and disabled the screencap feature..

---

