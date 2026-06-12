---
title: "/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by michael37 on 2007-10-09
I am running Gutsy beta with compiz 0.6 on ATI x1400 video card with fglrx driver.

What does this error message:
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image
mean?

---

### Post by baviskar on 2007-10-20
no idea, but im getting the same msg.

---

### Post by demarant on 2007-10-21
I just updated to ubuntu 7.10 and get the same error when reloading compiz
"Warn: No 8 bit GLX pixmap format, disabling YV12 image format"

That's what I get when restarting compiz via command "compiz --replace gconf":

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


It says Xgl not present. Any suggestion on what I should do?
I have laptop Dell Latitude X1 with Intel graphic chip:
Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS

---

### Post by michael37 on 2007-10-22
> **demarant said:**
> I just updated to ubuntu 7.10 and get the same error when reloading compiz
"Warn: No 8 bit GLX pixmap format, disabling YV12 image format"

That's what I get when restarting compiz via command "compiz --replace gconf":

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


It says Xgl not present. Any suggestion on what I should do?
I have laptop Dell Latitude X1 with Intel graphic chip:
Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS

You don't need Xgl since you have Intel video adapter.  Read up about Intel and AIGLX -- there are hundreds of posts on this subject.

---

### Post by FuturePilot on 2007-10-23
I'm seeing that same error. Anyone know what it means?

---

### Post by Koziasty on 2007-11-01
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

So do I. It is associated with a white screen :]. I run fglrx driver with aiglx enabled using [this guide](http://forlong.blogage.de/article/add_comment/796) and a patch for amd64.
any help would be welcomed, pls

---

### Post by Arghesis on 2007-11-02
I'm also having the same problem. But when i run
```

grep AIGLX /var/log/Xorg.*.log

```
it says nothing. So I figure I don't have AIGLX installed or smthing ...

Could you link to a post on how to do that ? Because I'm searching for more than 30 minutes and can't seem to find one. Thanks

---

### Post by ikkefc3 on 2007-11-02
> **Arghesis said:**
> I'm also having the same problem. But when i run
```

grep AIGLX /var/log/Xorg.*.log

```
it says nothing. So I figure I don't have AIGLX installed or smthing ...

Could you link to a post on how to do that ? Because I'm searching for more than 30 minutes and can't seem to find one. Thanks
It doesn't give anything at my pc (I'm running Gutsy with Compiz Fusion @ nvidia).
Which videocard driver are you using?

---

### Post by Arghesis on 2007-11-02
I installed Envy.
I have a GeForce FX5700LE

This is from my xorg.conf
```

Section "Device"
    Identifier     "nVidia Corporation NV36 [GeForce FX 5700LE]"
    Driver         "nvidia"
    Option         "DRI"     "true"
    Option         "XAANoOffscreenPixmaps" "true"
EndSection

```

The problem is that Compiz is not working well. Whenever I start it in with compiz --replace, at the end, it says this: 
```

pavel@pom:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 02:00.0 0300: 10de:0343 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```
 and then, if I close the Konsole (the terminal window), it stops working, the menubars from windows disappear, the taskbar also disappears ...
I'm thinking it's because I don't have AIGLX enabled ... but can't figure out how to do that ...

---

### Post by vs292 on 2007-11-03
I get the same "/usr/bin/compiz.real" line when I run compiz from Konsole, and closing Konsole causes my menubars etc. to disappear. I just installed Kubuntu 7.10 and wanted to check out compiz. I've got an nVidia go 6800.

 Does anyone have any suggestions? 

V

---

### Post by FuturePilot on 2007-11-03
Try starting Compiz from Alt+F2
I haven't noticed any problems from this error. I'm assuming it's a harmless error.

---

### Post by rafar on 2007-11-06
I'm not sure if these are related. However when I do Alt+Tab the little preview thumbnails of my opened windows turn out all white instead each reflecting their own preview. 
I'm running Gutsy, ATI HD 2600 with latest drivers and proper xorg.config. 
Thanks.

---

### Post by kentra on 2007-11-19
I have the same problem with my compiz fusion.
It worked fine for one week, but suddenly it happend.
Have anyone found a solution ?

> Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00c3 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by jimerickso on 2007-11-19
i have had that error for a long time. can't seem to put my finger on anything behind it. does it have something to do with videos flickering??

