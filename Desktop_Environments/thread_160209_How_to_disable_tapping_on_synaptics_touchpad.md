---
title: "How to disable tapping on synaptics touchpad?"
date: 2006-04-14
forum: Desktop Environments
---

### Post by dmbatcu on 2006-04-14
How can I disable tapping, but not moving the mouse with my laptop's touchpad. I disabled it through about:config for Firefox but am wondering if I can do it thoughout Kubunutu... it keeps messing up the documents I am typing in OO :)

---

### Post by cilynx on 2006-04-14
ksynaptics - A KDE application to configure Synaptics TouchPad

Never used it myself, but hey...give it a shot...

---

### Post by GeneralZod on 2006-04-14
Try ksynaptics - it should be in the repositories :)

Edit:

Gah - beaten by seconds!

---

### Post by Sgood1971 on 2006-04-14
I've had some mixed success with ksynaptics. If you can't get it to work right, try adding.

```
option tapbutton1 "0"
```

to xorg.conf

---

### Post by dmbatcu on 2006-04-14
[QUOTE=Sgood1971]I've had some mixed success with ksynaptics. If you can't get it to work right, try adding.

```
option tapbutton1 "0"
```

to xorg.conf[/QUOTE]

Thanks! That did it!

I installed ksynaptics and was able to click the disable tapping checkbox but it did not actually do anything.

---

### Post by brallan on 2006-04-15
I've been working on a wiki, at [SynapticsTouchpadHowTo]("https://wiki.ubuntu.com/SynapticsTouchpadHowTo")

but i'm afraid I don't know anything about Ksynaptics

please let me know if you see any mistakes or omissions.

thanks,
brian

---

### Post by linuxfanatic1024 on 2006-07-02
I use QSynaptics. KSynaptics doesn't work for me. :(

---

### Post by brockisit on 2006-07-09
Hello Everyone:

I dont have the file, and I would like to disable tapping too.

Any help would be great. jocase refered me to this website.

my name is brock

Always new to every website:) 

but Im on windows 2000 on a Inspiron 2650 notebook

---

### Post by jstroot on 2006-07-14
Hey all,
I'm using Gnome on Dapper. Can you use ksynaptics in Gnome? I've tried and cannot get it to work. 

I've also tried qsynaptics. It will actually run, but I can choose no options. My pad works fine, I just need to remove the tapping, it's driving me friggin nuts!!!](*,)

---

### Post by brallan on 2006-07-16
if qsynaptics does not work, this is likely because yours is not a synaptics touchpad, or else that dapper has misidentified it. Have a look at the wiki:
[https://wiki.ubuntu.com/SynapticsTouchpadHowTo](https://wiki.ubuntu.com/SynapticsTouchpadHowTo) for more info.

---

### Post by jstroot on 2006-07-19
> **brallan said:**
> if qsynaptics does not work, this is likely because yours is not a synaptics touchpad, or else that dapper has misidentified it. Have a look at the wiki:
[https://wiki.ubuntu.com/SynapticsTouchpadHowTo](https://wiki.ubuntu.com/SynapticsTouchpadHowTo) for more info.

Thanks! The wiki helped. I do have the synaptics touchpad, and it turned out that all I had to do was add one line to my xorg.conf file.

The touchpad already had its own input device section in xorg.conf, but was missing the following option:
```
        Option          "SHMConfig"             "on"
```

After adding that, qsynaptics allowed me to turn off the frakkin taps.

A light passed through the clouds, angels sang, and I cried out in rapture!

Thanks guys!!!

---

### Post by a2c39a on 2007-02-22
Hi Folks,

Many thanks for this thread. Like so many others, 'taps' on the Synaptics Touchpad on my Medion MD96400 were driving me mad! 
I had tried using 'tpconfig' with no success at all.
In the end all it took was to read this thread and add the line:
Option Tapbutton1 "0"

to the Synaptics Touchpad section of /etc/X11/xorg.conf file

and Taps were gone!!

Many thanks & best wishes, John.

---

