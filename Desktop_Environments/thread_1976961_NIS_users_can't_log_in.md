---
title: "NIS users can't log in"
date: 2012-05-09
forum: Desktop Environments
---

### Post by rbroberts on 2012-05-09
I've been using Fedora for a long time, but this is the first Ubuntu install I've done. I've install 12.04 64-bit and after a bit of trouble getting autofs to play nice with how Fedora does it's NIS maps, I have directories mounting just fine. But I can't figure out how to get the login screen to work for NIS users.

First, there is no place to enter a user name; they seem to come from /etc/passwd only. 

Second, while this link describes my problem pretty clearly ([http://ubuntuforums.org/showthread.php?t=1951849&highlight=nis+login](http://ubuntuforums.org/showthread.php?t=1951849&highlight=nis+login)), I can't log in. And that thread just ends without a resolution.

Last, it's pretty much the same as this thread ([http://ubuntuforums.org/showthread.php?t=1934743&highlight=nis+login](http://ubuntuforums.org/showthread.php?t=1934743&highlight=nis+login)), I can get the user name into the login screen by getting a console and su'ing to the nis user, but I can't log in as the user, neither at the console, nor vis the lightdm login screen.

nsswitch.conf is set to compat for users and groups, and I've added the + entries as the bottom (wasn't necessary with Fedora, but okay). 

This is a show stopper for me. What am I missing in the setup to get NIS users recognized?

---

### Post by rbroberts on 2012-05-10
Okay, progress, sort of. I can log in on the console. I was missing a colon in the + entry in /etc/passwd. I still can't log in via the GUI/lightdm because my user has disappeared from the list after an unsuccessful login attempt.

---

### Post by flip314 on 2012-05-11
I used this tutorial to add the ability to login as an "other" user to the login screen:
[http://www.tejasbarot.com/2012/04/30/howto-other-login-option-on-login-screen-ubuntu-12-04-lts-precise-pangolin/](http://www.tejasbarot.com/2012/04/30/howto-other-login-option-on-login-screen-ubuntu-12-04-lts-precise-pangolin/)

Does NIS come up successfully at boot for you?  I have to do a "sudo restart ypbind" before I can successfully login as a NIS user.

---

### Post by rbroberts on 2012-05-12
I ended up uninstalling network-manager and settting up the interface  manually. There seems to be some ordering issue with the network start  and ypbind. The GUI login screen would take several minutes to launch.  Since this is using NIS and is on a wired network, it's not like I need  network manager.

After doing an apt-get purge network-manager, then setting up the  interface manually, the host boots reliably and the X11 login screen  comes up right away. I ended up switching to use gdm to get the other  screen, although kdm worked fine, too. Thanks for the pointer on  enabling this with lightdm, I might try that now.

My next hurdle is trying to see how stable this is. The host is an ivy  bridge machine, and I've already had several hard lock-ups; X no longer  responds, I can't flip to another console window, and it stops  responding to pings on the network. I've already run MemTest86 and got a  clean bill of health; the whole system is fresh out the box, so this is  discouraging.

---

### Post by flip314 on 2012-05-13
I guess I'll have to take the plunge on uninstalling network manager.  I've heard from others that that seems to be the way to get NIS working at boot.

I haven't had a single crash or issue on this Sandy Bridge box, or my AMD boxes.  I'm running integrated graphics on Sandy Bridge, so the driver for those at least seems to be good.  I had the occasional X windows issue with 11.10 on a couple boxes, but 12.04 seems to be much better so far.

---

### Post by rbroberts on 2012-05-14
I guess I can consider this solved. The moral is:


[LIST=1]
[*]Don't use network manager, configure the interface manually. While it is convenient to have centralized host configuration, it's perfectly reasonable to expect NIS clients to have fixed IP addresses. This is essential to getting ypbind to work during boot and having the X login screen come up quickly.
[*]Edit the lightdm config to allow manually entering the NIS user name.
[/LIST]
The only outstanding issue is getting Gnome 3 to play nice with different per host configurations. The new host is running Ubuntu, but since it's an NIS client, and the old host was running Fedora, the config files are all in the same place, but they are not interchangeable. Bleh.

---

