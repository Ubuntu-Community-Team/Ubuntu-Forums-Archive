---
title: "EvilWM installation and basic setup"
date: 2007-07-19
forum: Desktop Environments
---

### Post by gunnihinn on 2007-07-19
I just finished installing and setting up EvilWM on my home box. For those who don't know, EvilWM is a minimalist window manager, much like Fluxbox except even more spartan. It's very well suited for older systems which don't have the resources to run Gnome or KDE, or for people who like their desktops uncluttered.

Most of the info I needed came up in various google searches, but I thought it would be nice to have it all in one place in case it could save someone else some trouble.

1. Installing EvilWM
EvilWM is in the Universe repository, so installing it can be as easy as typing
    $  sudo apt-get install evilwm
in a terminal. However the version available is 0.99.21-1 and as of June 2007 version 1.0.0 is out, so I decided to compile the latest version from source.

This isn't as scary as it sounds; the whole process takes about two minutes. First you have to get the source file from 
    $  [http://www.6809.org.uk/evilwm/install.shtml](http://www.6809.org.uk/evilwm/install.shtml)
Now open a terminal and cd to the file. Uncompress it with
    $  tar -xvvzf evilwm-VERSION
and cd to the newly created evilwm-VERSION folder. If you want you can have a look at the Makefile, which has various options you can configure but most are enabled by default. Else type
    $  make
    $  su
    $  make install
to install EvilWM. Note that you'll have to login as root via the su command, make sure to log out again (control-d) as soon as installation is completed.

There, now you've installed EvilWM.

2. Configure GDM
Now we want to configure GDM to show EvilWM as an option for a session on login (I think this is invariant of which xDM manager you're using, but I don't have any other ones installed to check). Go to
       /usr/share/xsessions
type
    $  sudo gedit evilwm.desktop
and paste the following:

       [Desktop Entry]
       Encoding=UTF-8
       # Custom entry.
       Name=EvilWM
       Comment=Evil window manager
       Exec=/usr/bin/evilwm
       Icon=
       Type=Application

then save and exit. Now EvilWM will show up at the login screen along with Gnome and whatever other window managers you've got installed.

Try starting EvilWM by choosing Session > EvilWM at the login screen. Most likely you're now looking at a white screen of nothing; that's the entire window manager. You can open a terminal window by pressing Control + Alt + Enter. Other commands are available, a handy overview is at the EvilWM website
       [http://www.6809.org.uk/evilwm](http://www.6809.org.uk/evilwm)
which you can access by starting Firefox (or the browser of your choice) at your open terminal by typing
    $  firefox & 

3. Startup programs
You'll most likely want a new background instead of the white one. There are tools available for that purpose, but since I've been using Fluxbox for a while I'm using one called fbsetbg. You can set a background by typing
    $  fbsetbg IMAGE
at a terminal, see man fbsetbg for available options. Chances are you don't want to do that every time you log in, so go to your home directory and create a file called ".xprofile" (without quotes), and put the 
       fbsetbg IMAGE
command in it. Whatever is in that file is executed when you log in, so now your background will come up automatically.

As I said I've been using Fluxbox for some time and have gotten quite used to it's customizable shortcut keys. The same effect can be acheived in EvilWM by installing a program called xbindkeys, and defining shortcuts in a file called .xbindkeysrc. The details are documented in its man page, but I reccommend putting a
       xbindkeys
command in the .xprofile file so it'll run automatically on login.

Finally some more information on EvilWM and further configuration is at the [EvilWM website]("http://www.6809.org.uk/evilwm") and the [Gentoo Wiki]("http://gentoo-wiki.com/HOWTO_EvilWM").

I'll finish this with a screenshot of my box running EvilWM with a background I found somewhere, and running Gedit, Pidgin, xmms and a terminal.

[IMG]http://www.hi.is/~gthm1/evilDesktop.jpg[/IMG]

---