---

### Post by kentra on 2007-11-19
Nope, i just restarted xgl and then it happend :confused:

---

### Post by kentra on 2007-11-20
I think it was the Kiba-dock that caused the problem, i figured that was the only ting i installed og modified that day.

But i still dont know how to fix the problem.

---

### Post by Amaranth on 2007-11-20
This is a warning, not an error. It just means we don't patch Xorg to support alpha-only GLX visuals so if you use the mplayer patch to make it use the compiz video plugin mplayer has to convert the video to RGB before handing it to compiz.

None of the problems people have mentioned here are related to this.

---

### Post by ceco91 on 2008-01-03
I recieved this error
```

* Decorator "" is invalid.
... choosing emerald --replace as default decorator
* nvidia found, exporting: __GL_YIELD="NOTHING" 
* Starting: compiz.real
compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```
when i try to start fusion-icon & .
I am total fool and don't know what to do.
Edit:
It wasnt a problem.

---

### Post by StubbsPKS on 2008-01-23
Try doing alt + f2 and typing in compiz --replace.

It should stay running then.

If you happen to be running KDE you can do the following to make it start up on it's own.


touch ~/.kde/Autostart/compiz

echo "compiz --replace" > ~/.kde/Autostart/compiz

and that should create a file in the correct directory that will start up compiz when you log in.

---------

Edit: Someone's already stated to use alt + F2, that'll teach me to read the whole thread first!

---

### Post by Virgilius on 2008-03-01
> Try doing alt + f2 and typing in compiz --replace.

It should stay running then.

If you happen to be running KDE you can do the following to make it start up on it's own.


touch ~/.kde/Autostart/compiz

echo "compiz --replace" > ~/.kde/Autostart/compiz

and that should create a file in the correct directory that will start up compiz when you log in.

---------

Edit: Someone's already stated to use alt + F2, that'll teach me to read the whole thread first!
Is there a similar code in GNOME that we could use for this?

---

### Post by soccerdog8 on 2008-03-05
I've got an ATI Radeon Mobility X1400 graphics card. I had Ubuntu installed on here a few weeks ago, and somehow i got compiz working fine. It never gave me a problem. But when i reinstalled today, it gave me this error you guys are getting. When i run "compiz" in the console, here's what i get:
```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```
Then the terminal hangs, and all my windows get a red color to them at the top instead of the normal orange. Like i said, it used to work, so my card is supported. How can i fix it? Do i need to reinstall ubuntu again?

---

### Post by Amaranth on 2008-03-05
This is not an error message, it doesn't hurt to see it. Your terminal hangs because you ran 'compiz' and not 'compiz &' so it is waiting for compiz to finish running. Your windows get a red border because you have emerald installed. Uninstall emerald and run 'compiz &' and it should all work fine.

---

### Post by Amaranth on 2008-03-05
> **Virgilius said:**
> Is there a similar code in GNOME that we could use for this?

In GNOME you go to System->Preferences->Appearance, click on the Visual Effects tab, and pick anything except None.

---

### Post by soccerdog8 on 2008-03-05
> **Amaranth said:**
> This is not an error message, it doesn't hurt to see it. Your terminal hangs because you ran 'compiz' and not 'compiz &' so it is waiting for compiz to finish running. Your windows get a red border because you have emerald installed. Uninstall emerald and run 'compiz &' and it should all work fine.

Thanks, Amaranth. That did the trick.

---

### Post by dom96 on 2008-05-20
still doesn't work for me i tried everything and it doesn't work please help

---

### Post by Xteven on 2008-05-31
Nothing worked for me until I found this:

[http://www.freesoftwaremagazine.com/articles/installing_compiz_fusion](http://www.freesoftwaremagazine.com/articles/installing_compiz_fusion)

Compiz works fine now.

---

### Post by evoviiigsr on 2008-07-01
I had the same prob but fixed it. For me, I am dual booting with windows vista. I disabled the "aero" feature in vista and then compiz started working in ubuntu..

---

### Post by macabro22 on 2008-07-22
> **evoviiigsr said:**
> I had the same prob but fixed it. For me, I am dual booting with windows vista. I disabled the "aero" feature in vista and then compiz started working in ubuntu..

How come? This is mystic.

---

