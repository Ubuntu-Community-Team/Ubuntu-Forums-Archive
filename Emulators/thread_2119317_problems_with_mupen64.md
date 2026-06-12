---
title: "problems with mupen64"
date: 2013-02-23
forum: Emulators
---

### Post by cjl77 on 2013-02-23
hey guy I am kinda new to Ubuntu and I am having a few issues with mupen64.  I looked on some other thread that I couldnt  find  after i signed up for a new account

Here is the script I used

cj@cj-Satellite-L305:~$ sudo sh /home/cj/Downloads/mupen64-0.5.tar.bz2
[sudo] password for cj: 
/home/cj/Downloads/mupen64-0.5.tar.bz2: 1: /home/cj/Downloads/mupen64-0.5.tar.bz2: SY&#65533;&#65533;j: not found
/home/cj/Downloads/mupen64-0.5.tar.bz2: 1: /home/cj/Downloads/mupen64-0.5.tar.bz2: BZh91AY: not found
/home/cj/Downloads/mupen64-0.5.tar.bz2: 14: /home/cj/Downloads/mupen64-0.5.tar.bz2: Syntax error: word unexpected (expecting ")")
cj@cj-Satellite-L305:~$

---

### Post by schragge on 2013-02-23
*mupen64-0.5.tar.bz2* is an archive, not a script. Try
```

tar xvf /home/cj/Downloads/mupen64-0.5.tar.bz2
cd mupen64-0.5
./mupen64

```

---

### Post by cjl77 on 2013-02-23
looks like its making progress but how do i open it?

here is the script
cj@cj-Satellite-L305:~$ tar xvf /home/cj/Downloads/mupen64-0.5.tar.bz2
mupen64-0.5/
mupen64-0.5/mupen64
mupen64-0.5/mupen64.ini
mupen64-0.5/whatsnew.txt
mupen64-0.5/save/
mupen64-0.5/save/empty
mupen64-0.5/doc/
mupen64-0.5/doc/readme.pdf
mupen64-0.5/doc/HiRezTexture.txt
mupen64-0.5/lang/
mupen64-0.5/lang/catalan.lng
mupen64-0.5/lang/pt_BR.lng
mupen64-0.5/lang/german.lng
mupen64-0.5/lang/spanish.lng
mupen64-0.5/lang/dutch.lng
mupen64-0.5/lang/italian.lng
mupen64-0.5/lang/english.lng
mupen64-0.5/lang/french.lng
mupen64-0.5/plugins/
mupen64-0.5/plugins/blight_input.so
mupen64-0.5/plugins/dummyaudio.so
mupen64-0.5/plugins/glN64.so
mupen64-0.5/plugins/jttl_audio.so
mupen64-0.5/plugins/mupen64_audio.so
mupen64-0.5/plugins/mupen64_input.so
mupen64-0.5/plugins/mupen64_soft_gfx.so
mupen64-0.5/plugins/mupen64_hle_rsp_azimer.so
mupen64-0.5/plugins/ricevideo.so
mupen64-0.5/plugins/RiceVideo6.1.0.ini
mupen64-0.5/plugins/Glide64.so
mupen64-0.5/plugins/Glide64.ini
mupen64-0.5/plugins/tr64gl.so
mupen64-0.5/jttl_audio.conf
mupen64-0.5/mupen64_icon.png
cj@cj-Satellite-L305:~$ cd mupen64-0.5
cj@cj-Satellite-L305:~/mupen64-0.5$ ./mupen64

---

### Post by schragge on 2013-02-23
You probably should look at what the readme says.
```

evince doc/readme.pdf

``` I guess you also need some ROMs to run the emulator. At the very least,
[http://mupen64.emulation64.com/test_demos.zip](http://mupen64.emulation64.com/test_demos.zip)

---

### Post by cjl77 on 2013-02-23
okay, i got mupen64plus to come up but now it is saying that it isnt recognizing the plugins 

here is the terminal
cj@cj-Satellite-L305:~$ mupen64plus '/home/cj/mupen64-0.5/Mario Tennis (E) [!].z64' 
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)  
Mupen64Plus Console User-Interface Version 1.99.5

UI-console: attached to core library 'Mupen64Plus Core' version 1.99.5
            Includes support for Dynamic Recompiler.
            Includes support for MIPS r4300 Debugger.
Core: Goodname: Mario Tennis (E) [!]
Core: Name: MarioTennis
Core: MD5: FFF9B3E22ABB9B60215DAFB13AD5A4DE
Core: CRC: 839f3ad5 406d15fa
Core: Imagetype: .z64 (native)
Core: Rom size: 16777216 bytes (or 16 Mb or 128 Megabits)
Core: Version: 1449
Core: Manufacturer: Nintendo
Core: Country: Europe (0x50)
UI-Console: Cheat codes disabled.
UI-console: using Video plugin: <dummy>
UI-console: using Audio plugin: <dummy>
UI-console: using Input plugin: <dummy>
UI-console: using RSP plugin: <dummy>
Core Warning: No video plugin attached.  There will be no video output.
Core Warning: No audio plugin attached.  There will be no sound output.
Core Warning: No input plugin attached.  You won't be able to control the game.
Core Warning: OpenGL function glActiveTexture() not supported.  OSD deactivated.
Core: Starting R4300 emulator: Dynamic Recompiler
Core: R4300: starting 64-bit dynamic recompiler at: 0x7f60476ac200
--input 'mupen64plus-input-sdl'

---

### Post by jody2 on 2013-08-05
I am having the same issue. Any answers or anything?

---

### Post by deadflowr on 2013-08-08
> **jody2 said:**
> I am having the same issue. Any answers or anything?

Depends on the problem.
Best to start a new thread.
This thread is about installing mupen64 from a tarball.

If your problem is mupen64plus related, then that would be different.
They seem the same, but mupen64 and mupen64plus are far different, as one is dead and the other is very much alive.

I would suggest starting a thread and pointing out the things that aren't working for you and what you've tried.

In my own personal take, use mupen64plus.
One, it's in the repos.
and Two, you'll get better support.

---

