---
title: "Avant Window Navigator Moves to Launchpad"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by andrewsomething on 2007-07-31
See this post by AWN's main developer: [http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=539&page=1&isLive=true](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=539&page=1&isLive=true)

AWN has moved from Google Code to Launchpad. Bug reports can now be filed there: [https://launchpad.net/awn/](https://launchpad.net/awn/)

Along with moving to Launchpad, AWN's source code has moved from Subversion to the Bazaar version control system. Here are the new source installation instructions:

Install all of the dependencies:

[INDENT]    sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common[/INDENT]

Install Bazaar, the program with which you will get the source:
[INDENT]
sudo apt-get install [/INDENT]


Get the source:

[INDENT]bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator[/INDENT]


Go to the source directory

[INDENT]cd avant-window-navigator[/INDENT]


Prepare for installation:
[INDENT]
./autogen.sh[/INDENT]


Compile:

[INDENT]make[/INDENT]


Install:

[INDENT]sudo make install[/INDENT]


Now that it is installed, type the following to run it:
[INDENT]
avant-window-navigator &[/INDENT]


Inorder to update your source in the future, enter the following in avant-window-navigator directory:

[INDENT]bzr update
./autogen.sh && make && sudo make install[/INDENT]

---

### Post by FuturePilot on 2007-07-31
Well it is supposed to be packaged in Gutsy so that's nice.

---

### Post by isaacj87 on 2007-08-01
Really?
 
Where did you hear that rumor?

---

### Post by FuturePilot on 2007-08-01
[https://bugs.launchpad.net/ubuntu/+bug/118589]("https://bugs.launchpad.net/ubuntu/+bug/118589")
It's in the Gutsy Wishlist and it's being worked on right now.

---

### Post by skroll on 2007-08-01
I have managed to create a proper deb set for gutsy using the latest svn (as of 19:30 GMT).  I haven't had a chance to test it yet (I compiled it remotely using pdebuild and my shell), but it theoretically should work.  I used reacocard's debian rules that he used to build the packages found in [this thread]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant"), so everything should work properly.

Is anyone willing to give them a shot?

---

### Post by cjules86 on 2007-08-01
I've been trying to install AWN using these steps but when I do the "./autogen.sh" command I get the following error:

```
shift: 364: can't shift that many
```

Im using Ubuntu 7.04 on an AMD64 processor.  Any help is appreciated.

---

### Post by andrewsomething on 2007-08-01
> **cjules86 said:**
> I've been trying to install AWN using these steps but when I do the "./autogen.sh" command I get the following error:

```
shift: 364: can't shift that many
```

Im using Ubuntu 7.04 on an AMD64 processor.  Any help is appreciated.

I forgot a dependency (now added to original post): automake1.9

Do you already have that package?

---

### Post by cjules86 on 2007-08-01
Yeah, that was the problem -- When looking at the output of what I was doing before I did see something about automake 1.9 but I wasn't sure what to do.

Thanks a lot!

---

### Post by walkerk on 2007-08-01
> **skroll said:**
> I have managed to create a proper deb set for gutsy using the latest svn (as of 19:30 GMT).  I haven't had a chance to test it yet (I compiled it remotely using pdebuild and my shell), but it theoretically should work.  I used reacocard's debian rules that he used to build the packages found in [this thread]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant"), so everything should work properly.

Is anyone willing to give them a shot?

I'll do it.. I have Gutsy on a virtualbox..

---

### Post by GumbyX on 2007-08-01
I keep having a problem trying to install AWN this way. BZR download the file fine, but when I try and compile it, I keep getting these errors:

make[3]: *** [install-notification_arealibLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/gumby/avant-window-navigator/applets/notification-area'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/gumby/avant-window-navigator/applets/notification-area'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/gumby/avant-window-navigator/applets'
make: *** [install-recursive] Error 1

Anyone out there think they can help?

Heads up, I am running a 64-bit build of Ubuntu right now. Please dont tell me that is the problem because I have been using the older versions without any problems.

EDIT: seems I was missing some dependency. Went to the project wiki and used the install guide from there and it compiled. Only problem I have now is trying to make a *.deb* file for it using *checkinstall*. Anyone think they can help me out?

---

### Post by Espreon on 2007-08-01
AWN is gonna be in Gutsy? Awesome!

---

### Post by cjules86 on 2007-08-01
Well been messing around with it for a while now and I can't seem to find how to make the bar reflective.  Also can't make the icons seem to be "up" the bar a little bit.  Can anyone offer some advice or shoot me somewhere that I can find out how to do this?

---

### Post by andrewsomething on 2007-08-01
> **GumbyX said:**
> I keep having a problem trying to install AWN this way. BZR download the file fine, but when I try and compile it, I keep getting these errors:

make[3]: *** [install-notification_arealibLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/gumby/avant-window-navigator/applets/notification-area'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/gumby/avant-window-navigator/applets/notification-area'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/gumby/avant-window-navigator/applets'
make: *** [install-recursive] Error 1

Anyone out there think they can help?

Heads up, I am running a 64-bit build of Ubuntu right now. Please dont tell me that is the problem because I have been using the older versions without any problems.

EDIT: seems I was missing some dependency. Went to the project wiki and used the install guide from there and it compiled. Only problem I have now is trying to make a *.deb* file for it using *checkinstall*. Anyone think they can help me out?

I updated to add some more dependencies that I assumed, but I've never used checkinstall at all so I'm not sure about that issue.

---

### Post by andrewsomething on 2007-08-01
> **cjules86 said:**
> Well been messing around with it for a while now and I can't seem to find how to make the bar reflective.  Also can't make the icons seem to be "up" the bar a little bit.  Can anyone offer some advice or shoot me somewhere that I can find out how to do this?

Both those options are not in the GUI yet. You need to go into gConfig apps>avant-window-navigator>bar and change the settings for bar_angle and icon_offset. Try 45 and 15.

---

### Post by GumbyX on 2007-08-01
> **andrewsomething said:**
> I updated to add some more dependencies that I assumed, but I've never used checkinstall at all so I'm not sure about that issue.

No Problem. Thanks for getting back to me. Only thing i have to ask is where can I get some help setting up Affinity? I cannot get tracker OR beagle to work with it. (compiled from SVN from howto I found here ([http://ubuntuforums.org/showthread.php?p=3118471#post3118471](http://ubuntuforums.org/showthread.php?p=3118471#post3118471))) Anywhere I can go?

Edit: I guess it DOES work with tracker from the SVN. I will just get rid of Beagle until support for it exists. Or just stick with Tracker.

---

### Post by cjules86 on 2007-08-01
> **andrewsomething said:**
> Both those options are not in the GUI yet. You need to go into gConfig apps>avant-window-navigator>bar and change the settings for bar_angle and icon_offset. Try 45 and 15.

The bar angle I figured out.  Icon Offset just seemed to make the bar a bit wider not position the icons toward the back of it.  Maybe I'm just crazy though.

What about the reflective surface?

---

### Post by andrewsomething on 2007-08-01
> **cjules86 said:**
> The bar angle I figured out.  Icon Offset just seemed to make the bar a bit wider not position the icons toward the back of it.  Maybe I'm just crazy though.

What about the reflective surface?

Please check that you actually changed the key for icon_offset. That is what moves the icons up on the bar, thus allowing you to see the reflection.

---

### Post by andrewsomething on 2007-08-02
[HOWTO: functional eye-candy with Avant-Window-Navigator and Affinity]("http://ubuntuforums.org/showthread.php?t=385981") has been updated to the new information. There you can also find instruction for frequently updated bzr debs in Reacocard's repo.

---

### Post by cjules86 on 2007-08-02
> **andrewsomething said:**
> Please check that you actually changed the key for icon_offset. That is what moves the icons up on the bar, thus allowing you to see the reflection.

After restarting my comp the changes have taken effect... So I'm guessing all I needed was a restart of Gnome.

---

### Post by happy-and-lost on 2007-09-03
Just a quick note that on Gutsy at least, the following dependencies must also be installed:

*python2.5-dev python-gtk2-dev python-cairo-dev*

:)

---

