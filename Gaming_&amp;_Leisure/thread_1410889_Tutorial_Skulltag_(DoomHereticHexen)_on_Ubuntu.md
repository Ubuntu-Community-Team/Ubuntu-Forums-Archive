---
title: "Tutorial: Skulltag (Doom/Heretic/Hexen) on Ubuntu"
date: 2010-02-19
forum: Gaming &amp; Leisure
---

### Post by frenc on 2010-02-19
I just wrote this for the Skulltag forums. If you don't know what Skulltag is, it's Doom, enhanced, online. It's quite amazing.

Check it out [here](http://skulltag.net/).

Here's the tutorial:

**A quick author's note:**

There was originally a large note here. I removed it as it is no longer necessary.

I would, however, appreciate constructive criticism as this is my first real contribution to the Skulltag community, and I'd like to be a good one.

Thanks, from frenc.

[size=150][color=#FFBF40][center]Skulltag-on-Ubuntu[/center][/color][/size]

**An introduction:**

In this tutorial we'll cover how to install the latest versions of Skulltag and Doomseeker on to your Ubuntu computer, where to place your IWADs (if you don't know what an IWAD is, don't panic just yet) and how to configure Doomseeker's directories, meaning you start playing straight away. This tutorial was created using and was designed for Ubuntu 9.10. If you're using an older version, menus may appear different (or programs that are shown throughout the tutorial may not even exist) and I recommend you upgrade as soon as possible. I will also give a list of commands you can use if you ever want to remove Skulltag and Doomseeker from your computer.

**[color=#FF0000]As you progress through this tutorial, you're going to be asked for your password several times by Ubuntu. Don't worry, you can type it in.[/color]**

Throughout this tutorial, all keywords will be highlighted in **bold text**. There are also a lot of images in this tutorial, to help users navigate menus and to help assure them they're doing everything right.

**The tutorial:**

First of all you're going to want to open the **Ubuntu Software Center**:

[center][http://i47.tinypic.com/2942gpy.png](http://i47.tinypic.com/2942gpy.png)[/center]

At the top you can see a button called **'Edit'**, right? Click it, then click **'Software Sources'**. Click the tab labelled **'Other Software'** tab at the top:

[center][http://i45.tinypic.com/24qpuf7.png](http://i45.tinypic.com/24qpuf7.png)[/center]

Click the **'Add'** button. Copy and paste the following code into the window that appears:

```
deb http://skulltag.net/download/files/release/deb/ jaunty multiverse
```

Now click **'Add Source'**. If you did this correctly, you should see the following window:

[center][http://i47.tinypic.com/ake2pz.png](http://i47.tinypic.com/ake2pz.png)[/center]

It's the same window as before, but with the new source added. Good job. Click **'Close'** at the bottom of the window. The **Ubuntu Software Center** will update the cache, as pictured below. Once this is done, you can close the window:

[center][http://i50.tinypic.com/1r5kw4.png](http://i50.tinypic.com/1r5kw4.png)[/center]

So, we've finished with **Ubuntu Software Center**. Now open the **Terminal**:

[center][http://i45.tinypic.com/107oohy.png](http://i45.tinypic.com/107oohy.png)[/center]

Now, enter the following command. This will download and install Skulltag. Remember, you will most likely be asked for your password:

```
sudo apt-get install skulltag
```

You will have confirm the installation up to two times. Usually by entering **'Y'** the first time, then **'y'** the second. For example:

[center][http://i46.tinypic.com/9atjwy.png](http://i46.tinypic.com/9atjwy.png)[/center]

Once that's finished, you have to type in another command, similar to the last one. This installs Doomseeker for Skulltag:

```
sudo apt-get install doomseeker-skulltag
```

You'll have to confirm this, too, like when we entered *sudo apt-get install skulltag* a second ago.

**What happened in my Terminal! Don't worry if this is confusing...**

david@XPS:~$ sudo apt-get install skulltag
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libflac++6 skulltag-client skulltag-data skulltag-data-announcer
  skulltag-data-extraskins skulltag-pk3 skulltag-server timidity
  timidity-daemon
Suggested packages:
  pmidi fluid-soundfont-gm fluid-soundfont-gs
The following NEW packages will be installed
  libflac++6 skulltag skulltag-client skulltag-data skulltag-data-announcer
  skulltag-data-extraskins skulltag-pk3 skulltag-server timidity
  timidity-daemon
0 upgraded, 10 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/25.2MB of archives.
After this operation, 33.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  skulltag-data skulltag-pk3 skulltag-client skulltag-server
  skulltag-data-extraskins skulltag-data-announcer skulltag
Install these packages without verification [y/N]? y
Selecting previously deselected package libflac++6.
(Reading database ... 143406 files and directories currently installed.)
Unpacking libflac++6 (from .../libflac++6_1.2.1-2build1_i386.deb) ...
Selecting previously deselected package skulltag-data.
Unpacking skulltag-data (from .../skulltag-data_0.98a_all.deb) ...
Selecting previously deselected package skulltag-pk3.
Unpacking skulltag-pk3 (from .../skulltag-pk3_0.98a_all.deb) ...
Selecting previously deselected package skulltag-client.
Unpacking skulltag-client (from .../skulltag-client_0.98a_i386.deb) ...
Selecting previously deselected package skulltag-server.
Unpacking skulltag-server (from .../skulltag-server_0.98a_i386.deb) ...
Selecting previously deselected package skulltag-data-extraskins.
Unpacking skulltag-data-extraskins (from .../skulltag-data-extraskins_0.98a_all.deb) ...
Selecting previously deselected package skulltag-data-announcer.
Unpacking skulltag-data-announcer (from .../skulltag-data-announcer_0.98a_all.deb) ...
Selecting previously deselected package skulltag.
Unpacking skulltag (from .../skulltag_0.98a_i386.deb) ...
Selecting previously deselected package timidity.
Unpacking timidity (from .../timidity_2.13.2-36_i386.deb) ...
Selecting previously deselected package timidity-daemon.
Unpacking timidity-daemon (from .../timidity-daemon_2.13.2-36_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libflac++6 (1.2.1-2build1) ...

Setting up skulltag-data (0.98a) ...
Setting up skulltag-pk3 (0.98a) ...
Setting up skulltag-client (0.98a) ...
--2010-02-19 13:41:15--  [http://www.fmod.org/index.php/release/version/fmodapi42416linux.tar.gz](http://www.fmod.org/index.php/release/version/fmodapi42416linux.tar.gz)
Resolving [http://www.fmod.org](http://www.fmod.org)... 209.240.153.48
Connecting to [http://www.fmod.org|209.240.153.48|:80](http://www.fmod.org|209.240.153.48|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11276420 (11M) [application/x-gzip]
Saving to: `fmodapi42416linux.tar.gz'

100%[======================================>] 11,276,420   176K/s   in 64s     

2010-02-19 13:42:20 (173 KB/s) - `fmodapi42416linux.tar.gz' saved [11276420/11276420]

ln: creating symbolic link `/usr/lib/libfmodex.so': File exists

Setting up skulltag-server (0.98a) ...
Setting up skulltag-data-extraskins (0.98a) ...
Setting up skulltag-data-announcer (0.98a) ...
Setting up skulltag (0.98a) ...
Setting up timidity (2.13.2-36) ...

Setting up timidity-daemon (2.13.2-36) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
david@XPS:~$ sudo apt-get install doomseeker-skulltag
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  doomseeker libqt4-core libqt4-test libwadseeker
The following NEW packages will be installed
  doomseeker doomseeker-skulltag libqt4-core libqt4-test libwadseeker
0 upgraded, 5 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/753kB of archives.
After this operation, 1,993kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libwadseeker doomseeker doomseeker-skulltag
Install these packages without verification [y/N]? y
Selecting previously deselected package libqt4-test.
(Reading database ... 143480 files and directories currently installed.)
Unpacking libqt4-test (from .../libqt4-test_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-core.
Unpacking libqt4-core (from .../libqt4-core_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libwadseeker.
Unpacking libwadseeker (from .../libwadseeker_0.3_i386.deb) ...
Selecting previously deselected package doomseeker.
Unpacking doomseeker (from .../doomseeker_0.4.1_i386.deb) ...
Selecting previously deselected package doomseeker-skulltag.
Unpacking doomseeker-skulltag (from .../doomseeker-skulltag_0.3_i386.deb) ...
Processing triggers for desktop-file-utils ...
Setting up libqt4-test (4.5.3really4.5.2-0ubuntu1) ...

Setting up libqt4-core (4.5.3really4.5.2-0ubuntu1) ...
Setting up libwadseeker (0.3) ...
Setting up doomseeker (0.4.1) ...
Setting up doomseeker-skulltag (0.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Once that's complete, we're almost done. Enter two following commands:

```
skulltag
```

And, after a second or two once it's finished, enter:

```
exit
```

If all things are going well, the **Terminal** should now be closed. Now navigate to your **home folder** and find the folder called **.skulltag**. If you can't see it, press **Ctrl and H**. This will make Ubuntu display hidden folders. Go into **'.skulltag'**.

Here's what you should look for:

[center][http://i47.tinypic.com/200crdi.png](http://i47.tinypic.com/200crdi.png)[/center]

Here is the contents of .skulltag:

[center][http://i45.tinypic.com/k012q1.png](http://i45.tinypic.com/k012q1.png)[/center]

As you can see, my .skulltag has a lot more files than yours. That's because I have already added my IWADs and a few more files.

Paste your **IWADs** in here. An IWAD is the main game file which contains maps, sounds and more. It is required for each game. Here's a list of IWADs you need at to play Skulltag, along with which game the represent:

```
Doom II: DOOM2.WAD
Doom: doom.wad
Final Doom - TNT: tnt.wad
Final Doom - The Plutonia Experement: plutonia.wad
Heretic: heretic.wad
Hexen: hexen.wad
```

Most people will have **DOOM2.WAD**. Since Doom II is the most popular Doom game, I, personally, consider it the most important IWAD. If you don't have it, you can buy it in many places, such as **[on Steam for £5.99](http://store.steampowered.com/app/2300/)**. Once you buy the game, the IWAD is included within the disc/download.

Don't get excited yet, we've still got to set up Doomseeker.

You should now be able to launch Doomseeker from the **Applications menu**, inside the **'Games'** section. It will look like this:

[center][http://i45.tinypic.com/bis18x.png](http://i45.tinypic.com/bis18x.png)

Oh, look at that. It's beautiful, isn't it? Don't get joining any games yet, though! We have to quickly (and I mean quickly) set the directories for current and downloaded WADs. At the top, click **'Options'** and then **'Configure'**. Nagivate to the tabs as seen in the following two images, and find your .skulltag folder. As you can see, mine's located in /home/david/.skulltag. This is the reason we didn't hide hidden folders yet, so you can easily find 'em. You don't need to modify any other settings:

These three images that were removed from the original because of the 8-image-per-post limit:

[center][http://i47.tinypic.com/szj4mq.png](http://i47.tinypic.com/szj4mq.png)[/center]

[http://i49.tinypic.com/4gqn2v.png](http://i49.tinypic.com/4gqn2v.png)[/center]

You can now press **Ctrl and H** once in your home folder again to avoid having all hidden folders revealed as it is no longer necessary to see them for this tutorial.

Click **'OK'** to close the configuration window.

You should be able to play Skulltag on Ubuntu now! Have fun!

**How to remove Skulltag and Doomseeker:**

To uninstall Skulltag and Doomseeker (but who wants to do that, right?), enter these three commands into the Terminal:

```
sudo apt-get --purge remove skulltag
sudo apt-get --purge remove doomseeker-skulltag
sudo apt-get autoremove
```

And then restart your computer to complete the uninstallation.

**Thanks for reading!**

---

### Post by frenc on 2010-02-19
I originally posted the images in "img" tags, meaning they loaded automatically. I posted the remaining 3 in here. This was stupid of me and I should have **read the rules**.

I apologise.

This post is no longer necessary.

---

### Post by mboufleur on 2010-07-14
This tutorial was indeed very helpfull.

I have steam installed in a Windows Vista partition from the same station. I was able to download the files from id's Superpack there and grab the WAD files to use with Skulltag in Ubuntu.

I am, however, unable to save games. Whenever I try, or if the game automatically tries to save a game on a new map, I get the message "could not create savegame ' ./skulltag/save0.zds'"

I've tried with Hexen and Heretic but both give the same results. Does anyone know if this might be a folder permission problem?

---

### Post by Roman0 on 2010-07-15
Wow, what a coincidence. I just noticed I also have this problem. I tried changing the directory's permissions, no luck :P Does Skulltag have a bugtracker? Would be useful at this point :P

---

### Post by mboufleur on 2010-07-21
As a matter of fact, this was a bug in the latest version of Skulltag (0.98c).

There is a [thread]("http://skulltag.net/forum/viewtopic.php?f=33&t=26059") about it in Skulltag.net forum, so it will probably be solved in next version.

In the meantime, you can manually edit the skulltag.ini file (located in ~/.skulltag folder).

Find the section "save_dir=" and change it to "save_dir=~/.skulltag". Also works for full paths as well.

---

### Post by perspectoff on 2010-08-14
Good tutorial. I condensed it into a few quick steps:

Ubuntuguide: [http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag](http://ubuntuguide.org/wiki/Ubuntu:All#Skulltag)

Kubuntuguide: [http://kubuntuguide.org/All#Skulltag](http://kubuntuguide.org/All#Skulltag)

Dependencies require that the Universe repositories be enabled.


I also have to put in a plug for Zdoom standalone on Ubuntu (although I prefer Skulltag):

[http://zdoom.org/wiki/Compile_ZDoom_on_Linux](http://zdoom.org/wiki/Compile_ZDoom_on_Linux)

---

### Post by gdbutcher on 2010-09-26
Thanks for this, your instructions were clear, it was easy to setup and it works great on my laptop running Ubuntu 10.10 64bit Beta. I just wanted to add that it also runs 'The Ultimate Doom' if you add 'doomu.wad' in your .skulltag folder :)

---

