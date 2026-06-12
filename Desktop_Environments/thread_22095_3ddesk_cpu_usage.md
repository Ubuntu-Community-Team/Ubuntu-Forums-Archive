---
title: "3ddesk cpu usage"
date: 2005-03-25
forum: Desktop Environments
---

### Post by mglukhovsky on 2005-03-25
Perhaps I'm one of the few people who bothered to try 3ddesktop, but I find it pretty cool... I just put a "Switch Virtual Desktop" launcher on a panel, and now I can use it easily. However, I've stopped using it because of its intolerable cpu usage. Has anyone else noticed that their cpu usage spikes every few seconds on a regular interval when running the 3ddesk daemon? I'm guessing that it's trying to update the mini-view of each desktop, but it slows down the entire system. Any ideas?

-Mike Glukhovsky

---

### Post by cwaldbieser on 2005-03-26
I have not noticed this, though I have a pretty good machine and a fast video card with good 3D hardware acceleration.  Are you using software emulation, maybe?

---

### Post by mglukhovsky on 2005-03-27
I'm definitely running in hardware mode. If you don't mind, I'd like to compare specs: I'm running a Pentium M (1.8 GHz) with a Radeon 9700 Mobility, a 7200 RPM hard drive, and 1 GB of RAM. Glxgears gets an average of 1564 fps.

I don't think this is slow hardware by many standards: I'm thinking it's either an ATI driver problem or a software conflict. If anyone has any idea why there ought to be a difference, give a shout.

---

### Post by cwaldbieser on 2005-03-27
I am running a Pentium 4 at 3 GHz, 1 GB system RAM, and an ATI Radeon 9800 with 128 MB of DDR SRAM.  Don't think the HD makes a difference, as I never hear it spin.

I did pull up kpm to watch again, though, and I see that you are right, something is fishy, though I don't experience it to the same degree you are.  I noticed if I let 3ddesk run, it's process stays around 3% CPU usage, but my Xorg process jumps up to 30% every couple of seconds.  If I keep moving a window or scroll bar around, I can notice this as a split-second "snag" where the windows just freeze and unfreeze really quickly.

I must say that I never noticed this under XFree86, but then I really didn't notice it under Xorg until you pointed it out, either.  Best thing would be to alert the maintainer to the problem.  I am actually still on the 3ddesk mailing list, so if you don't want to trouble yourself, I will write it up.

---

### Post by mglukhovsky on 2005-03-27
Interesting that yours only spikes to 30%. Perhaps becuase I'm running a Pentium M system under a 686 kernel (it's not really 686, but something in between a 386 and 686) but mine spikes up to 100%, where the windows really do stick eery few seconds, rendering it unusable.

If you'd like me to I could post something on the list but I'd appreciate it if you could as you seem a lot more familiar with 3ddesk than I do. Thanks so much!

---

### Post by cwaldbieser on 2005-03-27
I've posted a message to the list.  Traffic there is pretty low, so I would probably not expect to hear back for a couple of days, especially around the holidays.  I'll update this thread if I find anything out.

---

### Post by mglukhovsky on 2005-03-27
Thanks so much, hopefully we'll see something come out of it. It's a really neat app with some good potential as eye candy  :grin:  but hey, it looks impressive.

---

### Post by vaskark on 2005-03-27
I want to get 3D Desktop running, but I get this message in console:

 > # 3ddesk --acquire
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

I'm not sure how to configure hardware acceleration or if I even have the appropriate packages installed. Can someone help? My graphics card has 128 Mb memory and is a Sapphire Radeon 9200SE. Thanks.

---

