---
title: "[SOLVED] Quake III demo"
date: 2008-07-10
forum: Gaming &amp; Leisure
---

### Post by jon.mithe on 2008-07-10
Hi,

Any know if this works on Hardy heron?  I have been tring to install it and failing miserably :(

I run the executable as normal (after chmod +x), run as sudo and also with sh but get the same error:

Running with: sudo ./linuxq3ademo-1.11-6.x86.gz.sh -target ~/q3

returns the error:

```
Warning: unknown mime-type for "archive" -- using "application/*"
Warning: unknown mime-type for "integrity..." -- using "application/*"
Error: no such file "-r"
Error: no such file "-n"
Error: no such file "Verifying"
Error: no such file "archive"
Error: no such file "integrity..."
tail: cannot open `+6' for reading: No such file or directory
Warning: unknown mime-type for "-r" -- using "application/*"
Warning: unknown mime-type for "Error" -- using "application/*"
Warning: unknown mime-type for "in" -- using "application/*"
Warning: unknown mime-type for "check" -- using "application/*"
Warning: unknown mime-type for "sums" -- using "application/*"
Warning: unknown mime-type for "1808389199" -- using "application/*"
Warning: unknown mime-type for "1300192087" -- using "application/*"
Error: no such file "-r"
Error: no such file "Error"
Error: no such file "in"
Error: no such file "check"
Error: no such file "sums"
Error: no such file "1808389199"
Error: no such file "1300192087"
Press Return to close this window ...
```

The 'q3' directory is created, but it is empty.

I have been following these threads but with no luck

[http://ubuntuforums.org/showthread.php?t=307937](http://ubuntuforums.org/showthread.php?t=307937)
[http://ubuntuforums.org/showthread.php?t=258823](http://ubuntuforums.org/showthread.php?t=258823)

I am running an uptodate version of straight forward ubuntu (8.04), and if it makes a difference, I have an ATI card with the drivers set up OK (fglrxinfo reports back correctly) with dual monitors (via aticonfig pair-mode).

Thanks for any help
Jon

EDIT:
hmm, didnt like the look of those check and sum errors, found a -help and led me to a -check installer option and I get this:


```
./linuxq3ademo-1.11-6.x86.gz.sh -check
tail: cannot open `+6' for reading: No such file or directory
Error in check sums 110245027 1300192087
```

So I guess the installer is corrupt, tried downloading it a number of times so I guess the actual ID one is corrupt :/

---

### Post by eragon100 on 2008-07-10
download and install the .deb packages of the game openarena (version 0.7.7) from getdeb.net (which is down for the moment, but should return soon). Open Arena is a free exact, 100 % clone of quake 3 arena, altough it does have **more game modes** and, in the latest version, **better graphics with bloom lightning and 8 x full-screen AA**. !

While getdeb is down, you can download the 0.7.7 archive from [http://www.openarena.ws]("http://www.openarena.ws")

Have fun playing! :wink:

---

### Post by jon.mithe on 2008-07-11
Hi,

Cheers that looks exatly what I'm looking for.  Installed the deb packages from getDeb but unfortunatly it crashes on startup :(.  Switches to fullscreen, but doesnt make it into the app, I see a small portion of my wallpaper stretched up to 640x480 odd and it all just freezes.  I have to restart X to regain control of my pc. 

I'm gonna have a play around and see if I can get it working.

Cheers,
Jon.

---

### Post by steven75 on 2008-07-11
Maybe you need different version of OS. What version of OS did you use?

---

### Post by eragon100 on 2008-07-11
Do you have desktop effects enabled? Disabling them might solve the problem.

Also, ATI cards are generally a disaster under linux, if you want to game you should by yourself a cheap GeForce :wink:

---

### Post by jon.mithe on 2008-07-11
lol cheers.  Actually managed to get it working, not to sure how but after a few startups it came up in windowed mode, so I can set to fill my screen nicely without going to fullscreen.  Yeah I use a nvidia card at home and everything just works but swapping the card here is not an option.  But it all seems to work, so all is good!

Thanks again for the help,
Jon.

Edit: seems it is something strange with open arena on my system, I installed Alien arena (another QIII engine open source spin off) and that works fine in fullscreen.

---

### Post by mrlee on 2008-08-15
Hello,

I had same problem and after cca. 1h of googling I found solution for same situation. To have linuxq3ademo-1.11-6.x86.gz.sh demo installed pls try next:

On the command-line, simply execute the following:

export _POSIX2_VERSION=199209

Then execute on the command-line:  sh linuxq3ademo-1.11-6.x86.gz.sh --keep

[Here is the reference link with explanations]("http://www.linuxgamepublishing.com/faq.php?id=8&#faq_1_3") [http://www.linuxgamepublishing.com/faq.php?id=8&#faq_1_3](http://www.linuxgamepublishing.com/faq.php?id=8&#faq_1_3)


good luck

---

### Post by castano on 2009-01-03
That did not work for me. I think that the most simple approach is to do the following:

$ tail +165 linuxq3ademo-1.11-6.x86.gz.sh | gzip -cd | tar xvof -

and then:

$ sudo bash ./setup.sh

and after that just follow he instructions. Hope that helps!

---

### Post by LeDechaine on 2009-09-29
WOOHOO! Thanks a lot!
After hours (no, gladly, minutes) of searching how to install this, i've finally got to install!

**tail -n +165 linuxq3ademo.gz.sh | gzip -cd | tar xf -**
Is the command I needed, found it on a blog somehwere ;) (Edit: The comment [here]("http://blog.janus.cx/archives/268-Quake-3-Demo-on-Linux,-installation-problem-and-solution.html"))

Now off to find the problem with this "Can't find default.cfg"...
Edit: Problem solved by running "q3demo" directly from the directory
**ledechaine@QuadDamage:/usr/local/games/q3demo$ ./q3demo**
(Yes, my machine is really named "QuadDamage" ;))

Well, now i'm having that X "badmatch" error...

> Q3 1.11 linux-i386 Dec  4 1999
----- FS_Startup -----
Current search path:
/home/ledechaine/.q3a/baseq3
./baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/ledechaine/.q3a/demoq3
./demoq3/pak0.pk3 (1387 files)
./demoq3

----------------------
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: QuadDamage
IP: 127.0.1.1
----- R_Init -----
...loading libGL.so: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  37
  Current serial number in output stream:  40


I'll create a new thread for this.. ([here]("http://ubuntuforums.org/showthread.php?p=8024935#post8024935")!)

---

