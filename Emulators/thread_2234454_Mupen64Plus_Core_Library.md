---
title: "Mupen64Plus Core Library"
date: 2014-07-14
forum: Emulators
---

### Post by Lightning Dragon on 2014-07-14
Hello,

I'm trying to set this emulator up for my brother. I can't seem to get it to work at all (with CuteMupen). I tried the versions in the Synaptic Manager, tried the version in the Software Center and even tried installing it via an achive from the official google docs page. However, they all have the same problem; they cannot locate the Core Library. Running Mupen64Plus in the terminal gets me this:

```
LD@LDC:~$ mupen64plus
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Mupen64Plus Console User-Interface Version 2.0.0

UI-Console Error: dlopen('/usr/local/lib/libmupen64plus.so.2') failed: libpng15.so.15: cannot open shared object file: No such file or directory
UI-Console Error: dlopen('./libmupen64plus.so.2') failed: ./libmupen64plus.so.2: cannot open shared object file: No such file or directory
UI-Console Error: AttachCoreLib() Error: failed to find Mupen64Plus Core library
LD@LDC:~$ 


```

I found that "libmupen64plus.so.2" is installed in a lot of different locations, not of which actually works.

/usr/lib/ & /usr/lib/libmupen64plus.so.2 (the later is a folder, empty. Former is a set of files in that name)
/usr/local/lib & /usr/local/lib/mupen64plus (like the above, folder for the later with the files)

I thought maybe I have to install whatever "libpng15.so.15" is but I cannot find it in the Syntaptic Manager or the Software center.  I tried googling the problem but most of the threads about this issue were either never solved or were resolved installing an older package through the SM/SC--which doesn't work for me, since they are the newer versions anyways. When I purge everything related to Mupen64Plus, it says I have the Libpng files as well.

Installation of Mupen64Plus goes by smoothly, no errors or anything. Just when I attempt to launch it. 

Could someone help me out here? I purged so I should be clean of any installs.

Thanks!

---

### Post by Lightning Dragon on 2014-08-02
Hello,

I hate to bump this...but I have exhausted all other possibilities at fixing this. Does anyone know what I am doing wrong?

Thank you! :)

---

### Post by adec2 on 2014-08-03
Hi,

Try using this instead

[https://github.com/dh4/mupen64plus-qt](https://github.com/dh4/mupen64plus-qt)

I find it much better to use, the compile instructions are on that page and also here is a paste of my cofig file to help you with locations of files:

[Paths]
mupen64plus=/usr/local/bin/mupen64plus
roms=/media/Stuff/Roms/N64
plugins=/usr/local/share/mupen64plus
data=/usr/local/share/mupen64plus
config=/usr/local/share/mupen64plus

hope it helps

---

### Post by Lightning Dragon on 2014-08-03
> **adec2 said:**
> Hi,

Try using this instead

[https://github.com/dh4/mupen64plus-qt](https://github.com/dh4/mupen64plus-qt)

I find it much better to use, the compile instructions are on that page and also here is a paste of my cofig file to help you with locations of files:

[Paths]
mupen64plus=/usr/local/bin/mupen64plus
roms=/media/Stuff/Roms/N64
plugins=/usr/local/share/mupen64plus
data=/usr/local/share/mupen64plus
config=/usr/local/share/mupen64plus

hope it helps

Hi and thanks for the reply! 

I have not seen this before! Thank you! I will try it right away. 

However, do I need to keep my current Mupen64Plus install or do I need to purge (basically, does this binary download serve as the emulator installer as well as the QT installer) to use this?

Thanks again! ):P

p.s

also, those paths tend to be invalid but I will try them with this new install.

---

### Post by adec2 on 2014-08-06
Just use this frontend separately, it works fine for me. I also found mupen64plus a pain to configure but runs fine with this frontend. Hope it works for you too

---