### Post by mglukhovsky on 2005-03-27
Do you have the ATI fglrx drivers installed? I'm fairly sure the 9200SE is supported by the driver. Try taking a look at this: 
[http://ubuntuforums.org/showthread.php?t=3567](http://ubuntuforums.org/showthread.php?t=3567) 

To check if you are using hardware rendering, try running glxgears from the console. If it's hardware, you should see smoothly running gears and the fps range ought to be above 1000. If the driver reported by glxgears is Mesa, you know you're running software rendering and ought to follow the directions in the above link.

---

### Post by cwaldbieser on 2005-03-27
A nice fellow on the mailing list suggested to me that the [autoacquire] feature, which appears to be new in the version of 3ddesk that comes with Hoary, is the culprit.  The idea is that when this option is active, 3ddesk proactively goes out to your other desktops every couple of seconds and takes snapshots so it doesn't get out of date.  However, the higher your resolution, the more info it has to pull in each time, hence the spikes.

By experimenting, I found that if I put the line

```
autoacquire 0
```

in /etc/3ddesktop/3ddesktop.conf, I was able to stop my CPU from spiking.  I did have to put this up in the global options section of the config.  I initially tried putting it after the exaple view definitions and it had no effect.  I ran the daemon directly with 

```
$ 3ddeskd -v > log.txt
```

so I could capture the debugging output.  I saw a line like this

```
DDDDDDDDDDDDDD demand loading 0
```

which I believe means the autoacquire feature was turned off.

Hope that helps!

---

### Post by mglukhovsky on 2005-03-27
Wonderful! I'll try it and see how it affects performance. I have a 1280x800, which is not huge but still could contribute to that. Do you think it's possible to delay the auto-acquire feature to every few minutes, so that it still updates but does not adversely affect performance? There's got to be a better way to get the goods without the CPU tax.

In any case, thanks for all the help. I'll report back with the results.

---

### Post by mglukhovsky on 2005-03-28
The autoacquire option worked wonderfully for the cpu usage, but upon looking closer I saw that 3ddesk was chewing up 142 MB of memory. While I don't mind that much (what with my having 1 GB of RAM) it isn't too pleasant a thought either. How much RAM is 3ddesk using on your system?

---

### Post by cwaldbieser on 2005-03-28
It uses about 212 M virtual memory (39 M real memory) if it has acquired all 4 of my desktops.

---

### Post by vaskark on 2005-03-28
[QUOTE=mglukhovsky]Do you have the ATI fglrx drivers installed? I'm fairly sure the 9200SE is supported by the driver. Try taking a look at this: 
[http://ubuntuforums.org/showthread.php?t=3567]("http://ubuntuforums.org/showthread.php?t=3567")[/QUOTE]

OK, this is where i'm kinda confused. I followed the instructions in your link, and I do have the ati drivers installed for xorg.

 ```
$ echo fglrx | sudo tee -a /etc/modules
fglrx
``` 

Now it says to change "ati" to "fglrx" in my xorg.conf file. But I don't currently have "ati" in there! Here is my Device section:

 ```
Section "Device"
	Identifier	"S3 Inc. 86c764/765 [Trio32/64/64V+]"
	Driver		"s3"
	BusID		"PCI:0:8:0"
EndSection
``` 

Now I know I have a Radeon card but according to this I'm not using the ati driver. I tried changing "s3" to "fglrx" and rebooted but that didn't work. So this is the point that I'm stuck on. I've also attached my full xorg.conf file. Any help will be greatly appreciated. I should mention that I'm running hoary on MS Virtual PC.

Thanks.

P.S. Glxgears does not run smoothly for me, and the fps range is nowhere near 1000.

---

### Post by mglukhovsky on 2005-03-28
Well, there you go. If you're running any operating system within a "virtual environment" then there is NO support for hardware rendering. Since Hoary is inside of a virtual environment, it doesn't have direct access to your hardware. MS Virtual PC  probably uses an S3-compatible virtual video card.

Sorry to break the bad news to you, but it doesn't look like you'll be getting OpenGL support. Install Hoary next time directly on the computer.

---

### Post by vaskark on 2005-03-30
[QUOTE=mglukhovsky] Sorry to break the bad news to you, but it doesn't look like you'll be getting OpenGL support. Install Hoary next time directly on the computer.[/QUOTE]
I installed hoary directly and got 3ddesktop working fine! It's really sweet.

---

### Post by vaskark on 2005-03-30
Ok, i'm confused about the autorequire feature. Is this activated by default? If so, how often is it updating?

---

### Post by cwaldbieser on 2005-03-30
I believe that it is, and that it runs about every three seconds by default.  That is just based on experimentation, though.  I am guessing that because the feature is relatively new, it has not been adequately documented, yet.

---

### Post by Firetech on 2005-03-31
The Autoacquire 0 stops the CPU usage. However, if you set it to 60 or something, it wont be useful, because the autoacquire function just updates the current desktop (as far as my testing shows) which the program also does when you change the virtual desk with "3ddesk". The autoacquire function is because of this not useful, and should be turned off.
You can also lower your memory usage (i think) by changing the texturesize option. By default it is 1024, but if you want to use your computer doing something else than changing desktops in 3D, 256 is a good choice. More info on the settings are in the 3ddesktop.conf file.

---

