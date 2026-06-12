---
title: "Easy way to switch from Ubuntu to Xubuntu?"
date: 2010-07-03
forum: Desktop Environments
---

### Post by mathiasdk on 2010-07-03
Hi

Is there a possible way to switch from Ubuntu 10.4 to newest Xubuntu without re-installing the whole system?

---

### Post by aphatak on 2010-07-03
Yes, there is - all you need to do is install the package 'xubuntu-desktop'.  You can do it from the command line ('sudo apt-get install xubuntu-desktop'), or from Synaptic (see screenshot).  


The package manager will download a large number of files, and then install the desktop.  You can use the new desktop in one of two ways -

1) The simple way - log out from your session.  When you see the log-in screen, you will get a drop-down (well, it really drops UP!) from which you can select Gnome/Ubuntu or Xfce/Xubuntu environment.  You get to use one environment at a time.  I assume you want to start this way.

2) The complex way - you can start a new session by logging in again.  This one is tricky, but you can switch between Gnome- and Xfce environments at will.  If you want the complex way (and the power that goes with it), let me know and I will post detailed steps.

Let me know if it helps.

---

### Post by SlickRick on 2010-07-03
i would quite like to know the complex way. Is it anything to do with using tty. If yes then plz tell me how to get another X session going with it.

---

### Post by aphatak on 2010-07-03
Basically, you start a separate session for each desktop.  One way would be -
1) From the log-in screen, select the xfce session (Xubuntu desktop).
2) Once you are in the Xubuntu graphical environment, press ctl-alt-F2.  This will take you to a character console.
3) Log in with your ID and password.  You can use the same ID as the xfce session, or a different ID.
4) Start a new X-session with the command 'xinit -- :1 vt8' (note that there is a space between -- and :1).  the '--' tells xinit that you are not supplying any options, ':1' tells it to number the session as 1 (session numbers begin with 0), and 'vt8' tells it to associate the new session with virtual terminal 8, which corresponds to the ctl-alt-F8 key combination.  You should see another command line screen, this time managed by X.
5) Enter the command 'gnome-session'.  You should see a full red-blooded, green-eyed Gnome desktop, in all its resplendent glory.

You are done.  To go to the Xubuntu desktop, press ctl-alt-F7, to go to the Gnome desktop, press ctl-alt-F8.  You can start up to 4 more X-sessions - in place of ctl-alt-F2, use ctl-alt-(F3 to F6), in place of ':1', use ':2' to ':5', in place of vt8, use vt9 to vt12, and in place of ctl-alt-f8, use ctl-alt-(F9 to F12).  Now you are limited only by your imagination - different desktops, different user IDs, you name it.

Let me know if this works for you.

---

### Post by aphatak on 2010-07-03
One more possibly useful nugget of information - if you want to start desktops other than Gnome, the corresponding commands are 'startxfce4' for Xubuntu desktop, 'startkde' for Kubuntu desktop and so on.

---

### Post by mathiasdk on 2010-07-03
Easy version worked for me :)
Thanks so much!

Have a great weekend.

---

### Post by danielgrosvenor on 2010-07-03
Oh, and for future reference: *sudo apt-get purge xubuntu-desktop* should remove it cleanly should you decide to get rid of it.  :) (Failing that, use PureGnome: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome))  I've just had to do this with Kubuntu.

---

