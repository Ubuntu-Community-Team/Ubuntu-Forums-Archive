---
title: "compiz doesn't work"
date: 2008-12-08
forum: General Help
---

### Post by landilas on 2008-12-08
Hello,

my new config: asus p5b deluxe motherboard, nvidia geforce 6600 vga, ubuntu intrepid

My old config: asus p5l-mx with integrated intel vga, ubuntu hardy. Compiz worked well on this. The /home/.compiz directory wasn't deleted before installation to save my options.

I've installed intrepid and video driver. The screen resolution is good, the driver's working...

I can't switch to desktop effects on. Starting "compiz" in terminal, the message was:

Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"

I've tried with envyng - there was no changing.

I've downloaded a program from [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) . After installing it wrote, that there's something other composite running. Should he switch it off? Yes, I said. Now this program doesn't show any problem with my system.

After it I've tried to switch compiz on again. Now I can do this, but the windows and panels are blinking.

I've tried it with the 173 and 177 nvidia driver too (now 177's running).

I've tried with choosing xclient and gnome desktop at logging in.

I've tried to switch on with terminal (compiz and compiz --replace commands), with menu//effects on, and with a plus program to speed start/stop compiz.

Nothing change --- if I switch it on, the windows are blinking, I cannot read the message in terminal, I can't switch off only restarting the windowmanager (ctrl-alt-backspace).

I don't know what options/files have to view to see something about the error...

Please help me, if anyone knows!

Sorry for poor English...

---

