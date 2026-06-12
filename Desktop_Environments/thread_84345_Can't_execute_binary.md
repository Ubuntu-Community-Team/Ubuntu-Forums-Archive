---
title: "Can't execute binary"
date: 2005-10-30
forum: Desktop Environments
---

### Post by 357Magnum on 2005-10-30
Hi all, first post here and new to Linux. Looking forward to learning.

I'm a Linux Noob so I appreciate your patience. 

I'm slowly figuring out 5.10 but am becioming frustrated because I can't seem to be able to install anything unless I use the Synaptic. Some of the things I want to install are not there. Real Player 8 for instance. I found the RPM file on real.com and used alien to convert it to a .deb file. But then when I try to install it gives me a syntax error.

I tried downloading the .bin from real.com and did this...

cadan@Linux1:~/Desktop$ sudo chmod +x rp8_linux20_libc6_i386_cs1.bin
cadan@Linux1:~/Desktop$ sudo sh rp8_linux20_libc6_i386_cs1.bin
rp8_linux20_libc6_i386_cs1.bin: rp8_linux20_libc6_i386_cs1.bin: cannot execute binary file

I also downloaded the RPM version of the same file. Tried alien and got this.....

cadan@Linux1:~/Desktop$ sudo alien rp8_linux20_libc6_i386_cs1.rpm
realplayer_8.0-2_i386.deb generated
cadan@Linux1:~/Desktop$ sudo sh realplayer_8.0-2_i386.deb
realplayer_8.0-2_i386.deb: line 1: syntax error near unexpected token `newline'
realplayer_8.0-2_i386.deb: line 1: `!<arch>'

It's probably something simple I'm messing up but to a noob like myself I am totally lost. Can anyone help?

P.S. Both the .bin and the RPM file are at /home/cadan/Desktop

---

### Post by aysiu on 2005-10-30
Real Player 8 is in the repositories--you just have to [enable extra repositories](http://www.psychocats.net/linux/sources.php)

---

### Post by Xian on 2005-10-30
Quick Link: [realplayer_8.0.11](http://archive.ubuntu.com/ubuntu/pool/multiverse/r/realplayer/realplayer_8.0.11_i386.deb).

---

### Post by 357Magnum on 2005-10-30
Wow! Thank you for the fast replies. The Ubuntu community rocks!

Ok I'll look into that. By the way do you know why I'm having so much trouble executing the binaries? Am I using chmod wrong?

---

### Post by Xian on 2005-10-30
[QUOTE=357Magnum]By the way do you know why I'm having so much trouble executing the binaries? Am I using chmod wrong?[/QUOTE]
Here's the proper command sequence:

```
$ sudo chmod a+x rp8_linux20_libc6_i386_cs1.bin
Password:
$ sudo ./rp8_linux20_libc6_i386_cs1.bin
```

---

### Post by 357Magnum on 2005-10-30
Thank you Xian

Nice meeting you.

---

### Post by stuporglue on 2005-10-30
You were using "sh" to run the program. "sh" is an sh shell script interpreter, so it IS used to run somethings, but only things that are sh shell scripts. Since the file you listed had .bin ending, it needed to be run like one of the posters said, with just a ./program.bin

---

### Post by 357Magnum on 2005-10-30
Yes thank you all for the sh explanation.

I have a new problem to report though. I added the repositories that another poster suggested. Averything worked. But when I found Realplayer 8 and tried to install it, it ran the installer and kept telling me it couldn't find where it installed itself....So I manually typed in a few different filepaths where I thought it might have gone. I even noticed it had put a Realplayer.sh file in usr/bin but it just kept saying it couldn't find the RPM file. Well....I opened my applications menu and Realplayer is showing up there as if it were installed????? I tried to start it...it threw an error at me. So I went back to Synaptic and selected "Complete Removal" of Realplayer. And it told me this..

E: realplayer: subprocess post-removal script returned error exit status 1

What a headache. Anyone understand all this?

---

