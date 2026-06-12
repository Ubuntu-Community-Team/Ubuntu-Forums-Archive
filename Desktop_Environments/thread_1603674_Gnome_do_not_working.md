---
title: "Gnome do not working"
date: 2010-10-23
forum: Desktop Environments
---

### Post by laserbeam on 2010-10-23
Since I upgraded to 10.10, gnome-do stopped working... It keeps giving me this when I run it in from a terminal:


```
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Read (intptr,byte[],int,int,System.IO.MonoIOError&) <0x00062>
  at (wrapper managed-to-native) System.IO.MonoIO.Read (intptr,byte[],int,int,System.IO.MonoIOError&) <0x00062>
  at System.IO.FileStream.ReadData (intptr,byte[],int,int) <0x00047>
  at System.IO.FileStream.RefillBuffer () <0x0002b>
  at System.IO.FileStream.ReadByte () <0x000c7>
  at Mono.Addins.Serialization.BinaryXmlReader.ReadNext () <0x00031>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00053>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x0005f>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x0005f>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x0005f>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x0005f>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x0005f>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x0005f>
```
(the last lines repeat for ever...)

Really guys I have no Ideea what to do, I've installed and reinstalled if several times, also autoremoved between installs.

---

### Post by directhex on 2010-10-23
Erase ~/.local/share/gnome-do/ - it might help

---

### Post by hrickh on 2010-10-23
It may be that one of your plugins no longer works after the upgrade and you just have to figure out which one it is.

Have you gone through them and deactivated/reactivated them one by one? I know that's a pain, but it'll tell you which one is the culprit.

Having said that, I might also suggest Kupfer if you can't get Do to work. It's newer than Do (but has active development) and has most of the same type of plugins as well as a few more.

I switched from Do to Kupfer a few months ago, after Do kept crashing on me and I got tired of fixing it. I've been extremely happy with it. No offense to the Do developers. It just wasn't working for me.

R.
==

---

### Post by laserbeam on 2010-10-24
Yey... clearing ~/.local/share/gnome-do did the trick, thanks... I thought it was from one of the plugins, but I wanted to clear the configs any way. Found some in other places as well and I thought I had taken care of them... anyway, thanks! Marking as solved.

---

