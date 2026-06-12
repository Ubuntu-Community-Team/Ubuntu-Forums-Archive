---
title: "Another UT2004 sound problem"
date: 2010-12-22
forum: Gaming &amp; Leisure
---

### Post by HolyPhoenix on 2010-12-22
Ok, so I just installed ut2004 and it runs great.  Very fast, very clean.  The only problem is the sound.  I have searched over almost everything for a solution but have not been able to find it.  I am on ubuntu 10.10.

Here is the error I get when running it via terminal.

open /dev/[sound/]dsp: No such file or directory

Any help would be appreciated, and probably useful to other users who are trying to get the sound working.

---

### Post by Brebs on 2010-12-22
UT2004 uses [openal](http://packages.ubuntu.com/maverick/libopenal1), so maybe check your ~/.alsoftrc

---

### Post by HolyPhoenix on 2010-12-22
I just found this thread, so I spoke a bit soon.  Any idea how I can get it fixed without needing to type in the extra every time?

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=888950](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=888950)

I know I can add the command to the launcher, but it doesn't quite seem like an official fix.

---

### Post by Brebs on 2010-12-23
You should [symlink the libs](http://ubuntuforums.org/showthread.php?p=5511840#post5511840).

---

### Post by Gazhole on 2011-01-03
Using a different version of Ubuntu to you (9.10) i got it working like this (replace directories with your own, obviously):

First download the correct sound package:  
  sudo apt-get install libopenal1  
    
  Then make a symbolic link thusly:  
  sudo ln -s /usr/lib/libopenal.so.1 ~/Games/ut2004/System/openal.so  
    
  Then create a config file for openal in ~/.alsoftrc, and put these lines in it:  
   
  format = AL_FORMAT_STEREO16  
  frequency = 44100  
  drivers = alsa  
  layout_STEREO = fl=-100, fr=100  
   
  [alsa]  
  device = default  
  mmap = true  

Seemed to work for me, i don't know what your sound setup is but you can always RTFM for other config options ;).

Hope that helps.

---

