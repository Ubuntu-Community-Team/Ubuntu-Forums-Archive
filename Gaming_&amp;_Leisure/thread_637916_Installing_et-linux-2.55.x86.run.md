---
title: "Installing et-linux-2.55.x86.run"
date: 2007-12-11
forum: Gaming &amp; Leisure
---

### Post by Evil Jinn on 2007-12-11
I just installed Ubuntu last night as requested by a friend when I started getting some C++ error on WinXP.

I've never used Linux before and I'm so lost.  The only thing I am concerned about is getting my Enemy Territory up and running the rest can come later.  I'm the only girl in my gaming clan and it's important that I get back in game.

I've looked through many of the other ET topics and I'm still confused.  A simple step by step of exactly what to do would be awesome and appreciated.

**This is what I've tried so far:**

jinn@merlinslady:~$ chmod +x et-linux-2.55.x86.run
jinn@merlinslady:~$ ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password: 
/root/.setup8219: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
jinn@merlinslady:~$ sudo apt-get install et-linux-2.55.x86.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package et-linux-2.55.x86.run
jinn@merlinslady:~$ 


Can anyone tell me what is happening because I dont understand?  :(

---

### Post by Sockerdrickan on 2007-12-11
Hi just wanted to say that there's a new version [http://zerowing.idsoftware.com:6969/stats.html?info_hash=243223ae5a39909db07a338980f00dd868251f05](http://zerowing.idsoftware.com:6969/stats.html?info_hash=243223ae5a39909db07a338980f00dd868251f05)

et-linux-2.60.x86.run
Run with ```
sudo sh et-linux-2.60.x86.run
```
If it says that stuff with libgtk-1.2 you should install libgtk-1.2 (lol) Search for it in Synaptic :)

---

### Post by Evil Jinn on 2007-12-11
Thanks for replying so quickly.  Our clan still plays on 2.55 though. :)  Not sure what synaptic is but this should get interesting to say the least.  I have so much to learn after 8 years of using WinXP.  And I realized there's so much coding for Linux.  Any idea where I can find commands that might help me in the end to learn this new OS?

---

### Post by Sockerdrickan on 2007-12-11
You don't type anything, it's a program! Something like this "system\administration\synaptic packet manager" search for libgtk 1.2 and check it then install. Now you can run the et installer!

---

### Post by Evil Jinn on 2007-12-11
Here's what I'm getting now.  How do I fix this part?

jinn@merlinslady:~$ sudo sh et-linux-2.55.x86.run
[sudo] password for jinn:
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
Installing symlink /usr/local/bin/etded -> /usr/local/games/enemy-territory/etded
Removing existing et symlink
Installing symlink /usr/local/bin/et -> /usr/local/games/enemy-territory/et
ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/jinn/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3729 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...
jinn@merlinslady:~$

---

### Post by Sockerdrickan on 2007-12-11
You arn't using any graphics card drivers it seems! Do you know how to install them?

---

### Post by Evil Jinn on 2007-12-11
Not a clue.  I have xfire, msn, yahoo and aim if it would be easier for you to help me there.  I do know my video card is: NV43 GeForce 6600 LE.

---

### Post by Sockerdrickan on 2007-12-11
Are you using Ubuntu 7.04 or later?

---

### Post by Evil Jinn on 2007-12-11
Ubuntu 7.10 and I know on the Nvidia site it wants to know about 32 and 64 bit and that doesn't compute in my head.  : \

---

### Post by Sockerdrickan on 2007-12-11
You can just install it in ubuntu
Something like "system\administration\proprietary driver manager" check the nvidia one and install then reboot and you'll have your graphics card ready 2 go!

edit
You can get 32bit or 64bit type info with uname -m

i686 = 32bit
x86_64 = 64bit

---

### Post by Evil Jinn on 2007-12-11
That command came back as i686.

Here's a few more things: it's telling me some pk.3 are missing.  Where would I put them if I get them?  Also, when I click the icon, it asks me to display or run.  When I click run, it takes me to the terminal screen and says about install?  Is that how I always have to run it?  In addition, it's freezing up and not listing any of the server names for me to join.  Any ideas?  Should I use the 32-bit driver on the nvidia site or what can I do to fix this?

I know I apologize and I'm so new to this...If you think it's frustrating for you, imagine how I feel looking at a screen and asking "Which way do I go, George, which way do I go? LOL

---

### Post by Sockerdrickan on 2007-12-11
Don't worry about a driver if you installed it the way I just told you!

---

### Post by Evil Jinn on 2007-12-11
I installed the driver the way you said. 

I still have the issue of missing pk.3s that I don't know where to put them because I can't find a folder like I was able to with WinXP.

What is the command to run ET after the initial install?

This is all new to me; I feel like a complete idiot like when I got my first computer and was so overwhelmed on how to begin.

For some reason, even though I tell it to enable punkbuster, it doesn't.  I'm also going to need to replace my etkey with my admin and add my autoexec.cfg to my etmain.  Where do I find the right place to put these?

---

### Post by eljoeb on 2007-12-11
I'm really not sure what to say about Ubuntu but for me the install was easy; as long as you have the DVD in your drive when you run it you would be cool.  I know the pk.3's get copied during install... maybe Ubuntu does this different.  I had to choose a location for the install and the "etqw" file. Then open a terminal and get to that directory (cd etqw if the folder its in is etqw) and type ```
./etqw
```

Let us know what is happening so we can help you.

---

### Post by Evil Jinn on 2007-12-11
I know nothing of finding directories and subdirectories here.  My et-linux-2.55.x86.run is in my home folder so is my pbsetup.run.  I know that much because I directed them there.

I need my pb enabled because our server streams through pb or I can't even get to my clan mates.

hav0x said in another thread about click deploy, internet and enable from there.  I can't even find a function like that anywhere in my options.   *bangs head on keyboard*   AAAAAAAAH] 

These are the hopefully the last things I need:
1. find etmain to replace etkey with my admin one and my autoexec.cfg
2. enable punkbuster because the ingame feature will not let me do it from there.

I have no idea where to find etmain or how to enable pb so I'm at the mercy of everyone here.

---

### Post by eljoeb on 2007-12-11
Wow... pretty much everything you said is stuff I never had to do.  While I'm more than a little confused about the reason you're using Ubuntu, we should be able to help you.  What directory did you tell the installer to install to?   Did you download the nomedia installer or the full?

Its here: [http://zerowing.idsoftware.com/linux/etqw/](http://zerowing.idsoftware.com/linux/etqw/)

Just "cd" to this directory.  If you know where you told it to go tell us and we can tell you how to get there.  When you open a terminal, you are in home.  If you want to enter a folder in your home type:

```
cd foldername
```


If you need help running the installer or have questions, IM me in AIM... i sent you the screen name.  I'll try to help if I can.

---

### Post by Evil Jinn on 2007-12-11
Ok big problem.  Joe and I actually sat and tried to figure this out for many hours why pb will not recognize my game and initiate with et.

For some odd reason /home/jinn/.etwolf is empty

et was installed here instead /root/.etwolf (not sure why)

Now how do I uninstall this and do it properly so pb will recognize et?

This was the install command I used as I was told to use:
sudo sh et-linux-2.55.x86.run

I need to uninstall from /root/.etwolf and reinstall it to /home/jinn/.etwolf.

Any ideas because I cannot do this alone seeing it's only my first 24 hours of linux.

However my pb feels the need to associate et with this path:  /usr/local/games/enemy-territory.   UGH



NVM I fixed it.

---

