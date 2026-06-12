---
title: "WoW wine Graphics Lag"
date: 2007-01-30
forum: Gaming &amp; Leisure
---

### Post by cdevilrun on 2007-01-30
Alright, here's the deal. I'm fairly new to Linux and I've been working on getting WoW running perfectly.

Computer is a Dell Laptop 
1.6 ghz Celeron
1gb ram
Radeon Mobility 9000 (64mb video memory)
Edgy
Latest version of wine (upgraded it yesterday)
All graphics set to low

I know the computer is a bit slow for running the program, but in theory it should work.

When I run it in D3D mode the graphics are all perfect and the game runs fine for a bit. Every 5 minutes or so it drops down to 2-4 fps and becomes basically unplayable for 5 minutes. Everything lags here, cursor, entering text, etc. The lag then goes away and the cycle repeats. 

When I try to run it in OpenGL there are graphical errors in all the UI (bags, action bars, text, ect.) and I haven't been able to play long enough to see if the lag issue occurs.

Here are my questions:

Is there a difference in the way that wine handles D3D that would account for this problem?
If so, how do you suggest that I fix the graphics so that I can run OpenGL?
Do I need to go to ATI and see if there are more current drivers for the integrated video?
If so, what is the recommended procedure for upgrading the driver?
Can I allocate more system memory to the video? If so, how?

This forum is the number 1 reason I chose Ubuntu, thank you in advance for your assistance.

---

### Post by cdevilrun on 2007-01-31
Bump of desperation](*,)

---

### Post by Cable on 2007-01-31
[These]("http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft") instructions worked perfectly for me.  Try them out and report back here with any problems.  :-)

---

