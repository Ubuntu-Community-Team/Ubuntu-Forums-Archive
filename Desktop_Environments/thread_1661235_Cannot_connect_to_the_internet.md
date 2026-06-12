---
title: "Cannot connect to the internet"
date: 2011-01-06
forum: Desktop Environments
---

### Post by Cerapter on 2011-01-06
I've installed the kubuntu desktop environment over a ubuntu 10.04 installation. When I installed kubuntu, there was no desktop environment at all, due to a mistake of mine. However, the only internet connection that ever worked with kubuntu, was the wired connection I used to install the kubuntu desktop environment (via xterm). I no longer have access to that connection, and now neither wireless nor wired connections are noticed by kubuntu.

I would like to revert to the GNOME desktop enviroment, but I think I will have to do it without an internet connection. As I am still new to this, is there a way I can put the package on a USB stick and get it from there in kubuntu?

---

### Post by fagulhaspt on 2011-01-06
> **Cerapter said:**
> ...

I would like to revert to the GNOME desktop enviroment, but I think I will have to do it without an internet connection. 

You have ubuntu (which comes with the Gnome desktop-environment)
And you installed kubuntu, which in effect installed the Kde desktop-environment and a bunch of programs for Kde.

Now you have both Gnome and Kde in your computer, and you can use one or another :)
Probably by default your computer will enter in one of them, I guess that it enters Kde (from what you tell). 

So to go "out" from Kde and "start" with Gnome, it should be very easy:

  - in Kde, click the Kde-button in the lower-left-corner (it will appear a menu) 
  - then click the "Leave" button (a red square button in lower-right of the menu)
  - then click "Logout/End Session" button

And with this, it will logout from Kde. 

Now a login screen will appear. Before filling in your username and password, you have to find a options-button where it is possible to select the Desktop Environment that you want to use. Select the Gnome desktop, and after, fill in your username/password. It will then enter the Gnome desktop :)

For more information about how to make the Gnome desktop environment the default for every time you turn your computer on (instead of Kde), search in google information about "kdm" or "gdm" which are programs which launch Kde or Gnome at startup.

Hope it helps, please report back your advances so I know how it went, and others can learn from it :)

---

### Post by Cerapter on 2011-01-06
Thank you for the quick reply! I wish I could have done it that simple, but for some reason, none of the past environments I have installed have lingered. I have KDE, xterm, XBMC and three "guest-restricted" that do not work. Plus, of course, Default. Now, for all I know, I might still have all of the environments, only they are not visible. On the other hand, I do not know if there ever was enough disk capacity for this. Perhaps that is the reason why I do not have them all now.

Still, the problem is now more or less fixed. I managed to get wired access again through the command:

sudo dhclient eth0

Which I found by searching around a bit. I will now proceed to remove the KDE environment and revert back to GNOME, using the instructions I found [here]("http://www.psychocats.net/ubuntu/puregnomelucid"). :)

---

### Post by Cerapter on 2011-01-06
Sorry for double-posting, but I've found that the problem it not yet at its conclusion!

I cannot get packages. When I try to install or remove anything from the command line, I get this:

> 
(...)
Err [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) lucid/universe libmicrohttpd5 0.4.4-1
  Could not connect to no.archive.ubuntu.com:80 (129.241.93.37). - connect (111: Connection refused)
Failed to fetch [http://no.archive.ubuntu.com/ubuntu/pool/universe/libm/libmicrohttpd/libmicrohttpd5_0.4.4-1_amd64.deb](http://no.archive.ubuntu.com/ubuntu/pool/universe/libm/libmicrohttpd/libmicrohttpd5_0.4.4-1_amd64.deb)  Could not connect to no.archive.ubuntu.com:80 (129.241.93.37). - connect (111: Connection refused)
When I try though the Software Center, I get 

> Package dependencies cannot be resolved.

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.When I close Firefox and open it again, it's in Offline mode. It seems like the computer doesn't really know it's got an internet connection now.

EDIT: I'm trying a different mirror, I think it might work better...

---

### Post by Cerapter on 2011-01-10
Solved.

I didn't know I could right-click the networking icon. It gave me an option to enable networking.

Somehow, this was disabled without me ever knowing about it. It didn't go away when I installed gnome, but it did when I right-clicked. As such, it was not a desktop environment related problem, but a network related problem.

Also, changing the mirror enabled me to connect to the server.

---

