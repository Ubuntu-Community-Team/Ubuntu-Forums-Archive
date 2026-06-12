---
title: "Shoutcast streaming"
date: 2006-06-13
forum: Desktop Environments
---

### Post by DJeX on 2006-06-13
I want to connect to a shoutcast server and stream my radio station. I've installed darkcast and darksnow but can't get them to work. Any sugestions to what I can use to connect to the shoutcast server and stream the music to it? I've been trying for days now to get something to work, I'd like to get my station back up asap. I used to use a Windows computer with winamp but I decided to move to Linux because it runs better.

---

### Post by sYs^ on 2006-07-03
I have the same problem, do you know any good gui to stream to a shoutcast server? thx

---

### Post by FLeiXiuS on 2006-07-03
Ah I know the feeling, this may not be what you were expecting but it works!

[http://yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html](http://yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html)

---

### Post by RRS on 2006-07-03
I use Streamtuner with XMMS for both Shoutcast and Live365 streams.

---

### Post by sYs^ on 2006-07-05
FLeiXiuS: I knew about this, but has it a GUI?
RRS: For streaming music? I mean not only listening but "uploading" also.

---

### Post by puppetj on 2006-07-12
i just got this but when i run ./configure i get:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

AND.. WHEN I RUN "make" or "make install" i get

root@puppetj-desktop:/home/puppetj/Desktop/streamtuner-0.99.99# make
-bash: make: command not found
root@puppetj-desktop:/home/puppetj/Desktop/streamtuner-0.99.99# make install


WHY???

BTW  does this automatically add suport for xmms shoutcast stream and give a list like winamp?? or what happens...new to linux some what...i have been having probs with xmms and shoutcast streams not playing

---

### Post by andlinux21 on 2006-07-12
I have been running a shoutcast stream I just used the tools from the shoutcast web page i downloaded the 2 parts that i needed for linux and then configured the server it wasnt GUI but it runs and well.  As long as your mp3s are tagged right the info will show up in winamp xmms or whatever you are listening with.  If you need some help setting it up let me know.

---

### Post by puppetj on 2006-07-12
sorry i meant by listening to the shoutcasts, not serving them

---

### Post by andlinux21 on 2006-07-13
Puppetj no problem I thought you were having problems setting up a server.](*,)

---

### Post by puppetj on 2006-07-13
uhmmmm so can you help me out?? About what i asked!

---

### Post by FLeiXiuS on 2006-07-14
[quote=sys^]FLeiXiuS: I knew about this, but has it a GUI?[/quote]
Not a clue about the GUI part, read up on the program it's self.

[quote=puppetj]uhmmmm so can you help me out?? About what i asked![/quote]
Don't be afraid to google your errors.  I'm not going to walk you through each and every step of how to compile a program.  But, I will give you a clue here.  Notice it asks for a GCC Compiler.  In other words a program to compile the source into a readable executable.  
```
sudo apt-get install build-essential
```

---

### Post by puppetj on 2006-07-14
i did google around and it when to these forums...you lost me! btw i cant run make cmd and there is not help on the website itself, these forums are for help and that what i need. I dont know what else to, and i cant have winamp for linux, and if there is way its probaly even more compucated then just downloading and running it.
S can you Please help me!

---

