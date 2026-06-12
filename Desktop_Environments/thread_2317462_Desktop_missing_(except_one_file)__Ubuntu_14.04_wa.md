---
title: "Desktop missing (except one file)  Ubuntu 14.04 was working fine for 2 yrs."
date: 2016-03-16
forum: Desktop Environments
---

### Post by messypotamia on 2016-03-16
I've read through several threads this same subject but cannot find anything that helps. My 14.04 was a simple install on a small Acer Aspire One. Everything was whatever was on the default install of a new 14.04.
It's sole purpose was to autoload a browser upon boot, which inturn autoloads a streaming music station. That's all it did. (I did install UFW and maybe a Samba package but seldom used it).  It worked beautiful. Crontab rebooted every day at 0500 & 2200. I always had music in the garage. Although I would occasionally google a question about something I was working on, it otherwise sat there and played music. For over 2 years. Occasionally (once a year maybe?) I'd update security stuff from the desktop icon.
Today I go to use the browser and notice the browser is up, playing, but I have no desktop behind it. WTF, so I close the browser, and there is only the one file I had on my desktop ("bookmarks.html"), with nothing else (only had that one file).  So reboot. No help.  If I click on the bookmarks.html it brings up the browser, and it runs as a browser properly, but that's it. 
So I start googling and follow some of the suggestions.  I even tried to [re]install the gnome desktop, I got a message that it wasn't possible due to a bunch of reasons. 
I also tried booting to the GRUB, selecting a recovery option, tried a couple things, nothing helped; also booted to the earliest version, it came up the same, just an empty desktop except for the one .html file.  Disk space hasn't changed much, this is pretty much how it's always been.
uname -a 
Linux ph2-AOA110 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux
ph2@ph2-AOA110:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       6.3G  5.1G  966M  85% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            485M  4.0K  485M   1% /dev
tmpfs            99M  1.2M   98M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            495M  7.9M  487M   2% /run/shm
none            100M   24K  100M   1% /run/user
/dev/mmcblk0p1  7.5G  4.0G  3.5G  54% /media/ph2/FC30-3DA9

I don't know what to do. I'd hate to blow away the whole system and try reloading it again. And the SSD is only 8G (/dev/sda1) 

I'd really appreciate help with this. I mean if it happens again, after reinstalling all over, I wouldn't want to be faced with something that for me is again unsolvable.

Thanks, and sorry this might seem like a redundant post, but I read and tried several of the threads.

---

### Post by grahammechanical on 2016-03-16
You give a lot of information but I am still trying to understand what you mean by desktop missing.

I am assuming Ubuntu + Unity and also assuming automatic login and that the OS loads to a background wallpaper without a top panel and the launcher on the left side of the screen.

Questions. Are you using a proprietary video driver? Do you really need the proprietary video driver with that set up? Is the system set for automatic updates?

To get to System Settings we can right click the desktop wallpaper and select Change Desktop Background. That will open at System Settings>Appearance but from there we can get to the System Settings Window and select Software & Updates>Additonal Drivers tab and change to an open source video driver.

This command will reset compiz

```
 dconf reset -f /org/compiz/
```

This command will reset Unity

```
setsid unity
```

Either of which may bring back the top panel and the launcher.

Regards.

---

### Post by messypotamia on 2016-03-16
Right-clicking on the empty desktop does nothing now. As I said, the only thing on the desktop is a single file ("bookmarks.html") which I had stored, and is visible at /home/ph2/Desktop, it's the only file there.
One of the threads I used had the above commands you suggested [dconf ... setsid unity] The command window seemed to not respond after them, or couldn't finish. And I don't believe I'm using any proprietary video driver. When I installed 14.04 I didn't have to load anything else, as I recall. I did this on two Acer Aspire One's. The other one (seldom used or even turned on) was, at last boot, working just fine. 
Appreciate you ideas or things to try.

---

### Post by ajgreeny on 2016-03-16
I begin to wonder if an Acer Aspire One is man enough to run Unity properly as it requires good 3D graphics; what graphics does an Acer Aspire One have?

Also the vanilla Ubuntu with unity does not have an files in ~/Desktop.  What files are you expecting should be there?
A right click, however, should show you a context menu offering:-
New file or folder, 
Icon configuration options, (even though there are no icons on it by default), and 
Desktop background configuration.
Perhaps this is also a result of the graphics abilities of the machine.

---

### Post by messypotamia on 2016-03-16
Correction I can rt-clk on desktop, get into System settings, and can verify no proprietary drivers used. I tried
```
ph2@ph2-AOA110:~$ dconf reset -f /org/compiz/
error: Cannot autolaunch D-Bus without X11 $DISPLAY 
```
When I searched the error I got advice to do the following:
```

Switch to a virtual terminal (Ctrl+Alt+F1), log in and run the following commands:
[LIST=1]
[*]  sudo apt-get install gnome-panel
sudo mv ~/.Xauthority ~/.Xauthority.backup 
[*]Reboot and select gnome on login. 
[*]Once logged in open a terminal (e. g. with Ctrl+T) and run:
  sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity 
[*]Log out and log in again using Unity this time and that fixed it for me. 
[/LIST]

```  The I don't know what he means on his step #1, "select gnome on login", it auto logs me into my desktop with no top panel or launcher, and the only way I can get a terminal is ctrl+alt+F1, which gives me a login prompt. Longer story shorter, I changed grub to boot to text thereby not loading the gui, and tried the    but I get hundreds of lines of error still complaining about $DISPLAY, to wit:
```

(unity-tweak-tool:1387): dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY

(unity-tweak-tool:1387): dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY

(unity-tweak-tool:1387): dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY
WARNING: no DISPLAY variable set, setting it to :0
stop: Unknown job: unity-panel-service
start: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Fatal: Couldn't open display :0
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
Please log out and log back in.
ph2@ph2-AOA110:~$


```

I don't have a clue as to what happened, except a few days ago I did a  sudo apt-get update && sudo apt-get upgrade.  Somewhere therein  lies the clue.
This is perplexing me. Thank you for you sharing your knowledge about this area.

---