### Post by Cable on 2007-01-31
Also, make sure you have the fglrx ati driver installed.  Instructions [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

---

### Post by Sammi on 2007-01-31
Please post the output of these commands:    [LEFT]```
glxinfo | grep vendor[LEFT]glxinfo | grep 'OpenGL version'[/LEFT]

```[/LEFT]
 
And let this command run for a while, say 30 seconds, then post the output:    [LEFT]```
glxgears -printfps
```[/LEFT]
    Have you tried tweak nr. 1 in this howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ?

---

### Post by cdevilrun on 2007-01-31
Thanks for the responses guys. Unfortunately I am at work at the moment and can't try any of this. 

About Tweak #1

I went to do this last night and the most maddening thing happened. I couldn't change the name of the key. It just won't give me a text field. I've tried the drop-down, the edit menu, F2, soft-clicking the name. Nothing. I can change the string name. Weird. Maybe a wine issue?

I also tried loading the proprietary drivers but it seemed to slow the frames even more in D3D and broke OpenGL.

I'll post all the results of your suggestions tonight. 

Thanks again.

---

### Post by hikaricore on 2007-01-31
> **cdevilrun said:**
> 
Is there a difference in the way that wine handles D3D that would account for this problem?

Direct 3D support in wine is getting better every week, but still as it is a closed source rendering system this all pretty much needs to be reverse engineered.  (imagine trying to replace a parts inside your engine without a manual in the dark lol)  Sadly the state it is in now will NOT work for most WoW players.

> **cdevilrun said:**
> 
If so, how do you suggest that I fix the graphics so that I can run OpenGL?

There are a couple of graphic performace tweaks you may want to try out here: [http://help.ubuntu.com/community/WorldofWarcraft](http://help.ubuntu.com/community/WorldofWarcraft)

> **cdevilrun said:**
> 
Do I need to go to ATI and see if there are more current drivers for the integrated video?
If so, what is the recommended procedure for upgrading the driver?
Can I allocate more system memory to the video? If so, how?


I can't offer you any assistance with anything ATI, but I see you've been provided other suggestions in this area so hopefully they resolve your issue.

> **cdevilrun said:**
> 
This forum is the number 1 reason I chose Ubuntu, thank you in advance for your assistance.

This forum is a great community aside from a few stressful days here and there.  :)  We're all glad to have you here and just hope we're able to help.

---

### Post by Sammi on 2007-01-31
> **cdevilrun said:**
> About Tweak #1

I went to do this last night and the most maddening thing happened. I couldn't change the name of the key. It just won't give me a text field. I've tried the drop-down, the edit menu, F2, soft-clicking the name. Nothing. I can change the string name. Weird. Maybe a wine issue?
I encountered this exact same problem. I thought I was going mad too. But then I tried to see if I was able to change the value of some other key, and I was. So I went back to this one, and this time it worked :?

I find it to be a pretty strange glitch, which I have no explanation for. The Wine developers are really living up to their promise of porting the Win32 API "bug for bug" :D

---

### Post by cdevilrun on 2007-01-31
Yeah, they know about it though. [http://bugs.winehq.org/show_bug.cgi?id=7280](http://bugs.winehq.org/show_bug.cgi?id=7280)
Last time I checked it looked like a user was figuring out where the problem is occuring.

I can't wait to get home and try to make this work. My aha moment when I get it running perfectly in OpenGL is going to be glorious. I just turned my girlfriend on to the game too. I lost the "are you gonna play that game all night?" and gained a "why does it keep lagging so bad?" and a "not now baby, I need to get one more lynx collar." ;-) 

When I fix it everyone will be happier. And hey, 2 out of 3 ain't bad.

---

### Post by cdevilrun on 2007-01-31
Hmm, got the DisabledExtensions to work. OpenGL runs with non-corrupted graphics now. Still getting the periodic lag though. Gonna keep trying.

---

### Post by cdevilrun on 2007-02-01
Argh. So the next thing I'm trying is getting the proprietary drivers for the ATI Mobility 9000 IGP working. 

Here is how it looks when I try to run it.

sudo sh ati-driver-installer-8.26.18-x86.run
Password:
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 163: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

---

### Post by cdevilrun on 2007-02-01
libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

user@system:~$ glxinfo | grep 'OpenGL version'
libGL warning: 3D driver claims to not support visual 0x4b
OpenGL version string: 1.3 Mesa 6.5.1

Any thoughts?

---

### Post by cdevilrun on 2007-02-01
Oh, and

user@system:~$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
7857 frames in 5.0 seconds = 1571.333 FPS
7746 frames in 5.0 seconds = 1549.072 FPS
7804 frames in 5.0 seconds = 1560.688 FPS
7818 frames in 5.0 seconds = 1563.552 FPS

---

### Post by Sammi on 2007-02-01
This warning you're getting
```
libGL warning: 3D driver claims to not support visual 0x4b
```is bad. It means your video drivers are no good for 3d. But I see you are trying to install new ones, only it's not working.

Have you tried these guides?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by cdevilrun on 2007-02-01
Yeah, I don't like that warning either. What's really strange is that WoW does run fluidly for those first 10 minutes or so. Then it lags. Then it gets better. Then the cycle repeats. So weird. 

The first thought is overheating. I'm careful to keep the fans clear, so I don't think that's the problem. 64mb of video ram is supposed to be enough, so unless it's an allocation problem I don't really know what's up. I am continuing to try and load the proprietary drivers. (A prospect that doesn't make me particularly pleased as there is an OSS alternative and ATI has such a bad rep with Linux drivers.)

Thanks for staying current with me Sammi, even if I haven't made it work yet it's nice to not be entirely alone.

---

### Post by hikaricore on 2007-02-01
> **Sammi said:**
> This warning you're getting
```
libGL warning: 3D driver claims to not support visual 0x4b
```is bad. It means your video drivers are no good for 3d. But I see you are trying to install new ones, only it's not working.


Hmm... from memory I thought this meant that the video card only couldn't support direct rendering in the 0x4b bit depth.  My old card certainly had issues with this, but it still worked.  I got this message no matter what the colour depth was set to or screen resolution.

---

### Post by cdevilrun on 2007-02-01
Yeah, so if you search for that error message as a string of text it appears to be a very common problem. The overwhelming response, however, is that it does not effect things in any noticable way. All the same it looks to be "fixed" come Fiesty.

---

### Post by cdevilrun on 2007-02-01
Still curious as to whether I can "share" more than 64mb of memory with the video.

---

### Post by Sammi on 2007-02-01
hmmm... alright then. I must have misunderstood that from some other tread.

---

### Post by cdevilrun on 2007-02-02
So, funniest thing happened last night.
I was still getting the periodic graphics lag and hadn't found a solution. So I go about loading the ATI drivers from the wiki. I get to the end of the HowTo, reboot, and X is broken. Lame.
So I recover xorg.conf, restart, and start WoW. The lag is all gone now.

Thanks for the help everyone! I'll keep my eyes in the forums to try and pass it on to others.

---

### Post by Sammi on 2007-02-03
ATI :roll:

Glad you've gotten it to work :D

---