### Post by eternalnewbee on 2008-12-08
Installing nvidia 180.11 driver would help.
Here's the link. Read the instructions caefully.
[http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

---

### Post by landilas on 2008-12-08
> **eternalnewbee said:**
> Installing nvidia 180.11 driver would help.
Here's the link. Read the instructions caefully.
[http://ubuntuforums.org/showthread.php?t=1002828](http://ubuntuforums.org/showthread.php?t=1002828)

Thank you I will do it when I go home...

---

### Post by eternalnewbee on 2008-12-08
> Installing nvidia 180.11 driver would help.
I mean "could", not "would".

---

### Post by landilas on 2008-12-08
Thank you, but I'm afraid it couldn't...

or... I've installed 180.11 driver according to the link. It didn't send error message, I think. Though in the "closed drivers" menu (I don't know how it is in English, because I have Hungarian Ubuntu) says that there's no driver installed. There's a list: 173, 96 and 177 drivers, and I can't see the 180 driver. The compiz-check program says:

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV43 [GeForce 6600] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


So, I don't know exactly whether it is installed or not...

I can switch compiz on, but the monitor blinking is on, too - like with the other drivers. The blinking is not in equal timesteps, there are longer and shorter black pauses between two uplights. But the wallpaper isn't blinking - only the windows and panels!

In terminal it says: Xgl: not present (and others, but I can't read and copy here because of blinking). I've searched for xserver-xgl but it isn't in the repository.

Do you have any ideas? Maybe in the xorg.conf? Maybe the compiz settings?

---

### Post by eternalnewbee on 2008-12-08
> 
or... I've installed 180.11 driver according to the link. It didn't send error message, I think. Though in the "closed drivers" menu (I don't know how it is in English, because I have Hungarian Ubuntu) says that there's no driver installed. There's a list: 173, 96 and 177 drivers, and I can't see the 180 driver. The compiz-check program says:
Same here. See this thread (post 123)
[http://ubuntuforums.org/showthread.php?t=990978&page=13](http://ubuntuforums.org/showthread.php?t=990978&page=13)
By the way, Did you reboot the system?

---

### Post by landilas on 2008-12-09
> **eternalnewbee said:**
> Same here. See this thread (post 123)
[http://ubuntuforums.org/showthread.php?t=990978&page=13](http://ubuntuforums.org/showthread.php?t=990978&page=13)
By the way, Did you reboot the system?


Yes, it was rebooted...

I've looked at the suggested thread. I've runned the nvidia x server settings and really 180.11 driver is installed.

What does it mean in the nvidia list: GF 6600 0x00F2 and 0x0141? How can I see whether I have the same? I didn't found any data like this in x server settings...

---

### Post by eternalnewbee on 2008-12-09
> What does it mean in the nvidia list: GF 6600 0x00F2 and 0x0141? How can I see whether I have the same? I didn't found any data like this in x server settings...
I'm afraid I can't help you out with this one. You'll have to wait for users like **forlong** to give you proper instructions.

---

### Post by Forlong on 2008-12-09
**landilas**, the thread title is very misleading.

Compiz is working for you. As already mentioned, the reason why it did not at first, was the other compositor.

In other words: your problem is not regarding Compiz (or getting it to work) but most probably a driver or setup issue.

Please post the output of
```
ls ~/.compiz
```

---

### Post by landilas on 2008-12-09
> **Forlong said:**
> **landilas**, the thread title is very misleading.

Compiz is working for you. As already mentioned, the reason why it did not at first, was the other compositor.

In other words: your problem is not regarding Compiz (or getting it to work) but most probably a driver or setup issue.

Please post the output of
```
ls ~/.compiz
```


Sorry Forlong I'm not good at English, it was simple for me, but you're right. I'm new in ubuntuforums.org (I use ubuntu since january), what should I do? Modify the title? Can I do it at all?

Well, the output is:
tigger@coreduo:~$ ls ~/.compiz
session
tigger@coreduo:~$ 

edit: I don't know what it means, but would like to say, that I deleted all compiz function my last probe, whether it will be good - but not, unfortunately.

Can you help me?

---

### Post by landilas on 2008-12-09
Eternalnewby, thank you for your kindness!

---

### Post by eternalnewbee on 2008-12-09
> Eternalnewby, thank you for your kindness!
Thank you very much. Please believe me, If forlong has posted here, that means he knows something I don't. Forlong's been my guide to configuring and modifying compiz for some time now. I'm not kissing forlong's a** here. It's just that he's an authority in his own right within these forums, and if anyone can help you, he can.
There are several others who can help you, of course, but forlong's my personal choice.
And you can take that to the bank.

---

### Post by Forlong on 2008-12-09
> **landilas said:**
> Sorry Forlong I'm not good at English, it was simple for me, but you're right. I'm new in ubuntuforums.org (I use ubuntu since january), what should I do? Modify the title? Can I do it at all?
You could contact a moderator to do it for you.
But let's wait until we're sure what the problem is.
> **landilas said:**
> 
Well, the output is:
tigger@coreduo:~$ ls ~/.compiz
session
Alright, I just wanted to make sure you do not have any plugins installed that may be incompatible with the current version.
(the **ls** command **l**i**s**ts all files/directories of a directory, **~/** is short for /home/your_username/).

By the way: ~/.compiz is not the directory where Compiz' config files get stored.
Since you are on GNOME and I assume you did not change Compiz' backend, all settings will be stored in gconf (which is the global config system of GNOME, applications like Evolution use it too).

So, to make sure this is not a setup issue in Compiz, let's reset all settings:
First of all, make sure that Compiz is not running.
Then do a backup of those configs:
```
mv ~/.config/compiz ~/.config/compiz-bak
```
```
cp -r ~/.gconf/apps/compiz ~/.gconf/apps/compiz-bak
```
And finally, here's the command to reset the settings:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

OK, now run
```
compiz
```
and tell us about the result.

---

### Post by landilas on 2008-12-10
Dear Forlong, you're a "god"!

I've done what you wrote, the compiz is working (if it exact?), the output of "compiz" is:

tigger@coreduo:~$ mv ~/.config/compiz ~/.config/compiz-bak
tigger@coreduo:~$ cp -r ~/.gconf/apps/compiz ~/.gconf/apps/compiz-bak
tigger@coreduo:~$ gconftool-2 --recursive-unset -a /apps/compiz
tigger@coreduo:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

I don't know whether the last two warn line is good or not, but compiz is running.

Thank you very much! And thanks for the explanations, too. I don't "fear" from(?) terminal, know that it is very useful (I knew DOS commands anno well), but I've had no time to learn it yet.

---

### Post by Forlong on 2008-12-10
I'm glad you got it fixed. :)
> **landilas said:**
> I don't know whether the last two warn line is good or not
Those can be safely ignored. I think everyone gets this info, I know I do.

---

