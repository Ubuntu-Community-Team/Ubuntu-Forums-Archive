---
title: "GDM loops, cannot login as user"
date: 2005-05-05
forum: Desktop Environments
---

### Post by TaNeK on 2005-05-05
Hi.

A few hours ago, everything was working smoothly, now nothing is working properly, and GDM is in charge of this rebellion against me.

1. GDM won't load. I get the "working" mouse pointer, and the screen flashes, like when it loads the gdm-graphics, but it restarts GDM instead, and continues in a never ending loop.

2. I've tried KDM and XDM, and neither will let me login as user. They just restart when i try it. XDM, however lets me login as root.

So, here I am. No possibillity to login as user, and stuck with XDM or console login.

---

### Post by Ubiquitous on 2005-05-05
I've gotten myself in the same situation.  Have tried both kdm and gdm and same thing as you described, with no knowledge of how I got myself here.

Here's what I'm observing (does this sound at all familiar?):

1) When in either kdm or gdm I can enter username and password (with gnome or kde selected) and the screen blanks, I see the default background for kde with some garbage at the top, and then when I move the mouse or let it go for 4-5 seconds it dumps me back to the login menu

2) In kdm I can select console login, get the console, login, and use startx to launch gnome.  I cannot, however run startkde from the console as I get all kinds of "Cannot connect to display errors."  If I do launch gnome, however, I can launch a terminal, run startkde, and the kde desktop runs within gnome.

3) looking in ~/.xsession-errors I see a lot of this:
xset:  unable to open display ":0"
Xlib: connection to ":0.0" refused by server
Xlib: Protocol not supported by server

So I know kde will launch within gnome, so it isn't completely corrupted.  Seems to be a configuration issue.  Right before this seemed to go bad I installed a bunch of things with synaptic.  Here's the list:

atlantik (4:3.4.0-0ubuntu2)
atlantikdesigner (4:3.4.0-0ubuntu2)
festival (1.4.3-16)
festlex-cmu (1.4.0-6)
festlex-poslex (1.4.0-5)
festvox-kallpc16k (1.4.0-5)
kaddressbook-plugins (4:3.4.0-0ubuntu2)
kate-plugins (4:3.4.0-0ubuntu2)
kdeaddons (4:3.4.0-0ubuntu2)
kdeaddons-kfile-plugins (4:3.4.0-0ubuntu2)
kdeartwork-misc (4:3.4.0-0ubuntu1)
kdessh (4:3.4.0-0ubuntu2)
kdewebdev (4:3.4.0-0ubuntu2.1)
kfilereplace (4:3.4.0-0ubuntu2.1)
kicker-applets (4:3.4.0-0ubuntu2)
kimagemapeditor (4:3.4.0-0ubuntu2.1)
klinkstatus (4:3.4.0-0ubuntu2.1)
knewsticker-scripts (4:3.4.0-0ubuntu2)
kommander (4:3.4.0-0ubuntu2.1)
konq-speaker (0.4-kde3.1-7)
ksig (4:3.4.0-0ubuntu2)
kxsldbg (4:3.4.0-0ubuntu2.1)
libdb4.2++ (4.2.52-17ubuntu1)
libestools1.2c102 (1:1.2.3-8)
libfinance-quote-perl (1.08-1)
libhtml-tableextract-perl (1.08-1)
libhtml-tree-perl (3.18-1)
libio-stringy-perl (2.109-3)
libkdegames1 (4:3.4.0-0ubuntu2)
libmailtools-perl (1.62-1)
libmime-perl (5.415-1)
libnews-nntpclient-perl (0.37-5)
libtimedate-perl (1.1600-4)
libwww-perl (5.803-3)
noatun (4:3.4.0-0ubuntu3)
noatun-plugins (4:3.4.0-0ubuntu2)
openssh-server (1:3.9p1-1ubuntu2)
quanta (4:3.4.0-0ubuntu2.1)
quanta-data (4:3.4.0-0ubuntu2.1)
ssh (1:3.9p1-1ubuntu2)

---

### Post by TaNeK on 2005-05-05
I never got into gnome, startx gave me a grey screen. But almost the same. I've reinstalled my system again, and it's solved. But knowing what was wrong could be nice anyway...

---

### Post by Professor X on 2005-05-06
If this happens again, you might want to check your X log file (/var/log/Xorg.0.log) for clues.  Log files are usually pretty detailed and have helped debug problems for me.  Also, always be careful when making even minor changes to config files.

---

### Post by Ubiquitous on 2005-05-08
Yea, I've looked at /var/log/Xorg.0.log for clues and found nothing that has helped me find the problem.  It smacks of a configuration error, but can't for the life of me figure out what is going on.  

Unfortunately I will have probably have to reinstall to resolve this as well.  Been searching around the web and haven't found any good clues yet.

---

### Post by alastair on 2005-05-08
It might just be a desktop/session problem. Try logging in via GDM then, on failure, switch to a VT (CTRL+ALT+F1), login and look at the ~/..xsession-errors file. Perhaps a clue in there.

---

### Post by raphaelb on 2005-09-27
Hey guys, I had the same problem on my Squashed/Unionfs'd install.
I found I could fix it by following these steps:
as root:
chmod a+w /tmp
cd /dev
MAKEDEV generic
/etc/init.d/xserver-xorg restart
/etc/init.d/x11-common restart
killall gdm
/etc/init.d/gdm start

Seems GDM trys to lock something in /tmp but doesn't have write permission to do so....?
MAKEDEV may or may not be required.
Hope this helps.

---

