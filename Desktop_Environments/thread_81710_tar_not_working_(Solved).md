---
title: "tar not working (Solved)"
date: 2005-10-25
forum: Desktop Environments
---

### Post by iitywygms on 2005-10-25
I am trying to do this 

tar jx vlc-ty-i686-linux-r42.tar.bz2 /usr/lib/vlc/demux

I tried doing it with sudo

I tried doing it as root (sudo -s)

I am doing this from terminal.  No matter which way I try it just hangs.  It is a small file.  

I can unpack it easily by double clicking on it, but I need to get this to a directory that requires root permission.

What am I doing wrong?

---

### Post by heimo on 2005-10-25
Try: 
 tar fjx vlc-ty-i686-linux-r42.tar.bz2 /usr/lib/vlc/demux

---

### Post by aysiu on 2005-10-25
[QUOTE=iitywygms]
I can unpack it easily by double clicking on it, but I need to get this to a directory that requires root permission.[/QUOTE] Unpack it by double-clicking it. Then, Run this command (Alt-F2, not the terminal) ```
gksudo nautilus
``` and copy and paste the unpacked file into the directory you want it in.

---

### Post by iitywygms on 2005-10-25
Thanx for the quick reply.  This is what I get.  

kevin@LinuxBaby:~/Desktop$ ls
libty_plugin.so       vlc-ty-i686-linux-r42.tar.bz2
libvstream_plugin.so  vlc-vstream-i686linux-r37.tar.bz2
new file~
kevin@LinuxBaby:~/Desktop$  tar fjx vlc-ty-i686-linux-r42.tar.bz2 /usr/lib/vlc/demux
tar: /usr/lib/vlc/demux: Not found in archive
tar: Error exit delayed from previous errors
kevin@LinuxBaby:~/Desktop$ cd /usr/lib/vlc/demux
kevin@LinuxBaby:/usr/lib/vlc/demux$

---

### Post by iitywygms on 2005-10-25
Thank You AYSIU

I did as you said and I was able to get the files there.  
I am trying to get vlc to stream video from my tivo, still not working but this is not the correct place to ask about that.

I am very new at linux, so forgive me, I thought that since the files were green, and all the others in the directory were not, the permission was wrong, and that was why vlc was not working correctly.  Oh well, more reading is necessary.

Why are the files green? is there somewhere that will explain why some files are green, others red, and so on.  

Thanks again

---

### Post by heimo on 2005-10-25
[quote=iitywygms]Thanx for the quick reply.  This is what I get.  

kevin@LinuxBaby:~/Desktop$ ls
libty_plugin.so       vlc-ty-i686-linux-r42.tar.bz2
libvstream_plugin.so  vlc-vstream-i686linux-r37.tar.bz2
new file~
kevin@LinuxBaby:~/Desktop$  tar fjx vlc-ty-i686-linux-r42.tar.bz2 /usr/lib/vlc/demux
tar: /usr/lib/vlc/demux: Not found in archive
tar: Error exit delayed from previous errors
kevin@LinuxBaby:~/Desktop$ cd /usr/lib/vlc/demux
kevin@LinuxBaby:/usr/lib/vlc/demux$[/quote]

Ups, sorry. Change to the directory first, then extract.
```
cd /usr/lib/vlc/demux
tar fjx vlc-ty-i686-linux-r42.tar.bz2

```

---

### Post by aysiu on 2005-10-25
[QUOTE=iitywygms]
Why are the files green? is there somewhere that will explain why some files are green, others red, and so on.[/QUOTE] I'm not sure what you mean about the files being green. Do you have a mini-screenshot of it that you can attach to a post here?

---

### Post by iitywygms on 2005-10-25
here ya go

---

### Post by RAOF on 2005-10-25
[QUOTE=iitywygms]...
Why are the files green? is there somewhere that will explain why some files are green, others red, and so on.  
...[/QUOTE]
You mean, when you run ls?  The files are coloured based upon what they are - anything which is executable is coloured green, archives are coloured red, symbolic links are coloured light blue, directories are coloured darker blue.  Oh, and pink for images, I think.

The colourings are based upon guesses (file name, permissions, etc) unfortunately, so they're not always correct or complete.

---

### Post by iitywygms on 2005-10-25
The colourings are based upon guesses (file name, permissions, etc) unfortunately, so they're not always correct or complete.[/QUOTE]

So perhaps I am correct about these files being "different" and that is why vlc is not working when I try to connect to tivo.

---

### Post by RAOF on 2005-10-25
No, those two files are libraries.  The fact that they're coloured green indicates that they're executable, which is correct.

Edit: Whoops!  Quite correct.  I needed to look at your screenshot more closely.  All those files are libraries.  But I don't think they need to have the executable permission in order to be used.

---

### Post by iitywygms on 2005-10-25
Okay, and thaks for all the help.  FYI, I have tried xanros, suse, redhat, fedora, mandrake, and some others over the past 6 months.  I am pretty good at windblows, but want to get away from it.   Ubuntu is very close to making me windblows free.  Currently I only turn the windblows computer on maybe once a week, with help from people like you and Ubuntu, I will be windblows free.

---

