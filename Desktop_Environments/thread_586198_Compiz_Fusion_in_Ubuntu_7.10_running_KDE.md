---
title: "Compiz Fusion in Ubuntu 7.10 running KDE"
date: 2007-10-22
forum: Desktop Environments
---

### Post by computerex on 2007-10-22
Hello Guys. I am thinking of trying out the KDE desktop environment in my Ubuntu Gutsy installation. My question is, would I still have the Compiz Fusion effects in KDE?

---

### Post by FredB on 2007-10-22
There is no info on this on Kubuntu official site. But some search seems to tell me it is ok.

Sorry for not being more helpful :(

---

### Post by anubhavrocks on 2007-10-22
Yes Compiz Fusion is present in Kubuntu.Go try it out :)

---

### Post by bluefightingcat on 2007-10-22
Is there a way to quickly and easily turn it on, like in Ubuntu or would it involve installing it from the repos and manually messing around?

BFC

---

### Post by analox on 2007-10-22
i updated my laptop from Kubuntu 7.04 to 7.10 Gutsy but haven't found out how to enable compiz effect in this version. Guides I found so far are in the context of Gnome Ubuntu but not KDE. 
Please advice on how to get this feature in KDE :)

Many thanks

---

### Post by anubhavrocks on 2007-10-22
Press ALT+F2 and type
compiz --replace

---

### Post by analox on 2007-10-22
i try compiz --replace but it says no command found. I upgraded from Festi and no previous Compiz installed...

Any ideas?

---

### Post by Koroviev on 2007-10-22
```
sudo apt-get install compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-settings-manager
```

Check [http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users]("http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users") for more info. It's for Feisty, but most of it applies also to Gutsy. The main difference is that with Gutsy there is no need to add extra repositories.

---

### Post by piet hein on 2007-10-22
Hi all

I'm new on linux and this forum, and i have troubles with compiz.
i installed all the packages in the above post, i can get to the configuration files using the K menu etc. The only problem is that compiz doesn't work.
I try'd [ctrl] [alt] [arrow] to get the cube etc, set the windows to 'wobble', but nothing seems to have any effect.

if i typte 'compiz --replace'  i get:

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
no /usr/bin/metacity found, exiting


I hope somebody can help me to get compiz running, the youtube vids look really cool

thnx & greetz

---

### Post by computerex on 2007-10-22
Thanks for that! One slight annoyance. My desktop cube really isn't a cube anymore. It only shows 2 desktops, even though I have 4 workspaces.

---

### Post by analox on 2007-10-22
thanks Koroviev! I tried following the instructions in the link you post and installed all packages. 

Here is the error I get when type 'compiz --replace'
```
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e50 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting
```

I'm using ATI Mobility Radeon 9700/64Mb, the xorg.conf specifies
```

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "ati"
        Busid           "PCI:1:0:0"
EndSection

```
Anyone has a solution for this. I thought that Compiz will work fine with ATI :(

---

### Post by analox on 2007-10-24
I took too much time to find a solution for my ATI 9600/9700. Giving up, phew...

A bit disappointed on Gusty. Waiting for the driver updates, guess it's the only way :)

---

### Post by bluefightingcat on 2007-10-24
Hi,

I managed to get Compiz running quite easily on Kubuntu Gutsy with my ATI. It takes 4 steps to get compiz running:

1. Turn on the ATI driver. See the link in the next point.
2. Install XGL. Follow the instructions here: [http://ubuntuforums.org/showpost.php?p=3547657&postcount=7](http://ubuntuforums.org/showpost.php?p=3547657&postcount=7)
Only follow the instructions until point 2. After that move on to the next point in this post. 

3. Install Compiz Fusion. (Follow this tutorial:[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)) The tutorial was made for feisty but I think its been updated for Gutsy. I used this and it worked fine.

4. Make Compiz Fusion startup automatically at boot. 
You have to make an Autostart script for KDE. Use the following script:

#! /bin/sh
sleep 10
compiz --replace

If you don't know how to do this let me know and I will tell you. 

I am at work on my Windows computer so I can't remember everything to explain in detail. Do some googleing for more info on the topics. If you have problems let me know and I will try and be more specific. 

Good luck ;-)

BFC

---

### Post by bluefightingcat on 2007-10-24
Computerex:

Have a look at this blog to setup your compiz:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion). The following quote is taken from the blog and should fix your problem.

> Secondly, we have to increase the number of the virtual desktops to 4
at General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size
(the other two options have to be left at 1)


Let me know if you need more help.

BFC

---

### Post by analox on 2007-10-24
thanks a lot, BFC. It works, finally :D.

It seems that the graphic works normally when compiz is enabled. I tried your method before, but did not make compiz --replace autorun. The computer was very slow after xserver-xgl installed

Minor point: after enable compiz, all the text becomes very small (in firefox, file manager...). Any ideas to fix this? (currently change the font in firefox for every page by Ctrl - +) :">

---

### Post by bluefightingcat on 2007-10-24
Hi Analox,

Glad you got it working. I have the same issued. When XGL is activated (without compiz) the computer becomes very slow. But once compiz is started up then things works as normal. And since I have compiz start automatically its just a question of waiting a few seconds once the desktop appears after login. 

I have no idea about the fonts problem. Sorry!

BFC

---

### Post by bluefightingcat on 2007-10-25
Hi Analox,

I realised that once you get XGL working (to run compiz fusion) the restart and shutdown buttons go missing when you press ctrl-alt-del.

This bugged me a bit so I searched around and found a solution. I thought I'd share it with the rest of you just in case you have the same problem. 

[http://wiki.archlinux.org/index.php/Xgl#KDM](http://wiki.archlinux.org/index.php/Xgl#KDM)

I tried method C first but that made my KDM to crash. So I tried Method A which seems to be working so far (fingers crossed). The only difference with these instructions is that the file is located in a different place:

/etc/kde3/kdm

Make sure you backup your kdmrc just in case things go wrong. This way you can easily revert back to your old system and that way things will be ok again. 

Let me know if you need any more help. 

BFC

---

### Post by analox on 2007-10-25
wow, thanks for sharing this BFC. Method 1 works for me too ;)

The problem bugs me most is still the text font size. Have to press Ctrl+ + for every site I visited (not to mention the IM window, also hard to read :(.

Haven't found the solution for it yet...

---

### Post by Excalibre on 2007-10-29
Hey, I'm bumping this because I ran that compiz --replace command and I lost all window borders, so there's no title bars or anything. It looks quite bizarre. And my desktop cube is gone too.

I'm going to try the instructions in the blog post linked earlier but before that I'd like to know how to undo that command so that I can have KDE at least be usable in the meantime.

---

### Post by Saint Angeles on 2007-10-29
> **Excalibre said:**
> Hey, I'm bumping this because I ran that compiz --replace command and I lost all window borders, so there's no title bars or anything. It looks quite bizarre. And my desktop cube is gone too.

I'm going to try the instructions in the blog post linked earlier but before that I'd like to know how to undo that command so that I can have KDE at least be usable in the meantime.
kwin --replace

---

### Post by Excalibre on 2007-10-29
> **Saint Angeles said:**
> kwin --replace
Thanks!

---

### Post by piet hein on 2007-11-09
I had the same problem with window edges, i can get them running with

kde-window-decorator &

but it'll still crash a few times a day, really anoying, i'm thinking about switching to gnome

---

### Post by timohnani on 2007-11-10
Hey,

I can try and help you. but you have to tell me what exactly you have done so far. Did you follow the instructions in the thread?

BFC

---

