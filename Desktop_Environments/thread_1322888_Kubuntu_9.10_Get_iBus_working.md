---
title: "Kubuntu 9.10: Get iBus working"
date: 2009-11-11
forum: Desktop Environments
---

### Post by bruno.braga on 2009-11-11
After a while trying to figure out what was wrong with my installation, I finally get it to work properly, and would like to share with others that might be in the same situation (I could not see any post that gave me the answers I needed).

First of all, iBus works great in Ubuntu 9.10, although you still need to do some tweak to get it working (already posted here). For KDE (4.3.1) on Kubuntu 9.10, however, the story is completely different. 

Most common errors are:
- not installed by default
- default repository does not work (starts but can not display the IM options)

The solution was: recompile latest version, plus tweaks (I don't know if just the tweaks would work - someone try this first before getting the source).
[B]
1) Get sources[/B]

Go to: 

```
http://code.google.com/p/ibus/downloads/list
```

and download the latest (and stable) versions available (get ibus, ibus-table and the others you need).
[B]
2) Install dependencies[/B]

It took me a while to get through all the missing packages:

```

sudo apt-get install -y libglib2.0-dev libgtk2.0-dev libdbus-1-dev libgconf2-dev libanthy-dev swig python-dev

```
[B]
3) Compile[/B]

Go to each of the sources (ibus > ibus-table > etc) and type:

```

sudo ./configure
sudo make
sudo make install

```

If you are not lucky to pass through this stage, you may need additional packages (that my machine already has, for instance build-essentials, etc). I am assuming the machine has a minimum of compiling tools (see other threads on this subject for details, i you need)

[B]
4) Tweak 1: ~/.bashrc
[/B]
Append the following to your ~/.bashrc file:

```

export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus 

```
[B]
5) Tweak 2: im-switch[/B]

From the command line, type:

```
im-switch -s ibus
```
[B]
6) Start iBus[/B]

Here you still need to setup the input methods in the list. Go to the try icon:

```

Right Click > Preferences > Input Method > Select Input Method > Add

```
[B]
7) Logout/Login[/B]

I actually rebooted just in case, but the im-switch turns valid after logging out.
[B]
8) Done![/B]

And here (attachment) is how it should look like...

---

### Post by bruno.braga on 2009-11-11
Just forgot. To start the ibus (already posted here), just type:
```

ibus-daemon -d
```

If you still have problems, one way I could toubleshoot the isues was through:

```

ibus-daemon -xrv
```

which will log (verbosely or debug) on screen what's going wrong.

If you did the bashrc tweak, it will be started automatically when you login next time.

---

### Post by Wim van der Meer on 2009-11-17
Thank you for providing this information.

I could install ibus through the repository, so I didn't need to compile it.

However, to make ibus work, instead of .bashrc I had to edit the .profile file.

To make the ibus daemon start at boot, I had to go to System Settings, Advanced tab, Autostart, and add the ibus-daemon program. The command entry in the application tab needs to be changed to: "ibus-daemon -d".

---

### Post by Zorael on 2009-11-17
Nice guide.

If you use im-switch and point it to ibus, it should start the daemon upon boot, though unfortunately the panel applet will start *before* the GTK resource file is loaded. (That's the "theme file" that makes GTK apps look decent in KDE. So the panel will be grey and have weird fonts.)

Using im-switch it should set the correct environment variables to make ibus available in all GTK, Qt and XIM apps.

There's also an ibus-dev launchpad user with Intrepid, Karmic, Jaunty and Lucid ppas, with ibus packages updated regularly-ish, if you don't want to compile your own.

[ppa:ibus-dev/ibus-1.2-karmic](https://launchpad.net/~ibus-dev/+archive/ibus-1.2-karmic?field.series_filter=karmic)
[ppa:japanese-testers/ppa](https://launchpad.net/~japanese-testers/+archive/ppa?field.series_filter=karmic)
[ppa:japaneseteam/ppa](https://launchpad.net/~japaneseteam/+archive/ppa?field.series_filter=karmic)

---

### Post by LK_gandalf_ on 2009-12-30
This guide doesn't seem to work for me :( 
I downloaded the source ibus, ibus-table and ibus-anthy (I need the japanese support).
I compiled them apparently without problem.

But:
1) with the command 
im-switch -s ibus

it says: 
Error: no configuration file "ibus" exists.
Error: No action taken.     
even after a reboot.

If i try to start the daemon, it says:
ibus-daemon -d
ibus-daemon: error while loading shared libraries: libibus.so.1: cannot open shared object file: No such file or directory

Now I'll uninstall the sources and try again with the official packages from the repos. I see that they are updated to the last version. Why they should not work?

I tried every possible guide and it still doesn't work :( what a mess. I use kubuntu 9.10 64bit.

---

### Post by KageTora on 2010-01-01
I've got as far as downloading the ibus-source and ibus table, and they are sitting here on my desktop. What do I do with them now? That step seems to be missing from the guide above. 

I'm new to Linux, so I apologize for not knowing this.

Cheers!

---

### Post by bruno.braga on 2010-01-10
Thanks everyone for the feedback. This solution posted here was what worked for me, and in deed I was already expecting different approaches (I got to realize this happens fairly often).

KageTora, the step you are talking about is the (3), where you will need to compile the source code. Since this is probably your first time, you will also need to install:
```

sudo aptitude install build-essential

```
Once you have that, you open your terminal and go to the directory where the source code is, and type the commands as described in the first post.

Cheers,

---

### Post by sungohan on 2010-01-18
Thanks a million!
Got ibus working on my system with your instructions.

---

### Post by iGround on 2010-01-20
I had the same problem also, however after I reinstalled the system last night (the previous one was directly upgraded from 9.04) the installation for iBus appeared to be quite easy.

Here is a detailed instruction link: [http://www.pinyinjoe.com/linux/ubuntu-910-openoffice-chinese-setup.htm](http://www.pinyinjoe.com/linux/ubuntu-910-openoffice-chinese-setup.htm)

---

