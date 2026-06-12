---
title: "How to install Beryl?"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by M79 on 2007-04-21
Well, I finally have Ubuntu fully installed on my second HD (hooray for dual-booting!). Now I'm wondering, can someone explain to me a simple way of installing Beryl? Is it possible through the repository? 

Also, what's the best audio player for Linux? Something maybe like foobar.

---

### Post by FuturePilot on 2007-04-21
If you're using Feisty it's very simple. First install the graphics card driver with the Restricted Driver Manager. Then in a terminal just do ```
sudo apt-get install beryl beryl-manager emerald-themes
``` Then reboot and to test it out, in a terminal do```
beryl-manager
``` If it works and you like to have it run at login go System>Preferences>Sessions and then go to the Start Up Programs tab and click Add and just put in the box```
beryl-manager
```

---

### Post by M79 on 2007-04-22
> **FuturePilot said:**
> If you're using Feisty it's very simple. First install the graphics card driver with the Restricted Driver Manager. Then in a terminal just do ```
sudo apt-get install beryl beryl-manager emerald-themes
``` Then reboot and to test it out, in a terminal do```
beryl-manager
``` If it works and you like to have it run at login go System>Preferences>Sessions and then go to the Start Up Programs tab and click Add and just put in the box```
beryl-manager
```That was pure perfection. It all worked flawlessly, although it didn't prompt me to restart the computer. I'm loving Beryl so far. :) 

What about audio players? Is there anything out there similar to foobar2000, only for Linux?

---

### Post by M79 on 2007-04-22
I can't play .mp3 files? It says it's missing some gtstreamer plugin to decode .mp3 files. This is using the default audio player in Ubuntu. o_O

---

### Post by old_geekster on 2007-04-22
There are several music players for Feisty.  Here are a few: Amarok, Banshee (My favorite), Listen, Rythmbox and XMMS.

Take your pick.

---

### Post by Lord Darth Vader on 2007-04-22
gmplayer and mplayer play mp3 out of box. Try to set (for example) gmplayer in one of your mp3s properties as the application of choice for opening that file.

---

### Post by old_geekster on 2007-04-22
> **M79 said:**
> I can't play .mp3 files? It says it's missing some gtstreamer plugin to decode .mp3 files. This is using the default audio player in Ubuntu. o_O
You can use "Synaptic Package Manager" to install the gfstreamer plugin.

Here is a link to a website that will be a great help to you:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

You can find about anything that you require.

---

### Post by M79 on 2007-04-22
> **old_geekster said:**
> There are several music players for Feisty.  Here are a few: Amarok, Banshee (My favorite), Listen, Rythmbox and XMMS.

Take your pick.
Okay, I have XMMS. Umm, how do I install it?

Edit: Never mind. I found this - [http://ubuntuforums.org/showthread.php?t=183](http://ubuntuforums.org/showthread.php?t=183) That worked like a charm. Thanks. :) I really should search instead of making useless threads like this. =\

---

### Post by FuturePilot on 2007-04-22
Just do ```
sudo apt-get install xmms
```

As for other codecs you might want to look here for how to get them
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by M79 on 2007-04-22
Hm. Amarok crashed on me, and won't play my music files at all. XMMS is nice. It seems like a Linux version of Winamp. I'm going to try Banshee next.

Edit: And, Banshee won't play them either. Just gives me a red circle with a minus sign. What am I doing wrong?

---

### Post by aqwabawks on 2007-04-22
> **FuturePilot said:**
> If you're using Feisty it's very simple. First install the graphics card driver with the Restricted Driver Manager. Then in a terminal just do ```
sudo apt-get install beryl beryl-manager emerald-themes
``` Then reboot and to test it out, in a terminal do```
beryl-manager
``` If it works and you like to have it run at login go System>Preferences>Sessions and then go to the Start Up Programs tab and click Add and just put in the box```
beryl-manager
```

I did that last part there, adding beryl-manager to my sessions, but whenever I restart it's gone and I got to manually start up Beryl Manager.

---

### Post by M79 on 2007-04-22
Well, it doesn't matter (the other players). I'll stick with XMMS. Now I'm wondering, I just installed AVG Free Edition for Linux. But it doesn't allow me to make any updates. Is that normal on the Linux version? Because on Windows, you can make updates with the Free Edition. Should I go with AVG as my anti-virus?

---

### Post by uBrendon on 2007-11-25
> **FuturePilot said:**
> If you're using Feisty it's very simple. First install the graphics card driver with the Restricted Driver Manager. Then in a terminal just do ```
sudo apt-get install beryl beryl-manager emerald-themes
``` Then reboot and to test it out, in a terminal do```
beryl-manager
``` If it works and you like to have it run at login go System>Preferences>Sessions and then go to the Start Up Programs tab and click Add and just put in the box```
beryl-manager
```

Hey, I tryed that and it didn't work. This is what happens.

brendon@Brendon-laptop:~$ sudo apt-get install beryl beryl-manager emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
brendon@Brendon-laptop:~$ 
I have main universe restricted and multiverse checked. help please, thanks in advance

---

