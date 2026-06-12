---
title: "epsxe error - cannot open shared object file"
date: 2007-12-23
forum: Gaming &amp; Leisure
---

### Post by rzrgenesys187 on 2007-12-23
Okay I've been trying things for probably 5 hours now and can't find a solution or figure one out.  The error I'm getting is

```
plugins/libgpu.so: cannot open shared object file: No such file or directory
```

I'm running Ubuntu Gutsy, using epsxe.  *Any* help would be greatly appreciated

---

### Post by DoktorSeven on 2007-12-23
```
ldd plugins/libgpu.so | grep found
```

What does that give you?  Sounds like a plugin is missing a dependency.

---

### Post by rzrgenesys187 on 2007-12-23
```
ldd: plugins/libgpu.so: No such file or directory
```

I couldn't figure out what they meant by libgpu.so? I have the actual GPU plugins installed

---

### Post by DoktorSeven on 2007-12-23
You'll have to go wherever that plugin is and run ldd on it.  If epsxe is in /home/user/epsxe, you need to be in that directory to run it on plugins/:

**cd /home/user/epsxe**

Modify the above for your specific case, of course.  Or just find the actual location of that file and run it from there without the leading plugins/:
**ldd libgpu.so | grep found**

---

### Post by rzrgenesys187 on 2007-12-23
That's what I did

Tried this as well and it gives me nothing
```
ldd libgpu* | grep found
```

---

### Post by acoustibop on 2007-12-23
So how did you install your plugins, rzrgenesys187?  AIR you have to unpack the plugin and put the plugin file (the .so one) in the plugins folder, and the configuration files in the cfg folder.  You also need to make sure the right permissions are set.  All this should be in a text file for most plugins.  It's obviously a GPU plugin you're trying to install/get working - mind sharing with us which one?  And which version of ePSXe are you using?

FWIW, particularly if you're having problems with plugins, I'd recommend [pSX Emulator]("http://psxemulator.gazaxian.com/").  For starters, it's pluginless - and very easy to install, configure and run.  Of the three Playstation emulators available for Linux, PCSX and ePSXe are old, difficult and long out of development - ePSXe has ben dead for more than 4 years, for instance.

pSX is nearly two years old and still in active development.  The vast majority of users find it works far better than the other two, both in Linux and Windows (as you might expect), and it's my opinion that the Linux version works even better now than the Windows one.

The basic difference is that PCSX and ePSXe are both enhancing emulators - this is what necessitates a plugin system, and slows down their performance and compatibility.  pSX is around accurate rather than enhanced performance, and generally runs more consistently; you can't say it runs faster, because it runs games at the correct speed by default, while the other two can run games at whatever speeds they can manage (enhancement...).  However, pSX tends to run games consistently, without slowdowns, while ePSXe and PCSX, even when set to run fast, will always slow down at some points.

But it's pSX accuracy that makes it for me: I didn't realise 'till I started using it just how much ePSXe (and PCSX, but I was using ePSXe at the time) distorts the picture.  pSX, for me, is far more 'transparent' - i.e. it comes between you and the game much less than other emulators.

---

### Post by rzrgenesys187 on 2007-12-23
I actually downloaded pSX last night and it seems to be working well.  For epsxe: All my permissions were set to my username, all I did for the plugins was to untar them and copy the files where they needed to be.  I have the script I wrote to do it and included it.  I still want to figure out the problem and if you are still intereted I attached the script I wrote.  If you don't I'd just like to say thanks for all the help you gave.

---

### Post by frenchn00b on 2008-05-22
> **rzrgenesys187 said:**
> I actually downloaded pSX last night and it seems to be working well.  For epsxe: All my permissions were set to my username, all I did for the plugins was to untar them and copy the files where they needed to be.  I have the script I wrote to do it and included it.  I still want to figure out the problem and if you are still intereted I attached the script I wrote.  If you don't I'd just like to say thanks for all the help you gave.

could maybe be interesting to have a rapidshare of all the file and plugins??  
what other think about it ?

---

