---
title: "Unable to enable desktop effects in Gutsy using Inspiron 1420n"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by onemojofilter on 2007-10-20
I just today installed 7.10 on my Inspiron 1420n. I find that I cannot enable desktop effects at all. I go System->Preferences->Appearance and go to the "Visual Effects" tab. 

The screen greys out for 15 seconds and I finally get a dialog box saying "Desktop effects could not be enabled".

Can anyone help with this, please?

---

### Post by onemojofilter on 2007-10-21
Bump:

Is it possible that the video card that comes with the Inspiron 1420n is blacklisted? I'm not sure if it is related or not, but in reading some posts in this forum I tried the command 'compiz' and got the following output:

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

So, if this is the cause, my question is, why would this video card be blacklisted? Is there any work-around for this?

---

### Post by onemojofilter on 2007-10-21
Bump

Please, anyone? If my video card is blacklisted under 7.10, why was it not an issue running desktop effects under 7.04?

I would really like to see a resolution to this.

---

### Post by Raistlin355 on 2007-10-21
I am having the same problem except that mine says:

Checking for Xgl: Not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

this is on a Dell Inspirion 1501 with an ATI 1150 vid card, running Ubuntu 7.10 Gutsy

---

### Post by onemojofilter on 2007-10-21
I found the solution. 

The video card actually is blacklisted which means that enabling desktop effects may have a detrimental effect on video playback, etc... There may be other risks but at least I got my question answered.

The way to turn it on is to essentially tell compiz to not check if the video card is blacklisted or not.

Here's how I did it:

sudo vi /etc/xdg/compiz/compiz-manager

I added the following line:
SKIP_CHECKS=yes

Then, I was able to turn on the effects. I noticed that certain effects weren't available by default (such as desktop cubes, etc...)

You have to download and install the Compiz config manager. The package name is "compizconfig-settings-manager".

Then Alt-F2 and type 'ccsm'. You should be able to turn on and turn off any effect you want.

I think though, that the inherent caveat is well worth considering. If we have problems with video playback or any aspect OS operation due to desktop effects, then I suppose there is no other remedy but to disable it until another solution presents itself.

---

### Post by johndudley on 2007-10-21
This worked for me up to a point.  I was able to start the effects once skipping the checks as described but then the tops of all of my windows vanished.

Interestingly I had previous used compiz without any such problem.

---

### Post by n6k6t6 on 2008-02-24
I had the problem with window titles and borders vanishing for no reason under compiz on
a macbook.

The macbook comes with the same blacklisted intel integrated graphics

---

### Post by rakusson on 2008-02-26
hi,
I have ATI Radeon RV250 FireGL 9000 graphics card. I cannot enable desktop effect (even the simple one). I tried with compiz command. The output is:
```

ra@everest:~/Desktop$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c66 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (1024): Failed.
aborting and using fallback: /usr/bin/metacity 

```

I thought I should reduce the resolution of my screen (I remembered it while installing Beryl, I don't have it now though) to 1280 x 800 but same result. What should I do? 
I added the following line too in compiz-manager: SKIP_CHECKS=yes but not even simple effect

---

### Post by notwen on 2008-02-26
As far as the Inspiron 1420n and any other Intel 965GM X3100 chipset laptop go.  Compiz-Fusion has blacklisted the X3100 chipset.  A simple workaround can be found [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility"), but this disables video playback using 'xv', simply change it in VLC/GStreamer/MPlayer, whatever media player you prefer to use 'No XV".  More issues regarding your Inspiron 1420n can be found here on the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").

---

### Post by LittleKoy on 2008-02-26
I'm using this threat in order to not open another one, since my problem looks similar. 
When I try to enable the desktop effects it says "Desktop effects could not be enabled", and if I type compiz in the shell, this comes out:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5964 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

What should I do?

---

