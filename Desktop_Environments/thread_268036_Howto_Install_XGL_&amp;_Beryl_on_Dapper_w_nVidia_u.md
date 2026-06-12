---
title: "Howto: Install XGL &amp; Beryl on Dapper w/ nVidia using apt-get"
date: 2006-09-29
forum: Desktop Environments
---

### Post by djRobbieF on 2006-09-29
Version 1.5

I put together an easy-to-follow reference for installing XGL and Beryl on Dapper for those of us with nVidia cards.  This is taken from my blog at [blog.djrobbief.com?p=23](http://blog.djrobbief.com/?p=23).  Some sections will not apply to you, as they are specific to my hardware, so I have added _**headings**_ throughout the howto to help you skip over irrelevant information.

Remember, Beryl is still pre-alpha, and comes with no warranty.  I'm happy to help, but cannot be held liable for any problems.


_**Introduction**_

Since upgrading my system this week, I decided it would be best to reinstall my operating system. When I did this, I found that compiz has now been forked to beryl, and there are no “public” releases of beryl yet, and compiz has been removed from the apt repositories. SO, what am I to do? I’ve totally fallen in love with compiz over the past several weeks since first installing XGL, and I just cannot go back to a flat desktop.

I thought about jumping to Ubuntu 6.10 Edgy Knot-3, but after trying it from CD, it’s just too buggy for my tastes at the moment. My wireless simply would not work despite my brief efforts, and the OpenOffice crashing problem is not something I want to have to deal with. For now, I’m happy with Dapper 6.06, so I’ll just bite the bullet for the next month or so while we wait for a stable version of Edgy to be released in October. Of course, because I’ll be using Dapper, that means I will also require XGL to run Beryl.

**My Revised Specs:**

    * Intel Pentium D Processor, 3.4GHz (this is why we’re using the 686-smp kernel - notice, I’m staying away from the amd64 kernel, which I tested as actually being a LOT slower on this emt64 processor than the 686 kernel)
    * 2GB dual-channel DDR2-667 RAM (2 sticks of 1GB each)
    * 200GB 7200.10 RPM Seagate SATA Hard Drive
    * eVGA nVidia 7300 GT PCI-E Graphics Card with 256 MB DDR3, Dual-DVI
    * 1680×1050 Widescreen 20.1&#8243; TFT Display, DVI
    * Integrated Intel audio, lan, etc.
    * TRENDnet TEW-423PI wifi pci card (and TRENDnet says you can’t use it in Linux - HAH!)


_**Install Ubuntu**_

Ubuntu’s boot disk booted up no problem this time around. So I guess the previous problem was in fact my nvidia 7600 not working with the nv drivers.

Once I got to the desktop, the first thing I did was set up my wireless WEP password so that the installer could apt-get anything it needed. This was no problem, as my el-cheapo 802.11g card detected and functions fine.

Bring up the Ubuntu installer, and let it take over my whole 200 GB SATA drive. Once it’s done installing, I chose the “Reboot now option”.


_**Update Kernel**_

Once booted, I go into the Linux terminal and type:

```
[color=#FE000A]sudo apt-get update
sudo apt-get install linux-686-smp[/color]
```

This will allow me to take advantage of the dual-core nature of the Pentium D processor by installing the optimized kernel. Once that kernel is installed, I restart the computer.


_**Fix Wireless Networking**_

After updating the kernel, the wireless no longer worked. My wireless card uses the acx Linux wireless driver, so here’s the solution: (it’s always best to use the REAL Linux driver rather than ndiswrapper, which loads the [unstable] Windows driver into Linux)  I determined my driver by using the [color=#FE000A]iwconfig[/color] command and looking under "Nickname" for my wireless adapter.

```
[color=#FE000A]sudo rmmod acx
cd /lib/firmware/$(uname -r)/acx/default[/color]
```

Type ls .. to see the available acx firmware versions.
Find the firmware that works for you. Just do the following starting with the highest number and keep counting down until you find one that works. This way you know you’re using the “latest” which works with your card. This is the one that worked for my TRENDnet TEW-423PI rev.a card:

```
[color=#FE000A]sudo cp ../1.2.1.34/* .[/color] - YES - you have to include the period at the end
[color=#FE000A]sudo modprobe acx[/color]
```

Now, wireless networking is running in the 686 kernel.


_**Install & Configure nVidia Drivers**_

```
[color=#FE000A]sudo apt-get install nvidia-kernel-common nvidia-glx
sudo gedit /etc/X11/xorg.conf[/color]
```

Find the “Module” section. Comment out the “Glcore” and “dri” modules and make sure a “glx” module is there.

Now find the “Device” section.

Change every line but the “Identifier” line to look just like this:

```
Section "Device"
Identifier- leave this line alone!
Driver "[color=#FE000A]nvidia[/color]”
BusID “PCI:1:0:0&#8243;
[color=#FE000A]Option “RenderAccel” “true”[/color]
EndSection
```

I also take this time to add my screen resolution to each of the Display/Modes lines by adding [color=#FE000A]“1680×1050&#8243; “1280×800&#8243;[/color] to the start of each, allowing my widescreen, high-res display to function at super gorgeous resolution.

Make sure your default color depth is 24! ([color=#FE000A]DefaultDepth 24[/color] - in the “Screen” section). Save that file and close it.


_**Install & Configure XGL and Beryl**_

Now, edit /etc/apt/sources.list (sudo gedit /etc/apt/sources.list) and add:

```
[color=#FE000A]deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
sudo gedit /etc/gdm/gdm.conf-custom[/color]
```

Go to the very bottom of the file, and just below the [servers] section, add:

```
[color=#FE000A]0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true[/color]
```

Go to System –> Preferences –> Sessions –> Startup Programs and add the following two entries:
```
[color=#FE000A]xmodmap -e "keycode 22 = BackSpace"
beryl-manager[/color]
```

Reboot. Yes, a real reboot.  It may not be necessary; but it sure is fun to boot up into Beryl that first time  :)


_**Enjoy**_

Upon reboot, you will be in Beryl, and you’ll see a little beryl gem on your Gnome panel. Click on that for any settings or changes you’d like to make to your Beryl system, including themes, shadows, effects, skyboxes, etc.

Basic XGL / Beryl keys:
CTRL + ALT + Left/right arrow key. Switches to the new side of the cube.
CTRL + ALT + SHIFT + Left/Right arrow key- Takes the in focused app around cube.
CTRL + ALT + Hold Left Mouse Button - allows you to use the mouse to rotate cube.
ALT-TAB - Task switcher - choose a task on the current side of the cube
CTRL-ALT-TAB - Task Switcher - choose a task on ALL sides of the cube


Hope that helps some of you out.  And nice to find Beryl in the apt repositories this morning!  Thanks all!

---

### Post by beerorkid on 2006-09-29
nice just noticed the repo was filled up with goodies.

I already had quinstorms compiz and just did a 

```
sudo apt-get install beryl emerald emerald-themes
```
and it is rocking in shivvery blurry awesomeness.

---

### Post by djRobbieF on 2006-09-29
Woohoo!  Yeah, I'm loving it thoroughly  ;)

---

### Post by heisters on 2006-09-29
Hmmm... doesn't quite work for me. Beryl falls back to Metacity. When I run beryl from the commandline I get:

```

$ beryl --replace
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
$

```

The [edgy/beryl thread](http://www.ubuntuforums.org/showthread.php?t=263851) has repos for some hacked kernel modules, perhaps dapper needs something equivalent? Anyway, :(

---

### Post by beerorkid on 2006-09-29
> **heisters said:**
> Hmmm... doesn't quite work for me. Beryl falls back to Metacity. When I run beryl from the commandline I get:


did you try ```
beryl-manager
```

I still get an error when it starts up and have to open up the manager and get into beryl.

---

### Post by djRobbieF on 2006-09-29
Yeah, launching beryl without beryl-manager didn't work for me either; which is why I specified to use beryl-manager.

If it's defaulting to metacity at that point, I click on the beryl icon and choose "Select Window Manager" and click on Beryl.

---

### Post by squimmy on 2006-09-29
Is it possible to use this guide for ATI cards? Can I just ignore the nVidia section and go straight to "Install & Configure XGL and Beryl"?

---

### Post by jimtb on 2006-09-29
Hmm I guess I'm doing something wrong here. Beryl is a complete replacement for compiz isnt it? So I removed compiz... Can I make it work on KDE? I just get an X server crash when I select beryl instead of kwin...

---

### Post by GoombaDoolies on 2006-09-29
WHen I attempted to start to install the packages, I ended up with the message:

E: Couldn't find package beryl

Xserver and all that were fine.  I was aware of compiz changing their name and had to change the apt-get command to reflect beryl not compiz, emerald not cgwd, but it still can't find the right packages.

btw, i did add the 2 lines to /etc/apt/sources.list

---

### Post by beerorkid on 2006-09-29
well they are in the repository.

did you do a sudo apt-get update?

also not pushing my repo, but I think it is the main one that others mirror off of.  So it might be the most current.  I just host, not maintain.

---

### Post by GoombaDoolies on 2006-09-29
> **beerorkid said:**
> well they are in the repository.

did you do a sudo apt-get update?

also not pushing my repo, but I think it is the main one that others mirror off of.  So it might be the most current.  I just host, not maintain.

Cheers for that.  I haven't checked your repo, but I did put those lines there.  My bad.  I still haven't figured out how to get my DNS entries to remain at 4.2.2.1 and 4.2.2.2, they keep resetting themselves every few hours.  No biggie :)

---

### Post by sublimespot on 2006-09-29
Thank you very much. I installed Edgy last night to see Beryl live in action and loved it! but it crashed at least 4 times in the hour or so of playing. 

At work, I run XGL with Compiz on 6.06. When I got to work today I updated my apt sources to the ones you specified, installed Beryl and it works great! Im going to downgrade back to 6.06 at home and use this until Edgy goes final. Thanks !!!

---

### Post by GoombaDoolies on 2006-09-29
I killed my ubuntu and got stuck at the prompt.  I did realise that I hadn't added the rendering true line in my xorg.conf, so i did so from the prompt, but still didn't work.

I did skip over the bit where it says update the kernel - didn't know if I was on 686 or 386.  how would I check that?  I'm not on AMD64 because it doesn't really load well.

Sorry, I am a newb, know that, but i figure the more I cut my teeth, the more I'll learn.

Any suggestions?:)

---

### Post by beerorkid on 2006-09-29
to figure out your kernel: ```
uname -r
```

---

### Post by GoombaDoolies on 2006-09-29
Thanks for that again.  I'm reinstalling dapper (takes 20 minutes max), so I don't mind.  I want to go through the instructions slowly.

I have an ATI card, forgot to mention - I have to figure out how to update those drivers.

I think I have found somewhere.  Once I try it out, i will post the results.

I have a 386 based kernel, so i assume that i replace the 686 with 386 in the instructions?

---

### Post by squimmy on 2006-09-29
So is it possible to adapt this guide to use an ati card instead of a nvidia card?

---

### Post by djRobbieF on 2006-09-29
Hey all, sorry I was away for a bit and couldn't reply.

The kernel aspect of the howto is not what kernel you're RUNNING, it's what kernel you WANT to run.  uname -r will only show you what kernel you're RUNNING, not what kernel you want to run.  ALL Ubuntu installs (from the "PC" disc) will default as 386.  But that's not ideal for newer computers.  If you have anything after a Pentium II, you should probably try the 686 kernel (sudo apt-get install linux-686).  If your processor supports hyperthreading (pentium 4) or dual core (Pentium D, etc), you should also install the smp support to allow your Ubuntu installation to utilize both cores on your processor (sudo apt-get install linux-686-smp).  This is not to do with XGL or Beryl though; it's a simple preference to speed up your system - which can be nice!  But skipping this step will NOT affect your Beryl / XGL installation.  Extreme newbies / people not ready to experiment may wish to skip over the kernel update, as it can affect other things, like how it made my wireless stop working.  If you don't know how to resolve such an issue, it can be a headache and make you think your system is broken.  It's easy to roll-back, regardless, if you mess it up.

Note: If you WANT to be running the 386 kernel, you can completely skip over the kernel update section, as your system already HAS the 386 kernel.

Yes, you can adapt this tutorial to support ATI cards; no problem.  Just install your ATI drivers from the ATI site when you would normally install the nvidia drivers.  You may need to tweak some settings, and I'm sorry but I'm an anti-ATI guy  ;)  But I'm sure you can find some config help in the forum.  I know the ATI drivers are REALLY simple to install though (you set the file as executable, run it, and it pops up a nice GUI).  Are there any ATI users who wouldn't mind giving this a try and post your response in this thread to help the ATI users?

GoombaDoolies - I want to help you get your system back if I can.  What happens when you get the prompt?  Could it be the video card?  Do you have an nVidia card?  Because if you followed the directions for nVidia, but don't have nVidia, that may pose a problem; but it's easily resolvable.  What errors are being output to the terminal prior to getting the linux prompt?

I'll keep watching for questions in case you have any more problems.  Forgive me if I seem slow to respond this weekend, as I have to work  :(  Thanks to those pitching in with this thread (beerorkid - you rock!)  :)

Cheers,
Robbie

---

### Post by handband2 on 2006-09-29
Thanks for the Howto!!!!

Though I'm having a problem with setting up:

```
sudo gedit /etc/gdm/gdm.conf-custom
```
```
[color=#FE000A]
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true[/color]
```

I have xinerama setup (two monitors as one desktop) with an Nvidia 7600.  If I put what you have above in the gdm.con-custom file, gdm starts with errors.  Does anyone know how to fix this??

Thanks!!

Nevermind....DUH!!!  I forgot to install xserver-xgl with its dependencies.

It actually works perfect wine xinerama!!!

---

### Post by djRobbieF on 2006-09-29
Hmm, unfortunately I haven't tested with multi-monitors yet.  What are the errors you're getting, maybe someone will have an idea.

BTW, from your quote, you're missing 0=Xgl.  Did you leave that out of your file by chance?

---

### Post by beerorkid on 2006-09-29
I use it with twinview, works great.

[http://ubuntuforums.org/showthread.php?t=221174&highlight=twinview](http://ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

having an nvidia card is almost too easy.

---

### Post by djRobbieF on 2006-09-29
... not to mention sexy.  ;)

---

### Post by handband2 on 2006-09-29
Nevermind....DUH!!! I forgot to install xserver-xgl with its dependencies.

It actually works perfect wine xinerama!!!

---

### Post by djRobbieF on 2006-09-29
> **handband2 said:**
> Nevermind....DUH!!!  I forgot to install xserver-xgl with its dependencies.

It actually works perfect wine xinerama!!!

Hehe, yeah - installing the packages is perhaps an important step  ;)  Not to be omitted.  Cheers - glad you got it working!

---

### Post by sublimespot on 2006-09-29
I am also using Dapper 6.06 + Beryl + XGL + Twinview as BeerOrKid is. Works great and I got a lot of props at work today. :)

---

### Post by Vae Victis on 2006-09-29
This is Awesome! I just switched to Ubuntu about a week ago! This is definately what ive been looking for! Thanks so much for the help! Works Perfect!

---

### Post by GoombaDoolies on 2006-09-30
Hey peoples, I went away and found some additional material.  This is geared to both ATI cards, but works.  I have referenced the sites I got the info from.  Thank you so much (esp djRobbie...) for all your help and good wishes.

Download the fglrx driver for ATI [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

 Method 1: Installing Dapper's Included Driver (8.25.18)

The included fglrx driver supports Radeon 8500+ and the X-series cards up to X1900.

Unfortunately OpenGL seems to be broken for R200 cards (everything below Radeon 9500) in this driver version. The Troubleshooting section describes how to fix this after xorg-driver-fglrx is installed.
[edit]
Installing the driver

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

Help on enabling repositories can be found at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Now Reboot your system:

sudo shutdown -r now

An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc.
[edit]
Confirm that it works

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

Grab the stuff from the repositories as per this thread.  I found that the command line was a bit finicky, i just jumped into synaptic and grabbed all the ones listed on the line:

```
sudo apt-get update && sudo apt-get install xserver-xgl beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes 
```

SO basically from the synaptic (making sure you have the required lines added to /etc/apt/sources.list) package manager, click

beryl (which tags most of the bits)
xserver-xgl
emerald-themes

The afterwards, you need to create the Xserver file and set up beryl to work:

[http://www.ubuntuforums.org/showthread.php?t=268149&highlight=XGL+Beryl]("http://www.ubuntuforums.org/showthread.php?t=268149&highlight=XGL+Beryl")

I found that these instructions helped me get to the point where I could test if it was working before switching it permanently and thus still be able to use gnome.

Make a startup script for Xgl

There are many ways for this, however the following one was always working for me when the others failed.

make the file:
Code:

gedit ~/.Xsession

add these:

```

#!/bin/sh
# Start up Xgl and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start GNOME
exec gnome-session

```

save and make it executable:

Code:

chmod +x ~/.Xsession

This is it. Now reboot, and choose "Default Session". Open up a terminal and type
Code:

beryl-manager

You should see a splash screen and beryl will take over metacity. If anything went wrong you can switch back to normal, just log out, switch to GNOME Session and delete ~/.Xsession. If it works you should add "beryl-manager" in startup programs (System -> Preferences -> Sessions).
Also, if you have problems with your GTK theme/icons/numlock etc. after enabling Xgl, you should add "gnome-settings-daemon" in startup programs too (following the beryl entry").

Hope this isn't too long, helps out and is readable.  Glad I could help, i feel a little less like a noob now. :)

---

### Post by billflu on 2006-09-30
Thank you. This guide was very helpful. To improve it you might just want to add
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
```
after adding to the sources.list

---

### Post by ericesque on 2006-09-30
I can confirm that the install method for beryl works on my ATI system (mobile X600) I had the fglrx drivers going and followed the beryl direction in the first post.

Nice work.  XGL/Compiz were always a bit of a pain on my system.

---

### Post by elsupermang on 2006-09-30
Very nice, was easy to install.

Only complaint is, it's constantly using 20% CPU usage on idle and 30-35% with effects, is this because its still early development or because there is something wrong with my install?

---

### Post by orb9220 on 2006-09-30
Great guide been first day on edgy+beryl runs great on my nvidia. Pissed off some xp user's.

They asking me to show them more of this ubuntu thing. And I can hear them muttering under thier breathing gates,microcrap,*(&(m,*)(8,crap

---

### Post by theslut on 2006-09-30
this guide worked first time for me on dual monitors! So simple.


Totem and mplayer don't seem to want to work properly. any fix for this? i get window corruption in totem (the video is ok) and mplayer is just plain weird.

Lastly, how do i fix the the ctrl / alt +mousewheel feature in The GIMP to pan around and zoom in/out of an image? The function has now been taken over by beryl and seems to adjust the window contrast instead.

---

### Post by The Pinny Parlour on 2006-09-30
Thanks for the heads-up.  Just went into synaptic and updated anything with the word Beryl in it.  Works fine, but it seems I don't have any decent window border themes.  Anyone know where to get some great themes?

Cheers,

---

### Post by djRobbieF on 2006-09-30
> **The Pinny Parlour said:**
> Works fine, but it seems I don't have any decent window border themes.  Anyone know where to get some great themes?

Those should have come in when you apt-get'd emerald-themes.  Click on the ruby looking thing (Beryl Manager) and choose "Emerald Theme Manager".  You should see a bunch there.

---

### Post by djRobbieF on 2006-09-30
> **theslut said:**
> Totem and mplayer don't seem to want to work properly. any fix for this? i get window corruption in totem (the video is ok) and mplayer is just plain weird.

Yeah, well, it's still pretty early in development.  I get the same thing, but you minimize and restore it a couple times, or press F (fullscreen) and it usually goes away pretty quickly.  Just one of those little bugs that they'll be working out, I'm sure.


> Lastly, how do i fix the the ctrl / alt +mousewheel feature in The GIMP to pan around and zoom in/out of an image? The function has now been taken over by beryl and seems to adjust the window contrast instead.

Not sure the specific fix, but you could either re-assign the GIMP feature, or the Beryl feature (your choice).  It'll probably be easier to find it in GIMP, as Beryl's config could take some looking through before you find the combination.  Let us know if you find it.  It's simply that BOTH programs are associating with the same key combination; so changing either program should resolve the conflict.

---

### Post by djRobbieF on 2006-09-30
> **billflu said:**
> 
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -
```
after adding to the sources.list

I have never used wget.  What do these commands accomplish?  I'll be happy to add them to the tutorial with an explanation.  Thanks!!

---

### Post by djRobbieF on 2006-09-30
> **GoombaDoolies said:**
> Hey peoples, I went away and found some additional material.  This is geared to both ATI cards, but works....

Thanks for your ATI addition, GommbaDoolies!!  And for the props  ;)

---

### Post by theslut on 2006-09-30
think i worked it out, go to the "brightness and saturation" settings and uncheck the shift and control checkboxes in the mouse tab.

I've got 3 more issues now :)

1. everytime i log into the desktop it switches to American keyboard. Which is annoying as I use a Swedish one.

2. How do i get rid of that mouse gesture for cascading the windows or bringing the window i was working on to the centre of the screen? It drives me totally nuts, especially since i seem to do it without knowing what i am doing.

3. Is there anyway of turning of transparency for a particular application? It's really annoying to what a video witha  transparent window just because it's not focussed at the front.

---

### Post by djRobbieF on 2006-09-30
> **theslut said:**
> think i worked it out, go to the "brightness and saturation" settings and uncheck the shift and control checkboxes in the mouse tab.

Glad you got it fixed!  Thanks for posting the fix.


> 1. everytime i log into the desktop it switches to American keyboard. Which is annoying as I use a Swedish one.

That's an easy one.  Remember when you added "xmodmap /usr/share/xmodmap/xmodmap.us" to the startup?  **Remove it.**  But make sure you then add:
```
xmodmap -e "keycode 22 = BackSpace"
```

Those commands will make sure you don't have the "shift-backspace crashes Beryl" problem.  ;)


> 2. How do i get rid of that mouse gesture for cascading the windows or bringing the window i was working on to the centre of the screen? It drives me totally nuts, especially since i seem to do it without knowing what i am doing.

I dont' know what you're referring to - the "mouse gesture".  :-k 


> 3. Is there anyway of turning of transparency for a particular application? It's really annoying to what a video with a transparent window just because it's not focussed at the front.

I know the answer to this is YES; but I don't know how yet.  I still haven't begun experimenting with transparencies yet.  For now, until someone provides a better solution, go to Beryl Manager --> Beryl Settings Manager, choose **Window focus leaves a trail** and change "Opacity level of completely unfocused windows" to 100%.

---

### Post by OpticalIllusion on 2006-09-30
IT WORKS!  Thank you!

My only problem right now is that during the installation (either the kernel or XGL) direct rendering was turned off on my Nvidia card.  How do I turn it back on?

---

### Post by djRobbieF on 2006-09-30
> **OpticalIllusion said:**
> My only problem right now is that during the installation (either the kernel or XGL) direct rendering was turned off on my Nvidia card.  How do I turn it back on?

XGL does not allow direct rendering.  Once Edgy is stable, we'll be using Xorg 7.1, and will no longer require XGL - but for now, you can't use direct rendering with this configuration.  Sucks, I know.  But we're all eager for Edgy Stable  ;)

Sorry I don't have better news  :???:

---

### Post by OpticalIllusion on 2006-09-30
> **djRobbieF said:**
> Did you remember to add glx to the module section of xorg.conf?  When you commented out dri, you should have made sure there was a [COLOR="Red"]Load "glx"[/COLOR] command in there.
Yeah, it was already there after installing the Nvidia driver from Automatix.

---

### Post by djRobbieF on 2006-09-30
> **OpticalIllusion said:**
> Yeah, it was already there after installing the Nvidia driver from Automatix.

Please read my edited post.  You caught me as I was still thinking  ;)

---

### Post by OpticalIllusion on 2006-09-30
> **djRobbieF said:**
> Please read my edited post.  You caught me as I was still thinking  ;)
Ok, gotcha.  But, don't I need direct rendering to work to be able to use the desktop cube?  Because right now, ALT + TAB + Left/Right Arrow isn't doing anything.

---

### Post by djRobbieF on 2006-09-30
No, you don't.  And that key combination does not exist.

Try: CTRL-ALT-left arrow.

---

### Post by trivialpackets on 2006-09-30
This worked perfectly well for me.  Thanks for the How To.

---

### Post by djRobbieF on 2006-09-30
> **eric.proctor said:**
> This worked perfectly well for me.  Thanks for the How To.

Glad it worked for you eric.  Cheers!

---

### Post by OpticalIllusion on 2006-09-30
> **djRobbieF said:**
> CTRL-ALT-left arrow.
Yeah, my bad ment to say CTRL + ALT + arrow, but it doesn't work.

---

### Post by djRobbieF on 2006-09-30
Did you remember to set beryl-manager to autostart with your system?  Drop to a linux terminal and type beryl-manager, and then try.

---

### Post by OpticalIllusion on 2006-09-30
> **djRobbieF said:**
> Did you remember to set beryl-manager to autostart with your system?  Drop to a linux terminal and type beryl-manager, and then try.
Yes, it's set to autostart.

I did notice that when I switch workspaces, it rotates around a cube, but I can't manually control the cube in any way.

---

### Post by djRobbieF on 2006-09-30
CTRL-ALT-HOLD MOUSE BUTTON and move the mouse.

---

### Post by OpticalIllusion on 2006-09-30
Doesn't work. :(

---

### Post by djRobbieF on 2006-09-30
weird.  And you're sure you didn't miss ANY steps?

Do you see the beryl manager icon up at the top right of your screen?

---

### Post by OpticalIllusion on 2006-09-30
I got it!  Turns out I had a Triplebuffer option turned on in my xorg.conf.  I think I had to turn it on the last time I tried to install Compiz (which didn't work).

Once, again, thank you very much for this How To. :D

---

### Post by djRobbieF on 2006-09-30
> **OpticalIllusion said:**
> I got it!  Turns out I had a Triplebuffer option turned on in my xorg.conf.  I think I had to turn it on the last time I tried to install Compiz (which didn't work).

Once, again, thank you very much for this How To. :D

Wonderful!  Glad it's working for you now!!!

Beautiful, aint it?  ;)

---

### Post by OpticalIllusion on 2006-09-30
> **djRobbieF said:**
> Wonderful!  Glad it's working for you now!!!

Beautiful, aint it?  ;)
Yes it is.  This is the first XGL that I've even gotten to work, btw.  Maybe it's because I'm finally using Beryl instead of the outdated Compiz?

---

### Post by beerorkid on 2006-09-30
> **theslut said:**
> 
2. How do i get rid of that mouse gesture for cascading the windows or bringing the window i was working on to the centre of the screen? It drives me totally nuts, especially since i seem to do it without knowing what i am doing.


beryl settings manager --> scale --> screen edges and corners

or just turn it off.

---

### Post by djRobbieF on 2006-09-30
> **OpticalIllusion said:**
> Yes it is.  This is the first XGL that I've even gotten to work, btw.  Maybe it's because I'm finally using Beryl instead of the outdated Compiz?

Well, I had compiz running using practically the same method as I've used here... so I'll bet it's just the method.  So I'm glad you've got 'er going based on this.  Makes me feel good to know I've helped some people get this going  :)

---

### Post by The Pinny Parlour on 2006-09-30
> **djRobbieF said:**
> Those should have come in when you apt-get'd emerald-themes.  Click on the ruby looking thing (Beryl Manager) and choose "Emerald Theme Manager".  You should see a bunch there.

Thanks for your reply. 

None listed there though.  :(

---

### Post by djRobbieF on 2006-09-30
> **The Pinny Parlour said:**
> Thanks for your reply. 

None listed there though.  :(

Do a:
```
sudo apt-get update
sudo apt-get install emerald emerald-themes
```

Then try.  Let me know.

---

### Post by theslut on 2006-09-30
> **beerorkid said:**
> beryl settings manager --> scale --> screen edges and corners

or just turn it off.

thats the one :) thank you!

---

### Post by The Pinny Parlour on 2006-09-30
> **djRobbieF said:**
> Do a:
```
sudo apt-get update
sudo apt-get install emerald emerald-themes
```

Then try.  Let me know.

Has done the trick. Thank you very much.  :)

---

### Post by djRobbieF on 2006-09-30
> **The Pinny Parlour said:**
> Has done the trick. Thank you very much.  :)

Great.  No problem.

---

### Post by squimmy on 2006-09-30
Am I the only one finding some of the effects ugly? When I change window focus, the new window fades in in what appears to be just 2 frames, so it looks very choppy. Same for maximising an open-but-not-maximised-window, when I hit the maximise button, it maximises very choppily. Also, resizing windows is *incredibly choppy. **incredibly** choopy. Near unusable.*

In fact a lot of it is very choppy.


Aprt from the choppiness, it looks great! I LOVE the minimise thing where I kinda gets sucked into the taskbar. Very cool. Also, I assume that I am supposed to of lost hardware acceleration?

Gotta say, I prefer compiz. But this is still very good and very cool.

---

### Post by djRobbieF on 2006-09-30
> **squimmy said:**
> In fact a lot of it is very choppy.

None of what you've explained is normal.  You either have something configured incorrectly, or your system cannot handle the effects.

---

### Post by beerorkid on 2006-09-30
and all of the "features" can be customized.  I make most really fast so they do not take away from my productivity but I can still have cool stuff.

Anyone know how to get wobbly menu's back?

---

### Post by squimmy on 2006-09-30
Damn, I was afraid of that. My system:

amd 3200+
1 gig ram
radeon x800


itis a pretty good system. I can run 99% of windows games at full settings with no chopiness.

I'm using the fglrx drivers that come with ubuntu repository, 8.25.18 although when I do "flgrxinfo" I get.....

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.5814 (8.25.18)
```


I followed [this guide.]("http://www.ubuntuforums.org/showpost.php?p=1561758&postcount=26")


Anything I've done wrong?

---

### Post by djRobbieF on 2006-09-30
> **beerorkid said:**
> Anyone know how to get wobbly menu's back?

Woohoo!  Another lover of the wobbly!

Beryl Settings Manager --> Wobbly Windows --> Map Window Types

Turn on PopupMenu, Unknown and DropdownMenu

!!

---

### Post by djRobbieF on 2006-09-30
> **squimmy said:**
> OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.5814 (8.25.18)

I am not familiar with your card (I really do hate ATI cards), but the first thing I notice is that your drivers are old.

Current ATI Radeon drivers are Version: 8.29.6

---

### Post by steveneddy on 2006-09-30
OK - I have installed compix in the past and it said on restart that I need to choose the keyboard options for X or Gnome. As I would like to go back to using compiz/beryl again, could someone please tell what KB settings I need to use? I would assume X, but an answer would help me when I get off of work today and try this on my home PC.

ALSO - do I need to uninstall compiz to run beryl? I think I installed from the repos (Synaptic) and it is still installed, but I haven't been running it (compiz). 

Looking forward to wasting my Saturday night ignoring the kids and playing with this. Sounds exciting. 

ALSO - one last thing - I was on #beryl the other night a few days ago and I was able to DL a version or beryl, but it didn't install, do I need to delete this directory from my /home folder?

Sorry for all of the questions, but I would like to get this right this time around. 

I guess I need to uninstall xcompmgr also? I use xcompmgr to see the pretty drop shadows and some transparancy sometimes, just for show purposes to friends and when I'm bored. 

I'm not a noobee, but ... "...not too bright, though."

Thanks in advance - StevenEddy in beautiful downtown Fort Worth, Texas.

Yes - I am THE StevenEddy - thank you. Glad to meet cha. How's the wife & kids?

---

### Post by djRobbieF on 2006-09-30
> **steveneddy said:**
> ... could someone please tell what KB settings I need to use? I would assume X, but an answer would help me when I get off of work today and try this on my home PC.

Go through the installer first, and THEN ask us, if it appears again.  I've never seen that issue in relation to compiz OR Beryl.  Seems like something else altogether.


> ALSO - do I need to uninstall compiz to run beryl? I think I installed from the repos (Synaptic) and it is still installed, but I haven't been running it (compiz).

Although it's not technically necessary, I would suggest you remove all the old packages.


> ALSO - one last thing - I was on #beryl the other night a few days ago and I was able to DL a version or beryl, but it didn't install, do I need to delete this directory from my /home folder?

You will not need those downloads anymore, as Beryl is now available through apt-get, as per my tutorial at the top of this thread.


> Sorry for all of the questions, but I would like to get this right this time around.

Don't apologize for asking questions; that's what this is here for  :)


> I guess I need to uninstall xcompmgr also? I use xcompmgr to see the pretty drop shadows and some transparancy sometimes, just for show purposes to friends and when I'm bored.

Once you get beryl running, you won't need a shadow thing... it's all built-in.  So go ahead and remove it if you like  :)

---

### Post by squimmy on 2006-09-30
I don't see how it will make a difference though, I'm having to run it on xserver 1:0 and that doesn't appear to have any hardware acceleration. The driver is running on 0:0 or something like that. That's what fglrxinfo is telling me.


I'll upgrade it, or try to and see what happens.

---

### Post by djRobbieF on 2006-09-30
> **squimmy said:**
> I don't see how it will make a difference though, I'm having to run it on xserver 1:0 and that doesn't appear to have any hardware acceleration. The driver is running on 0:0 or something like that. That's what fglrxinfo is telling me.

Yeah; well, I admit, I'm really not sure when it comes to ATI cards.  WHEN I had an ATI card, I found I had to always have the latest drivers, or else some 3d stuff sucked.  So that's just the first place I'd start in your case.

Let us know how it goes.

---

### Post by squimmy on 2006-09-30
Well, i've just upgraded to 8.29.6.

Amazingly, my glxgears score has gone *down.* By 3000.

No difference has been made in Beryl :(

Damn dissapointment.

---

### Post by djRobbieF on 2006-09-30
My gosh.  That bites.  Sorry I don't know more about ATI squimmy.  Maybe check the official beryl forums and see if someone there is able to help?  [GO HERE]("http://forum.beryl-project.org/")

---

### Post by handband2 on 2006-09-30
Here is how I created an Xgl session.  Rather than have Xgl load on Defualt Session.

Here is the original post which helped me:  [http://forum.beryl-project.org/viewtopic.php?id=389]("http://forum.beryl-project.org/viewtopic.php?id=389")

If you used the Howto of [djRobbieF]("http://ubuntuforums.org/showpost.php?p=1559948&postcount=1") You'll need to remove the files or turn it off:
```
sudo gedit /etc/gdm/gdm.conf-custom
```
Turn off XGL from the default gnome session.
```
#0=Xgl
#[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
#flexible=true
```

Now lets start creating a new session for XGL/Beryl.
Open /usr/bin/startxgl.sh
```
sudo gedit /usr/bin/startxgl.sh
```
Copy and Paste below in /usr/bin/startxgl.sh
```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session
```
Make the file executable
```
sudo chmod 755 /usr/bin/startxgl.sh
```
Open /usr/share/xsessions/xgl.desktop file
```
sudo gedit /usr/share/xsessions/xgl.desktop
```

Copy and paste below into /usr/share/xsessions/xgl.desktop
```

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

Reboot

Once rebooted
Click on **Options **-> Select **Session..** -> Select **XGL**

Some more helpful links with programs running within XGL:
[TVTIME]("http://www.ubuntuforums.org/showthread.php?t=209843&highlight=compiz+tvtime")
[Play openGL based games]("http://www.ubuntuforums.org/showthread.php?t=176636")

---

### Post by steveneddy on 2006-09-30
> Once you get beryl running, you won't need a shadow thing... it's all built-in.  So go ahead and remove it if you like  :)

Thanks - I am finally home and hope to have the time tonight to get most if not all of this done. 

Thanks for the tutorial, of which if these weren't here I wouldn't have tried ANYTHING on Linux or Ubuntu, and thank the posters (is that the correct term?) and the moderators.

I'll let you know how it goes....

Again, Thank You - Steven Eddy

---

### Post by Solver on 2006-09-30
Would this be also safe to try if running the amd64 kernel?

---

### Post by steveneddy on 2006-09-30
> **steveneddy said:**
> Thanks - I am finally home and hope to have the time tonight to get most if not all of this done. 

Sweet!! - SWEET!!!!!

This is so cool - it looks much better than when I did this last year. 

SWEET!!!!

Thank you to whomever made this possible!!!!

Now - daughter wants me to install more memory and PCLinuxOS on her machine.

I almost forgot to mention----

SWEET!!!

Thanks - SE

---

### Post by kebes on 2006-09-30
I've created a wiki version for "Installing Beryl on Dapper w/ nVidia", based on these instructions:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/nVIDIA)

Please update the wiki with any changes required or fixes to common problems.

Oh, and many thanks to djRobbieF for posting the instructions. They worked perfectly for me.

---

### Post by andril on 2006-09-30
Like I said it works great but I noticed my top Panel disappeared :confused: 

it may be the remains of the Compiz - can you tell me what i need running in my Sessions > Startup?

I am running Ubuntu 6.06 LTS
             Gnome
             Nvidia fx5500

Here is my sessions:

compiz --replace gconf (disabled) 
update-notifier (enabled)
cgwd & (enabled)
beryl-manager (enabled)
gnome-window-decorator (disabled)
gnome-power-manager (enabled)
gnome-volume-manager --sm-disable (disabled)
xmodmap /usr/share/xmodmap/xmodmap.us (enabled)
compiz-manager (enabled)
/usr/bin/startcompiz & (disabled)
nm-applet --sm-disable (enabled)


Thanks In Advance!

---

### Post by djRobbieF on 2006-09-30
> **Solver said:**
> Would this be also safe to try if running the amd64 kernel?

Yes, it would.  Just don't install the kernel.  Skip over that.

---

### Post by djRobbieF on 2006-09-30
> **steveneddy said:**
> I almost forgot to mention----

SWEET!!!

Thanks - SE

Another satisifed customer  ;)  LOL.  Glad it worked for you!  Enjoy!!

---

### Post by djRobbieF on 2006-09-30
> **kebes said:**
> I've created a wiki version for "Installing Beryl on Dapper w/ nVidia", based on these instructions

Haha, thanks.  I only just joined the community like a week ago, and I already feel like a celeb!  lol

I really appreciate the community here.  I came from Linspire, and you guys are just SO much nicer  \\:D/

Thanks for putting the credit at the bottom of the wiki.  I appreciate people giving credit where it is due.

Cheers,
Robbie

---

### Post by steveneddy on 2006-09-30
OK - my issues. It is working well, BTW, and I am very happy so far, BUT--

1. No spinning cube. Maybe I need to play with the beryl settings a little more. I don't know at this point. I can make the cube spin if I go to the workspaces area on the lower toolbar (Gnome) and even move apps between them, but no mouse or KB gentures are able to make the cube spin.

2. The . on the NUM keys doesn't work and my NUM LOCK light won't come on at all.

3 Print screen doesn't seem to work for me.

** ** ** ** ** ** ** ** ** ** ** ** ** *

Maybe I need to fool around with it a little, but I remember the cube working in compiz, but it crashed a lot. 

I'm not affraid of the command line, so whomever has an answer, I'll try almost anything. 

I have the Beryl icon and the pretty goodness, wobbly windows, cool transparent window borders, drop shaddow.....just want the cube to tune.

Again...thanks...SE

---

### Post by h0ax on 2006-09-30
Triplebuffer option turned on in my xorg.conf

I am have the same problem as you - where do I turn this off/on whatever?

my ctrl+alt + arrows / left mouse don't work

---

### Post by djRobbieF on 2006-09-30
Yes, hOax and steveneddy - you must turn off triplebuffer in xorg.conf as per the previous posts.

---

### Post by djRobbieF on 2006-09-30
**_Fix the Movie Player_**

theslut private messaged me, asking about fixing the totem movie player.

Here's how.

```
gedit ~/.gnome2/totem_config
```

Hit CTRL-F and search for:
```
video.driver
```

You'll see a line that says #video.driver:auto

Change it to this: (dont' forget to remove the #)
```
video.driver:xshm
```

Now, the anomalies and messed-up grids in movie player will be gone, and it works perfectly.

Cheers.

---

### Post by h0ax on 2006-09-30
I don't see that option in xorg.conf
see:

Section "Monitor"
    Identifier     "DELL 2407WFP"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Monitor        "DELL 2407WFP"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x6
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x6
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x6
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x6
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x6
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x6
    EndSubSection
EndSection

---

### Post by djRobbieF on 2006-09-30
WOW that's a nice monitor.  I thought I had it good  ;)

Are your Modes lines actually truncated like that, or is it just the way it got pasted?

... and why is the busid missing from your Device section?

---

### Post by djRobbieF on 2006-09-30
Under Device, add this:

```
Option "TripleBuffer" "false"
```

---

### Post by steveneddy on 2006-09-30
> **steveneddy said:**
> 
Maybe I need to fool around with it a little, but I remember the cube working in compiz, but it crashed a lot. 



OK - I messed around (don't know what I did) & I was looking at the settings in beryl-manager to get the KB shortcusts and when I tried it, beaytiful spinning wonderfulness!

Sorry for making you read the last post of mine. 

I wanted to post what I did, but honestly, all I did was go to the b-m GUI and look at the settings. 

Thanks for this great tuturial, DJ. Hope we can make you famous.

-SE

---

### Post by h0ax on 2006-09-30
just how it got pasted

yah - got me a 24" dell :]
i just want this to werk - nvidia is working because I get the splash screen when I start into X server
I just don't know how to turn the other thing off
when I do ctl+alt+arrows/mouse I just get the regular desktop switch 
I have beryl installed because the icon is up top - red diamond

---

### Post by h0ax on 2006-09-30
im still getting nothing - 
do I need to install more of nvidia stuff? 
I put that in my xorg - restarted X - still have nothing
btw last post was truncated because of the paste, yes
help =P

busId was missing - I ran this nvidia command and it backed up my xorg // replaced it with a new one - but I just put the old one back with the new device addition

---

### Post by djRobbieF on 2006-09-30
> **h0ax said:**
> when I do ctl+alt+arrows/mouse I just get the regular desktop switch I have beryl installed because the icon is up top - red diamond

Oh gosh, that explains it (you're still using matacity).

Single-click the beryl icon.

Choose SELECT WINDOW MANAGER

Choose Beryl.

---

### Post by h0ax on 2006-09-30
My screen just flickers a little and then it goes back to Gnome one 
hmm...

---

### Post by djRobbieF on 2006-09-30
Argh.  You've gotta be kidding!  Well, you're getting close, I can feel it  :)

Look over the tutorial and make sure you got all the key stuff.

I gotta run for the night, but I'll be back tomorrow!  Surely there are others who can help too.

Have a good one.

---

### Post by djRobbieF on 2006-09-30
WAIT - before I go, I think I found your problem.

Beryl is loading BEFORE the xmodmap command.

For today, REMOVE the xmodmap command from your startup applications.  Tomorrow, I will make you a nice little sh script to load them in the proper order!

So disable the xmodmap command from your startup, and restart the computer.

And whatever you do, don't push SHIFT-Backspace.

Night.

---

### Post by h0ax on 2006-09-30
well
removing the xmod map makes the beryl work fine -- will look forward to hearing from you tom.
having fun playing with it for now :)
thanks man

---

### Post by bored4 on 2006-09-30
hey, i followed it exactly and it didn't work for me. :( 
when i rebooted the x server failed to start. so i use "startx" and it said something like no screen found. ill post my config files.

my xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Option		"UseFBDev"		"true"
        Option          "RenderAccel"           "True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

gdm
```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

im using nvidia drivers 1.0.8762 (6600gt)
kernel 2.6.15-27-686
i do have xmod map before beryl manager

im kinda of a linux newbie so i dunno what i did wrong.

---

### Post by bored4 on 2006-09-30
ok stupid me for not trying this first. but snice xserver did start i reset to an old xorg.conf. well when i started, the beryl manager still loaded. well  i click on the gem and select beryl instead of metacity, and beryl loads, and now it works. but i still don't know why it won't work when i boot into it. if there is something wrong with my xorg.conf or what. so just an update.

---

### Post by djRobbieF on 2006-09-30
Hmm, well, if it works, we're happy  :)   Glad you had an "old" xorg.conf handy anyways.

If you really want us to look through, that's cool - but I assume because it's working now, you're good?

---

### Post by djRobbieF on 2006-09-30
> **h0ax said:**
> well
removing the xmod map makes the beryl work fine -- will look forward to hearing from you tom.
having fun playing with it for now :)
thanks man

Woohoo!  Once again, I was RIGHT!  That's like 3 times in ONE DAY!  A record!  lol

add this to your startup (in replacement for the original xmodmap command:
```
xmodmap -e "keycode 22 = BackSpace"
```

My original code has caused a few glitches, so I think I'll update the howto now  ;)  [done]

---

### Post by bored4 on 2006-09-30
no, when i reboot the x server fails to start. i think theres something wrong with my xorg.conf.  beryl started working once i booted with it off then from the red gem selecting it as my windows manager. i would like to work when i boot into my system instead of everytime i get on, having to select beryl.

---

### Post by djRobbieF on 2006-09-30
Oh, so you mean it is LOADING and all, but you have to set it as your Window Manager each time?

---

### Post by bored4 on 2006-09-30
yes, exactly

---

### Post by djRobbieF on 2006-09-30
Hmm, you're the second person to report that.

My questions to try to get this figured out:

1) Do you have a pretty "default" display setup?  Like, you haven't got X running on a different TTY than F7?

2) Did you use MY instructions for how to run XGL, or someone else'?

3) Have you, in the past, added any other programs to your startup which may be loading after Beryl, causing this issue?

I believe the culprit here would POSSIBLY be if XGL were not loaded PRIOR to Beryl.  That's just ONE idea; but that would cause this.  If you followed my directions in the first post of this thread, it should work though.

Please answer my three questions and we'll HOPE to find a fix for you quickly.

---

### Post by bored4 on 2006-09-30
> **djRobbieF said:**
> Hmm, you're the second person to report that.

My questions to try to get this figured out:

1) Do you have a pretty "default" display setup?  Like, you haven't got X running on a different TTY than F7?

2) Did you use MY instructions for how to run XGL, or someone else'?

3) Have you, in the past, added any other programs to your startup which may be loading after Beryl, causing this issue?

I believe the culprit here would POSSIBLY be if XGL were not loaded PRIOR to Beryl.  That's just ONE idea; but that would cause this.  If you followed my directions in the first post of this thread, it should work though.

Please answer my three questions and we'll HOPE to find a fix for you quickly.

im running a new install of ubuntu 6.06 all ive done is install the nvidia drivers with automatix and updated the system. 

i followed your instructions exactly from the first page.

my session manager reads: 
update-notifier
beryl-manager
gnome-power-manager
gnome-volume-manager  --sm-disable
xmodmap /usr/share/xmodmap/xmodmap.us


my xorg.conf file is in my post on page 10.

---

### Post by djRobbieF on 2006-09-30
Hmm... I'm really at a loss at the moment, as I haven't been able to emulate this problem.

I don't feel that it's your xorg.conf - because it DOES work once you select it as the window manager, right?

What if you choose Beryl as the window manager, and then click the icon, and choose Quit in Beryl Manager, and then reboot?  Does it restore to Beryl then?

---

### Post by bored4 on 2006-09-30
my current xorg.conf doesn't have this line in it

Option “RenderAccel” “true”

looks like this
```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Option		"UseFBDev"		"true"
EndSection
```

one other thing ive never seen before at the end of my xorg.conf ,is this:
```
Section "DRI"
	Mode	0666
```

well i don't know what has changed but i rebooted and now beryl loads, the splash screen pops up twice when i log into gnome. so i guess if it works, don't mess with it.

---

### Post by djRobbieF on 2006-09-30
you should have RenderAccel set to true though.  But yes, if it works, WHOOP, there it is.

---

### Post by bored4 on 2006-09-30
im afraid to add it and then when i reboot the xserver fails to start. but i guess i can try it. 

thanks for the help tho man.

---

### Post by djRobbieF on 2006-09-30
if it fails when you restart, do this:  (write it down, it's easy)

sudo vi /etc/X11/xorg.conf

Move to the section of the file and hold the DEL key on your keyboard to delete the line that is causing problems.

Then, push :w to write the changes, and then :q to quit.

Just a little to give you peace of mind that IF this one little setting screws things up, you can EASILY undo it from the command prompt.

Cheers.

---

### Post by steveneddy on 2006-10-01
Maybe I'm having a problem and don't realise it. After coming tonight to play a little with the new beryl, it still won't rotate the cube, but NOW, whenever I put the mouse next to the edge of the window, the cube rotates. I even went to the beryl-manager and found the command and it wasn't enabled.

I'm a little frustrated. I mean, I'm getting shadow, wobble, fade in and out (cool), transparant window borders, but these issues.

Still no NUM LOCK light....

no cube rotate....

let's leave it at that for now.

maybe we can get these things working and then move on to some more bugs.

** ** ** ** ** ** ** ** ** *

I really don't have these kinds of problems when I try stuff, new I guess, on Ubuntu.

I'll come back often to check out the page to read all of the posts....maybe I'll get it figured out tomorrow afternoon.

Any help appreciated - SE

---

### Post by djRobbieF on 2006-10-01
Did you make the xmodmap change as posted earlier?  That should resolve your issue.  ([http://ubuntuforums.org/showpost.php?p=1565829&postcount=102]("http://ubuntuforums.org/showpost.php?p=1565829&postcount=102"))

---

### Post by Greeface on 2006-10-01
EDIT:  Nevermind, the sound didn't work because somehow the PCM got muted.  Sorry!

Great guide, by the way!

---

### Post by Seine on 2006-10-01
Thank you for this guide. Easily done and working well. :KS

---

### Post by theslut on 2006-10-01
> **djRobbieF said:**
> **_Fix the Movie Player_**

theslut private messaged me, asking about fixing the totem movie player.

Here's how.

```
gedit ~/.gnome2/totem_config
```

Hit CTRL-F and search for:
```
video.driver
```

You'll see a line that says #video.driver:auto

Change it to this: (dont' forget to remove the #)
```
video.driver:xshm
```

Now, the anomalies and messed-up grids in movie player will be gone, and it works perfectly.

Cheers.

that works nicely!

---

### Post by techstop on 2006-10-01
A big thanks to djRobbieF, this was very easy. I tried xgl/compiz earlier in the year and was very underwhelmed. This is way cool though, and *very* functional for pre-alpha software! The emerald themes are nice too. Cheers.

---

### Post by djRobbieF on 2006-10-01
> **theslut said:**
> that works nicely!

I've still got the OCCASIONAL (and I mean *occasional*) blip, but all-in-all, it seems to be a sufficient fix for the moment.

---

### Post by djRobbieF on 2006-10-01
techstop, Seine

You're very welcome.  Glad I could help, and glad you like the software!

---

### Post by h0ax on 2006-10-01
Yo djRobbiE!  Thanks dude - I got it up and running -
Could you enlighten me on what that command does?  You can PM me if you think it's spam on this board.
By the way - I accidentally hit shit+backspace twice in between, lols... :/
First time I was trying to make a >_. face and tried to erase the last one while I still had shift down
Second time I was writing you a thank you note in here and I pushed backspace while I was holding shift.. :/ hah

Thanks for all your help tho freal - I look to be like you when I get enough Ubuntu/Linux knowledge - [ just erased my XP partition last night ] - only other linux exp I have is slackware - so we'll see how this goes :D
Thanks again dude!

---

### Post by h0ax on 2006-10-01
Is there any way to disable that shift+backspace - still kicks me out of X

---

### Post by steveneddy on 2006-10-01
> **steveneddy said:**
> Maybe I'm having a problem and don't realise it. After coming tonight to play a little with the new beryl, it still won't rotate the cube, but NOW, whenever I put the mouse next to the edge of the window, the cube rotates. I even went to the beryl-manager and found the command and it wasn't enabled.

I'm a little frustrated. I mean, I'm getting shadow, wobble, fade in and out (cool), transparant window borders, but these issues.

Still no NUM LOCK light....

no cube rotate....

let's leave it at that for now.

maybe we can get these things working and then move on to some more bugs.

** ** ** ** ** ** ** ** ** *



OK - the new xmodmap did the trick for most of my issues, and like many others, while trying to post last night, hitting SHIFT+BACKSPACE really fragged what I had to say.

Now I do have new issues.

Cube rotates fine, I have wobbly bits and NUM LOCK key is on now.

1. On the NUM keypad, the "+" and the "-" aren't functional. Is there something I can edit to get these back. I use these keys for calc.

**EDIT - and the "/" and the "*" on the NUM LOCK pad are out of commission, also.

This may go back to my post about the keyboard, when I restarted before the new xmodmap, the OS would ask if I wanted to use the keyboard settings from Xorg or Gnome. I clicked Xorg and clicked the little window for "Don't show me this message again".

2. Now I have these crazy lines that draw all over my screen when I try to open up an application. They look like an outline box or somethink and move across the screen kinda slow, like maybe....almost one second. Yellow in color and black arounf the edge.

3. Is there any way to use the cdwg (or whatever the old compiz themer was called) themes in beryl. There are a bunch of cool themes that I would like to try, but they wold install, for me anyway, so I could use them. I've even tried extracting them and making them fit the format.

** ** ** ** ** ** *

I'm not complaining, this is a very nice change from a year ago when I tried this. I can also change the window manager to metacity, I guess, to do calc, but why?

The lines are just annoying.

Thanks - SE

EDIT: Went to the keyboard settings in Gnome and changed the default KB until I came up with a solution that worked. I nao have my /*-+ keys back on the NUM KEYPAD.

Now about those annoying lines it draws all over my screen.... -  :)

---

### Post by eraser_rx on 2006-10-01
THX!!!....i can't believe Beryl works on my P3 800MHz...

but i think what really makes Beryl work is my GF4 Ti4200 w/128MB...

for eyecandy......who needs Windows Vista or iMac.... :P

---

### Post by silent_scream on 2006-10-01
how can i change the the window manager to be beryl??
I right click to the gem, and select window manager to be beryl, but it doesn't work. it brings back metacity as the default...

I also have installed compiz. should i remove it?
it also starts with the session with beryl.

---

### Post by sleeperknight on 2006-10-01
do you really need to have the Aiglx at the end or is it XGL?

```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
```

---

### Post by djRobbieF on 2006-10-01
> **h0ax said:**
> Could you enlighten me on what that command does?

It simply tells your system that "if you push SHIFT-Backspace, just treat it like a Backspace".


> You can PM me if you think it's spam on this board.

I prefer to keep everything in the public thread, because who knows; someone else may have the same question.


> By the way - I accidentally hit shit+backspace twice in between, lols... :/

When it first happened to me, I had just written a long business email, and in my signature I mistyped and pressed backspace while still holding SHIFT.  BOY did that suck.  ;)


> Thanks for all your help tho freal - I look to be like you when I get enough Ubuntu/Linux knowledge - [ just erased my XP partition last night ] - only other linux exp I have is slackware - so we'll see how this goes :D  Thanks again dude!

No problem!  Glad to help.  And doesn't it feel GREAT to finally wipe out XP?  That was my victory day!

---

### Post by djRobbieF on 2006-10-01
> **h0ax said:**
> Is there any way to disable that shift+backspace - still kicks me out of X

We've been through this several times now in this very thread h0ax.  Please look back over the solution.

---

### Post by silent_scream on 2006-10-01
> **silent_scream said:**
> how can i change the the window manager to be beryl??
I right click to the gem, and select window manager to be beryl, but it doesn't work. it brings back metacity as the default...

I also have installed compiz. should i remove it?
it also starts with the session with beryl.

I exited beryl-manager and ran it from console, 
and when i select beryl to be the window manager, it changes for a while and then it's metacity again..

console displays this message:

```
              $ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

```

---

### Post by logix on 2006-10-01
Many thanks for the howto, I had one strange issue which I'll document in case anyone else sees it.

After installation, I was prompted that updates were available, I chose to ignore that for the time being, because I was following the howto to the letter.

After rebooting for the first time - X failed to start with the following message:

(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.

I then did a manual apt-get install of the updated packages, rebooted, and all worked OK.

Thanks once again!

---

### Post by logix on 2006-10-01
Oh, one other thing - I'd previously been altering the panels on my desktop and had removed the top one and moved everything to the bottom panel.

When starting beryl-manager, the beryl icon didn't establish itself in the lower panel - even after re-adding the top panel, the icon refused to appear.

Having read another post on this forum, the work-around was to rename my .gnome and .gconf directories, and fresh ones were created with the panels restored to the defaults.  Now when starting beryl-manager, the icon appears correctly.

---

### Post by heisters on 2006-10-01
> **djRobbieF said:**
> Yeah, launching beryl without beryl-manager didn't work for me either; which is why I specified to use beryl-manager.

If it's defaulting to metacity at that point, I click on the beryl icon and choose "Select Window Manager" and click on Beryl.

> **beerorkid said:**
> did you try ```
beryl-manager
```

I still get an error when it starts up and have to open up the manager and get into beryl.

Oh, should have mentioned that. I followed the instructions; beryl-manager starts and runs fine. On startup, Metacity is loaded. So I go to beryl-manager's icon, click on "Select Window Manager" and click on Beryl. The screen blinks, the WM dissapears and then Metacity comes back. Metacity is selected as the "Fall-back Window Manager". Running beryl-manager manually has this not unexcpected output:
```

$ beryl-manager --help

** (process:7035): WARNING **: Can't run more than one beryl-manager.
(couldn't obtain lock) Error:Resource temporarily unavailable

```

---

### Post by logix on 2006-10-01
OK, i've had problems with the shift/backspace thing.

Solved by entering

xmodmap -e \"keycode 22 = BackSpace Delete\"

Rather than 

xmodmap -e "keycode 22 = BackSpace Delete"

The session editor does wierd things with the quotes and even after entering it with the \'s it doesn't display properly when you exit and go back in again.

This solution already posted on another thread by Dinerty.

---

### Post by Foucault on 2006-10-01
Hi there,
followed your guide, but whenever I choose Beryl from the tray icon X restarts back in the login manager screen.

I've tried this both in gnome using your guide, and in kde (which is my default desktop, but anyway) by editing the /etc/kde3/kdm/kdmrc file.

Whatever I do when I choose Beryl X restarts :-(

My VGA is a NVidia 6800GT and I am using the NVidia.com driver.

No luck with xmodmap too.

---

### Post by beerorkid on 2006-10-01
> **djRobbieF said:**
> Woohoo!  Another lover of the wobbly!

Beryl Settings Manager --> Wobbly Windows --> Map Window Types

Turn on PopupMenu, Unknown and DropdownMenu

!!

nice thanks

---

### Post by beerorkid on 2006-10-01
FYi I have set up [www.beerorkid.com/beryl](www.beerorkid.com/beryl) it is a symlink to the compiz dir.  Seeing how they are getting away from compiz and changing over to beryl.  seem more appropriate.

---

### Post by heisters on 2006-10-01
I tried a couple more things:

Once started, I killed beryl-manager and restarted it from a terminal. Then I manually selected Beryl as the WM, and this was printed to the terminal:
```

Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

```
I also tried disabling the xmodmap command in my session startup queue, as well as deleting my ~/.gnome2/session file to force it to be recreated. None of these changed Beryl's behavior..

---

### Post by agentstewie on 2006-10-01
> **GoombaDoolies said:**
> Hey peoples, I went away and found some additional material.  This is geared to both ATI cards, but works.  I have referenced the sites I got the info from.  Thank you so much (esp djRobbie...) for all your help and good wishes.

Download the fglrx driver for ATI [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

 Method 1: Installing Dapper's Included Driver (8.25.18)

The included fglrx driver supports Radeon 8500+ and the X-series cards up to X1900.

Unfortunately OpenGL seems to be broken for R200 cards (everything below Radeon 9500) in this driver version. The Troubleshooting section describes how to fix this after xorg-driver-fglrx is installed.
[edit]
Installing the driver

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

Help on enabling repositories can be found at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Now Reboot your system:

sudo shutdown -r now

An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc.
[edit]
Confirm that it works

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)

Grab the stuff from the repositories as per this thread.  I found that the command line was a bit finicky, i just jumped into synaptic and grabbed all the ones listed on the line:

```
sudo apt-get update && sudo apt-get install xserver-xgl beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes 
```

SO basically from the synaptic (making sure you have the required lines added to /etc/apt/sources.list) package manager, click

beryl (which tags most of the bits)
xserver-xgl
emerald-themes

The afterwards, you need to create the Xserver file and set up beryl to work:

[http://www.ubuntuforums.org/showthread.php?t=268149&highlight=XGL+Beryl]("http://www.ubuntuforums.org/showthread.php?t=268149&highlight=XGL+Beryl")

I found that these instructions helped me get to the point where I could test if it was working before switching it permanently and thus still be able to use gnome.

Make a startup script for Xgl

There are many ways for this, however the following one was always working for me when the others failed.

make the file:
Code:

gedit ~/.Xsession

add these:

```

#!/bin/sh
# Start up Xgl and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start GNOME
exec gnome-session

```

save and make it executable:

Code:

chmod +x ~/.Xsession

This is it. Now reboot, and choose "Default Session". Open up a terminal and type
Code:

beryl-manager

You should see a splash screen and beryl will take over metacity. If anything went wrong you can switch back to normal, just log out, switch to GNOME Session and delete ~/.Xsession. If it works you should add "beryl-manager" in startup programs (System -> Preferences -> Sessions).
Also, if you have problems with your GTK theme/icons/numlock etc. after enabling Xgl, you should add "gnome-settings-daemon" in startup programs too (following the beryl entry").

Hope this isn't too long, helps out and is readable.  Glad I could help, i feel a little less like a noob now. :)


this is the error i get....
```

rahul@behera-laptop:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
rahul@behera-laptop:~$ beryl-manager
rahul@behera-laptop:~$
** (beryl-manager:5540): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.

rahul@behera-laptop:~$

```

EDIT: I do get beryl (seemingly working fine) to launch, but im not able to do any of the cool xgl stuff.....

---

### Post by Foucault on 2006-10-01
Ok, mystiriously enough, by creating a new session just like a poster said before I managed to load XGL + Beryl. I've only replaced gnome-session with startkde.

However, apart from english language I am using greek as well (which is my native) in my keyboard. However I can't switch languages any more and only english shows up. I know it must have something to do with xmodmap, however I am not really familiar with it.

Any ideas?

Oh, and the numlock button seems dead!

---

### Post by adrift on 2006-10-01
I'm completely new to Linux and I probably should have tackled a few less daunting task before trying to install beryl. Anyways, here's my problem. I can't seem to get xgl to install. When i try to install it through Adept (i'm on Kubuntu) i get an install(break) message; when trying to install it through the terminal i get this:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages
```

how do i meet my unmet depedencies? :D

---

### Post by h0ax on 2006-10-01
> **heisters said:**
> Oh, should have mentioned that. I followed the instructions; beryl-manager starts and runs fine. On startup, Metacity is loaded. So I go to beryl-manager's icon, click on "Select Window Manager" and click on Beryl. The screen blinks, the WM dissapears and then Metacity comes back. Metacity is selected as the "Fall-back Window Manager". Running beryl-manager manually has this not unexcpected output:
```

$ beryl-manager --help

** (process:7035): WARNING **: Can't run more than one beryl-manager.
(couldn't obtain lock) Error:Resource temporarily unavailable

```

Read my post before - the solution is that remove xmodmap from your sessions - Beryl is running before that command.
Remove it - reboot, you should see the splash menu from Beryl pop up
Then re-add the command as the other poster said: 
xmodmap -e \"keycode 22 = BackSpace Delete\" 
In the interim don't push shift+backspace

h0ax

---

### Post by leoscuro on 2006-10-01
Hello. I followed this instructions and I use to have old compiz on my machine...I  must say this is working perfectly for now...Thanks to everybody that contributed to this excelent how to...

Now, I must ask for some help on an issue that has been following me since my last compiz install...I refer any kind soul to this other thread..

[http://ubuntuforums.org/showthread.php?t=268956](http://ubuntuforums.org/showthread.php?t=268956)

Please if somebody could read it and comment on it...

Thanks..

---

### Post by jaredvolkl on 2006-10-01
I've been following this thread since it started in hopes of getting beryl running on my machine and so far, I haven't been able to get it going.

First of all, I'm not running an ubuntu kernel. I had to compile my own to get my IDE controller working. Though I don't think this matters as I have the nvidia driver working OK with my custom kernel.

Where I'm at right now is I've created the XGL session to log into. When I log into it, I get an error message after 10 seconds saying there was an error starting the session and I can view the .xsession-errors log. So I check the box and view the error which tells me the startxgl.sh script generates a segfault. I think it also says something about "cannot find display." I noticed the line specifies a display of 1 and that doesn't sound right to me. I figured maybe if replaced the 1's with 0's then it would resolve the issue.

After doing that, I can log into the session and get to a desktop without the segfault. Though beryl-manager still shows I'm running Metacity and selecting Beryl just makes the screen flicker a few times and then return to Metacity.

I checked .xsession-errors again and found this

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jared"
/etc/gdm/Xsession: Beginning session setup...

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

SESSION_MANAGER=local/menace:/tmp/.ICE-unix/15142
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-panel:15215): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:15215): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -15 and height 24

```

Checking .xsession-errors again after selecting beryl in beryl-manager, I find this added

```

Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
beryl: No composite extension
XGL Absent, checking for NVIDIA
Nvidia Present
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
beryl: No composite extension
XGL Absent, checking for NVIDIA
Nvidia Present
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.

```

Is there some way to test XGL to make sure I have it running OK? I feel like I'm so close and that starting XGL is the only problem I'm having.

---

### Post by techstop on 2006-10-01
I encountered my first problem after moving to Beryl...VMware Server would no longer work in full screen. (ie. the guest would not maximise to full screen). The error said something like;

> Unable to find an appropriate host video mode.....Failed to switch to full screen SVGA mode

After a bit of searching I came across this;

[http://www.ubuntuforums.org/showpost.php?p=1380049&postcount=436](http://www.ubuntuforums.org/showpost.php?p=1380049&postcount=436)

However, the new code to add as per that post was incorrect for me, and VMware server would not start at all. Instead of this;

```
pref.autoFitFullScreen = "FitGuestToHost"
```

It should be this;

```
pref.autoFitFullScreen = "fitGuestToHost"
```

Notice the lower case "f". It all works fine again for me now. I am still stunned at the quality of the Beryl package, it really is very polished. So many options!

Oh, and another heads up for a working solution to running OpenGL programs simply;

[http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

Works a treat.

---

### Post by adrift on 2006-10-01
> **adrift said:**
> I'm completely new to Linux and I probably should have tackled a few less daunting task before trying to install beryl. Anyways, here's my problem. I can't seem to get xgl to install. When i try to install it through Adept (i'm on Kubuntu) i get an install(break) message; when trying to install it through the terminal i get this:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages
```

how do i meet my unmet depedencies? :D

Disregard this post, i apparently solved it by reinstalling. but now i have another issue. I can't seem to get permission to save or write to gdm.conf-custom. And also, there isn't a "severs" section in the file when opened in kate it appears blank.

---

### Post by knuckles on 2006-10-01
Hey everyone

I am trying to get beryl working on my system. I think I have everything I need installed, but when I use beryl as my windows manager, I dont get any of the cool effects I was hoping for. Instead, all that happens are the window buttons (close(x) shrink (-)...) in the top right corner of the windows dissappear. There is no cube to be rotated either.
These are the first few lines when I use the command glxinfo:

name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2


it says direct rendering is off. How do I fix this? Is this the problem?

this is my xorg.conf:
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    #HorizSync       28.0 - 84.0
    #VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "RenderAccel"        "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
                                                                                                                                    
 Depth       1
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection

Oh yah, and this is the fist post I have ever made on a forums page. Thanks in advance to anyone who can help me. I am linux novie so any words of advice are appreciated.

---

### Post by techstop on 2006-10-02
> **knuckles said:**
> 
it says direct rendering is off. How do I fix this? Is this the problem?


this was answered back here;

[http://www.ubuntuforums.org/showpost.php?p=1563195&postcount=40](http://www.ubuntuforums.org/showpost.php?p=1563195&postcount=40)

xgl does not allow direct rendering, so it is supposed to be off.

Also, your section of xorg.conf looks borked;

> Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver "nvidia"
Option "RenderAccel" "True"
EndSection


There is no busid section. You are also missing the option to set Triple Buffering to false. I don't think your nvidia drivers are installed correctly. Did ppracer or glxgears work correctly for you before you installed xgl/beryl? My equivalent section of xorg.conf is below. You can see it is quite different. (identifier, busid and triplebuffer)

> Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
        Option          "RenderAccel"     "true"
        Option          "TripleBuffer"    "false"
EndSection


Those things stick out, but other than that, you will have to wait for one of the experts to have a look.

---

### Post by philetus on 2006-10-02
Is this: 0=Xgl a zero or a Capitol Oh?

---

### Post by techstop on 2006-10-02
It's a zero. Cut and paste from the HOWTO is the easiest, saves typing!

---

### Post by philetus on 2006-10-02
Thanks. I figured it was.
The reason I asked is because this is the second time I installed Dapper, updated it, and followed the Howto and ended up with a crashed x.

I'm getting: (EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found)
(EE) xf86OpenSerial: Cannot open device /dev/wacom
            No such file or directory

---

### Post by logix on 2006-10-02
hi Philetus,

See my posting on page 13 about your problem.

I did a command line update/upgrade/dist-upgrade to get the latest updates, then rebooted and all was OK.

---

### Post by moon_dog on 2006-10-02
installation went smoothly, no problems.  but now all the panels are gone, all it gives me is a blank desktop.  what gives?  how do i get my panels back?

---

### Post by silent_scream on 2006-10-02
i fixed my prob...
but now tvtime and gnomeradio don't work... :S](*,)

---

### Post by h0ax on 2006-10-02
yo djRobbie!
my shift+backspace still kills my X 
hmm... :/

---

### Post by logix on 2006-10-02
Hoax, can you confirm you've entered the xmodmap as follows, and not just copy/pasted the howto?

> **logix said:**
> OK, i've had problems with the shift/backspace thing.

Solved by entering

xmodmap -e \"keycode 22 = BackSpace Delete\"

Rather than 

xmodmap -e "keycode 22 = BackSpace Delete"

The session editor does wierd things with the quotes and even after entering it with the \'s it doesn't display properly when you exit and go back in again.

This solution already posted on another thread by Dinerty.

---

### Post by depu on 2006-10-02
just installed the packages. and it looks gr8...
wonder how long it takes to have all this in the standard distro..

---

### Post by skyee on 2006-10-02
> **logix said:**
> 

 Originally Posted by logix  View Post
OK, i've had problems with the shift/backspace thing.

Solved by entering

xmodmap -e \"keycode 22 = BackSpace Delete\"

Rather than

xmodmap -e "keycode 22 = BackSpace Delete"

The session editor does wierd things with the quotes and even after entering it with the \'s it doesn't display properly when you exit and go back in again.

This solution already posted on another thread by Dinerty.


I follow the howto in the first post ,but it doesnt work.
I think the cmd 'xmodmap -e "keycode 22 = BackSpace Delete"' which i enter  screwed it up
but now i cant login into gnome ,how could I change the xmod cmd without startup gnome-session-properties aka "System –> Preferences –> Sessions –> Startup Programs"

---

### Post by rsambuca on 2006-10-02
I'm obviously doing something wrong here (complete noob).

Whenever I try to run the sudo apt-get update and sudo apt-get install ... stuff, it seems to stop and says 

E: Couldn't find package Beryl.

I have added the 2 lines to the sources list, and tried many times.  Any ideas what I might have been doing incorrectly?

---

### Post by jaredvolkl on 2006-10-02
> **rsambuca said:**
> I'm obviously doing something wrong here (complete noob).

Whenever I try to run the sudo apt-get update and sudo apt-get install ... stuff, it seems to stop and says 

E: Couldn't find package Beryl.

I have added the 2 lines to the sources list, and tried many times.  Any ideas what I might have been doing incorrectly?After you added those lines to sources.lst, did you save them? You have to do update and dist-upgrade before you try to get beryl. Also make sure beryl is all lower case as that is the package name.

---

### Post by Foucault on 2006-10-02
```

```> **Foucault said:**
> Ok, mystiriously enough, by creating a new session just like a poster said before I managed to load XGL + Beryl. I've only replaced gnome-session with startkde.

However, apart from english language I am using greek as well (which is my native) in my keyboard. However I can't switch languages any more and only english shows up. I know it must have something to do with xmodmap, however I am not really familiar with it.

Any ideas?

Oh, and the numlock button seems dead!

Solved! :-D

The problem with the layouts was due to the fact that XKB failed to load. Even if one tried to launch it manually with 

```
setxkbmap -model pc105 -layout us,gr -variant ,extended -option grp:alt_shift_toggle
```

(which is suitable for greek keyboards)

all they would get is

```
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault

```

A little workaround I found [here]("http://forum.compiz-fr.org/viewtopic.php?pid=1026"). In order to issue the correct command for xkb the command:

```
xprop -root -f _XKB_RULES_NAMES 8s -set _XKB_RULES_NAMES xorg
```

must be typed in first. Then the suitable command for xkb can be given as normally. And the numlock key works just great again.

---

### Post by beerorkid on 2006-10-02
> **rsambuca said:**
> I'm obviously doing something wrong here (complete noob).

Whenever I try to run the sudo apt-get update and sudo apt-get install ... stuff, it seems to stop and says 

E: Couldn't find package Beryl.

I have added the 2 lines to the sources list, and tried many times.  Any ideas what I might have been doing incorrectly?

also maybe just try to find it in synaptic

---

### Post by Genix on 2006-10-02
Is there anyway to get this working on AMD64 with Ubuntu 64-bit version installed?

---

### Post by GoombaDoolies on 2006-10-02
I haven't had time to play too much with it or the computer it works on.

The computer it's on hangs fairly soon after it is switched on.  Monitor goes into standby and I can't Ctrl-Alt-Backspace to shutdown the gnome session.  If I try to do something too much in Mozilla or try to change some settings in Admin.

My gut feeling is that the fglrx driver sent my video card up the poo, but I can't confirm that, but i do remember it playing up after I changed it from the ati driver to fglrx driver, but because  I was on a roll, I installed beryl so quickly afterwards and got it working so quickly afterwards, I hadn't had the ability to test the theory.  Once I have time, I will jump on, go to safe recovery and see what I can do.](*,)

---

### Post by ceenvee703 on 2006-10-02
> **jaredvolkl said:**
> After you added those lines to sources.lst, did you save them? You have to do update and dist-upgrade before you try to get beryl. Also make sure beryl is all lower case as that is the package name.

I'm having the same problem, and yes, edits to /etc/apt/sources.list were saved, and I did an update and dist-upgrade. I'm still geting "couldn't find package beryl." Is this because I'm on AMD64? Thanks.

---

### Post by bennyj on 2006-10-02
Hello there!Just wanted to say thanks to all for this great tutorial.I installed and everything is working as expected except my printer.Before installing XGL and Beryl it was working fine.Now when I go to print I can see in cups that the job was excepted and my printer will pop up and say printing one job,it just never prints though.

I have tried rebooting,turning the printer off and back on.still nothing.would changing windows managers effect this.Anyone have any ideas how I might be able to get this working and keep Beryl.

HP 3100 series PhotoSmart
Ubuntu 6.06

Thanks

---

### Post by rsambuca on 2006-10-02
> **ceenvee703 said:**
> I'm having the same problem, and yes, edits to /etc/apt/sources.list were saved, and I did an update and dist-upgrade. I'm still geting "couldn't find package beryl." Is this because I'm on AMD64? Thanks.

I got it to work on the 32bit system.  Instructions worked perfectly.  I couldn't get it to work on the AMD64 distro earlier after many different attempts.

---

### Post by beerorkid on 2006-10-02
I figure there will be a 64bit howto comming soon.

Quinn does not have a amd64 machine to work on.  Others compile them.

The beryl wiki should be updated here soon.

---

### Post by philetus on 2006-10-02
> **logix said:**
> hi Philetus,

See my posting on page 13 about your problem.

I did a command line update/upgrade/dist-upgrade to get the latest updates, then rebooted and all was OK.
Tried that this morning and it didn't work.Then I had to go to work.

Still getting

(EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found)
(EE) xf86OpenSerial: Cannot open device /dev/wacom
           No such file or directory

---

### Post by philetus on 2006-10-02
If I did this sudo apt-get install nvidia-kernel-common nvidia-glx

Why would I not have a suitable nvidia driver?

---

### Post by billflu on 2006-10-02
I had this same problem, but now my friend is having it. I forgot how I fixed it a few days ago. :( 

Whenever he tries to load the Beryl window manager it crashes and defaults back to Metacity. I was looking for the solution for a few hours to no avail ](*,) Any help would be greatly appreciated :-D

---

### Post by philetus on 2006-10-03
I have a fresh, updated, upgraded install of Dapper 6.06.
I installed the 2.6.15-27-686 kernel.

Do I need to do anything else before I  Install XGL & Beryl on Dapper w/ nVidia using apt-get, from the Howto? 

When I tried this the first two times, I didn't have a "Glcore" in the Module section.Should it be there?

I'm too old and I've killed too many brain cells to become a linux expert.
I just want the best OS that money can't buy.

---

### Post by Seine on 2006-10-03
I have installed this no problem, but I have to choose Beryl as a window manager manually. It defaults to Metacity on startup. How can I change this?

---

### Post by smdeep on 2006-10-03
Hi
Thanks for the great howto! Beryl is fantastic, much better than compiz on opensuse 10.1.

One thing I would like to ask though, Gnome menus look rather boring compared to the rest of the desktop. How can one spruce them up a bit?

Once again thanks for the great HOWTO.

---

### Post by techstop on 2006-10-03
I have come across another problem, my numeric keypad numbers work, but the operators don't (* / + - ).....

???

I followed version 1.5 of the howto, and didn't change anything to do with modmap.

---

### Post by h0ax on 2006-10-03
I have fixed my numpad, end/pageupdown, shift+backspace dilemma
I changed my keyboard in System->Preferences->Keyboard to what it actually is (it was listed)
now everything works as expected..
Good luck all!

---

### Post by techstop on 2006-10-03
:oops: Wow, that was so....obvious! It's always the simple things. Thanks for the heads up, my numpad works now!

---

### Post by jimtb on 2006-10-03
Very beautiful effects although the CPU usage is a bit high. I had this  problem when I was using compiz too and it doesnt seem to be fixed in beryl. Some tray icons, most of the times adept notifier, appear like very small windows on the upper left of the screen and the only way to close them is to kill the application.

---

### Post by beerorkid on 2006-10-03
> **jimtb said:**
> Very beautiful effects although the CPU usage is a bit high. I had this  problem when I was using compiz too and it doesnt seem to be fixed in beryl. Some tray icons, most of the times adept notifier, appear like very small windows on the upper left of the screen and the only way to close them is to kill the application.

for the "leftovers" might try reloading the window manager. Ahhh the joys of being bleeding edge ;)

---

### Post by jimtb on 2006-10-03
Nah it just wont work. The only solution is to kill adept notifer and then start it again.
I can wait a bit I guess. :-)

---

### Post by beerorkid on 2006-10-03
:(

prob not gonna have to wait too long till the next update.  According to the [blog](http://blog.beryl-project.org/) there is more comming.  might check and see if it is in the bug tracker. [http://bugs.beryl-project.org/](http://bugs.beryl-project.org/)

---

### Post by rsambuca on 2006-10-03
Thanks h0ax,

I had the same issue with the keyboard numberpad.  Problem solved!  Great thread guys!  As a new Linux user, you guys make things very easy.  (Perhaps too easy!!)

---

### Post by groove on 2006-10-03
Can you show some pics?

---

### Post by beerorkid on 2006-10-03
> **groove said:**
> Can you show some pics?

how about video ;)

[http://www.youtube.com/results?search_query=beryl&search=Search](http://www.youtube.com/results?search_query=beryl&search=Search)

---

### Post by nophun on 2006-10-03
Hi,

why my ubuntu says that it can't find a 'beryl'-package. I have done everything right before it using this Howto-guide. Does it matter if i'm using a 64-bit version of ubuntu? And what kernel should i install?

---

### Post by beerorkid on 2006-10-03
> **nophun said:**
> Hi,

why my ubuntu says that it can't find a 'beryl'-package. I have done everything right before it using this Howto-guide. Does it matter if i'm using a 64-bit version of ubuntu? And what kernel should i install?

cant find much cept for this
```
deb http://www.amd64.aceracerftw.com/ edgy main-edgy
``` for the repo

from this thread: [http://forum.beryl-project.org/topic-4861-2.html](http://forum.beryl-project.org/topic-4861-2.html)

---

### Post by bgood4000 on 2006-10-03
My cube is back... thank you, thank you and thank you again.

You rock.:mrgreen:

---

### Post by BLTicklemonster on 2006-10-03
Yay, another new and interesting way to kill X. I'll keep at it though. I always wondered what you all keep getting excited about.

Worse yet, when I try to log out, everything has changed. No restart or shut down. I can log out, but I go to 

ticklemonster@ticklemonster:~$


and have to type sudo reboot if I want to reboot. 

I can't even log out to see if beryl is there or not.

*edit:
I have an emerald, but it does nothing for me. Lots of neat looking stuff in it, though.

I get this log when I try to boot with "Option “RenderAccel” “true”" in devices in xorg.conf. If I edit it and comment that one thing out, I'm okay. Still don't have the same options I used to have on log out, though. My mouse buttons stopped working, also. 

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ticklemonster 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Tue Oct  3 22:38:55 2006
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 94 of section Device in file /etc/X11/xorg.conf
	The Option keyword requires 1 or 2 quoted strings to follow it.
Parse error on line 94 of section Device in file /etc/X11/xorg.conf
	"“true”" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
```

Oh, and I get some IO error about buffers and my hard drive clicks only when I have the Option “RenderAccel” “true” line in xorg.conf. 

I'm running an evga 5500 card.

---

### Post by rsambuca on 2006-10-03
Fantastic Howto!!  

OK, I think I got the hang of this one.  Next, I want to set up dual monitors.  Am I supposed to use Twinview or Xinerama, or does it matter?

I have an nVidia 6600GT card.

---

### Post by beerorkid on 2006-10-03
> **rsambuca said:**
> Fantastic Howto!!  

OK, I think I got the hang of this one.  Next, I want to set up dual monitors.  Am I supposed to use Twinview or Xinerama, or does it matter?

I have an nVidia 6600GT card.

twinview
this would be the thread: [http://ubuntuforums.org/showthread.php?t=221174&highlight=twinview](http://ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

this is how:



HowTo:

Add the following lines in your "Device" Sections and I'll explain what each line mean. sudo gedit /etx/X11/xorg.conf

```


Option "TwinView" "True" 
Option "TwinViewOrientation" "RightOf" 
Option "UseEdidFreqs" "True" 
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
```

    * The first two lines are self-explainary.
    * "UseEdidFreqs" allows the NVIDIA X driver to use the valid HorizSync and VertRefresh frequency ranges from the EDID whenever possible.
    * "The MetaModes tells the driver what resolutions to use for the two monitors, with the resolution reported back to Xorg being the sum of the dimensions. In this case, 2560x1024 or 2048x768" -Ubuntu Hacks

That's it.

---

### Post by rsambuca on 2006-10-04
Right on!  Everything seems to be working really well with Twinview.  I'll just have to modify my desktop backdrops as the pictures are now s t r e t c h e d across two monitors!  GIMP here I come!

Beerorkid --> You are da Man:cool: 

I really appreciate your assistance.

---

### Post by beerorkid on 2006-10-04
sheeeeeeeeeeet I just happen to be by a computer way too often.

Glad things are working out well for ya.

I just regurgitate others figuring-outins.

---

### Post by aidanr on 2006-10-04
just installed beryl and xgl, very awesome, thanks for the how-to:)

---

### Post by croppyboy on 2006-10-04
Great how-to . . . New to Linux and had no problems with the install . . . Thanks! :D

---

### Post by alxjl on 2006-10-04
Great How-To. As i write this my knees are as wobbly as the effects this thing can do. I used to have XGL installed using a GeForce4 videocard. But i removed it coz it froze on me every few minutes or so. Now i decided to give  it another try and looks like it's stable for me. Thanks..

---

### Post by nophun on 2006-10-04
> **beerorkid said:**
> cant find much cept for this
```
deb http://www.amd64.aceracerftw.com/ edgy main-edgy
``` for the repo

from this thread: [http://forum.beryl-project.org/topic-4861-2.html](http://forum.beryl-project.org/topic-4861-2.html)

ok, thank you! It works fine now :)

---

### Post by Phil_McCrackin on 2006-10-04
Got it installed and it looks great. One problem, though, is now when I shut-down, I just get a blank screen and my machine never actually shuts off. My monitor is still getting a signal, fans running, but totally unresponsive. Any ideas?

I am running 2.6.15-27-686

---

### Post by rupy on 2006-10-04
For some reason Beryl-Manager sets the default windows manager to KWin instead of Beryl? Everytime the system starts up I have to go and manually set it. Any ideas?

Sorry if this has been covered already, but I couldn't find it anywhere.

---

### Post by beerorkid on 2006-10-04
woops

---

### Post by beerorkid on 2006-10-04
> **Phil_McCrackin said:**
> Got it installed and it looks great. One problem, though, is now when I shut-down, I just get a blank screen and my machine never actually shuts off. My monitor is still getting a signal, fans running, but totally unresponsive. Any ideas?

I am running the most recent 686

hmmmmm... seems like it might be a kernel version problem.

I have run into this a few times. i should be K7, but am running 386 because of such issues.
not sure, just a suggestion

uname -r

will show kernel version

---

### Post by maxres on 2006-10-04
beerorkid's Avatar is scary

pleeeeeze beerorkid make it stop

---

### Post by beerorkid on 2006-10-04
> **maxres said:**
> beerorkid's Avatar is scary

pleeeeeze beerorkid make it stop

he he

It has been grandfathered in because I was a member of these forums many a fortnight ago.  One of the lucky few to have an animated avitar.

why are you worried by it? wink wink ;)

---

### Post by Seine on 2006-10-04
As long as it doesn't kill any kittens, I'm OK with it.

---

### Post by m.musashi on 2006-10-04
Okay, I've decided it's time to get some eye candy. I have my new nvidia card installed and I'm ready to go.

I start with the how to and I make the following changes to the xorg.conf file...
```
Section "Device"
Identifier- leave this line alone!
Driver "nvidia&#8221;
BusID &#8220;PCI:1:0:0&#8243;
Option &#8220;RenderAccel&#8221; &#8220;true&#8221;
EndSection
```
I restart just to make sure and wham, xserver fails to start. I go in and undo the changes one at a time and it seems that the "renderaccel" "true" part is the problem. What is the renderaccel and what could cause me to have problems with it. I have an xfx 7600gs card and I get very good glxgears numbers. As far as I know I have 3d acceleration working. Is that what this is about and if 3d is working do I need the renderaccel line?

I used Automatix to install the nvidia driver and it has been working fine. I get the splash screen and if I try and install following the how to it tells me I already have the latest driver installed.

Any ideas?
Thanks.

---

### Post by h0ax on 2006-10-05
Found a bug:
I was messing around with my screen savers - now I'm stuck on one that as soon as you preview it - it kills beryl
and I cannot change it without it crashing my X =/

---

### Post by logix on 2006-10-05
> **m.musashi said:**
> Okay, I've decided it's time to get some eye candy. I have my new nvidia card installed and I'm ready to go.

I start with the how to and I make the following changes to the xorg.conf file...
```
Section "Device"
Identifier- leave this line alone!
Driver "nvidia”
BusID “PCI:1:0:0&#8243;
Option “RenderAccel” “true”
EndSection
```
I restart just to make sure and wham, xserver fails to start. I go in and undo the changes one at a time and it seems that the "renderaccel" "true" part is the problem. What is the renderaccel and what could cause me to have problems with it. I have an xfx 7600gs card and I get very good glxgears numbers. As far as I know I have 3d acceleration working. Is that what this is about and if 3d is working do I need the renderaccel line?

I used Automatix to install the nvidia driver and it has been working fine. I get the splash screen and if I try and install following the how to it tells me I already have the latest driver installed.

Any ideas?
Thanks.

Mine set as follows, note I explicitly added the no triplebuffer thing.

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6200?]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "TripleBuffer"          "false"

EndSection

---

### Post by billflu on 2006-10-05
> **m.musashi said:**
> I restart just to make sure and wham, xserver fails to start. I go in and undo the changes one at a time and it seems that the "renderaccel" "true" part is the problem. What is the renderaccel and what could cause me to have problems with it. I have an xfx 7600gs card and I get very good glxgears numbers. As far as I know I have 3d acceleration working. Is that what this is about and if 3d is working do I need the renderaccel line?

After it crashes and you're in command line type ```
sudo nano /etc/X11/xorg.conf
``` Check to make sure that the renderaccel line is using quotes. I installed this on two different machines and for some reason those quotes where showing up as boxes, so I changed them backed to quotes, saved the file and typed ```
startx
``` Everything worked fine after that. Hope this helps.

---

### Post by darqfaux on 2006-10-05
I followed the Howto step by step but beryl wouldn't start after reboot. I don't have the ruby on my panel but I do have Beryl Settings manager & Emerald theme manager in System->Preferences. It's seems to default to metacity when I boot. I tried to run beryl from the terminal and I get this error.```
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```
Can someone please help me?

---

### Post by rylasasin on 2006-10-05
I INSTALLED THIS STUFF OCCORDING TO THE FIRST PAGE OF THIS AND NOW ITS RUINED BOTH MY UBUNTU AND MY KUBUNTU BUILD HELP HELP i NEED HELP TAKING IT OFF!!!

KUBUNTU HANGS AFTER THE BOOT LOADS AND UBUNTU GIVES ME X FAILED TO LOAD ERRORS PLEASE HELP DAMMIT!

---

### Post by pony-tail on 2006-10-05
I mananaged to get it working BUT !
I started with Kubuntu "Dapper" Installed as per your instructions - Replaced kdm with gdm - still no joy . installed gnome-core - Working - but gnome only !
System is PIII 800 - 256meg ram - GF4 Ti4400.
Is there any way to get it working in KDE ?
I am going to try it on my main 32bit machine (Shuttle SB61 / 3.2 / 1gig /Gf5900xt but I have to clear my personal documents first . Will post back with results.
Speed is acceptable on the PIII (quite useable ) but you would not want to use anything mutch slower.

---

### Post by rylasasin on 2006-10-05
Come On Guys I Need Answers!!! ](*,) ](*,) ](*,)

---

### Post by ltr20 on 2006-10-05
It doesn't work for me! Once installed I do see the little beryl icon but when I select beryl as the window manager my screen goes black with green bars and just locks up. I'm using a geforce ti 4800 128 MB, 2ghz processor on drapper.

---

### Post by Pooz on 2006-10-05
Yayyyy...

Finally got it to work using my ATI card.

many thanks everyone:D 

Effects very cool:p 

Richie

---

### Post by m.musashi on 2006-10-06
> **rylasasin said:**
> I INSTALLED THIS STUFF OCCORDING TO THE FIRST PAGE OF THIS AND NOW ITS RUINED BOTH MY UBUNTU AND MY KUBUNTU BUILD HELP HELP i NEED HELP TAKING IT OFF!!!

KUBUNTU HANGS AFTER THE BOOT LOADS AND UBUNTU GIVES ME X FAILED TO LOAD ERRORS PLEASE HELP DAMMIT!

Can't help with the kubuntu side but I also got the xserver failed to load message. I haven't found a solution but it's easy to role back. Just copy the backup you made and replace the xorg.conf file with it. You did make a backup, right? If not, there were only a few changes to the xorg.conf file. Just take them out. You should be able to start x after that. You might need to reboot. If you made a lot more changes then I'm not sure what to tell you. You will have to edit the file from the command prompt. I think the command is ```
sudo nano /etc/X11/xorg.conf
``` Make the changes, save and reboot. If this doesn't get your x server working again you might need to supply more info. I'm pretty new at this stuff still so others may have better advice.

---

### Post by m.musashi on 2006-10-06
> **logix said:**
> Mine set as follows, note I explicitly added the no triplebuffer thing.

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6200?]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "TripleBuffer"          "false"

EndSection

Thanks for the help. I didn't try the last two options yet but with only the "BusID" line I notice I also get the xserver crash. How do I know that I want "PCI:1:0:0" instead of something else. With this line in there it creashes and with just the renderaccel line it crashes. Clearly my ubuntu doesn't like something in here. Do I have to do the rest of the how to first before restarting? I reloaded X after this change to make sure it would work (and it doesn't). Is that to be expected if I didn't finish the how to?

Thanks in advance.

---

### Post by tomBorgia on 2006-10-06
Hiya, Howto worked wonderfully...
Anyone know how to _switch_ XGL / Beryl off - It uses quite a lot of memory and is preventing Doom3 from running (disaster:mad: ) but I don't want to uninstall it totally.
Thanks.

---

### Post by beerorkid on 2006-10-06
> **tomBorgia said:**
> Hiya, Howto worked wonderfully...
Anyone know how to _switch_ XGL / Beryl off - It uses quite a lot of memory and is preventing Doom3 from running (disaster:mad: ) but I don't want to uninstall it totally.
Thanks.

well if you have beryl-manager going, click th icon in your notification area and you can switch with ease.

---

### Post by darqfaux on 2006-10-06
Can anyone help me with my prior post. I still haven't got it to work.

---

### Post by beerorkid on 2006-10-06
> **darqfaux said:**
> Can anyone help me with my prior post. I still haven't got it to work.

have you tried running just "beryl-manager"?

---

### Post by dannyboy79 on 2006-10-06
I am curious, when i setup xgl and compiz awhile ago I set it up so that it was an entirely different session so when I logged into gnome i could either choose xgl and compiz or just a normal gnome session. i wanted it this way so that when I wanted to graphic entensive things compiz wouldn't be on. i haven't used it in so long since the compiz guys really made a lot of changes. 

beerokid states, "well if you have beryl-manager going, click th icon in your notification area and you can switch with ease." I am curious, will this have the same effect as entering a session without compiz at all? affect on system resources etc etc? how would I setup this up so that it was a different session like before? could I use the same method but change/modify applicable things to now use beryl etc.?

---

### Post by beerorkid on 2006-10-06
> **dannyboy79 said:**
> I am curious, when i setup xgl and compiz awhile ago I set it up so that it was an entirely different session so when I logged into gnome i could either choose xgl and compiz or just a normal gnome session. i wanted it this way so that when I wanted to graphic entensive things compiz wouldn't be on. i haven't used it in so long since the compiz guys really made a lot of changes. 

beerokid states, "well if you have beryl-manager going, click th icon in your notification area and you can switch with ease." I am curious, will this have the same effect as entering a session without compiz at all? affect on system resources etc etc? how would I setup this up so that it was a different session like before? could I use the same method but change/modify applicable things to now use beryl etc.?

well I had it set up with different sessions once and just went in normaly (metacity) and would launch compiz-manager (back in the day) to switch.  Not really sure how to do different sessions besides system --> preferences --> sessions and adding it there.

I now add beryl-manager in there on the startup tab.

---

### Post by handband2 on 2006-10-06
> **dannyboy79 said:**
> I am curious, when i setup xgl and compiz awhile ago I set it up so that it was an entirely different session so when I logged into gnome i could either choose xgl and compiz or just a normal gnome session. i wanted it this way so that when I wanted to graphic entensive things compiz wouldn't be on. i haven't used it in so long since the compiz guys really made a lot of changes. 

beerokid states, "well if you have beryl-manager going, click th icon in your notification area and you can switch with ease." I am curious, will this have the same effect as entering a session without compiz at all? affect on system resources etc etc? how would I setup this up so that it was a different session like before? could I use the same method but change/modify applicable things to now use beryl etc.?

See if my earlier post helps you:  [http://ubuntuforums.org/showthread.php?p=1564565#post1564565](http://ubuntuforums.org/showthread.php?p=1564565#post1564565)

---

### Post by handband2 on 2006-10-06
> **tomBorgia said:**
> Hiya, Howto worked wonderfully...
Anyone know how to _switch_ XGL / Beryl off - It uses quite a lot of memory and is preventing Doom3 from running (disaster:mad: ) but I don't want to uninstall it totally.
Thanks.

tomBorgia,

The best way to get away from it using resources is to make another session.  See if this helps:  [http://ubuntuforums.org/showthread.php?p=1564565#post1564565](http://ubuntuforums.org/showthread.php?p=1564565#post1564565)

For playing 3d games I found just having it as a session works good but if you want to run your 3d games while in Beryl check out this link:  [http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

I hope that helps.

---

### Post by darqfaux on 2006-10-06
> **beerorkid said:**
> have you tried running just "beryl-manager"?

Yes, when I type beryl-manager into terminal I get this:
```
** (process:5872): WARNING **: Can't run more than one beryl-manager.
(couldn't obtain lock) Error:Resource temporarily unavailable

```

---

### Post by handband2 on 2006-10-06
If you have problems booting with no graphics here are some helpful commands:

This will reconfigure your graphics settings
```

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
```

Info you will need for dpkg-reconfigure xserver-xorg:
[LIST]Monitor - Resolutions[/LIST]
[LIST]Monitor - HORIZONTAL SCAN - kHz[/LIST]
[LIST]Monitor - VERTICAL SCAN - Hz[/LIST]
[LIST]Video Card Memory - Convert MB to KB - [Converter]("http://www.csgnetwork.com/memconv.html")[/LIST]

To find your BusID:
```
#lspci -X
```

Here is some helpful hints for the NVIDIA people who upgraded to the [NVIDIA drivers]("https://help.ubuntu.com/community/NvidiaManual"):
[LIST]
[*]Was Xorg already properly configured for the nv drivers?
[/LIST]
[LIST]
[*]Did you remove the nvidia-glx, nvidia-settings, and
nvidia-kernel-common packages installed via apt or synaptic?[/LIST]
[LIST]
[*]Did you read the log found in /var/log/nvidia-installer-log for errors that can guide you?
[/LIST]
[LIST]
[*]Did you install the kernel headers (and possibly source package)?
[/LIST]
[LIST]
[*]Did you check the Nvidia readme found on their site to make sure your card is supported with that version of driver?
[/LIST]
[LIST]
[*]Did you check the Nvidia Linux Forums for any current 'known issues' with the latest drivers?
[/LIST]

Notes on XGL:  [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

IF you have more notes to help others please share!!

---

### Post by m.musashi on 2006-10-06
Handband2. Thanks for the tips. I admit most made little sense to me but the BusID comand did the trick. The # sign had to be left off to get it to display. Anyone having trouble with the xserver crashing may want to check this. It turns out that for me the correct BusID was 3:0:0.

I have it all set up now. VERY COOL! Thanks for the help and the nice how to. Does anyone know how compiz and beryl are different? Is compiz gone and replaced?

I was also wondering about themeing for beryl. It seems to be a modification of my current desktop theme rather than a complete replacement. Lots to learn here. Thanks for the tips and help.

---

### Post by darkcow on 2006-10-07
eeek.. i keep on having random crashes. its annoying me. no matter what im doing XGl  will just crash out on me and it will reload gnome.


any idea's?

---

### Post by pony-tail on 2006-10-07
Worked on the Shuttle P4 too !
Some issues but I muddled through them .
All fixed .

---

### Post by handband2 on 2006-10-07
> **darkcow said:**
> eeek.. i keep on having random crashes. its annoying me. no matter what im doing XGl  will just crash out on me and it will reload gnome.


any idea's?

darkcow,

You might find your answer looking at the logs:

```
gedit /var/log/messages
```

or

```
gedit /var/log/Xorg.0.log
```

or look into the gdm logs

```
nautilus /var/log/gdm
```

I hope that can help....

---

### Post by handband2 on 2006-10-07
> **m.musashi said:**
> Handband2. Thanks for the tips. I admit most made little sense to me but the BusID comand did the trick. The # sign had to be left off to get it to display. Anyone having trouble with the xserver crashing may want to check this. It turns out that for me the correct BusID was 3:0:0.

I have it all set up now. VERY COOL! Thanks for the help and the nice how to. Does anyone know how compiz and beryl are different? Is compiz gone and replaced?

I was also wondering about themeing for beryl. It seems to be a modification of my current desktop theme rather than a complete replacement. Lots to learn here. Thanks for the tips and help.

m.musashi,

I'm glad my tips could help.

Here is info on compiz and beryl:
[http://forum.beryl-project.org/topic-4591-beryl-informations-announcement]("http://forum.beryl-project.org/topic-4591-beryl-informations-announcement")
[http://forum.beryl-project.org/topic-4562-1.html]("http://forum.beryl-project.org/topic-4562-1.html")

For more information on beryl themes check out the beryl forum:
[http://forum.beryl-project.org/forum-15-themes-etc]("http://forum.beryl-project.org/forum-15-themes-etc")
[http://forum.beryl-project.org/forum-3-questions-answers]("http://forum.beryl-project.org/forum-3-questions-answers")

---

### Post by Beebs on 2006-10-07
> **darqfaux said:**
> I followed the Howto step by step but beryl wouldn't start after reboot. I don't have the ruby on my panel but I do have Beryl Settings manager & Emerald theme manager in System->Preferences. It's seems to default to metacity when I boot. I tried to run beryl from the terminal and I get this error.```
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```
Can someone please help me?

> **darqfaux said:**
> Yes, when I type beryl-manager into terminal I get this:
```
** (process:5872): WARNING **: Can't run more than one beryl-manager.
(couldn't obtain lock) Error:Resource temporarily unavailable

```

I am experiencing exactly the same issue. Anyone got any tips for sorting this out?

---

### Post by Beebs on 2006-10-07
OK. I removed beryl-manager from the startup programs and restarted the session. I then ran beryl-manager from the command line. This gave me the red diamond (ruby?) on the top panel. Then i could click on it and set the window manager to beryl. Once I'd done that I re-added beryl-manager to startup programs. Now beryl starts correctly when I logon. Bizarrely I still don't get the beryl-manager icon.

---

### Post by Subban on 2006-10-07
great guide and pretty painless to setup.
I initially had a problem with GDM not coming up, quickly solved that tho by correcting the quoatation marks from pasting from the web page, they seemed to be some kind of html quaotation mark rather than a 'normal' mark.

Also I had to change:
BusID “PCI:1:0:0&#8243;
to:
BusID “PCI:5:0:0&#8243;

I now have one problem remaining which I can't fix and can't find reference to in this thread or the forums, When Beryl is running (rather than metacity etc) my middle mouse button and my right mouse button don't work correctly.

My Middle Mouse button has taken on the role of the Right Mouse Buton, and the Right Mouse Button now sends windows into the background ('under' other windows)

I am using an MX1000 mouse setup via [HERE]("http://www.ubuntuforums.org/showthread.php?t=188302&highlight=mx1000+evdev")
(Yes I see the big red warning message but when I tried to update to the newer method it didn't workout)

Anyone give me a pointer to get these buttons switched to work in Beryl as they do in Metacity etc.

Regards
John

---

### Post by logix on 2006-10-07
> **Beebs said:**
> OK. I removed beryl-manager from the startup programs and restarted the session. I then ran beryl-manager from the command line. This gave me the red diamond (ruby?) on the top panel. Then i could click on it and set the window manager to beryl. Once I'd done that I re-added beryl-manager to startup programs. Now beryl starts correctly when I logon. Bizarrely I still don't get the beryl-manager icon.

Beebs,

Try renaming your .gconf and .gnome1 directories in home and restarting.  This should rebuild your gnome menus.  I had probs with beryl-manager not creating an icon, and this fixed it.

---

### Post by m.musashi on 2006-10-07
Since I got this working I thought I would set it up on my laptop too. I have a presentation in a couple weeks and I want to use my ubuntu + beryl and show off a bit.

However, on the laptop I now have a pretty borked system. It loads and I can spin the cube but nothing draws right. Apps load and look kind of like a TV with vertical-hold out of wack. It's very slow to redraw too. After 5-10 minutes the whole thing just logs out on its own and bring be back to the gdm log in screen. It does this even I've chosen metacity instead of beryl (beryl is still loaded though).

I've been scanning the thread but haven't found a particular fix for this. Any ideas? The laptop should be able to run this fine. It has a core duo processor and a dedicated nvidia card. I get glx numbers of 1500 fps so I'm pretty sure the driver is installed and working fine. I also get the nvidia splash screen.

Thanks in advance. If I can manage to get a screen shot I'll post one.

---

### Post by m.musashi on 2006-10-07
Okay. Here is a screenshot. It actually doen't look like this unless I click shutdown. It looks more normal with only parts of windows looking like this. However, it sure shows the problem well.

Thanks

---

### Post by cafg10 on 2006-10-07
Well i was having some problems on amd64, and it can be solved with the following:

[LIST]
[*]sudo apt-get build-dep source beryl --build

[*]install the produced debs with gdebi.

[*]sudo apt-get build-dep source beryl-plugins beryl-settings beryl-manager --build

[*]install the resulting packages

[*]sudo apt-get build-dep source emerald --build

[*]install the resulting packages

[*]Next there is some tweakage use the separate session mode for runing XGl a session option.

[*]Add emerald to Session programs

[*]restart your X session
[/LIST]

Note all this is for beryl 0.1 (10-08-2006) from the repositories, becuase there are only source code version of them.

Maybe i will be able to publish my debs in a web page,(need to ask for permision of my boss to use my companies host)

---

### Post by handband2 on 2006-10-07
> **m.musashi said:**
> Okay. Here is a screenshot. It actually doen't look like this unless I click shutdown. It looks more normal with only parts of windows looking like this. However, it sure shows the problem well.

Thanks

m.musashi,

REMEMBER: every time your kernel is upgraded or changed with another one you have to reinstall the drivers.

Check this site out from [tseliot]("http://ubuntuforums.org/member.php?u=19388"):
[http://albertomilone.com/latest_nvidia_udsf.html]("http://albertomilone.com/latest_nvidia_udsf.html")
or
follow below:

[LIST=1]
[*]Download the installer - [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")
[*]```
uname -r
sudo apt-get install linux-headers-$(uname -r) build-essential gcc gcc-4.0 xserver-xorg-dev
```
[*]Remove files
```
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
```
[*]Manually remove files (If there is any)
```
sudo rm /etc/init.d/nvidia-*
```
[*]Press CTRL-ALT-F1 (CTRL-ALT-F7 to come back to graphical desktop)
```
sudo /etc/init.d/gdm stop

## Goto where you downloaded the NVIDIA-Linux-x86-1.0-8774-pkg1.run file
cd /home/*username*/Desktop/

## Run the script
sudo sh NVIDIA-Linux-x86-1.0-8774-pkg1.run

##At the end of the install process, installer will ask you to run the configuration script. Select **"yes"**.

sudo /etc/init.d/gdm start
``` 
[/LIST]
I hope that fixes the problem...

---

### Post by de4th on 2006-10-07
This guide helped me better than anyone to install xgl!
Thanx :D 8)

---

### Post by Psquared on 2006-10-07
Worked flawlessly for me. I must say, the first it started I had to say WOW - this is too cool.

Question though. Now I've got a bunch of updates to install. Should I install them or leave well enough alone. (comment out the sources list??)

---

### Post by lockdown571 on 2006-10-07
The first time I did it the x server crashed; I eventually traced that to the 'Option “RenderAccel” “true”' line.  Once I deleted that,  everything worked.  What does that line do anyways?

---

### Post by m.musashi on 2006-10-07
> **handband2 said:**
> I hope that fixes the problem...
Well, thanks for trying but I am still having the exact same problem. I think I had the right drivers installed. I installed them with Automatix and with each kernel upgrade they seemed to be upgraded as well. However, after installing the 686-smp kernel I wasn't sure so I tried the steps you outlined. No luck. However, I do know what is causing the problem. I just don't know how to fix it.
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```
If I comment out these changes everything works fine. I think that means that something here isn't working as it should on my system. However, I don't really know what any of this does. I guess that's one problem with just copying commands. When it all works - great. If not, it's hard to know what to do to fix it.

Anyway, any guesses as to what is my problem here?

Thanks again.

---

### Post by pony-tail on 2006-10-08
I just installed (clean install) ubuntu Dapper.
I then installed FGLRX drivers (radeon X800 pro)
I then installed XGL and Beryl - although it kind of works I have to manually load beryl-manager the cube works but windows behave strangely (some do not even have borders ) and I get this error message in the terminal -
ian@SB61ATI:~$ beryl-manager
ian@SB61ATI:~$
** (beryl-manager:5392): WARNING **: Couldn't find a Selection Owner, perhaps no  WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn 't follow the standards.
Falling back to looking for a defined WM in xlsclients.
XGL Present
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
Initiating splash
X connection to :1.0 broken (explicit kill or server shutdown).
XGL Present
Initiating splash
ian@SB61ATI:~$

Any ideas

---

### Post by _lynX on 2006-10-08
> **m.musashi said:**
> Well, thanks for trying but I am still having the exact same proble. I think I had the right drivers installed. I installed them with Automatix and with each kernel upgrade they seemed to be upgraded as well. However, after installing the 686-smp kernel I wasn't sure so I tried the steps you outlined. No luck. However, I do know what is causing the problem. I just don't know how to fix it.
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```
If I comment out these changes everything works fine. I think that means that something here isn't working as it should on my system. However, I don't really know what any of this does. I guess that's one problem with just copying commands. When it all works - great. If not, it's hard to know what to do to fix it.

Anyway, any guesses as to what is my problem here?

Thanks again.

I have the same problem. As long as the Xgl server is set to run, X crashes  when trying to load GDM. 

Here is the errors from my Xorg log file from my last boot:

> 
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded


All help is *greatly* appreciated! Thanks in advance!

---

### Post by pony-tail on 2006-10-08
My /etc/X11/xorg.conf -
> 
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"L1510B"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Monitor		"L1510B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"gdm.conf
	Mode	0666
EndSection

My /etc/gdm/gdm.conf-custom
> # GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true


My /etc/gdm/gdm.conf
> # GDM Configuration file.
#
# You should not update this file by hand.  Since GDM 2.13.0.4, configuration
# choices in the gdm.conf-custom file will override the default values
# specified in this file.  This file may be overwritten on upgrade, so to
# ensure that your configuration choices are not lost, please make sure that
# your modifications are only made to the gdm.conf-custom file.  If you were
# using a previous version of GDM and had made changes to your gdm.conf file,
# this file should have been automatically renamed as gdm.conf-custom to ensure
# that your previous modifications are preserved.
#
# You can use the gdmsetup program to graphically edit the gdm.conf-custom
# file.  Note that gdmsetup does not support every option in this file, just
# the ones that most users want to change.  If you feel that gdmsetup should
# support additional configuratio options, please file a bug report at
# [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/).
#
# If you hand-edit the GDM configuration, you should run the following command
# to get the GDM daemon to recognize the change.  Any running GDM GUI programs
# will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the GNOME help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Some values are commented out but show their default values.  Lines
# that begin with "#" are considered comments.
#
# Have fun!

[daemon]
# Automatic login, if true the first local screen will automatically logged in
# as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The GDM configuration program that is run from the login screen, you should
# probably leave this alone.
#Configurator=/usr/sbin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone.
#Chooser=/usr/lib/gdm/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/lib/gdm/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/lib/gdm/gdmlogin

# Launch the greeter with an additional list of colon separated GTK+ modules.
# This is useful for enabling additional feature support e.g. GNOME
# accessibility framework. Only "trusted" modules should be allowed to minimize
# security holes
#AddGtkModules=false
# By default, these are the accessibility modules.
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this value.
# This value will be overridden with the value from /etc/default/login if it
# contains "ROOT=<pathvalue>".
#DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this value.
# This value will be overridden with the value from /etc/default/login if it
# contains "SUROOT=<pathvalue>".
#RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and want
# GDM to kill/restart the server, turn this on.  On Solaris, this value is
# always true and this configuration setting is ignored.
#AlwaysRestartServer=false

# User and group used for running GDM GUI applicaitons.  By default this is set
# to user "gdm" and group "gdm".  This user/group should have very limited
# permissions and access to ony the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# does not always work, only if those clients have a window of their own.
#KillInitClients=true
LogDir=/var/log/gdm
# You should probably never change this value unless you have a weird setup.
PidFile=/var/run/gdm.pid

# Note that a post login script is run before a PreSession script.  It is run
# after the login is successful and before any setup is run on behalf of the
# user.
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say VGA
# mode, allowing a login, could you please send it to me?
#FailsafeXServer=
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can run an X
# configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing
# Reboot, Halt and suspend commands, you can add different commands separated
# by a semicolon.  GDM will use the first one it can find.
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
# Probably should not touch the below this is the standard setup.
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal X
# session, but it shares a lot of stuff with that.  See the provided default
# for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live.  It is
# really a PATH style variable since 2.4.4.2 to allow actual interoperability
# with KDM.  Note that <dmconfdir>/Sessions is there for backwards
# compatibility reasons with 2.4.4.x.
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this
# behavior.
UserAuthDir=
# Fallback directory for writing authorization file if user's home directory
# is not writable.
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is no
# activity and no one logged on.  Set to 0 to turn off the reaping.  Does not
# affect Xnest flexiservers.
#FlexiReapDelayMinutes=5
# The X nest command.
Xnest=/usr/bin/Xnest -br -br -audit 0 -name Xnest
# Automatic VT allocation.  Right now only works on Linux.  This way we force
# X to use specific vts.  turn VTAllocation to false if this is causing
# problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change VT's
# on Linux and FreeBSD systems for console logins)
#DoubleLoginWarning=true
# Should a second login always resume the current session and switch VT's on
# Linux and FreeBSD systems for console logins
#AlwaysLoginCurrentSession=true

# If true then the last login information is printed to the user before being
# prompted for password.  While this gives away some info on what users are on
# a system, it on the other hand should give the user an idea of when they
# logged in and if it doesn't seem kosher to them, they can just abort the
# login and contact the sysadmin (avoids running malicious startup scripts).
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used when there
# are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

# This determines whether GDM will honor requests DYNAMIC requests from the
# gdmdynamic command.
#DynamicXServers=false

# This determines whether GDM will send notifications to the console.
#ConsoleNotify=true

# How long gdm should wait before it assumes a started Xserver is defunct and
# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
GdmXserverTimeout=50

[security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=true
# Allow login as root via XDMCP.  This value will be overridden and set to
# false if the /etc/default/login file exists and contains
# "CONSOLE=/dev/login", and set to true if the /etc/default/login file exists
# and contains any other value or no value for CONSOLE.
AllowRemoteRoot=false
# This will allow remote timed login.
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions.
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# Number of seconds to wait after a failed login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line, a
# good default to have (why is this a "negative" setting? because if it is
# false, you could still not allow it by setting command line of any particular
# server).  It's probably better to ship with this on since most users will not
# need this and it's more of a security risk then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do not add
# a "-nolisten tcp", as then the query just wouldn't work, so this setting only
# affects truly local sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS by
# detecting "root-squashing".  It seems bad practice to place cookies on things
# that go over the network by default and thus we do not do it by default.
# Sometimes you can however use safe remote filesystems where this is OK and
# you may want to have the cookie in your home directory.
#NeverPlaceCookiesOnNFS=true
# Will cause PAM_DISALLOW_NULL_AUTHTOK to be passed as a flag to
# pam_authenticate and pam_acct_mgmt, disallowing NULL password.  This setting
# will only take effect if PAM is being used by GDM.  This value will be
# overridden with the value from /etc/default/login if it contains
# "PASSREQ=[YES|NO]"
#PasswordRequired=false
# Specifies the PAM Stack to use, "gdm" by default.
PamStack=gdm

# XDMCP is the protocol that allows remote login.  If you want to log into GDM
# remotely (I'd never turn this on on open network, use ssh for such remote
# usage that).  You can then run X with -query <thishost> to log in, or
# -indirect <thishost> to run a chooser.  Look for the 'Terminal' server type
# at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
# Honor indirect queries, we run a chooser for these, and then redirect the
# user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests.
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time.
#MaxSessions=16
# Maximum wait times.
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way.
#Port=177
# Willing script, none is shipped and by default we'll send hostname system id.
# But if you supply something here, the output of this script will be sent as
# status of this host so that the chooser can display it.  You could for
# example send load, or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc that
# we need.  Unless you need a specific gtkrc that doesn't correspond to a
# specific theme, then just use the GtkTheme key.
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the GUI.
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does not yet
# have this ability.
AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can also
# specify 'all' to allow all installed themes.  These should be just the
# basenames of the themes such as 'Thinice' or 'LowContrast'.
GtkThemesToAllow=Human,HighContrast,HighContrastInverse,LowContrast

# Maximum size of an icon, larger icons are scaled down.
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# The following options for setting titlebar and setting window position are
# only useful for the standard login (gdmlogin) and are not used by the
# themed login (gdmgreeter).
#
# The standard login has a title bar that the user can move.
#TitleBar=true
# Don't allow user to move the standard login window.  Only makes sense if
# TitleBar is on.
#LockPosition=false
# Set a position for the standard login window rather then just centering the
# window.  If you enter negative values for the position it is taken as an
# offset from the right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0

# Enable the Face browser.  Note that the Browser key is only used by the
# standard login (gdmlogin) program.  The Face Browser is enabled in 
# the Graphical greeter by selecting a theme that includes the Face
# Browser, such as happygnome-list.  The other configuration values that
# affect the Face Browser (MinimalUID, DefaultFace, Include, Exclude,
# IncludeAll, GlobalFaceDir) are used by both the Standard and Themed
# greeter.
Browser=false
# The default picture in the browser.
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the face
# browser or in the gdmselection list for Automatic/Timed login.  They will not
# be displayed regardless of the settings for Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in the
# gdmsetup selection list for Automatic/Timed login.  Users should be separated
# by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from the
# gdmsetup selection list for Automatic/Timed login.  Excluded users will still
# be able to log in, but will have to type their username.  Users should be
# separated by commas.  
Exclude=bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users will be
# displayed except users excluded via the Exclude setting and user ID's less
# than MinimalUID.  Scanning the password file can be slow on systems with
# large numbers of users and this feature should not be used in such
# environments.  The setting of IncludeAll does nothing if Include is set to a
# non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture.
#GlobalFaceDir=/usr/share/pixmaps/faces/

# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with GDM and edit it.  It is not a standard locale.alias
# file, although GDM will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter.
#Logo=/usr/share/pixmaps/gdm-foot-logo.png
# Logo shown on file chooser button in gdmsetup (do not modify this value).
#ChooserButtonLogo=/usr/share/pixmaps/gdm-foot-logo.png
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true

# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however.
#SystemMenu=true
# Configuration is available from the system menu of the greeter.
ConfigAvailable=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user to
# connect to some remote host.  Local XDMCP does not need to be enabled,
# however.
#ChooserButton=true

# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome to
# "Welcome" and for DefaultWelcome to "Welcome to %n", and properly translate
# the message to the appropriate language.  Note that %n gets translated to the
# hostname of the machine.  These default values can be overridden by setting
# DefaultWelcome and/or DefaultRemoteWelcome to false, and setting the Welcome
# and DefaultWelcome values as desired.  Just make sure the strings are in
# utf-8 Note to distributors, if you wish to have a different Welcome string
# and wish to have this translated you can have entries such as
# "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n

# Xinerama screen we use to display the greeter on.  Not for true multihead,
# currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
# The Standard greeter (gdmlogin) uses BackgroundColor as the background
# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor
# as the background color.
BackgroundColor=#2b0600
GraphicalThemedColor=#2b0600
# XDMCP session should only get a color, this is the sanest setting since you
# don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true

# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# If this is true then the background program is run always, otherwise it is
# only run when the BackgroundType is 0 (None).
#RunBackgroundProgramAlways=false
# Delay before starting background program
#BackgroundProgramInitialDelay=30
# Should the background program be restarted if it is exited.
#RestartBackgroundProgram=true
# Delay before restarting background program
#BackgroundProgramRestartDelay=30

# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode
# where the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=auto
# Use circles in the password field.  Looks kind of cool actually, but only
# works with certain fonts.
UseCirclesInEntry=true
# Do not show any visible feedback in the password field. This is standard for
# instance in console, xdm and ssh.
#UseInvisibleInEntry=false

# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=circles/:happygnome
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false

# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font to
# be used when displaying the contents of the file.
#InfoMsgFont=Sans 24

# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
# user successfully logs in.
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
# user fails to log in.
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# Specifies a program to be called by the greeter/login program when the
# initial screen is displayed.  The purpose is to provide a hook where files
# used after login can be preloaded to speed performance for the user. The
# program will only be called once only, the first time a greeter is displayed.
# The gdmprefetch command may be used.  This utility will load any libraries
# passed in on the command line, or if the argument starts with a "@"
# character, it will process the file assuming it is an ASCII file containing a
# list of libraries, one per line, and load each library in the file.
#PreFetchProgram=/usr/lib/gdm/gdmprefetch /etc/gdm/gdmprefetchlist

# The chooser is what's displayed when a user wants an indirect XDMCP session,
# or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts.
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png.
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are scanning
# actually, we continue to listen even after this has expired).
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to a
# query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer.
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced
# when officially registered xdmcp multicast address of TBD will be available.
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names.
#AllowAdd=true

[debug]
# This will cause GDM to send debugging information to the system log, which 
# will create a LOT of output.  It is not recommended to turn this on for
# normal use, but it can be useful to determine the cause when GDM is not
# working properly.
Enable=false
# This will enable debug messages for accessibilty gesture listeners into the
# syslog.  This includes output about key events, mouse button events, and
# pointer motion events.  This is useful for figuring out the cause of why the
# gesture listeners may not be working, but is too verbose for general debug.
Gestures=false

[servers]
# These are the standard servers.  You can add as many you want here and they
# will always be started.  Each line must start with a unique number and that
# will be the display number of that server.  Usually just the 0 server is
# used.
#0=Standard
1=Standard
# Note the VTAllocation and FirstVT keys on Linux and FreeBSD.  Don't add any
# vt<number> arguments if VTAllocation is on, and set FirstVT to be the first
# vt available that your gettys don't grab (gettys are usually dumb and grab
# even a vt that has already been taken).  Using 7 will work pretty much for
# all Linux distributions.  VTAllocation is not currently implemented on
# anything but Linux and FreeBSD.  Feel free to send patches.  X servers will
# just not get any extra arguments then.
#
# If you want to run an X terminal you could add an X server such as this:
#0=Terminal -query serverhostname
# or for a chooser (optionally serverhostname could be localhost):
#0=Terminal -indirect serverhostname
#
# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look at
# the security/DisallowTCP setting!

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

#priority=0

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params anyway,
# and terminate would be bad for xdmcp choosing).  You can make a terminal
# server flexible, but not with an indirect query.  If you need flexible
# indirect query server, then you must get rid of the -terminate and the only
# way to kill the flexible server will then be by Ctrl-Alt-Backspace.
flexible=false
# Not local, we do not handle the logins for this X server.
handled=false

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Chooser]
name=Chooser server
command=/usr/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you wish to
# allow a chooser server then make this true.  This is the only way to make a
# flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a machine they
# will get this same server but run with "-terminate -query hostname".
chooser=true

Some of the entries are different to the nvidia ones because of the fglrx drivers - I believe them to be configured correctly
but if you spot anything let me know.Other than being a little flakey it is working - after a complete shutdown then cold start Beryl loads on it's own
so it does work on Ati cards .

---

### Post by m.musashi on 2006-10-08
> **handband2 said:**
> m.musashi,

I'm glad my tips could help.

Here is info on compiz and beryl:
[http://forum.beryl-project.org/topic-4591-beryl-informations-announcement]("http://forum.beryl-project.org/topic-4591-beryl-informations-announcement")
[http://forum.beryl-project.org/topic-4562-1.html]("http://forum.beryl-project.org/topic-4562-1.html")

For more information on beryl themes check out the beryl forum:
[http://forum.beryl-project.org/forum-15-themes-etc]("http://forum.beryl-project.org/forum-15-themes-etc")
[http://forum.beryl-project.org/forum-3-questions-answers]("http://forum.beryl-project.org/forum-3-questions-answers")

I've been exploring these links but I can't find anything that explains the various settings and how to use them. For example, how do you set a picture to the "space" behind the cube. I see other people with stuff there. Mine is just black. What about the top and bottom of the cube. Can you do anything with them. What about 6 desktops with ones on the top and bottom? How about the mouse gestures. I see that top-right and bottom left show all open windows ala OSX (which is very cool) but what about top-left and bottom-right? That does something too but I don't see the point. Lots more questions but googling on beryl hasn't produced much. Is there any kind of manuel out there?

---

### Post by zues on 2006-10-08
> **pony-tail said:**
> My /etc/X11/xorg.conf -

Section "Module"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

It looks like you didnt have dri pounded out in your xorg.conf

---

### Post by loell on 2006-10-08
I just bought an nvidia card yesterday and followed a part of your howto, and it works smoothly in my xubuntu, 

Thank You :mrgreen:

---

### Post by zues on 2006-10-08
There are two things I noticed.  One was that for an Athlon X2 you should use
```
sudo apt-get install linux-k7-smp
```

instead of the intel smp

and there is a portion in the xorg.conf that when copied and pasted it actually creates blocks instead of quotes.  Its the line that says render accel yes.  (something like that).  You must edit that when x fails or make sure you actually write that line into your xorg.conf.

Having said that, i think this is awesome and one of the best tuitorials out.

Oh there was the key import too, that nees to be added into the instructions after editing the sources.list.

One thing i noticed also was that I cannot resize my firefox..  example, when I open it , it goes beyond the size of the window.  I cant grab the corner because its just too big.  And when clicking on the taskbar icon and choosing resize , its innefective.

One cool feature !! shift-f9 works awesome and shift-f8 is like a windshield wiper.  Try it out!

How do you set a super key?

thanks for a great tuitorial.

---

### Post by handband2 on 2006-10-08
> **m.musashi said:**
> Well, thanks for trying but I am still having the exact same problem. 

m.musashi,

Curious?  What is your output when you you type:
```
ps uax | grep Xorg | grep Xgl
```

Also what is your xorg.conf look like?

Try this...remove :0
Here is what I have:
```
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

---

### Post by zues on 2006-10-08
My buddy came over and helped me resize the window by rightclicking the title bar and then choosing resize and then using the arrow keys to resize then enter to save the change to the window.  Alot of you guys new this i know but I didnt and i figured someone else may want to know this.

---

### Post by handband2 on 2006-10-08
> **_lynX said:**
> I have the same problem. As long as the Xgl server is set to run, X crashes  when trying to load GDM. 

Here is the errors from my Xorg log file from my last boot:



All help is *greatly* appreciated! Thanks in advance!

_lynX,

Could you post your 

/etc/X11/xorg.conf

file and

/etc/gdm/gdm.conf-custom

---

### Post by handband2 on 2006-10-08
> **pony-tail said:**
> I just installed (clean install) ubuntu Dapper.
I then installed FGLRX drivers (radeon X800 pro)
I then installed XGL and Beryl - although it kind of works I have to manually load beryl-manager the cube works but windows behave strangely (some do not even have borders ) and I get this error message in the terminal -
ian@SB61ATI:~$ beryl-manager
ian@SB61ATI:~$
** (beryl-manager:5392): WARNING **: Couldn't find a Selection Owner, perhaps no  WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn 't follow the standards.
Falling back to looking for a defined WM in xlsclients.
XGL Present
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
Initiating splash
X connection to :1.0 broken (explicit kill or server shutdown).
XGL Present
Initiating splash
ian@SB61ATI:~$

Any ideas

pony-tail,

Try this with **FGLRX** drivers:

Change standard server to 1
```
sudo gedit /etc/gdm/gdm.conf
```
[INDENT]```
#0=Standard
1=Standard

[servers]
1=Xgl #Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR FGLRX, 0 works on Edgy+FGLRX).  

[server-Xgl] 
name=Xgl server
command=/usr/bin/Xgl -fullscreen -br -accel xv:pbuffer -accel glx:pbuffer -dpi 100 -nolisten tcp
flexible=true
```[/INDENT]

Let us know if that works...

Installation - ATI/XGL/Beryl
[ATI Driver Install]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")
[Install XGL]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper")

---

### Post by _lynX on 2006-10-08
> **handband2 said:**
> _lynX,

Could you post your 

/etc/X11/xorg.conf

file and

/etc/gdm/gdm.conf-custom


xorg.conf:
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
EndSection

Section "Monitor"
	Identifier	"DELL E773c"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"DELL E773c"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


gdm.conf-custom:
> 
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
# 
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
# 
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
# 
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
# 
# NOTE: Lines that begin with "#" are considered comments.
# 
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glxbuffer -accel xv:fbo
flexible=true


I tried changing it to 1=Xgl and using :1 and I was able to actually boot up gdm, but the screen kept flashing black every few seconds and after I logged in, the screen went black for a bit and beryl did nothing.

---

### Post by roncrump on 2006-10-08
How cool is that!
Followed the instructions and whoosh! Success, pretty windows bling all over the place.

Three small queries:
(1) When I ran sudo apt-get update there were two errors reported at the end, relating to something not being present and therefore being unable to check things (public keys? MDS?). Sorry I forgot to note it down at the time - too excited to move onto the next step, which ran without a hitch, and don't want to re-run it now because of...

(2) As I was doing the updates and installs for beryl, my system update tool decided to tell me that I needed to do some updates. A lot of these updates are X and OpenGL related. Is this just coincidental, or is it going to mess up my new installation to make these updates (I would normally just let the system update whenever it wants to, but I'm a bit nervous about this one). Should I do this updating? I'm avoiding it at present.

(3) The windows of applications in beryl do not have the "ubuntu look" - ie they have no orange-brown header. Is there any way of getting it look more like ubuntu?

Thanks for a great guide.

Regards,
Ron Crump

---

### Post by Julolidine on 2006-10-08
n00b alert!

Anyways, I followed the guide, and now my computer is pretty much useless.  After log in I have is a small square (approx 33% of the size of the screen) of interlaced noise in the middle of my screen, and the rest is black.  I can't access *anything* in the GUI, as I can't see anything because its all just bars of noise.  

How do I drop to terminal only with a shortcut and or kill my session so I can go back and comment out some of these updates?


](*,)

edit: OK, used the 'recovery mode' to get to the terminal.  How do I now edit the startup sessions from terminal?

edit2:Problem solved everything works OK now, moral of the story, don't do stuff you don't understand on sunday morning and forget to add :
BusID “PCI:1:0:0&#8243;
Option “RenderAccel” “true”
to xorg.conf

Slightly humbled but now happy.  :rolleyes:

---

### Post by gslo on 2006-10-08
Huge thanks for the How-To, it works beautifully
gslo

---

### Post by pony-tail on 2006-10-08
> pony-tail,

Try this with FGLRX drivers:

Change standard server to 1
It is already st to 1

I just installed the FGLRX drivers from ATI (the Debian way) as per Debain forum now Beryl works correctly .
The bad thing is if I change my kernel it will screw up.
I am about to try to install it on a Shuttle SN45v with Nvidia GF 5900xt
See how it goes

---

### Post by pony-tail on 2006-10-08
No issues at all on the SN45g Shuttle (nForce 2 )
Everything went smoothly -

---

### Post by handband2 on 2006-10-08
> **_lynX said:**
> xorg.conf:


gdm.conf-custom:


I tried changing it to 1=Xgl and using :1 and I was able to actually boot up gdm, but the screen kept flashing black every few seconds and after I logged in, the screen went black for a bit and beryl did nothing.

_lynX,

Try this in your /etc/X11/xorg.conf:
```
Section "Device"
Identifier "NVIDIA Corporation NV35 [GeForce FX 5900XT]"
Driver "nvidia"
BusID "PCI:1:0:0" **#Make sure your BusID is correct. In the terminal run $lspci -X**
Option "RenderAccel" "true"
EndSection

Section "Monitor"
Identifier "DELL E773c"
HorizSync       30.0 - 70.0
VertRefresh     50.0 - 160.0 **#http://support.dell.com/support/edocs/monitors/e773c/En/specs.htm**
Option "DPMS"
EndSection

```

Since you are not using module "dri" turn it off:
```
#Section "DRI"
#Mode 0666
#EndSection
```

This is up to you...
It looks like you are not using WACOM from your logs.  This is how you turn them off.  It should increase your boot [by maybe 1 or 2 seconds :)]:
```
#Section "InputDevice"
#Driver "wacom"
#Identifier "stylus"
#Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
#Option "Type" "stylus"
#Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "eraser"
#Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
#Option "Type" "eraser"
#Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#Driver "wacom"
#Identifier "cursor"
#Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
#Option "Type" "cursor"
#Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection
```

Change your **ServerLayout:**
```
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
#InputDevice "stylus" "SendCoreEvents"
#InputDevice "cursor" "SendCoreEvents"
#InputDevice "eraser" "SendCoreEvents"
EndSection
```
Let me know if that works...

---

### Post by handband2 on 2006-10-08
> **pony-tail said:**
> It is already st to 1

I just installed the FGLRX drivers from ATI (the Debian way) as per Debain forum now Beryl works correctly .
The bad thing is if I change my kernel it will screw up.
I am about to try to install it on a Shuttle SN45v with Nvidia GF 5900xt
See how it goes

pony-tail,
Great to hear you got it working!!

Just a not: every time your kernel is upgraded or changed with another one you have to reinstall the drivers.

---

### Post by m.musashi on 2006-10-08
> **handband2 said:**
> m.musashi,

Curious?  What is your output when you you type:
```
ps uax | grep Xorg | grep Xgl
```
This didn't give any output but I don't have beryl running right now since it's hard to do much if it is.

EDIT: I turned everything back on and I got this:
```
root       4719   1.6   0.6   17460 13892 tty7    SLs+ 14:00   0:01 /usr/bin/Xorg vt7 -auth /tmp/ .Xgl-auth-Mhb0xD -nolisten tcp :93 -terminate
```
I had to input that by had as the laptop is not able to connect to the internet at the moment.

> Also what is your xorg.conf look like?
I'll post this in a bit. For some reason my wireless adapter on my laptop decided to stop working. However, it is not unlike the example.

> Try this...remove :0
Which :0 are you refering to? One in the BusID line or somewhere else?

EDIT: Nevermind. Found it. 
> Here is what I have:
```
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```
That is exactly the same as mine. Only I had to comment this out to avoide the problems I described.

EDIT: Okay. I made the change and took out the :0. It didn't change anything. The problem still exists.

Thanks again for helping me work this out.

---

### Post by _lynX on 2006-10-08
> **handband2 said:**
> _lynX,

Try this in your /etc/X11/xorg.conf:

Since you are not using module "dri" turn it off:

This is up to you...
It looks like you are not using WACOM from your logs.  This is how you turn them off.  It should increase your boot [by maybe 1 or 2 seconds :)]:

Change your **ServerLayout:**

Let me know if that works...

The bus id was correct, but this made it work! Thank you so much for your help!

Edit: I am still having a problem. When I try to switch to one of the 3d screensaves, it becomes extremely laggy and the screensaver looks terrible. It's performing like it used to before I installed my nVidia drivers.

---

### Post by handband2 on 2006-10-08
> **m.musashi said:**
> This didn't give any output but I don't have beryl running right now since it's hard to do much if it is.

EDIT: I turned everything back on and I got this:
```
root       4719   1.6   0.6   17460 13892 tty7    SLs+ 14:00   0:01 /usr/bin/Xorg vt7 -auth /tmp/ .Xgl-auth-Mhb0xD -nolisten tcp :93 -terminate
```
I had to input that by had as the laptop is not able to connect to the internet at the moment.


I'll post this in a bit. For some reason my wireless adapter on my laptop decided to stop working. However, it is not unlike the example.


Which :0 are you refering to? One in the BusID line or somewhere else?

EDIT: Nevermind. Found it. 

That is exactly the same as mine. Only I had to comment this out to avoide the problems I described.

EDIT: Okay. I made the change and took out the :0. It didn't change anything. The problem still exists.

Thanks again for helping me work this out.

m.musashi,

```
ps uax | grep Xorg | grep Xgl
```
This only can be ran when you have xgl running.

This shows your display number. 93 is the default.

I'm just curious what your xorg.conf looks like.  Everything else seems to be okay.

---

### Post by handband2 on 2006-10-08
> **_lynX said:**
> The bus id was correct, but this made it work! Thank you so much for your help!

Edit: I am still having a problem. When I try to switch to one of the 3d screensaves, it becomes extremely laggy and the screensaver looks terrible. It's performing like it used to before I installed my nVidia drivers.

_lynX,

I would imagine GeForce FX 5900XT card might run a little slow.  

What is your glx output?

Run this with Beryl turned off and on:
```
glxgears -info
```

---

### Post by Charles Hand on 2006-10-08
Geforce go7600 - after the Nvidia splash screen I get black. Commenting out "0=Xgl" restores the system to normal.

xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "SHMConfig" "1"
    Option         "MinSpeed" "0.3"
    Option         "MaxSpeed" "1.0"
    Option         "AccelFactor" "0.07"
    Option         "LeftEdge" "0"
    Option         "TopEdge" "0"
    Option         "RightEdge" "950"
    Option         "BottomEdge" "650"
    Option         "VertScrollDelta" "30"
    Option         "HorizScrollDelta" "30"
    Option         "RTCornerButton" "0"
    Option         "LTCornerButton" "0"
    Option         "RBCornerButton" "0"
    Option         "LBCornerButton" "0"
    Option         "PalmDetect" "1"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"

#    Driver         "nv"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID "PCI:1:0:0"
    Option          "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
    Option "TripleBuffer" "false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option          "RenderAccel" "true"
#    Option         "NvAGP" "0"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection
```

gdm.conf-custom

```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
SoundOnLogin=false
GraphicalTheme=Camping
DefaultWelcome=false
Welcome=This machine is %n

[chooser]

[debug]

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true



```

---

### Post by m.musashi on 2006-10-08
> **handband2 said:**
> I'm just curious what your xorg.conf looks like.  Everything else seems to be okay.

I still can't figure out what is wrong my with wireless on my laptop. I don't see how anything I've been doing would bork wireless.

Anyway, copied the xorg.conf file to a flash drive. Here it is in its glorious entirety.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Aug  1 21:11:12 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "MinSpeed" "1.0"
    Option         "MaxSpeed" "1.0"
    Option         "AccelFactor" "0.2"
    Option         "SHMConfig" "on"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "TrippleBuffer" "false"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection
```

EDIT: I just saw that the device section is not right. I swear I did not right it like this.
```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "TrippleBuffer" "false"
    SubSection     "Display"
```

I just corrected it and rebooted but it is still not working right.

Thanks again.

EDIT: as a test I ran glxgears. It looks choppy with beryl running but it still prints fps of over 3000. Not sure why it looks choppy but that is consistent with the other problems. Everything redraws slowly if at all.

---

### Post by handband2 on 2006-10-08
> **m.musashi said:**
> I still can't figure out what is wrong my with wireless on my laptop. I don't see how anything I've been doing would bork wireless.

Anyway, copied the xorg.conf file to a flash drive. Here it is in its glorious entirety.

m.musashi,

The wireless network problems might be due to kernal changes.

I noticed a few things in your xorg.conf. Backup your current xorg.conf and try this xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Tue Aug  1 21:11:12 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "MinSpeed" "1.0"
    Option         "MaxSpeed" "1.0"
    Option         "AccelFactor" "0.2"
    Option         "SHMConfig" "on"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"    
    BusID          "PCI:1:0:0"                          **[COLOR="Red"]#To find this run $lspci -X[/COLOR]**
    Option         "RenderAccel" "true"  		**[COLOR="Red"]#This belongs in "Device" not "Screen"[/COLOR]**
    Option         "AllowGLXWithComposite" "true"	**[COLOR="Red"]#This belongs in "Device" not "Screen"  [/COLOR]**
    Option         "TrippleBuffer" "false"		[COLOR="Red"]**#This belongs in "Device" not "Screen"**[/COLOR]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24					[COLOR="Red"]**#Your DefaultDepth needs to be 24**[/COLOR]
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

```

---

### Post by _lynX on 2006-10-08
> **handband2 said:**
> _lynX,

I would imagine GeForce FX 5900XT card might run a little slow.  

What is your glx output?

Run this with Beryl turned off and on:
```
glxgears -info
```

With:
> 
684 frames in 6.0 seconds = 114.792 FPS
570 frames in 5.1 seconds = 111.785 FPS
570 frames in 5.0 seconds = 113.626 FPS


Without:
> 
943 frames in 5.6 seconds = 168.688 FPS
912 frames in 5.5 seconds = 165.398 FPS


Even the gears display terribly. The gears will turn very slightly every second and a half or so, and then have a big jump every five seconds or so, and then go back to moving slowly for another five seconds.

---

### Post by m.musashi on 2006-10-08
> **handband2 said:**
> m.musashi,

The wireless network problems might be due to kernal changes.
Before starting this, I already had the 686-smp kernel installed and running so I did not make any kernel changes lately - unless reinstalling the nvidia drivers could have done something.

> I noticed a few things in your xorg.conf. Backup your current xorg.conf and try this xorg.conf:


Sweet, that fixed it. It was the default depth part. I had found and fixed the others (device parts in screen - don't know how that happend). I changed the default depth and it all works fine now.

Thank you very much for the help. Now if I can just find a nice wallpaper to go with my green and black theme :).

---

### Post by handband2 on 2006-10-08
> **_lynX said:**
> With:


Without:


Even the gears display terribly. The gears will turn very slightly every second and a half or so, and then have a big jump every five seconds or so, and then go back to moving slowly for another five seconds.

_lynX,

What *NVIDIA Driver Version* you running?

To check:
```
nvidia-settings
```

---

### Post by handband2 on 2006-10-08
> **m.musashi said:**
> Before starting this, I already had the 686-smp kernel installed and running so I did not make any kernel changes lately - unless reinstalling the nvidia drivers could have done something.



Sweet, that fixed it. It was the default depth part. I had found and fixed the others (device parts in screen - don't know how that happend). I changed the default depth and it all works fine now.

Thank you very much for the help. Now if I can just find a nice wallpaper to go with my green and black theme :).

m.musashi,

Good to hear you got it running.  

To get the wireless network card working, I would try a reinstall.

---

### Post by _lynX on 2006-10-08
> **handband2 said:**
> _lynX,

What *NVIDIA Driver Version* you running?

To check:
```
nvidia-settings
```

```
mark@ubuntu-box:/$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

```

The actual nvidia-settings GUI didn't give me a version number. I assume this is where the problem lies. On startup, I get the nVidia splash screen before it loads gdm, and I installed some nVidia drivers before, which worked.

---

### Post by m.musashi on 2006-10-08
> **handband2 said:**
> m.musashi,

Good to hear you got it running.  

To get the wireless network card working, I would try a reinstall.

Yeah, that is what I was thinking too. I want make a few changes anyway to how it's partitioned so might as well do it all at once. One of the coolest things about Ubuntu is that it's only a 20 or 30 minute process to reinstall as opposed to the several hours that Windows usually invoves.

Thanks again for your help (one of the other really cool things about Ubuntu).

---

### Post by Psquared on 2006-10-08
> **roncrump said:**
> How cool is that!
Followed the instructions and whoosh! Success, pretty windows bling all over the place.

Three small queries:
(1) When I ran sudo apt-get update there were two errors reported at the end, relating to something not being present and therefore being unable to check things (public keys? MDS?). Sorry I forgot to note it down at the time - too excited to move onto the next step, which ran without a hitch, and don't want to re-run it now because of...

(2) As I was doing the updates and installs for beryl, my system update tool decided to tell me that I needed to do some updates. A lot of these updates are X and OpenGL related. Is this just coincidental, or is it going to mess up my new installation to make these updates (I would normally just let the system update whenever it wants to, but I'm a bit nervous about this one). Should I do this updating? I'm avoiding it at present.

(3) The windows of applications in beryl do not have the "ubuntu look" - ie they have no orange-brown header. Is there any way of getting it look more like ubuntu?

Thanks for a great guide.

Regards,
Ron Crump

Same thing happened to me. I held my breath and updated. The updates were fine and didn't disturb a thing. I think you are safe to go ahead with those updates but use the update tool not synaptic.

I also suggest using aptitude rather than apt-get. I read that it handles dependencies better. Not sure if that's true, but that is what I did and sure enough it notified me of missing packages and offered to download and install them for me.

---

### Post by handband2 on 2006-10-08
> **_lynX said:**
> ```
mark@ubuntu-box:/$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

```

The actual nvidia-settings GUI didn't give me a version number. I assume this is where the problem lies. On startup, I get the nVidia splash screen before it loads gdm, and I installed some nVidia drivers before, which worked.

_lynX,

Try following this guide to reinstall the drivers (**[COLOR="Red"]MAKE SURE TO BACK UP YOUR /etc/X11/xorg.conf FILE!!![/COLOR]**):
[http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756]("http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756")

---

### Post by handband2 on 2006-10-08
> **m.musashi said:**
> Yeah, that is what I was thinking too. I want make a few changes anyway to how it's partitioned so might as well do it all at once. One of the coolest things about Ubuntu is that it's only a 20 or 30 minute process to reinstall as opposed to the several hours that Windows usually invoves.

Thanks again for your help (one of the other really cool things about Ubuntu).

m.musashi,

Glad to help!!

If you are going to redo your system I recommend reformatting your system like so:
[LIST]
[*]**/boot** (100 MB)
[/LIST]
[LIST]
[*]**/ ** (Root - 20 - 40 GB)
[/LIST]
[LIST]
[*]**swap** (Size = x2 of your current memory)
[/LIST]
[LIST]
[*]**/home** (The rest of your drive)
[/LIST]

You might already know? But....
What is nice doing it this way is all your home settings and program settings are as they were before (Note: you'll have to reinstall your non-default programs).  When you reinstall just partion and format the **/boot**, **/ **(root), **swap** partitions.  Just mark the **/home** directory.  Don't partiton it.

I also like to always have a backup of my xorg.conf and sources.list files.  Always nice to have :)

---

### Post by handband2 on 2006-10-09
> **Psquared said:**
> Same thing happened to me. I held my breath and updated. The updates were fine and didn't disturb a thing. I think you are safe to go ahead with those updates but use the update tool not synaptic.

I also suggest using aptitude rather than apt-get. I read that it handles dependencies better. Not sure if that's true, but that is what I did and sure enough it notified me of missing packages and offered to download and install them for me.

Psquared,

Thanks for the info.  If anyone wants to read more about it you can go here:
[http://www.psychocats.net/ubuntu/aptitude]("http://www.psychocats.net/ubuntu/aptitude")

The guide talks about [**gtkorphan**]("http://www.marzocca.net/linux/goshots.html").  I would recommend installing this program.

---

### Post by lammer on 2006-10-09
I've try almost everything, but this is kind of desperate :( 

I have the latest NVIDIA (legacy) drivers. Followed this tutorial:
[http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756](http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756) so I think that the driver is NOW properly installed.

My xorg.conf says something like:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@rothera)  Thu Jan  5 15:32:31 UTC 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    #InputDevice    "stylus" "SendCoreEvents"
    #InputDevice    "cursor" "SendCoreEvents"
    #InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    #Identifier     "stylus"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "stylus"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    #Identifier     "eraser"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "eraser"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    #Identifier     "cursor"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "cursor"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "BenQ T90X"
    Option         "DPMS"
EndSection

Section "Device"
   	Identifier     "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true"
	Option 		"TripleBuffer" 		"false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Monitor        "BenQ T90X"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```

I'm trying to make this thing work with an XGL session, so I have made a /usr/share/xsessions/gnome-xgl.desktop file with this content:

```
[Desktop Entry]
Encoding=UTF-8
Name=gnome-xgl
Exec=/usr/bin/startgnomexgl.sh
Icon=
Type=Application
```

And a /usr/bin/startgnomexgl.sh with this other:

```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Iniciar Gnome
exec gnome-session
```

chmod both:
```
sudo chmod 755 /usr/bin/startgnomexgl.sh
sudo chmod 755 /usr/share/xsessions/gnome-xgl.desktop
```

Logoff and then, logon again with XGL session. I have also try the startup program fix "xmodmap -e keycode\ 22\ =\ BackSpace\ Delete " but everytime when I logon the XGL session and try to run beryl-manager from console, it says this:

```
Couldn't load settings.  Reverting to defaults.
XGL Present
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

** (beryl-manager:7255): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
XGL Present
beryl-xgl: Support for non power of two textures missing
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :1.0

** (beryl-manager:7255): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.

```

What that this means? What I'm doing wrong? :-(

---

### Post by Charles Hand on 2006-10-09
> **handband2 said:**
> _lynX,

What *NVIDIA Driver Version* you running?

To check:
```
nvidia-settings
```

What version should it be? Mine is 1.0-8762, and I get black screen when I try to run xgl.

---

### Post by handband2 on 2006-10-09
> **lammer said:**
> I've try almost everything, but this is kind of desperate :( 

I have the latest NVIDIA (legacy) drivers. Followed this tutorial:
[http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756](http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756) so I think that the driver is NOW properly installed.

What that this means? What I'm doing wrong? :-(

lammer,

Did you turn off XGL in gdm.conf-custom?
```
sudo gedit /etc/gdm/gdm.conf-custom
```
```
#0=Xgl
#[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
#flexible=true
```

---

### Post by handband2 on 2006-10-09
> **Charles Hand said:**
> What version should it be? Mine is 1.0-8762, and I get black screen when I try to run xgl.

Charles Hand,

1.0-8762 should be fine.  I have that driver version running perfectly on my work machine.

To fix the black screen problem could you paste your /etc/X11/xorg.conf file and what happens when you run:
```
glxgears -info
```

---

### Post by Charles Hand on 2006-10-09
> **handband2 said:**
> Charles Hand,

1.0-8762 should be fine.  I have that driver version running perfectly on my work machine.

To fix the black screen problem could you paste your /etc/X11/xorg.conf file and what happens when you run:
```
glxgears -info
```

xorg.conf is posted [here]("http://www.ubuntuforums.org/showthread.php?p=1594438#post1594438")

glxgears -info:
```
GL_RENDERER   = GeForce Go 7600 GT/PCI/SSE2
GL_VERSION    = 2.0.2 NVIDIA 87.62
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
50426 frames in 5.0 seconds = 10085.192 FPS
69826 frames in 5.0 seconds = 13965.134 FPS
69176 frames in 5.0 seconds = 13835.119 FPS
64366 frames in 5.0 seconds = 12873.055 FPS
66771 frames in 5.0 seconds = 13351.216 FPS
65028 frames in 5.0 seconds = 13005.574 FPS
70937 frames in 5.0 seconds = 14187.330 FPS
67040 frames in 5.0 seconds = 13407.900 FPS


```

---

### Post by handband2 on 2006-10-09
> **Charles Hand said:**
> xorg.conf is posted [here]("http://www.ubuntuforums.org/showthread.php?p=1594438#post1594438")



Try this for your xorg.conf:
```
Section "Device"
#   Driver         "nv"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID 	   "PCI:1:0:0"			[COLOR="Red"]**#Make sure this is correct by running $lspci -X**[/COLOR]
    Option         "RenderAccel" "true"
    Option 	   "AllowGLXWithComposite" "true"
    Option 	   "TripleBuffer" "false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
#   Option         "RenderAccel" "true"		[COLOR="Red"]**#Only have it once in the "Device" or "Screen" Section**[/COLOR]
#   Option         "NvAGP" "0"
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection
```

---

### Post by Charles Hand on 2006-10-09
> **handband2 said:**
> Try this for your xorg.conf:
```
Section "Device"
#   Driver         "nv"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID 	   "PCI:1:0:0"			[COLOR="Red"]**#Make sure this is correct by running $lspci -X**[/COLOR]
    Option         "RenderAccel" "true"
    Option 	   "AllowGLXWithComposite" "true"
    Option 	   "TripleBuffer" "false"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
#   Option         "RenderAccel" "true"		[COLOR="Red"]**#Only have it once in the "Device" or "Screen" Section**[/COLOR]
#   Option         "NvAGP" "0"
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection
```


Here is lspci -x 
```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00: 86 80 a0 27 06 01 90 20 03 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
00: 86 80 a1 27 07 04 10 00 03 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 20 20 00 00
20: 00 d0 f0 d1 01 b0 f1 bf 00 00 00 00 00 00 00 00
30: 00 00 00 00 88 00 00 00 00 00 00 00 07 01 08 00

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio
Controller (rev 02)
00: 86 80 d8 27 06 00 10 00 02 00 03 04 10 00 00 00
10: 04 00 30 d2 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 50 00 00 00 00 00 00 00 04 01 00 00

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00: 86 80 d0 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 02 03 00 30 30 00 00
20: 00 c8 f0 c9 01 c0 f1 c1 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 03 01 04 00

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00: 86 80 d2 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 04 05 00 40 40 00 00
20: 00 ca f0 cb 01 c2 f1 c3 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 07 02 04 00

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00: 86 80 d4 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 06 07 00 50 50 00 00
20: 00 cc f0 cd 01 c4 f1 c5 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 0b 03 04 00

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00: 86 80 d6 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 08 09 00 60 60 00 00
20: 00 ce f0 cf 01 c6 f1 c7 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 04 04 00

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1
(rev 02)
00: 86 80 c8 27 05 00 80 02 02 00 03 0c 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 05 01 00 00

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2
(rev 02)
00: 86 80 c9 27 05 00 80 02 02 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 21 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 03 02 00 00

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3
(rev 02)
00: 86 80 ca 27 05 00 80 02 02 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 41 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 03 00 00

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4
(rev 02)
00: 86 80 cb 27 05 00 80 02 02 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 61 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 07 04 00 00

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00: 86 80 cc 27 06 00 90 02 02 20 03 0c 00 00 00 00
10: 00 40 30 d2 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 50 00 00 00 00 00 00 00 05 01 00 00

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00: 86 80 48 24 07 00 10 00 e2 01 04 06 00 00 01 00
10: 00 00 00 00 00 00 00 00 00 0a 0e 20 70 70 80 22
20: 00 d2 00 d2 01 88 f1 89 00 00 00 00 00 00 00 00
30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 00 00 00

0000:00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00: 86 80 bd 27 07 00 10 02 02 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00: 86 80 df 27 05 00 88 02 02 8a 01 01 00 00 00 00
10: 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00
20: 81 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 01 00 00

0000:00:1f.2 RAID bus controller: Intel Corporation 82801GHM (ICH7-M DH) Serial
ATA Storage Controllers cc=RAID (rev 02)
00: 86 80 c6 27 07 00 b0 02 02 00 04 01 00 00 00 00
10: c9 18 00 00 ad 18 00 00 c1 18 00 00 a9 18 00 00
20: b1 18 00 00 00 44 30 d2 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 80 00 00 00 00 00 00 00 0a 02 00 00

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
00: 86 80 da 27 01 00 80 02 02 00 05 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: e1 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 02 00 00

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0399
(rev a1)
00: de 10 99 03 07 00 10 00 a1 00 00 03 00 00 00 00
10: 00 00 00 d1 0c 00 00 b0 00 00 00 00 04 00 00 d0
20: 00 00 00 00 01 20 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 60 00 00 00 00 00 00 00 07 01 00 00

0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)00: 86 80 22 42 06 00 10 00 02 00 80 02 10 00 00 00
10: 00 00 00 cc 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 50 10
30: 00 00 00 00 c8 00 00 00 00 00 00 00 0b 01 00 00

0000:0a:03.0 CardBus bridge: Texas Instruments: Unknown device 8039
00: 4c 10 39 80 07 00 10 02 00 00 07 06 08 a8 82 00
10: 00 70 00 d2 a0 00 00 02 0a 0b 0e b0 00 00 00 88
20: 00 f0 ff 89 00 00 00 8a 00 f0 ff 8b 00 74 00 00
30: fc 74 00 00 00 78 00 00 fc 78 00 00 ff 01 c0 05
40: 4d 10 fd 81 01 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

0000:0a:03.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
00: 4c 10 3a 80 06 00 10 02 00 10 00 0c 10 40 80 00
10: 00 60 00 d2 00 00 00 d2 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 44 00 00 00 00 00 00 00 07 01 03 04

0000:0a:03.2 Mass storage controller: Texas Instruments: Unknown device 803b
00: 4c 10 3b 80 00 00 10 02 00 00 80 01 10 40 80 00
10: 00 40 00 d2 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 44 00 00 00 00 00 00 00 03 02 07 04

0000:0a:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)
00: 86 80 92 10 07 00 90 02 02 00 00 02 10 40 00 00
10: 00 50 00 d2 01 70 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 dc 00 00 00 00 00 00 00 0b 01 08 38

charlie@gemini:~$ lspci -x | more
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00: 86 80 a0 27 06 01 90 20 03 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
00: 86 80 a1 27 07 04 10 00 03 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 20 20 00 00
20: 00 d0 f0 d1 01 b0 f1 bf 00 00 00 00 00 00 00 00
30: 00 00 00 00 88 00 00 00 00 00 00 00 07 01 08 00

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio
Controller (rev 02)
00: 86 80 d8 27 06 00 10 00 02 00 03 04 10 00 00 00
10: 04 00 30 d2 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 50 00 00 00 00 00 00 00 04 01 00 00

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00: 86 80 d0 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 02 03 00 30 30 00 00
20: 00 c8 f0 c9 01 c0 f1 c1 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 03 01 04 00

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00: 86 80 d2 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 04 05 00 40 40 00 00
20: 00 ca f0 cb 01 c2 f1 c3 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 07 02 04 00

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00: 86 80 d4 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 06 07 00 50 50 00 00
20: 00 cc f0 cd 01 c4 f1 c5 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 0b 03 04 00

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00: 86 80 d6 27 07 04 10 00 02 00 04 06 10 00 81 00
10: 00 00 00 00 00 00 00 00 00 08 09 00 60 60 00 00
20: 00 ce f0 cf 01 c6 f1 c7 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 04 04 00

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1
(rev 02)
00: 86 80 c8 27 05 00 80 02 02 00 03 0c 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 05 01 00 00

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2
(rev 02)
00: 86 80 c9 27 05 00 80 02 02 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 21 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 03 02 00 00

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3
(rev 02)
00: 86 80 ca 27 05 00 80 02 02 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 41 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 03 00 00

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4
(rev 02)
00: 86 80 cb 27 05 00 80 02 02 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 61 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 07 04 00 00

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00: 86 80 cc 27 06 00 90 02 02 20 03 0c 00 00 00 00
10: 00 40 30 d2 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 50 00 00 00 00 00 00 00 05 01 00 00

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00: 86 80 48 24 07 00 10 00 e2 01 04 06 00 00 01 00
10: 00 00 00 00 00 00 00 00 00 0a 0e 20 70 70 80 22
20: 00 d2 00 d2 01 88 f1 89 00 00 00 00 00 00 00 00
30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 00 00 00

0000:00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00: 86 80 bd 27 07 00 10 02 02 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00: 86 80 df 27 05 00 88 02 02 8a 01 01 00 00 00 00
10: 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00
20: 81 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 01 00 00

0000:00:1f.2 RAID bus controller: Intel Corporation 82801GHM (ICH7-M DH) Serial
ATA Storage Controllers cc=RAID (rev 02)
00: 86 80 c6 27 07 00 b0 02 02 00 04 01 00 00 00 00
10: c9 18 00 00 ad 18 00 00 c1 18 00 00 a9 18 00 00
20: b1 18 00 00 00 44 30 d2 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 80 00 00 00 00 00 00 00 0a 02 00 00

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
00: 86 80 da 27 01 00 80 02 02 00 05 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: e1 18 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 02 00 00

0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0399
(rev a1)
00: de 10 99 03 07 00 10 00 a1 00 00 03 00 00 00 00
10: 00 00 00 d1 0c 00 00 b0 00 00 00 00 04 00 00 d0
20: 00 00 00 00 01 20 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 60 00 00 00 00 00 00 00 07 01 00 00

0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)00: 86 80 22 42 06 00 10 00 02 00 80 02 10 00 00 00
10: 00 00 00 cc 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 86 80 50 10
30: 00 00 00 00 c8 00 00 00 00 00 00 00 0b 01 00 00

0000:0a:03.0 CardBus bridge: Texas Instruments: Unknown device 8039
00: 4c 10 39 80 07 00 10 02 00 00 07 06 08 a8 82 00
10: 00 70 00 d2 a0 00 00 02 0a 0b 0e b0 00 00 00 88
20: 00 f0 ff 89 00 00 00 8a 00 f0 ff 8b 00 74 00 00
30: fc 74 00 00 00 78 00 00 fc 78 00 00 ff 01 c0 05
40: 4d 10 fd 81 01 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

0000:0a:03.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
00: 4c 10 3a 80 06 00 10 02 00 10 00 0c 10 40 80 00
10: 00 60 00 d2 00 00 00 d2 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 44 00 00 00 00 00 00 00 07 01 03 04

0000:0a:03.2 Mass storage controller: Texas Instruments: Unknown device 803b
00: 4c 10 3b 80 00 00 10 02 00 00 80 01 10 40 80 00
10: 00 40 00 d2 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 44 00 00 00 00 00 00 00 03 02 07 04

0000:0a:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)
00: 86 80 92 10 07 00 90 02 02 00 00 02 10 40 00 00
10: 00 50 00 d2 01 70 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4d 10 fd 81
30: 00 00 00 00 dc 00 00 00 00 00 00 00 0b 01 08 38

```

Is this the one for the Nvidia chip?

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)

And so would I put BusID "PCI:0:0:1" in xorg.conf?

Thanks.:o :o

---

### Post by handband2 on 2006-10-09
> **Charles Hand said:**
> 
Is this the one for the Nvidia chip?

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)

And so would I put BusID "PCI:0:0:1" in xorg.conf?

Thanks.:o :o


Sorry...type this in:
```
lspci -X
```
**[COLOR="Red"]NOT[/COLOR]**
```
lspci -x
```

---

### Post by _lynX on 2006-10-09
> **handband2 said:**
> _lynX,

Try following this guide to reinstall the drivers (**[COLOR="Red"]MAKE SURE TO BACK UP YOUR /etc/X11/xorg.conf FILE!!![/COLOR]**):
[http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756]("http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756")

I followed the tutorial and everything is still running fine. The screensaver is still pretty jerky, but it's much less so than before. Here's the updated glxgears info with beryl:
```
mark@ubuntu-box:/$ glxgears
829 frames in 5.3 seconds = 155.244 FPS
798 frames in 5.5 seconds = 143.888 FPS
798 frames in 5.4 seconds = 147.753 FPS
798 frames in 5.4 seconds = 146.591 FPS

```

---

### Post by m.musashi on 2006-10-09
> **handband2 said:**
> m.musashi,

Glad to help!!

If you are going to redo your system I recommend reformatting your system like so:
[LIST]
[*]**/boot** (100 MB)
[/LIST]
[LIST]
[*]**/ ** (Root - 20 - 40 GB)
[/LIST]
[LIST]
[*]**swap** (Size = x2 of your current memory)
[/LIST]
[LIST]
[*]**/home** (The rest of your drive)
[/LIST]

You might already know? But....
What is nice doing it this way is all your home settings and program settings are as they were before (Note: you'll have to reinstall your non-default programs).  When you reinstall just partion and format the **/boot**, **/ **(root), **swap** partitions.  Just mark the /home directory.  Don't partiton it.

I also like to always have a backup of my xorg.conf and sources.list files.  Always nice to have :)
I'm drifting a bit off topic here. But since it came up, how do you specify the /boot partition? Is it /dev/sda1 or /sda0 or something? My dell has a hidden partition with a drive image for reinstallation and I think it was /sda1 with windows on sda2 (not entirely sure since I don't have the computer with me at the moment). /boot would be where grub is installed, right? Since the ubuntu installer sets this automatically, is there a need to worry about it?

Also, how firm is the swap 2x the memory rule. I usually do a 3GB swap since that is what Ubuntu seems to default to if I don't specify. I have a gig on my desktop. I did the same 3GB swap on the laptop but it actually has 2GB of memory. Do I really need a 6GB swap partiton or is the 2x rule more for low memory systems?

Thanks again.

---

### Post by handband2 on 2006-10-09
> **_lynX said:**
> I followed the tutorial and everything is still running fine. The screensaver is still pretty jerky, but it's much less so than before. Here's the updated glxgears info with beryl:
```
mark@ubuntu-box:/$ glxgears
829 frames in 5.3 seconds = 155.244 FPS
798 frames in 5.5 seconds = 143.888 FPS
798 frames in 5.4 seconds = 147.753 FPS
798 frames in 5.4 seconds = 146.591 FPS

```

It appears your NVIDIA driver isn't installed and/or running correctly.

What is your output when you run:
```
glxgears -info
```

Did you install your NVIDIA Driver with [Automatix]("http://www.getautomatix.com/")?

---

### Post by _lynX on 2006-10-09
> **handband2 said:**
> It appears your NVIDIA driver isn't installed and/or running correctly.

What is your output when you run:
```
glxgears -info
```

Did you install your NVIDIA Driver with [Automatix]("http://www.getautomatix.com/")?

```
mark@ubuntu-box:/$ glxgears -info
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.5.1)
GL_VENDOR     = Mesa project: www.mesa3d.org
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_vertex_program GL_ARB_window_pos GL_ATI_texture_mirror_once GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow
373 frames in 5.9 seconds = 63.093 FPS

```

I installed the drivers using the link you gave me, downloading them directly from Nvidia.com.

---

### Post by handband2 on 2006-10-09
> **m.musashi said:**
> I'm drifting a bit off topic here. But since it came up, how do you specify the /boot partition? Is it /dev/sda1 or /sda0 or something? My dell has a hidden partition with a drive image for reinstallation and I think it was /sda1 with windows on sda2 (not entirely sure since I don't have the computer with me at the moment). /boot would be where grub is installed, right? Since the ubuntu installer sets this automatically, is there a need to worry about it?

Also, how firm is the swap 2x the memory rule. I usually do a 3GB swap since that is what Ubuntu seems to default to if I don't specify. I have a gig on my desktop. I did the same 3GB swap on the laptop but it actually has 2GB of memory. Do I really need a 6GB swap partiton or is the 2x rule more for low memory systems?

Thanks again.

m.musashi,

If you already have a dual boot system don't worry about /boot partition.  Creating /boot partition might mess things up.  Just use:
[B][LIST]
[*]/ (Root)
[/LIST]
[LIST]
[*]Swap
[/LIST]
[LIST]
[*]/home
[/LIST][/B]

As long as you have a seperate /home partition.  Reinstalls are less of a headaches ](*,) 

I wouldn't touch the hidden partition made by Dell.  You might need that partition later on.

This might help with the issue of the swap partition:
[http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs03.html]("http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/apbs03.html")

---

### Post by handband2 on 2006-10-09
> **_lynX said:**
> 

I installed the drivers using the link you gave me, downloading them directly from Nvidia.com.

Try using Automatix to install the NVIDIA Driver:
[Automatix2]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_on_.28K.2FX.29Ubuntu_6.06_i386_amd64_.28Dapper.29")

---

### Post by rolando2424 on 2006-10-09
It worked like a charm.

Thanks man :D

---

### Post by frobroj on 2006-10-09
I installed it 6 times on 3 different machines with fresh installs of ubuntu 6.06 and it works great on all machines until I reboot the second time. Kablow! they wont load x after that. Well I will try it on 6.10 maybe I will have better luck. If not its back to compiz. arrghhh... Want the pretty! Cant have the pretty... :(

---

### Post by Charles Hand on 2006-10-09
> **handband2 said:**
> Sorry...type this in:
```
lspci -X
```
**[COLOR="Red"]NOT[/COLOR]**
```
lspci -x
```

```

PCI:0:0:0 Host bridge: Intel Corporation Mobile Memory Controller Hub
PCI:0:1:0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port
PCI:0:27:0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
PCI:0:28:0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1
PCI:0:28:1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2
PCI:0:28:2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3
PCI:0:28:3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4
PCI:0:29:0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1
PCI:0:29:1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2
PCI:0:29:2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3
PCI:0:29:3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4
PCI:0:29:7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller
PCI:0:30:0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge
PCI:0:31:0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge
PCI:0:31:1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller
PCI:0:31:2 RAID bus controller: Intel Corporation 82801GHM (ICH7-M DH) Serial ATA Storage Controllers cc=RAID
PCI:0:31:3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller
PCI:1:0:0 VGA compatible controller: nVidia Corporation: Unknown device 0399
PCI:6:0:0 Network controller: Intel Corporation: Unknown device 4222
PCI:10:3:0 CardBus bridge: Texas Instruments: Unknown device 8039
PCI:10:3:1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
PCI:10:3:2 Mass storage controller: Texas Instruments: Unknown device 803b
PCI:10:8:0 Ethernet controller: Intel Corporation: Unknown device 1092

```

So I guess PCI:1:0:0 is correct? Or is it the Express Graphics Port, 0:1:0?

---

### Post by handband2 on 2006-10-09
> **frobroj said:**
> I installed it 6 times on 3 different machines with fresh installs of ubuntu 6.06 and it works great on all machines until I reboot the second time. Kablow! they wont load x after that. Well I will try it on 6.10 maybe I will have better luck. If not its back to compiz. arrghhh... Want the pretty! Cant have the pretty... :(

frobroj,

Have you looked into your logs to see the problems?
```
gedit /var/log/messages
gedit /var/log/Xorg.0.log
```
and look into the gdm logs:
```
nautilus /var/log/gdm
```

Also double check your */etc/X11/xorg.conf* file.  Usually when X crashes it has to do with the xorg.conf file

---

### Post by handband2 on 2006-10-09
> **Charles Hand said:**
> 

So I guess PCI:1:0:0 is correct? Or is it the Express Graphics Port, 0:1:0?

You're correct.  Your card is:
> PCI:1:0:0 VGA compatible controller: nVidia Corporation: Unknown device 0399

Did you uncomment server-XGL in gdm.conf-custom?
```
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

Oh, just double check your xorg.conf one more time for any mistakes.

---

### Post by frobroj on 2006-10-09
Well that would be fine but I cant even get cntrl alt f1 to work. I mean its HUNG. Anywho I am too damn lazy to put in knoppix and go hunting. I dont want to use a product that I have to coax and tweak to get to work. I would rather have one that works out of the box(Hmm since its open source it never really comes out of a box so that little saying may have to be revamped..).  THanks for the help. I'll see if I have any luck on Edgy. If not then compiz it is. THanks for the help though! :)

---

### Post by Charles Hand on 2006-10-09
> **handband2 said:**
> You're correct.  Your card is:


Did you uncomment server-XGL in gdm.conf-custom?
```
0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

Oh, just double check your xorg.conf one more time for any mistakes.

Ok, well, the only thing I have changed is to remove the redundant "RenderAccel" from the Screen section and only have it in the Device section.

I still get black screen after the Nvidia splash when I uncomment 0=Xgl. Did I mention I'm SMP? Maybe that has something to do with it.

Thanks for the help. I'll wait a few weeks. Nice thing about Linux is, you wait a few weeks and somebody changes something which solves your problem. I only look forward to getting up to speed and becoming one of the fixers. I figure XGL is a little too bleeding-edge for me to start with, though.;)

---

### Post by m.musashi on 2006-10-09
> **Charles Hand said:**
> Ok, well, the only thing I have changed is to remove the redundant "RenderAccel" from the Screen section and only have it in the Device section.

I still get black screen after the Nvidia splash when I uncomment 0=Xgl. Did I mention I'm SMP? Maybe that has something to do with it.
I can confirm that beryl works with an smp kernel. I installed the 686-smp on my laptop and I have it running fine. It was a somewhat bumpy road but in the end it was just not having all the config files set up right.

> I only look forward to getting up to speed and becoming one of the fixers.
As soon as you figure out what is causing your problem you will be able to help others who have a similar problem. I don't know much about Linux, but when someone has a problem similar to one I've had and fixed I can usually share that and hopefully help them.

---

### Post by handband2 on 2006-10-09
> **Charles Hand said:**
> Ok, well, the only thing I have changed is to remove the redundant "RenderAccel" from the Screen section and only have it in the Device section.

I still get black screen after the Nvidia splash when I uncomment 0=Xgl. Did I mention I'm SMP? Maybe that has something to do with it.

Thanks for the help. I'll wait a few weeks. Nice thing about Linux is, you wait a few weeks and somebody changes something which solves your problem. I only look forward to getting up to speed and becoming one of the fixers. I figure XGL is a little too bleeding-edge for me to start with, though.;)

Charles Hand,

I'm running on smp just fine right now.  I also ran into some errors where I would get black screens when I first installed Beryl.  Like you, I thought everything was fine because when I ran glxgears I got good FPS's.  Then I realized the reason for my errors was because I installed the NVIDIA drivers with the original kernel (non-smp).  Once I upgraded to the most recent NVIDIA drivers with my current smp kernel everything ran fine! :) 

This is the method I used to upgrade my drivers to my current kernel:
[http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756]("http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756")

---

### Post by handband2 on 2006-10-09
> **frobroj said:**
> Well that would be fine but I cant even get cntrl alt f1 to work. I mean its HUNG. Anywho I am too damn lazy to put in knoppix and go hunting. I dont want to use a product that I have to coax and tweak to get to work. I would rather have one that works out of the box(Hmm since its open source it never really comes out of a box so that little saying may have to be revamped..).  THanks for the help. I'll see if I have any luck on Edgy. If not then compiz it is. THanks for the help though! :)

frobroj,

Turn off XGL then try to update out of gdm.  If you can't Ctrl+Alt+F1,F2,F3,F4,F5,F6 you might have more problems later on.

You shouldn't need knoppix to fix the problem.  There are only few files you have to edit once you get your drivers upgraded with your current kernel:
```
sudo gedit /etc/apt/sources.list
sudo gedit /etc/apt/sources.list
sudo gedit /etc/gdm/gdm.conf-custom
```

Oh, The last time I tried it on Edgy it had some problems but I noticed there has been a few updates since then so some of the bugs might have been fixed.

---

### Post by _lynX on 2006-10-09
> **handband2 said:**
> Try using Automatix to install the NVIDIA Driver:
[Automatix2]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_on_.28K.2FX.29Ubuntu_6.06_i386_amd64_.28Dapper.29")

Doing that caused an error on reboot having to do with not being able to load the X server because the nVidia drivers mismatched the hardware or something along the lines of that, so I had to reinstall the drivers using the nvidia.com linux package you showed me earlier.

Edit: I just noticed that you gave a link to Automatix2, while I was using Automatix1. Trying again.

---

### Post by Charles Hand on 2006-10-10
I was getting a black screen when 0=Xgl was enabled in gdm.conf-custom. 

I followed the procedure here:
[http://www.biodesign.com.ar/blog/?p=16](http://www.biodesign.com.ar/blog/?p=16)
which creates a desktop session in lieu of the gdm.conf-custom thing, and presto! Beryl works.

I don't know what the difference between the two is.

This one doesn't work for me (in gdm.conf-custom)

```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

This does work for me, in /usr/bin/startxgl.sh
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session
```

which is started by a .desktop file as described in the above howto.

I actually like this method because I get to pick XGL or non-XGL when I log in.

Sony Vaio VGN-AR170P with Nvidia GEforce GO7600.

Maybe it's the :1 instead of :0, but I think I tried changing zeros to ones in gdm.conf-custom to no avail. I could be mistaken.

---

### Post by dckirba on 2006-10-10
[QUOTE=djRobbieF;1559948]Version 1.5


```
[color=#FE000A]0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true[/color]
```

Could you please let me know what this does? I have a seperate xgl session enabled, do I still need to use this?

Thanks,
David K

---

### Post by dannyboy79 on 2006-10-10
> **dckirba said:**
> [QUOTE=djRobbieF;1559948]Version 1.5


```
[color=#FE000A]0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true[/color]
```

Could you please let me know what this does? I have a seperate xgl session enabled, do I still need to use this?

Thanks,
David K

You don't need that, that is for people who want xgl and compiz as their main session. I am like you and have a different session when I want to compiz it up. You can read the post directly above yours and read that he doesn't use that either with his different session so you'll be fine without it.

---

### Post by handband2 on 2006-10-10
> **Charles Hand said:**
> I was getting a black screen when 0=Xgl was enabled in gdm.conf-custom. 

I followed the procedure here:
[http://www.biodesign.com.ar/blog/?p=16](http://www.biodesign.com.ar/blog/?p=16)
which creates a desktop session in lieu of the gdm.conf-custom thing, and presto! Beryl works.

which is started by a .desktop file as described in the above howto.

I actually like this method because I get to pick XGL or non-XGL when I log in.

Sony Vaio VGN-AR170P with Nvidia GEforce GO7600.

Maybe it's the :1 instead of :0, but I think I tried changing zeros to ones in gdm.conf-custom to no avail. I could be mistaken.

Charles Hand,

I'm glad you got it working by creating a session.  I should of offered that to you earlier because I had a quick guide to do it:
[http://www.ubuntuforums.org/showpost.php?p=1564565&postcount=75]("http://www.ubuntuforums.org/showpost.php?p=1564565&postcount=75")

Please make note to what is says in the gdm.conf file for a future reference:
```
sudo gedit /etc/X11/gdm/gdm.conf
```
[I]> # How long gdm should wait before it assumes a started Xserver is defunct and
# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
GdmXserverTimeout=10[/I]

---

### Post by PingunZ on 2006-10-10
Better then quinn's compiz
Works like a charm 
Great guide ! :KS 

Cheers

---

### Post by lammer on 2006-10-10
> **handband2 said:**
> lammer,
Did you turn off XGL in gdm.conf-custom?


Yes hadnband2, this is my gdm.conf-custom content right now:

```

[daemon]

[security]

[xdmcp]

[gui]

[greeter]
SoundOnLoginSuccessFile=/usr/share/sounds/startup.wav
DefaultWelcome=false

[chooser]

[debug]

[servers]

```

As you can see the file is empty. I understand that if I use an XGL session to try to make Beryl work, this file is not needed.

If I try to use this file, and not an XGL session, I get a beautyful X server crash, with no output.

Any ideas?

Thanks for your help dude!!!

---

### Post by _lynX on 2006-10-10
Autinatux2 installs the same drivers as Automatix, so I came up with the same problem. I'm back on the drivers from the nvidia site.

---

### Post by handband2 on 2006-10-10
> **lammer said:**
> Yes hadnband2, this is my gdm.conf-custom content right now:

As you can see the file is empty. I understand that if I use an XGL session to try to make Beryl work, this file is not needed.

If I try to use this file, and not an XGL session, I get a beautyful X server crash, with no output.

Any ideas?

Thanks for your help dude!!!

Everything looks good on the XGL setup.  

Double check to see if your NVIDIA drivers are installed correctly.  What is your output when you run:
```
glxgears -info
```

---

### Post by handband2 on 2006-10-10
> **_lynX said:**
> Autinatux2 installs the same drivers as Automatix, so I came up with the same problem. I'm back on the drivers from the nvidia site.

_lynX,

Have you tried this:
[http://www.ubuntuforums.org/showpost.php?p=1591756&postcount=237]("http://www.ubuntuforums.org/showpost.php?p=1591756&postcount=237")
to update the NVIDIA driver?

---

### Post by lammer on 2006-10-10
> **handband2 said:**
> Double check to see if your NVIDIA drivers are installed correctly.  What is your output when you run:
```
glxgears -info
```

This is the output:

```
GL_RENDERER   = RIVA TNT2/AGP/3DNOW!
GL_VERSION    = 1.5.3 NVIDIA 71.84
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture ...
```

I understand that my nvidia drivers are the latest, as long as I have tried both with automatix and with the Nvidia website (The ones I have now installed). They fully work 'cause the gears are shown, and I can run OpenGL games...

In case that's important, I'm running the AMD kernel, not the default 386. And yes, I have installed the Nvidia drivers **after** the kernel update.

Maybe the problem is with my old TNT2 card. I think it's possible that this card is not fully suported... Or maybe is my OLD AMD850Mhz with 512Mb...

:-?

---

### Post by handband2 on 2006-10-10
> **lammer said:**
> This is the output:

I understand that my nvidia drivers are the latest, as long as I have tried both with automatix and with the Nvidia website (The ones I have now installed). They fully work 'cause the gears are shown, and I can run OpenGL games...

In case that's important, I'm running the AMD kernel, not the default 386. And yes, I have installed the Nvidia drivers **after** the kernel update.

Maybe the problem is with my old TNT2 card. I think it's possible that this card is not fully suported... Or maybe is my OLD AMD850Mhz with 512Mb...

:-?

Your card should be fine.  It is in the list of compatible chipsets for the driver.  Since your card is setup correctly lets check some other stuff.

Here are few things to troubleshoot:
[LIST]
[*]See if your **BusID** is correct in your **xorg.conf** file
```
lspci -X
```[/LIST]
[LIST]
[*]Try turning on **RenderAccel** in your **xorg.conf**
```
Option "RenderAccel" "true"
```
[/LIST]
[LIST]
[*]Make sure you don't have any sessions that could interfere with the start of Beryl/Xgl (Go to **System –> Preferences –> Sessions –> Startup Programs**)
```
xmodmap -e "keycode 22 = BackSpace"
beryl-manager
```
[/LIST]
[LIST]
[*]Make sure you place the code in the right places
```
/usr/bin/startxgl.sh
not
/usr/bin/startgnomexgl.sh
```
```
sudo chmod 755 /usr/bin/startxgl.sh
sudo gedit /usr/share/xsessions/xgl.desktop
not
sudo chmod 755 /usr/bin/startgnomexgl.sh
sudo chmod 755 /usr/share/xsessions/gnome-xgl.desktop
```
[/LIST]
[LIST]
[*]chmod only
```
sudo chmod 755 /usr/bin/startxgl.sh
not
sudo chmod 755 /usr/share/xsessions/gnome-xgl.desktop
```
[/LIST]

Double check my howto and see where you might of made the mistakes from what you did:
[My Howto]("http://ubuntuforums.org/showpost.php?p=1564565&postcount=75")
[What you did]("http://ubuntuforums.org/showpost.php?p=1595854&postcount=278")

EDIT:  I found this as requirements to run XGL:
All NVIDIA cards need the proprietary driver for running Xgl. Currently you will need to uninstall and reinstall the xgl rpm after installing the proprietary NVidia driver.

[LIST]
[*]    GeForce 4xxx series - XVideo is not accelerated on these cards.
[*]    GeForce FX 5xxx series, Quadro FX series - Accelerated XVideo is hitting a slow path on these cards, it is under investigation.
[*]    GeForce 6xxx series
[*]    GeForce 7xxx series
[/LIST]

---

### Post by Johntam on 2006-10-10
I am looking forward to trying out Beryl on my Dapper64 install.
But I would like to resolve a few possible problems first.

I am using a BFG 7600gt nVidia card.
nVidia Driver installed using Automtix1.

First problem,the Device setion of my xorg.conf file has only 2 lines :
"Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection"
Is it safe to just add the other lines indicated in the HowTo ?

2nd problem, when run "glxgears -info, I get this:
"johntam@papa:~$ glxgears -info
GL_RENDERER   = GeForce 7600 GT/PCI/SSE2
GL_VERSION    = 2.0.2 NVIDIA 87.62
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum"

How can I get it to show the FPS.


Thanks 
JT

---

### Post by m.musashi on 2006-10-10
> **Johntam said:**
> I am looking forward to trying out Beryl on my Dapper64 install.
But I would like to resolve a few possible problems first.

I am using a BFG 7600gt nVidia card.
nVidia Driver installed using Automtix1.

First problem,the Device setion of my xorg.conf file has only 2 lines :
"Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection"
Is it safe to just add the other lines indicated in the HowTo ?
Yes, you can safely modify the xorg.conf file. Make a backup just in case and make sure you can replace it or edit it from a terminal session (i.e. no gui). I have the xfx 7600gs card and it works fine. I'm sure the gt will be just that much better.

> 2nd problem, when run "glxgears -info, I get this:
"johntam@papa:~$ glxgears -info


How can I get it to show the FPS.
Thanks 
JT

```
glxgears -printfps
```
I get about 4500fps with my card so you will likely see similar if all is installed correctly.

EDIT: I just noticed that the -printfps is not working for some reason. Maybe there was an update or maybe it's because I'm running beryl - I don't really know. However, just the "glxgears" command seems to run both the gears and give the fps printout. I also noticed that my fps is now 7900fps. Odd, I would have thought beryl would have decreased those numbers not increased them. Oh well, I guess that's why they say it's not a benchmark tool :).

---

### Post by Charles Hand on 2006-10-10
> **handband2 said:**
> 
Please make note to what is says in the gdm.conf file for a future reference:
```
sudo gedit /etc/X11/gdm/gdm.conf
```
```

 # How long gdm should wait before it assumes a started Xserver is defunct and
# kills it. 10 seconds should be long enough for X, but Xgl may need 20 or 25.
GdmXserverTimeout=10
```
**

OK, I took care of that. Much obliged.

Do you know anything about this weird business with the shutdown and reboot buttons in this thread?
[http://www.ubuntuforums.org/showthread.php?t=244662](http://www.ubuntuforums.org/showthread.php?t=244662)

---

### Post by Johntam on 2006-10-10
Musashi, thanks for the quick help.
glxgears -printfps worked.
This is what I got:
johntam@papa:~$ glxgears -printfps
53187 frames in 5.0 seconds = 10637.341 FPS
53142 frames in 5.0 seconds = 10628.400 FPS
53186 frames in 5.0 seconds = 10637.165 FPS
53170 frames in 5.0 seconds = 10633.968 FPS
53154 frames in 5.0 seconds = 10630.649 FPS
53186 frames in 5.0 seconds = 10637.049 FPS
53193 frames in 5.0 seconds = 10638.428 FPS
53154 frames in 5.0 seconds = 10630.700 FPS
53149 frames in 5.0 seconds = 10629.624 FPS
53193 frames in 5.0 seconds = 10638.485 FPS
53146 frames in 5.0 seconds = 10629.042 FPS
53118 frames in 5.0 seconds = 10623.464 FPS
53025 frames in 5.0 seconds = 10604.958 FPS
53144 frames in 5.0 seconds = 10628.615 FPS
53178 frames in 5.0 seconds = 10635.540 FPS
53168 frames in 5.0 seconds = 10633.556 FPS
53151 frames in 5.0 seconds = 10630.005 FPS
53183 frames in 5.0 seconds = 10636.462 FPS
53180 frames in 5.0 seconds = 10635.890 FPS
53152 frames in 5.0 seconds = 10630.212 FPS
52981 frames in 5.0 seconds = 10596.134 FPS
X connection to :0.0 broken (explicit kill or server 

I think the VC is working.
I will give Beryl a try.

Thanks,
JT

---

### Post by m.musashi on 2006-10-10
> **Johntam said:**
> Musashi, thanks for the quick help.
glxgears -printfps worked.
This is what I got:
johntam@papa:~$ glxgears -printfps
53187 frames in 5.0 seconds = 10637.341 FPS
.
.
.
X connection to :0.0 broken (explicit kill or server 

I think the VC is working.
I will give Beryl a try.

Thanks,
JT
Damn, those are high numbers. I guess the GT is that much better than the GS. Of course for what I'm doing I doubt I would notice any improvment. What cpu do you have? I suppose that would make a difference too.

Good luck with beryl. Follow the how to closely. I had a few bumps but it's working great now. It's very cool.

---

### Post by Johntam on 2006-10-10
I am running a Opteron 148 stock.

I am sure I will be back for some more hand holding.
This is a 60 year old men trying to learn new trick !

JT

---

### Post by handband2 on 2006-10-10
> **Johntam said:**
> I am looking forward to trying out Beryl on my Dapper64 install.
But I would like to resolve a few possible problems first.

I am using a BFG 7600gt nVidia card.
nVidia Driver installed using Automtix1.

First problem,the Device setion of my xorg.conf file has only 2 lines :
"Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection"
Is it safe to just add the other lines indicated in the HowTo ?

2nd problem, when run "glxgears -info, I get this:
"johntam@papa:~$ glxgears -info

Thanks 
JT

Johntam,

In your "Device" Section you'll need the BusID.  To check it your BusID run:
```
lspci -X
```
You might need the following depending on your card:
```
    Option         "RenderAccel" "true"
```
and
```
    Option         "AllowGLXWithComposite" "true"
```
```
    Option         "TrippleBuffer" "false"
```

Also, when running
```
glxgears -info
```
to get FPS you let it keep running.  I you let the gears run about every 5 seconds you'll notice the FPS's appear in your terminal.

---

### Post by handband2 on 2006-10-10
> **Charles Hand said:**
> OK, I took care of that. Much obliged.

Do you know anything about this weird business with the shutdown and reboot buttons in this thread?
[http://www.ubuntuforums.org/showthread.php?t=244662](http://www.ubuntuforums.org/showthread.php?t=244662)

Charles Hand,

Try this:
[LIST=1]
[*]Right click on **Desktop -> Create Launcher**
[*]Type this for shutdown:
```
Name: Shutdown Computer
Generic Name:  Shutdown
Comment:  Shutdown
Command:  sudo /sbin/shutdown -h 0
Type:  Application
``` 
[*]Type this for restart:
```
Name:  Restart Computer
Generic Name:  Restart
Comment:  Restart
Command:  sudo /sbin/restart
Type:  Application
```
[*]Type this for logout
```
Name:  Logout Computer
Generic Name:  Logout
Comment:  Logout
Command:  /usr/bin/gnome-session-save --kill
Type:  Application
```
[*]Now goto
```
Applications > Desktop Preferences > Advanced > Sessions
``` 
> Uncheck the option box **Prompt on logout**

[*]Login as root user
[*]Type
```
visudo
```
[*]Put at the bottom
```
*username* localhost= NOPASSWD: /sbin/shutdown -h 0
*username* localhost= NOPASSWD: /sbin/reboot
```
> **CTRL+X** to exit. 
Press** Y** to save
[*]Reboot
[/LIST]
Let me know if that works?

---

### Post by wolf202 on 2006-10-11
I followed this guide and now my X server won't boot.  The problem is detailed here

[http://ubuntuforums.org/showthread.php?p=1603684#post1603684](http://ubuntuforums.org/showthread.php?p=1603684#post1603684)

Please Help!!

-wolf

---

### Post by handband2 on 2006-10-11
> **wolf202 said:**
> I followed this guide and now my X server won't boot.  The problem is detailed here

[http://ubuntuforums.org/showthread.php?p=1603684#post1603684](http://ubuntuforums.org/showthread.php?p=1603684#post1603684)

Please Help!!

-wolf

wolf202,

Could you post your **/etc/X11/xorg.conf** file?

---

### Post by lammer on 2006-10-11
> **handband2 said:**
> 
[LIST]
[*]See if your **BusID** is correct in your **xorg.conf** file
```
lspci -X
```[/LIST]



Allready checked, but anyway, here is the output:

```

PCI:0:0:0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
PCI:0:1:0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
PCI:0:12:0 Multimedia audio controller: Creative Labs SB Live! EMU10k1
PCI:0:12:1 Input device controller: Creative Labs SB Live! MIDI/Game Port
PCI:0:16:0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
PCI:0:16:1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
PCI:0:16:2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
PCI:0:16:3 USB Controller: VIA Technologies, Inc. USB 2.0
PCI:0:17:0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
PCI:0:17:1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
PCI:0:18:0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II]
[B]PCI:1:0:0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]
[/B]
```


> **handband2 said:**
> 
[LIST]
[*]Try turning on **RenderAccel** in your **xorg.conf**
```
Option "RenderAccel" "true"
```
[/LIST]


Ok, will try on next logoff...
 
> **handband2 said:**
> 
[LIST]
[*]Make sure you don't have any sessions that could interfere with the start of Beryl/Xgl (Go to **System –> Preferences –> Sessions –> Startup Programs**)
```
xmodmap -e "keycode 22 = BackSpace"
beryl-manager
```
[/LIST]


Hey, maybe that's a point. I have some things round there... Gmail notifier, volume, power managment...
 
> **handband2 said:**
> 
[LIST]
[*]Make sure you place the code in the right places
```
/usr/bin/startxgl.sh
not
/usr/bin/startgnomexgl.sh
```
```
sudo chmod 755 /usr/bin/startxgl.sh
sudo gedit /usr/share/xsessions/xgl.desktop
not
sudo chmod 755 /usr/bin/startgnomexgl.sh
sudo chmod 755 /usr/share/xsessions/gnome-xgl.desktop
```
[/LIST]
[LIST]
[*]chmod only
```
sudo chmod 755 /usr/bin/startxgl.sh
not
sudo chmod 755 /usr/share/xsessions/gnome-xgl.desktop
```
[/LIST]



I will remove all the files, and start all over again with your tips.
 
> **handband2 said:**
> 
Double check my howto and see where you might of made the mistakes from what you did:
[My Howto]("http://ubuntuforums.org/showpost.php?p=1564565&postcount=75")
[What you did]("http://ubuntuforums.org/showpost.php?p=1595854&postcount=278")


Yes sir!!! ;) In case everythig else fails, I will start at the very first step of your guide after removing everything.
 
> **handband2 said:**
> 
EDIT:  I found this as requirements to run XGL:
All NVIDIA cards need the proprietary driver for running Xgl. Currently you will need to uninstall and reinstall the xgl rpm after installing the proprietary NVidia driver.

[LIST]
[*]    GeForce 4xxx series - XVideo is not accelerated on these cards.
[*]    GeForce FX 5xxx series, Quadro FX series - Accelerated XVideo is hitting a slow path on these cards, it is under investigation.
[*]    GeForce 6xxx series
[*]    GeForce 7xxx series
[/LIST]

Another good point to start looking arround. I will try to remove all the beryl packages and install them again.

Let me try, and in a few days I'll post back.

Thanks a lot!! Cheers from Spain! :KS

---

### Post by seuaniu on 2006-10-11
Thanks for the easy howto :) .  I can confirm that this works just fine on my work machine:

Dell somethin-or-other desktop

P4 2.4
512 MB memory
**Intel onboard graphics**

went through the relevant parts of the howto and everything worked without a hitch.  It is a bit, um, sluggish.  Thats probably due to the shared graphics memory and relatively low-powered chipset.

---

### Post by smdeep on 2006-10-11
Hi
Thanks for the great HOWTO, everything works well. I have a Nvidia Fx5200 card and glxinfo says:
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

I was wondering why direct rendering is off? Is it because Xgl does not need it or do I have an improperly configure nvidia driver?

Thanks in advance.

---

### Post by handband2 on 2006-10-11
> **smdeep said:**
> Hi
Thanks for the great HOWTO, everything works well. I have a Nvidia Fx5200 card and glxinfo says:
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2

I was wondering why direct rendering is off? Is it because Xgl does not need it or do I have an improperly configure nvidia driver?

Thanks in advance.

smdeep,

You can turn on direct rendering in your **/etc/X11/xorg.conf** file:
```
Option "RenderAccel" "true"
```

You can find more information here:  [X config Options]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html")

---

### Post by wolf202 on 2006-10-11
My  /etc/X11/xorg.conf file
 
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath     "/usr/share/X11/fonts/misc"
    FontPath     "/usr/share/X11/fonts/cyrillic"
    FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath     "/usr/share/X11/fonts/Type1"
    FontPath     "/usr/share/X11/fonts/100dpi"
    FontPath     "/usr/share/X11/fonts/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "ddc"
    Load  "dri"
    Load  "extmod"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "vbe"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc104"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ExplorerPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/wacom"          # Change to 
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "G701PF"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "ATI Technologies, Inc. Radeon R300 NE [Radeon 9500 Pro]"
    Driver      "ati"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies, Inc. Radeon R300 NE [Radeon 9500 Pro]"
    Monitor    "G701PF"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]"
    Device     "aticonfig-Device[0]"
    Monitor    "aticonfig-Monitor[0]"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection

```

A little more info:

I can get into gnome by typing startx in the command line. When I'm in Beryl runs on startup but it is defaulting to metacity. If I try to change it It will still go back to metacity.

the error that shows before I get the command line is:

```
xf860 OpenSerial: Cannot Open Device /dev/wacom
No Such Directory Found
```

-wolf

---

### Post by techstop on 2006-10-11
Direct rendering is switched off by Beryl, it is explained on the first page here;

[http://ubuntuforums.org/showpost.php?p=1563195&postcount=40](http://ubuntuforums.org/showpost.php?p=1563195&postcount=40)

I think you would be asking for trouble by adding that line to xorg.conf. Mine is disabled and beryl is working perfectly.

---

### Post by handband2 on 2006-10-11
> **wolf202 said:**
> My  /etc/X11/xorg.conf file
 
A little more info:

I can get into gnome by typing startx in the command line. When I'm in Beryl runs on startup but it is defaulting to metacity. If I try to change it It will still go back to metacity.

the error that shows before I get the command line is:

```
xf860 OpenSerial: Cannot Open Device /dev/wacom
No Such Directory Found
```

-wolf

Try running:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then
```
sudo dpkg-reconfigure xserver-xorg
```
Make sure yout select **fglrx **for your video driver and everything else can stay the default.

Let me know if you still have problems...

---

### Post by handband2 on 2006-10-11
> **techstop said:**
> Direct rendering is switched off by Beryl, it is explained on the first page here;

[http://ubuntuforums.org/showpost.php?p=1563195&postcount=40](http://ubuntuforums.org/showpost.php?p=1563195&postcount=40)

I think you would be asking for trouble by adding that line to xorg.conf. Mine is disabled and beryl is working perfectly.

techstop,

Thanks!!!

Here is more info on the subject:
> **Direct rendering does not work when running Xgl, but it does on Xorg. Why are OpenGL applications not accelerated?**
Do not intermix hardware acceleration and direct rendering. OpenGL applications will be hardware accelerated on Xgl if the driver supports pBuffers or FBOs, like the nvidia and fglrx drivers do. Direct rendering on the other hand is impossible to implement at the moment, the necessary extensions for implementing that feature are not even specified yet, let alone being implemented.
Direct rendering implies hardware acceleration, but not the other way round. Direct rendering is a bit faster than indirect rendering, but indirect rendering is not as bad as it sounds.
Direct rendering is active if running glxinfo|grep direct on top of Xorg (not Xgl!) shows you "Yes". On top of Xgl this will always show you "No". Unfortunately, for Xorg having direct rendering is a synonym for having accelerated graphics, and it is more difficult to detect whether hardware accleration is available than it is to detect direct rendering.

Source:  [http://en.opensuse.org/Xgl]("http://en.opensuse.org/Xgl")

---

### Post by GoombaDoolies on 2006-10-11
Hi, me again.  More ATI information, if required.

I had problems with my computer locking up, so the following information might be useful for anyone using ATI that has the same problem.

To stop it locking up, I reverted the driver back from fglrx to ati (I have a Radeon 9550 with 256mb ram).  Since i had issues with even getting a Gnome session to run for more than a minute without locking up, I booted the computer as a safe recovery mode.

At the prompt (yes I figured out how to use the little black screen) I typed:
```
 sudo nano /etc/X11/xorg.conf 
```

went down to the server section and changed the "driver" from "fglrx" back to "ati".  Exited and saved.

Restarted from the command prompt with:

```
 shutdown -r now 
```

loaded Ubuntu normally and at the login screen, clicked the sessions button in the bottom left corner and started a Gnome session.  it asks me whether to make it default, I did yes.

I then went to the settings menu, administration, sessions and removed beryl manager from it.  

Interestingly the diamond still appears if you don't load a normal gnome session but a souped up session and the effects (except the cube) worth with emerald.  

I will research that and come back with an answer (when my kids are well and I have the time - sorry).  I'm figuring that if it was the driver causing my system to go pear-shaped and not beryl (haven't confirmed this), then it seems I might be able to use my standard ATI driver to run it without fglrx.  Like I said, I will eventually try it out and get back to you all on it.  Hoping this "how to undo" works.  It has for me, I now have a system back up and running (burning and backup up in my case).

Kind regards to all.

---

### Post by Aberrix on 2006-10-11
This worked perfect for me! no hassle or problems at all!

Thanks for the awesome write-up!

---

### Post by lammer on 2006-10-12
Here I go again (as Whitesnake said)...

As all the stuff that I have tried failed (even [this tips]("http://www.ubuntuforums.org/showthread.php?p=1604847#post16048")), I think that the best thing to do is start all over again.

On this post I'm going to describe the uninstallation process, I think that's correct, but I write this in case I'm missing something.

[LIST]
[*]First, I have remove all the sessions I have write up before: /usr/bin/startgnomexgl.sh, /usr/bin/startxgl.sh, /usr/share/xsessions/gnome-xgl.desktop and /usr/share/xsessions/xgl.desktop
[*]Then, empty all the startup programs, at System –> Preferences –> Sessions –> Startup Programs (not just beryl, but all)
[*]Then, uninstall the NVIDIA driver:
```

uname -r
*2.6.15-27-k7*
sudo apt-get --purge remove nvidia-glx-legacy nvidia-xconfig nvidia-settings linux-restricted-modules-2.6.15-27-k7 linux-restricted-modules-common

```
```

sudo /etc/init.d/gdm stop **(from Ctrl+Alt+F1)**
sh NVIDIA-Linux-x86-1.0-8756-pkg1.run --extract-only
cd NVIDIA-Linux-x86-1.0-7184-pkg1/
sudo ./nvidia-installer --uninstall
sudo rm /etc/init.d/nvidia-*
sudo dpkg-reconfigure xserver-xorg **(note)**
sudo /etc/init.d/gdm restart

```
**(note)**: I have some problems with my spanish keyboard, so I have restore an old backup of my xorg.conf with the opensource 'nv' driver. This is the content:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"BenQ T90X"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"BenQ T90X"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

```

[*]I finished with a restart to make sure that everything is working as expected.
[/LIST]

Also there is my gdm.conf-custom file right now:

```
[daemon]

[security]

[xdmcp]

[gui]

[greeter]
SoundOnLoginSuccessFile=/usr/share/sounds/startup.wav
DefaultWelcome=false

[chooser]

[debug]

[servers]
```

I think that now I have all my system "clean", so in a few hours I'm going to start all the process again, and write up on the forum. Hope that all this effort can fix the problems, anyway, I'm learning so much things :)

---

### Post by handband2 on 2006-10-12
> **lammer said:**
> Here I go again (as Whitesnake said)...

[*]Then, empty all the startup programs, at System –> Preferences –> Sessions –> Startup Programs (not just beryl, but all)

**(note)**: I have some problems with my spanish keyboard, so I have restore an old backup of my xorg.conf with the opensource 'nv' driver. This is the content:

I think that now I have all my system "clean", so in a few hours I'm going to start all the process again, and write up on the forum. Hope that all this effort can fix the problems, anyway, I'm learning so much things :)

lammer,

Remember that ***All NVIDIA cards need the proprietary driver for running Xgl!!***

I'm glad you are learning a lot.  

We all get educated when people share :)

---

### Post by whein on 2006-10-12
Ok, so I'm all a tingle to try out beryl since the little bit of compiz I got working a few weeks back was sweet.  I started following this tutorial, and got stuck when it got to the bit about installing emerald and beryl using apt-get.  I'm using Synaptic as a front end, and I've edited my sources.list to include everything under the sun including repositories mentioned in this post, and those at [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/).  After reloading the Synaptic package lists with the new repositories, I cannot find any packages for either emerald or beryl.  I found one for emerald-themes and another related to beryl, but not the two themselves.  Manually perusing the repositories I find that no one appears to have a deb compiled for amd64 for Dapper.  One or two for Edgy and a bunch for i386.  But I'm running an amd64-k8 version of the 2.6.15 kernel on an Athlon 64 X2 4400+.  Does anyone have a deb for this configuration? 
-Will

---

### Post by maxdy on 2006-10-12
i just recently done up my own XGL/Beryl setup.

it's cool! and sexy! :D

but the problem with shift + backspace key combo is still there. i did everything that tutorial has said and read through everything that's in this thread.

someone help pls. this is getting annoying.

---

### Post by beerorkid on 2006-10-12
> **maxdy said:**
> i just recently done up my own XGL/Beryl setup.

it's cool! and sexy! :D

but the problem with shift + backspace key combo is still there. i did everything that tutorial has said and read through everything that's in this thread.

someone help pls. this is getting annoying.

maybe this will help?
[http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz](http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz)

---

### Post by maxdy on 2006-10-12
> **beerorkid said:**
> maybe this will help?
[http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz](http://forum.beryl-project.org/topic-1199-solved-shift-backspace-crashes-compiz)
that's for compiz.

since we are using beryl, there's no more compiz startup script.


even by using this code:
```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

which i presume was to be added to the sessions -> startup programs, it still doesn't work.

---

### Post by handband2 on 2006-10-12
> **whein said:**
> Ok, so I'm all a tingle to try out beryl since the little bit of compiz I got working a few weeks back was sweet.  I started following this tutorial, and got stuck when it got to the bit about installing emerald and beryl using apt-get.  I'm using Synaptic as a front end, and I've edited my sources.list to include everything under the sun including repositories mentioned in this post, and those at [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/).  After reloading the Synaptic package lists with the new repositories, I cannot find any packages for either emerald or beryl.  I found one for emerald-themes and another related to beryl, but not the two themselves.  Manually perusing the repositories I find that no one appears to have a deb compiled for amd64 for Dapper.  One or two for Edgy and a bunch for i386.  But I'm running an amd64-k8 version of the 2.6.15 kernel on an Athlon 64 X2 4400+.  Does anyone have a deb for this configuration? 
-Will

whein,

Make sure you have ***multiverse universe*** repositories turned on.

Note the different repositories for 64 bit:
```
sudo gedit /etc/apt/sources.list
```
Copy and paste these at the bottom in your ***/etc/apt/sources.list***:
```
deb http://www.beerorkid.com/compiz dapper main main-amd64
deb http://media.blutkind.org/xgl/ dapper main main-amd64
deb http://xgl.compiz.info/ dapper main main-amd64
```

Now add the key to the corrisponding repository (Copy and Paste in your Terminal):
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
wget http://media.blutkind.org/xgl/quinn.key.asc -O - | sudo apt-key add -

```

More info here:
[http://www.beerorkid.com/compiz/]("http://www.beerorkid.com/compiz/")
or
[http://media.blutkind.org/xgl/]("http://media.blutkind.org/xgl/")

If you installed ***Compiz*** in the past, run the following in the Terminal (Copy and Paste):
```
sudo apt-get remove compiz compiz-gnome cgwd cgwd-themes xserver-xgl csm
```

Now run the howto on this thread:
[http://www.ubuntuforums.org/showthread.php?t=268036]("http://www.ubuntuforums.org/showthread.php?t=268036")

---

### Post by maxdy on 2006-10-12
i found my own solution to the shift + backspace problem :D

found it over at beryl-project's forum


here's the solution i quoted over from beryl-projects forums:


> 
Keep in mind you must replace "USERNAME" with your own username.

1. Enter this in the console:

sudo gedit /home/USERNAME/berylscript.sh

2. Paste this inside the new text file:

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

Save and close the text file.

3. Enter the following command in console:

sudo chmod 755 /home/USERNAME/berylscript.sh

4. Now go to System -> Preferences -> Sessions -> Startup Programs and then add this:

/home/USERNAME/berylscript.sh

Step #1 created a new text file for our script. Step #2 was the code to eliminate that annoying shift +backspace bug. Step #3 made our script executable. Step #4 made our script start up automatically when logging in.

I'm sure a more efficient way of doing this will be made available to us soon, so in the meantime you can do this. When the better way of doing this is found, you can uninstall this script:

To uninstall this script, navigate to your home folder (Places -> Home Folder) and delete "berylscript.sh". Then, go to System -> Preferences -> Sessions -> Startup Programs and delete the "/home/USERNAME/berylscript.sh".


Now, time for the fix for Super Key not working! This one is really easy.

Go to:

System > Preferences > Keyboard > Layout Options > Alt/Win Key behavior

and select "Super is mapped to the Win-keys(default)."


---

### Post by whein on 2006-10-12
handband2,

I have all of the repositories that come in the default install of Ubuntu 6.06.1 uncommented in the sources.list file, which should include the multiverse and universe repositories if I recall correctly.  I have added all the repositories you listed as well.

That said, by poking around the following repository URLs I have been unable to find any .deb files for amd64 architecture for emerald and beryl that are not marked as Edgy.  I'm still a noob so I'm not sure what will happen if I install Edgy packages into a Dapper system, but I'd rather do things by the book if I can.

So I'm back to my original question of where (if at all) can I find a .deb package for amd64 architecture for Dapper for emerald and beryl?
-Will  

[http://www.beerorkid.com/compiz/pool/main/](http://www.beerorkid.com/compiz/pool/main/)
[http://www.beerorkid.com/compiz/pool/main-amd64/](http://www.beerorkid.com/compiz/pool/main-amd64/)
[http://media.blutkind.org/xgl/pool/main/](http://media.blutkind.org/xgl/pool/main/)
[http://media.blutkind.org/xgl/pool/main-amd64/](http://media.blutkind.org/xgl/pool/main-amd64/)
[http://xgl.compiz.info/pool/main/](http://xgl.compiz.info/pool/main/)
[http://xgl.compiz.info/pool/main-amd64/](http://xgl.compiz.info/pool/main-amd64/)
[http://packages.ubuntu.com/dapper/allpackages/](http://packages.ubuntu.com/dapper/allpackages/)

---

### Post by beerorkid on 2006-10-12
> **whein said:**
> handband2,

I have all of the repositories that come in the default install of Ubuntu 6.06.1 uncommented in the sources.list file, which should include the multiverse and universe repositories if I recall correctly.  I have added all the repositories you listed as well.

That said, by poking around the following repository URLs I have been unable to find any .deb files for amd64 architecture for emerald and beryl that are not marked as Edgy.  I'm still a noob so I'm not sure what will happen if I install Edgy packages into a Dapper system, but I'd rather do things by the book if I can.

So I'm back to my original question of where (if at all) can I find a .deb package for amd64 architecture for Dapper for emerald and beryl?
-Will  

[http://www.beerorkid.com/compiz/pool/main/](http://www.beerorkid.com/compiz/pool/main/)
[http://www.beerorkid.com/compiz/pool/main-amd64/](http://www.beerorkid.com/compiz/pool/main-amd64/)
[http://media.blutkind.org/xgl/pool/main/](http://media.blutkind.org/xgl/pool/main/)
[http://media.blutkind.org/xgl/pool/main-amd64/](http://media.blutkind.org/xgl/pool/main-amd64/)
[http://xgl.compiz.info/pool/main/](http://xgl.compiz.info/pool/main/)
[http://xgl.compiz.info/pool/main-amd64/](http://xgl.compiz.info/pool/main-amd64/)
[http://packages.ubuntu.com/dapper/allpackages/](http://packages.ubuntu.com/dapper/allpackages/)

try adding this to your sources.list
```
deb http://www.amd64.aceracerftw.com/ edgy main-edgy
```

---

### Post by whein on 2006-10-12
> **beerorkid said:**
> try adding this to your sources.list
```
deb http://www.amd64.aceracerftw.com/ edgy main-edgy
```

Hmm, this might just be what I need.  However, you list the Edgy repositories and I'm looking for Dapper.  Any way to verify that the stuff under the [http://www.amd64.aceracerftw.com/pool/main/](http://www.amd64.aceracerftw.com/pool/main/) directory is in fact Dapper friendly?  If so I should be able to put
```
deb http://www.amd64.aceracerftw.com/ dapper main
```
in my sources.list?
-Will

---

### Post by lammer on 2006-10-12
> **handband2 said:**
> lammer,

Remember that ***All NVIDIA cards need the proprietary driver for running Xgl!!***

I'm glad you are learning a lot.  

We all get educated when people share :)

Sure!! The only thing that I tried to do is leave my system as clean as possible to start installing beryl again.

I'm going to start [all the steps]("http://www.ubuntuforums.org/showthread.php?t=268036") right now, with the configuration I have posted a few minutes ago. Wish me luck!

Oh! Of course that I will share my experience, even it's a bad one :(

---

### Post by beerorkid on 2006-10-12
> **whein said:**
> Hmm, this might just be what I need.  However, you list the Edgy repositories and I'm looking for Dapper.  Any way to verify that the stuff under the [http://www.amd64.aceracerftw.com/pool/main/](http://www.amd64.aceracerftw.com/pool/main/) directory is in fact Dapper friendly?  If so I should be able to put
```
deb http://www.amd64.aceracerftw.com/ dapper main
```
in my sources.list?
-Will

well it looks like it had both dists in the repo, but I do not know if they are dapper friendly.  i just found that repo in the beryl forums a while back.

Guessin you can try and always remove them.

I have a amd 64 but just run 32.  Also Quinn does not have a 64bit machine so others compile them for her.  Srry I do not have much more info.

---

### Post by smdeep on 2006-10-12
> **handband2 said:**
> smdeep,

You can turn on direct rendering in your **/etc/X11/xorg.conf** file:
```
Option "RenderAccel" "true"
```

You can find more information here:  [X config Options]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html")

Hi

I do have that option turned on. It seems I read somewhere that Xgl turns it off? Not sure but I think I read about it somewhere. I am trying to get Beryl to work in Mepis but to now avail. I get a blank white screen and strangely the desktop cube rotates!

Thanks for your attention.
Sudeep

---

### Post by handband2 on 2006-10-12
> **smdeep said:**
> Hi

I do have that option turned on. It seems I read somewhere that Xgl turns it off? Not sure but I think I read about it somewhere. I am trying to get Beryl to work in Mepis but to now avail. I get a blank white screen and strangely the desktop cube rotates!

Thanks for your attention.
Sudeep

smdeep,

Check one of my earlier posts.  It might fix your problem:
[http://ubuntuforums.org/showpost.php?p=1600594&postcount=306]("http://ubuntuforums.org/showpost.php?p=1600594&postcount=306")

---

### Post by lammer on 2006-10-12
I think that it will be a good thing to try make the things work following some steps [from here]("http://www.ubuntuforums.org/showthread.php?p=1591756#post1591756"), and [from here]("http://albertomilone.com/latest_nvidia_udsf.html"), rather than try to download the Nvidia drivers with apt-get

This is a step by step guide of what I've done to try to make beryl work on a Nvidia TNT2 64:

[LIST]
[*] First thing is to check my kernel version:
```

uname -r
*2.6.15-27-k7*

```

[*] Now it's time to download the Nvidia Legacy driver from here [http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html) and extract the file:
```

sh NVIDIA-Linux-x86-1.0-7184-pkg1.run --extract-only

```

[*] Install gcc,xserver and linux-headers for my kernel:

```

sudo aptitude install linux-headers-2.6.15-27-k7 build-essential gcc gcc-3.4 xserver-xorg-dev
sudo rm /etc/init.d/nvidia-*

```

[*] Logoff and go to a terminal window (Ctrl+Alt+F1), then shut down gdm:
```

sudo /etc/init.d/gdm stop

```

[*]Now, I have go to the previous extracted folder and run the installer with this options:
```

cd NVIDIA-Linux-x86-1.0-7184-pkg1
sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-2.6.15-27-k7

```

[*] Install and run the nvidia-xconfig:
```

sudo aptitude install nvidia-xconfig
sudo nvidia-xconfig

```

[*]Start X again:
```

sudo /etc/init.d/gdm start

```

[*] Time to edit xorg.conf:
```

sudo gedit /etc/X11/xorg.conf

```
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    **Load           "glx"**
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "es"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "BenQ T90X"
    Option         "DPMS"
EndSection

Section "Device"
   	Identifier     "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	[B]Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true"
	Option 		"TripleBuffer" 		"false"[/B]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Monitor        "BenQ T90X"
    **DefaultDepth    24**
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

Section "Extensions"
         ** Option  "Composite" "Enable"**
EndSection

```

[*]Added this to /etc/apt/sources.list:
```

deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

```
[*]```
sudo aptitude update
```

[*] Time to install Beryl and XGL:
```

sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes

```

[/LIST]

Hey! Here comes the bad news! I cannot install all of them, because they are allready installed. I just tried to apt-get reinstall, but I'm not pretty sure that this is the best way...

Maybe that's the point? I have tried to follow the last steps, and beryl is not working but with metacity, the same problem as before. So I'm guess if the problem is with this files, that need to be reinstalled, but I don't know how...

I think that I can write up the last steps I have followed:

[LIST]
[*] change gdm.conf-custom (I think it's easier than make a session):
```

sudo gedit /etc/gdm/gdm.conf-custom

```

At the very end of the file:

```

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

[*] Go to System –> Preferences –> Sessions –> Startup Programs
```

xmodmap -e "keycode 22 = BackSpace"
beryl-manager

```

[/LIST]

---

### Post by lammer on 2006-10-12
> **lammer said:**
> 
Hey! Here comes the bad news! I cannot install all of them, because they are allready installed. I just tried to apt-get reinstall, but I'm not pretty sure that this is the best way...

Maybe that's the point? I have tried to follow the last steps, and beryl is not working but with metacity, the same problem as before. So I'm guess if the problem is with this files, that need to be reinstalled, but I don't know how...


It was not that files :( I found a way to reinstall all of them: 
```
sudo aptitude reinstall xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

But most of the times I run beryl-manager on the startup, the X server crashes. And if I try to make it work from command line, it brings me the same error as [the first time]("http://www.ubuntuforums.org/showthread.php?p=1595854#post159585") 

In case it's important, my X server does extrange things when I wrote this lines on the gdm.conf-custom and log again:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

I'm not sure that this is normal until you run beryl-manager. But in my case the screen seems to be misconfigurated, as long as blinks, the cursor sometimes have a trail, and it comes unestable.

---

### Post by handband2 on 2006-10-12
> **lammer said:**
> 
Time to install Beryl and XGL:
```

sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes

```

Hey! Here comes the bad news! I cannot install all of them, because they are allready installed. I just tried to apt-get reinstall, but I'm not pretty sure that this is the best way...



lammer,

Thanks for your descriptive install.  It will come in handy for many others :)

When re-installing XGL/Beryl did you try uninstalling everything?
```
sudo apt-get --purge remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

Just to check again...
What was your **glxgears -info** or **glxgears -printfps** output?

---

### Post by lammer on 2006-10-12
> **handband2 said:**
> lammer,

Thanks for your descriptive install.  It will come in handy for many others :)


That was my intention ;)

> **handband2 said:**
> 
When re-installing XGL/Beryl did you try uninstalling everything?
```
sudo apt-get --purge remove xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```


Yes and no. I have tried, but when I try to do that it says me that it needs to remove all this programs:
```
 amarok* amarok-xine* amule* audacity* beryl* beryl-core* beryl-manager*
  beryl-plugins* beryl-settings* bum* democracyplayer* deskbar-applet*
  emerald* emerald-themes* fast-user-switch-applet* freeglut3* gdebi* gdm*
  gksu* gnome-app-install* gnome-netstatus-applet* gnome-system-monitor*
  gnome-volume-manager* gstreamer0.10-gl* hal-device-manager* hwdb-client*
  libgksu1.2-1* libgksuui1.0-1* libgl1-mesa* libgl1-mesa-dri* libglew1*
  libglitz-glx1* libglu1-mesa* libwxgtk2.4-1* libwxgtk2.6-0*
  libxine-extracodecs* libxine-main1* mesa-utils* mozilla-mplayer* mplayer*
  mplayer-386* mplayer-fonts* python-gnome2-extras* python2.4-gnome2-extras*
  rss-glx* sbackup* serpentine* totem* totem-xine* ubuntu-desktop*
  update-notifier* vlc* vlc-plugin-alsa* vlc-plugin-arts* vlc-plugin-esd*
  wine* wxvlc* x-window-system-core* xbase-clients* xdriinfo* xscreensaver-gl*
  xserver-xgl* xserver-xorg*

```

I don't want to remove all that files. How can I do that without need to remove all those programs? For example, there is mplayer, amarok, democracy player... I want to keep this files installed.

If I try to remove them with aptitude it says that I need to remove even more files, or just get with my old files:
```
No se satisfacen las dependencias de los siguientes paquetes:
  beryl-core: Depende: libgl1-mesa pero no es instalable o
                       libgl1-mesa-glx que es un paquete virtual.
  mesa-utils: Depende: libgl1-mesa pero no es instalable o
                       libgl1 que es un paquete virtual.
  libglew1: Depende: libgl1-mesa pero no es instalable o
                     libgl1 que es un paquete virtual.
  x-window-system-core: Depende: xserver-xorg pero no es instalable
                        Depende: libgl1-mesa pero no es instalable
  libwxgtk2.4-1: Depende: libgl1-mesa pero no es instalable o
                          libgl1 que es un paquete virtual.
  xscreensaver-gl: Depende: libgl1-mesa pero no es instalable o
                            libgl1 que es un paquete virtual.
  libwxgtk2.6-0: Depende: libgl1-mesa pero no es instalable o
                          libgl1 que es un paquete virtual.
  libglu1-mesa: Depende: libgl1-mesa pero no es instalable o
                         libgl1 que es un paquete virtual.
  mplayer: Depende: libgl1-mesa pero no es instalable o
                    libgl1 que es un paquete virtual.
  ubuntu-desktop: Depende: libgl1-mesa pero no es instalable
  xdriinfo: Depende: libgl1-mesa pero no es instalable o
                     libgl1 que es un paquete virtual.
  beryl-manager: Depende: emerald pero no es instalable
  libxine-main1: Depende: libgl1-mesa pero no es instalable o
                          libgl1 que es un paquete virtual.
  amarok: Depende: libgl1-mesa pero no es instalable o
                   libgl1 que es un paquete virtual.
  wine: Depende: libgl1-mesa pero no es instalable o
                 libgl1 que es un paquete virtual.
  vlc: Depende: libgl1-mesa pero no es instalable o
                libgl1 que es un paquete virtual.
  gstreamer0.10-gl: Depende: libgl1-mesa pero no es instalable o
                             libgl1 que es un paquete virtual.
  libgl1-mesa-dri: Depende: libgl1-mesa (= 6.5.1+cvs20060824) pero no es instalable
  rss-glx: Depende: libgl1-mesa pero no es instalable o
                    libgl1 que es un paquete virtual.
  freeglut3: Depende: libgl1-mesa pero no es instalable o
                      libgl1 que es un paquete virtual.

```

That's why I have choose to **reinstall**, not to **purge** with aptitude.

> **handband2 said:**
> 
Just to check again...
What was your **glxgears -info** or **glxgears -printfps** output?

glxgears -info:
```
GL_RENDERER   = RIVA TNT2/AGP/3DNOW!
GL_VERSION    = 1.4 (1.5.3 NVIDIA 71.84)
GL_VENDOR     = NVIDIA Corporation

```

glxgears -printfps:
```
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info

```

Maybe this is not the last version on glxgears?

I have notice that it seems that the gears now "jump" a little bit, I mean, that they're not as fluid as other times, but maybe it's because I have restarted X and GDM so much times. I will check again that in the next reboot.

Thanks for all your help!!!

---

### Post by lammer on 2006-10-12
> **lammer said:**
> 
Maybe this is not the last version on glxgears?

I have notice that it seems that the gears now "jump" a little bit, I mean, that they're not as fluid as other times, but maybe it's because I have restarted X and GDM so much times. I will check again that in the next reboot.


Fixed, as I wonder, the gears are now at full speed:

```
692 frames in 5.1 seconds = 135.622 FPS
753 frames in 6.2 seconds = 121.396 FPS
619 frames in 6.1 seconds = 101.648 FPS
502 frames in 5.7 seconds = 88.330 FPS
502 frames in 10.0 seconds = 50.343 FPS
879 frames in 6.4 seconds = 138.076 FPS
251 frames in 9.5 seconds = 26.372 FPS
376 frames in 7.0 seconds = 53.468 FPS
628 frames in 5.9 seconds = 106.562 FPS

```

The low rates are just while I was opening Firefox.

Any idea of what to do next? Im kind of ](*,)

---

### Post by lammer on 2006-10-12
Sorry for the triple posting, but I think I'm on the right way!!!

I have done this:

```
sudo apt-get --purge remove xserver-xgl xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

Notice that I have not include libgl1-mesa, and everything was removed, without any waring or any other package needed to be removed.

Then, I have reinstall all the packages with aptitude:

```
sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

Now, when I log in (before updating  /etc/gdm/gdm.conf-custom) the screen doesn't make "extrange things" and is almost stable. 

The problem gets only when I run beryl-manager, and select the beryl window manager, not the metacity one...

I'm going to try different configurations on the xorg.conf or even make a gnome session just to try...

I will pos back the results!

:eek:

---

### Post by handband2 on 2006-10-12
> **lammer said:**
> Sorry for the triple posting, but I think I'm on the right way!!!

I have done this:

```
sudo apt-get --purge remove xserver-xgl xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

Notice that I have not include libgl1-mesa, and everything was removed, without any waring or any other package needed to be removed.

Then, I have reinstall all the packages with aptitude:

```
sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

Now, when I log in (before updating  /etc/gdm/gdm.conf-custom) the screen doesn't make "extrange things" and is almost stable. 

The problem gets only when I run beryl-manager, and select the beryl window manager, not the metacity one...

I'm going to try different configurations on the xorg.conf or even make a gnome session just to try...

I will pos back the results!

:eek:


lammer,

It will be interesting if you do get it running on a TNT2 card because XGL is a HOG in resources.  Here are a couple of sites to see the requirements:
[LIST]
[*][http://en.opensuse.org/Xgl#Hardware_Advisory]("http://en.opensuse.org/Xgl#Hardware_Advisory")
[*][http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL")
[*][http://www.freesoftwaremagazine.com/node/1757]("http://www.freesoftwaremagazine.com/node/1757")
[/LIST]

---

### Post by lammer on 2006-10-12
Sure, but I'm kind of exausted :(

I have tried to remove ALL the programs than **apt-get** said to me, including amarok, amule, vlc, totem...

After that, I have tried with sudo **aptitude dist-upgrade** to check lost packages. Nothing new.

But I see some light at the end of the tunnel, when I discovered **sudo aptitude**. On the front-end I have checked "upgrade" and then it has show me some more packages that needed to me removed, in order to get the dependecies right. I have checked all, fixed all the packages, and 1 hour later, I have my system clean as a hospital room.

Buuuuut... I have tried to install again all the packages: 
```
sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

And enter to my XGL session (following [your guide]("http://ubuntuforums.org/showpost.php?p=1564565&postcount=75")), try to run beryl-manager, and the f"·$%& same server crash.

I'm tired, maybe this weekend I will be more fresh. But now, I almost think that this is kind of impossible to run this kind of card with Beryl.

Maybe a good point could be posting the log of the error on the beryl forums... But this will be this weekend, for me the day is over. Thanks for all your help handband2

[-o<

---

### Post by Charles Hand on 2006-10-12
> **m.musashi said:**
> Damn, those are high numbers. I guess the GT is that much better than the GS. Of course for what I'm doing I doubt I would notice any improvment. What cpu do you have? I suppose that would make a difference too.


I'm getting fps over 10,000 with Geforce GO7600 and T2500 (intel core duo). What suprised me, though, is that the fps stays the same as I rotate the cube. Distributed processing at its finest! Welcome to the 21st century, eh?

---

### Post by m.musashi on 2006-10-13
> **Charles Hand said:**
> I'm getting fps over 10,000 with Geforce GO7600 and T2500 (intel core duo). What suprised me, though, is that the fps stays the same as I rotate the cube. Distributed processing at its finest! Welcome to the 21st century, eh?

That is cool. I have got to get a core 2 but I have a athlon now and will need new mobo and memory too - not fair. However, the other guy was using an Opteron. I think that is a single core and he still had high numbers - although he didn't say what happened as he rotated the cube. I don't really have a good grasp of video cards but I suspect that most of the process for beryl takes place on the card.

What is a GO7600? I'm only familiar with the 7600GS and GT.

---

### Post by Johntam on 2006-10-13
Finally worked my way down the HowTo to installing Beryl.

Please take a look at my Sources.list, something may be wrong with it,
I am not able to get Beryl completly installed.

When I run "sudo apt-get update", I get :
"johntam@papa:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:2 [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:3 [http://media.blutkind.org](http://media.blutkind.org) dapper Release.gpg [189B]
Get:4 [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release.gpg [189B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper Release
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://media.blutkind.org](http://media.blutkind.org) dapper/main-amd64 Packages
Ign [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main-amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main-amd64 Packages
Hit [http://media.blutkind.org](http://media.blutkind.org) dapper/main-amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Hit [http://xgl.compiz.info](http://xgl.compiz.info) dapper/main-amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hit [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main-amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 618B in 1s (548B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Pac kages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_bin ary-amd64_Packages)

When I run "sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes", I get :
"Reading package lists... Done
Building dependency tree... Done
xserver-xgl is already the newest version.
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
libglitz-glx1 is already the newest version.
E: Couldn't find package beryl"

Or

"Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "beryl".  However, the following
packages contain "beryl" in their name:
  beryl-plugins-data
No candidate version found for emerald
The following packages are BROKEN:
  emerald-themes
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1292kB of archives. After unpacking 3207kB will be used.
The following packages have unmet dependencies:
  emerald-themes: Depends: emerald (>= 0.1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

Either way, Beryl did not get installed.

And here is my sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
# xgl and beryle
# deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
# deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main main-amd64
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main main-amd64
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main main-amd64

Thanks
JT

---

### Post by handband2 on 2006-10-13
> **Johntam said:**
> Finally worked my way down the HowTo to installing Beryl.

Please take a look at my Sources.list, something may be wrong with it,
I am not able to get Beryl completly installed.

Thanks
JT

Johntam,

If you are trying to install Beryl on a AMD64 you might want to change your sources.list like so:
```
#xgl and beryle
#deb http://www.beerorkid.com/compiz dapper main aiglx
#deb http://media.blutkind.org/xgl/ dapper main aiglx
#deb http://www.beerorkid.com/compiz dapper main main-amd64
#deb http://media.blutkind.org/xgl/ dapper main main-amd64
#deb http://xgl.compiz.info/ dapper main main-amd64
deb http://www.amd64.aceracerftw.com/ dapper main
```
Source:  [http://ubuntuforums.org/showpost.php?p=1609098&postcount=344]("http://ubuntuforums.org/showpost.php?p=1609098&postcount=344")

---

### Post by Charles Hand on 2006-10-13
> **m.musashi said:**
> What is a GO7600? I'm only familiar with the 7600GS and GT.

Excuse me. GeForce Go 7600 GT.

---

### Post by m.musashi on 2006-10-13
> **Charles Hand said:**
> Excuse me. GeForce Go 7600 GT.

Ah, this is a notebook gpu. I didn't know they had that. My notebook has a quadro something and I don't think it's as nice as the 7600 you have. My numbers are no where near 10,000. Shucks.

---

### Post by handband2 on 2006-10-13
Here is a good source for Howto's and FAQ's:
[http://wiki.beryl-project.org/index.php/Main_Page]("http://wiki.beryl-project.org/index.php/Main_Page")

---

### Post by Johntam on 2006-10-13
Handband2, thanks for the pointer.

I am still unable to get Beryl installed.

If I use :
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main main-amd64
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main main-amd64
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main main-amd64
I get:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "beryl".  However, the following
packages contain "beryl" in their name:
  beryl-plugins-data
The following packages are BROKEN:
  emerald-themes
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1292kB of archives. After unpacking 3207kB will be used.
The following packages have unmet dependencies:
  emerald-themes: Depends: emerald (>= 0.1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

If I use: 
deb [http://www.amd64.aceracerftw.com/](http://www.amd64.aceracerftw.com/) dapper main
I get:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "beryl"
Couldn't find any package whose name or description matched "emerald-themes"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Both are way over my head.
Please help!!!

Thanks
JT

---

### Post by raintheory on 2006-10-13
Thanks for this!  

Got it working just fine on my Toshiba Satellite P15 S420, nVIDIA GeForce FXgo 5100...

I previously had XGL/Compiz running so this was quite an easy transition.  

One question though...   Is there a way that I can add an entry for the older Compiz as the fall-back window manager?

---

### Post by handband2 on 2006-10-14
> **Johntam said:**
> Handband2, thanks for the pointer.

I am still unable to get Beryl installed.

If I use :
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main main-amd64
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main main-amd64
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main main-amd64
I get:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "beryl".  However, the following
packages contain "beryl" in their name:
  beryl-plugins-data
The following packages are BROKEN:
  emerald-themes
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1292kB of archives. After unpacking 3207kB will be used.
The following packages have unmet dependencies:
  emerald-themes: Depends: emerald (>= 0.1) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

If I use: 
deb [http://www.amd64.aceracerftw.com/](http://www.amd64.aceracerftw.com/) dapper main
I get:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "beryl"
Couldn't find any package whose name or description matched "emerald-themes"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Both are way over my head.
Please help!!!

Thanks
JT

Johntam,

I know this doesn't help much but it seems most of the 64bit work for Beryl is being done for Edgy 6.10.  If you plan on upgrading here is one of the repos:
```
deb http://compiz-mirror.lupine.me.uk/ edgy main-edgy main-edgy-amd64
```

---

### Post by raintheory on 2006-10-15
I want to experiment with different settings within the beryl-manager, but also be able to eaily revert to my current setup...

Short of writing all of my changes down, is there an easy way to back up the config data?

---

### Post by Tombius on 2006-10-15
Hi there, i took the instructions from page #1, i did all the installation, but this thing never work, something got real wrong the first time, on startup, a screen appears and tells me that the X server failed, then prompts me to login in the command line, so i repeated all the instructions using command line, after all instructions, i try and reboot the system, then again the same failure shows, there i am again in the command line, i can log into my session, and when i am in i type X in the command line, then an Nvidia splash screen blinks for half second, and then i get a grey screen, and my mouse moves but has a bold X shape, no response from keyboard (at least no response visible), only visible things are the gray pattern in the screen and the mouse moving around, i am new in this, but i am not afraid of trying any solution, i know there should be a way to restore things to its previous state, it is just a display issue. I am sure that you can help me and give me some expert advice, i had to start a session in windows XP to post this thread, but with your help, the next post will be a thank you reply, from the fixed System. :D

---

### Post by m.musashi on 2006-10-15
> **Tombius said:**
> Hi there, i took the instructions from page #1, i did all the installation, but this thing never work, something got real wrong the first time, on startup, a screen appears and tells me that the X server failed, then prompts me to login in the command line, so i repeated all the instructions using command line, after all instructions, i try and reboot the system, then again the same failure shows, there i am again in the command line, i can log into my session, and when i am in i type X in the command line, then an Nvidia splash screen blinks for half second, and then i get a grey screen, and my mouse moves but has a bold X shape, no response from keyboard (at least no response visible), only visible things are the gray pattern in the screen and the mouse moving around, i am new in this, but i am not afraid of trying any solution, i know there should be a way to restore things to its previous state, it is just a display issue. I am sure that you can help me and give me some expert advice, i had to start a session in windows XP to post this thread, but with your help, the next post will be a thank you reply, from the fixed System. :D
I ran in to similar problems. You can open and edit the xorg.conf file from the command line using ```
sudo vi /etc/X11/xorg.conf or
sudo nano /etc/X11/xorg.conf
``` From there, just undo the changes. You might also need to undo the changes in /etc/gdm/gdm.conf-custom. Just comment them out with # and reboot. If everything is fine then it is just a matter of finding and fixing the offending lines in the config files or possibly making some changes to fit your hardware. If you can get logged in after fixing the files, post the contents of the xorg.conf. Someone will probably be able to spot the problem.

EDIT: one more thing. You might look back through the last week or so of this thread. I know that myself and few others had similar problems. There were some solutions offered that might also help you. My problem was that color depth was set to 16 and not 24. If you post your xorg.conf file others will be able to look it over and see what might be the problem.

---

### Post by Tombius on 2006-10-15
many Thanks, at the time you wrote me your kind suggestion i was struggling with the reconfiguration of the system i am kind of proud that i got access to the graphical mode, i am writong in Dapper with the plain desktop, i spot some issues that are not covered in the How to,

1) after editing the sources.list (i had to do it in nano, and of course learning how to use it on the march)i add the codes deb http beerorkiddapper main 
and the http media blutkind, but then when prompted to 

sudo apt -get update it showed an error or warning message stating that there was NO PUBKEY i paid no attention to that and instead head to the next task

("darn i realized that the use of $sudo dpkg-reconfigure xserver-xorg changed also my keyboard")

ok done:
After:

sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes

i realized that it was doing just nothing so i decided to write

sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1

and voila! the xserver installed but not beryl so in an attempt to install 

i wrote :

sudo apt-get install beryl emerald emerald-themes and it just answered that there was NO file called Beryl. I let that go and proceeded.

At first reboot the machine again showed the Xserver failed to load, so i wrote again $sudo dpkg-reconfigure xserver-xorg and went trough all the process to reconfigure.

you know that includes Video upgrade, the monitor, the keyboard, the mouse, well everything.

after all the process in the prompt again i wrote : sudo reboot

and then at start up a splash Nvidia screen showed up for half a second. And i couldnt believe that i recovered the graphical system but i did, now i dont know if  at the startup and reboot again, this will keep stable.

so i am going to post to you ALL screens so in case xserver cant load again at least the specs keep online so i can check suggestions.

many thanks for your replies, i am going to post the specs and files, but i wont do anything until some analyzing process.

here they are:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Tarjeta de vídeo genérica"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	VideoRam	32000
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de vídeo genérica"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---------HERE IS THE SOURCES.LIST----------------------

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main main-amd64 
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main main-amd64
deb [http://compiz-mirror.lupine.me.uk/dapper](http://compiz-mirror.lupine.me.uk/dapper) main main-amd64
deb [http://ubuntu.compiz.net/dapper](http://ubuntu.compiz.net/dapper) main main-amd64

--------------------HERE IS THE GDM.CONF----------------------
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=libre

[security]

[xdmcp]

[gui]

[greeter]
Browser=true

[chooser]

[debug]

[servers]
 0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

------here is the list of tasks that are going to run next start up-----
**-The lines are located in System->Preferences->Sessions->Startup Programs

xmodmap -e keycode 22=BackSpace 
update-notifier 
beryl-managerReboot 
gnome-power-manager 
gnome-volume-manager --sm-disable 
xmodmap /usr/share/xmodmap/xmodmap.us 

*-/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/-*/

I really dont know if this thing is going to be stable enough to run again when i reboot the system, but the specs that have changed are posted as they are right now.

I am going to test my luck and reboot soon after i post this message, next time either in Ubuntu or whatever OS available, i will check your suggestions now that the specs are posted. 

Thanks for any help, and thanks musashi, i can not follow your suggestion at once, because this is the first time i managed to reboot the system and have the luxury of using the graphic mode. I need to read the previous posts you mention, because if i execute them, maybe the specs i posted are likely to change.

Anyway, if this thing reboot and work "ok" even without Beryl, i am going to perform any suggestion given:-D .

Thank you so much.

---

### Post by Tombius on 2006-10-15
Ok i won access again to the graphical system. 

Now i will perform the upgrades that the system require. That should buy some time until a reply with some ideas is posted.

Thanks.

---

### Post by m.musashi on 2006-10-15
> **Tombius said:**
> Ok i won access again to the graphical system. 

Now i will perform the upgrades that the system require. That should buy some time until a reply with some ideas is posted.

Thanks.

In looking over the xorg.conf you posted, my first thought is the busid might be wrong. You have ```
BusID "PCI:0:5:0"
``` but the how to suggests ```
BusID "PCI:1:0:0"
``` It is different for different people. Did you try ```
lspci -X
``` to find the id of the video card? When I run this I get ```
PCI:3:0:0 VGA compatible controller: nVidia Corporation: Unknown device 0392
``` and that tells me I need BusID "PCI:3:0:0".

Handband2 posted some good tips [here](http://www.ubuntuforums.org/showpost.php?p=1588195&postcount=224).

I also notice the xorg.conf does not include the following:
```
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "TrippleBuffer" "false"
```
I can't say for sure if all of these are required and if some hardware may be different but the RenderAccel line seems to be one that is needed.

For comparison, the relevant section of my xorg.conf looks like this:
```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID          "PCI:3:0:0"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "TrippleBuffer" "false"
EndSection
```

---

### Post by Johntam on 2006-10-15
Back to report on my Beryl experiment.

The bad,
I gave up on trying to get it working on 6.06 AMD64 for now.
I will wait for 6.10, and see what it will do then.

The good,
Loaded a fresh copy of 6.06 386, 
Beryl installed and works fine as far as I can tell.

Playing with it for now, still trying to find out what will do.

Thanks for all the help everyone.
JT

---

### Post by Tombius on 2006-10-15
thanks but the fact is that i cant load beryl

somehow it says that there is no beryl available

i will try later, but the fact is when i updates the system it said again that there was no public key.

What does that mean?
:confused:

---

### Post by beerorkid on 2006-10-15
> **Tombius said:**
> thanks but the fact is that i cant load beryl

somehow it says that there is no beryl available

i will try later, but the fact is when i updates the system it said again that there was no public key.

What does that mean?
:confused:

you can still install without importing the key, but it is nice to just get the key so that warning does not come up.

check here [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) and import the key for the repo you are using.

---

### Post by Tombius on 2006-10-16
OK now i have some more info to get the beryl running but how do i execute the command Ispci -x i mean the exact syntaxis because when i run #Ispci -x in my terminal it just doesnt do anything at all.

---

### Post by handband2 on 2006-10-16
> **Tombius said:**
> OK now i have some more info to get the beryl running but how do i execute the command Ispci -x i mean the exact syntaxis because when i run #Ispci -x in my terminal it just doesnt do anything at all.

Tombius,

Run:
```
lspci -x
```
not
```
Ispci -x
```

Also if you are having a problem rebooting with X crashing make sure your nvidia driver matches your **nvidia-glx** binaries.  You can check by doing an **NVIDIA** search in your Synapic Package Manager.

---

### Post by Charles Hand on 2006-10-16
> **handband2 said:**
> Tombius,

Run:
```
lspci -x
```
not
```
Ispci -x
```

If you're checking your busid, use
```

lspci -X

```
upper-case X not lower-case x.

If you have nvidia, look for the line containing the word nVidia

i.e.
```

lspci -X | grep -i nvidia

```

---

### Post by Tombius on 2006-10-16
Thanks but isnt it the same both codes you posted?

---

### Post by Tombius on 2006-10-16
Ah got it, it starts with L not I sorry well i ran it and this came:

PCI:0:0:0 RAM memory: nVidia Corporation C51 Host Bridge
PCI:0:0:1 RAM memory: nVidia Corporation C51 Memory Controller 0
PCI:0:0:2 RAM memory: nVidia Corporation C51 Memory Controller 1
PCI:0:0:3 RAM memory: nVidia Corporation C51 Memory Controller 5
PCI:0:0:4 RAM memory: nVidia Corporation C51 Memory Controller 4
PCI:0:0:5 RAM memory: nVidia Corporation C51 Host Bridge
PCI:0:0:6 RAM memory: nVidia Corporation C51 Memory Controller 3
PCI:0:0:7 RAM memory: nVidia Corporation C51 Memory Controller 2
PCI:0:5:0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge
PCI:0:9:0 RAM memory: nVidia Corporation MCP51 Host Bridge
PCI:0:10:0 ISA bridge: nVidia Corporation MCP51 LPC Bridge
PCI:0:10:1 SMBus: nVidia Corporation MCP51 SMBus
PCI:0:10:2 RAM memory: nVidia Corporation MCP51 Memory Controller 0
PCI:0:11:0 USB Controller: nVidia Corporation MCP51 USB Controller
PCI:0:11:1 USB Controller: nVidia Corporation MCP51 USB Controller
PCI:0:13:0 IDE interface: nVidia Corporation MCP51 IDE
PCI:0:14:0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller
PCI:0:15:0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller
PCI:0:16:0 PCI bridge: nVidia Corporation MCP51 PCI Bridge
PCI:0:16:1 0403: nVidia Corporation MCP51 High Definition Audio
PCI:0:20:0 Bridge: nVidia Corporation MCP51 Ethernet Controller
 so wich do i use the 0:5:0 or the 0:16:0 ?

---

### Post by Tombius on 2006-10-16
Here i am again, step by step.

sudo apt-get install nvidia-kernel-common nvidia-glx
the result: All nvidia drivers up to date 
nvidia-kernel-common 
nvidia-glx

/-/-/-/-/-
sudo gedit /etc/X11/xorg.conf

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

As you may see, there is no Glcore or dri but there is a glx
/*-/*/-/*-/-/*-/*-

Section "Device"
	Identifier	"Tarjeta de vídeo genérica"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	VideoRam	64000
        Option "RenderAccel""true"
        Option         "AllowGLXWithComposite" "true"
        Option         "TrippleBuffer" "false" 

EndSection

As you may see, added the 3 options 2 of them are not in the original post of this "how to"

/*-/*/*-/*-/-/*-/-/-/--*/-*/-*/

Also the monitor and screen settings are as follows

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de vídeo genérica"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Default is 24 nothing more nothing less

I saved and closed the xorg.conf

about the nvidia identifier, i ran the lspci -X | grep -i nvidia and got this:

PCI:0:0:0 RAM memory: nVidia Corporation C51 Host Bridge
PCI:0:0:1 RAM memory: nVidia Corporation C51 Memory Controller 0
PCI:0:0:2 RAM memory: nVidia Corporation C51 Memory Controller 1
PCI:0:0:3 RAM memory: nVidia Corporation C51 Memory Controller 5
PCI:0:0:4 RAM memory: nVidia Corporation C51 Memory Controller 4
PCI:0:0:5 RAM memory: nVidia Corporation C51 Host Bridge
PCI:0:0:6 RAM memory: nVidia Corporation C51 Memory Controller 3
PCI:0:0:7 RAM memory: nVidia Corporation C51 Memory Controller 2
PCI:0:5:0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge
PCI:0:9:0 RAM memory: nVidia Corporation MCP51 Host Bridge
PCI:0:10:0 ISA bridge: nVidia Corporation MCP51 LPC Bridge
PCI:0:10:1 SMBus: nVidia Corporation MCP51 SMBus
PCI:0:10:2 RAM memory: nVidia Corporation MCP51 Memory Controller 0
PCI:0:11:0 USB Controller: nVidia Corporation MCP51 USB Controller
PCI:0:11:1 USB Controller: nVidia Corporation MCP51 USB Controller
PCI:0:13:0 IDE interface: nVidia Corporation MCP51 IDE
PCI:0:14:0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller
PCI:0:15:0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller
PCI:0:16:0 PCI bridge: nVidia Corporation MCP51 PCI Bridge
PCI:0:16:1 0403: nVidia Corporation MCP51 High Definition Audio
PCI:0:20:0 Bridge: nVidia Corporation MCP51 Ethernet Controller

so wich do i use the 0:5:0 or the 0:16:0 ?

/*//*/*/*/*/*/*/*/**/*/*/*/*/*/*

I have ALL this in the /etc/apt/sources.list

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main main-amd64 
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main main-amd64
deb [http://compiz-mirror.lupine.me.uk/dapper](http://compiz-mirror.lupine.me.uk/dapper) main main-amd64
deb [http://ubuntu.compiz.net/dapper](http://ubuntu.compiz.net/dapper) main main-amd64
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx 
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx 

Mainly Because there are references about this in the beerorkid page.

Wich do i have to conserve?

the "how to" suggeted lines or the "beerorkid" suggested lines or maybe both?  i am trying now with both, just to see what happens.
/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*

then the apparently unnecesary keys.

wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -

those links downloaded a 1.7 kb file
/*/*/*/*/*/*/*/*/*/*/*/ 

Then the most important file

sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes

xserver-xgl already updated
libgl1-mesa already updated
xserver-xorg already updated
libglitz-glx1 already updated

E: Could not find the  beryl package.

So all is lost as you see, the main file beryl can not be found.

/*/*/*/*/*/*/*/*/*/***/*/*/*/*/

Now it is time to some experimental procedure.

sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1

alone and result is: that all of them are updated

and i will try with 

sudo aptitude update
sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes

as for the aptitude update command, warnings among them the        NO_PUBKEY 31A5F97FED8A569E. Warnings are not errors so i continue.

the other one the:

sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes

it says that there is no beryl package but there is a beryl-plugins-data and the notification that emerald-themes is a broken package.

so i changed the orders from 
sudo aptitude install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes

to

sudo aptitude upgrade xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes

it says all is OK and upgraded

BUT still emerald-themes is a broken package for some reason, what i am doing now is ignoring the fact that the beryl package does not exist and i continue.
/*/*/*/*/*/*/*/*/*/*/*/*/*/*/

sudo gedit /etc/gdm/gdm.conf-custom

to the bottom of the page it already says:
[servers]
 0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

it is like this since first time i try to install beryl

/*/*//*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/

It is supposed that this is ALL i need to get the Beryl up and running i am going to reboot (and pray for the system to not crash miserably). 

I think i am being a very descriptive person. I beg for your patience and will thank any suggestion, i already took some advices and that is why i have more information about the system.

Thanks, now let me see if this thingy works.
If not, please can anyone tell me how do i get beryl to work? The system is not a real crap, is 512 mb Kingston DDR3200, Amd 64 Socket-939 3000+, and has a GYGABYTE mobo that has Nvidia GeForce 6600 integrated.

I read that there are Users that have less than this settings and have their beryl packages running, so i say, come on!? my system can do better than just plain Desktop.

Thanks for any help given. :-D

---

### Post by lammer on 2006-10-16
> **handband2 said:**
> lammer,

It will be interesting if you do get it running on a TNT2 card because XGL is a HOG in resources.  Here are a couple of sites to see the requirements:
[LIST]
[*][http://en.opensuse.org/Xgl#Hardware_Advisory]("http://en.opensuse.org/Xgl#Hardware_Advisory")
[*][http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL")
[*][http://www.freesoftwaremagazine.com/node/1757]("http://www.freesoftwaremagazine.com/node/1757")
[/LIST]

Someone on #ubuntu-xgl at freenode, has told me that the problem could be on my card, that is rather old, and it will possible fail to start beryl. He points to this phrase on my error message: **beryl-xgl: Support for non power of two textures missing** He thinks I need some video card with **GL_ARB_texture_non_power_of_two** :confused: 

He also post me this site: [http://www.worldwindcentral.com/wiki/Video_Card_Compatibility#nVidia](http://www.worldwindcentral.com/wiki/Video_Card_Compatibility#nVidia) where my video card is listed. On the site says that I need to "downgrade" my video driver to **45.23**, but it only list the Windows video driver: [http://www.nvidia.com/object/winxp-2k_45.23.html](http://www.nvidia.com/object/winxp-2k_45.23.html)

I have tried to look for a similar version in Linux, just to try, and I have found this one: [http://www.nvidia.com/object/linux_display_ia32_1.0-4496.html](http://www.nvidia.com/object/linux_display_ia32_1.0-4496.html) and this other one: [http://www.nvidia.com/object/linux_display_ia32_1.0-5328.html](http://www.nvidia.com/object/linux_display_ia32_1.0-5328.html)
The linux ones are about the same date as the windows ones, so I think I can try with them...

For sure, this is going to be my last workarround. 45€ is the market price of a "normal" Nvidia card with 256Mb, it is cheaper than all my *wasted* time .

I will post back the results as allways.

:-k

---

### Post by handband2 on 2006-10-16
> **Tombius said:**
> It is supposed that this is ALL i need to get the Beryl up and running i am going to reboot (and pray for the system to not crash miserably). 

I think i am being a very descriptive person. I beg for your patience and will thank any suggestion, i already took some advices and that is why i have more information about the system.

Thanks, now let me see if this thingy works.
If not, please can anyone tell me how do i get beryl to work? The system is not a real crap, is 512 mb Kingston DDR3200, Amd 64 Socket-939 3000+, and has a GYGABYTE mobo that has Nvidia GeForce 6600 integrated.

I read that there are Users that have less than this settings and have their beryl packages running, so i say, come on!? my system can do better than just plain Desktop.

Thanks for any help given. :-D

Tombius,

If you are running this on a 64bit machine check out my earlier posts:
[http://ubuntuforums.org/showpost.php?p=1612716&postcount=360]("http://ubuntuforums.org/showpost.php?p=1612716&postcount=360")

[http://ubuntuforums.org/showpost.php?p=1616421&postcount=366]("http://ubuntuforums.org/showpost.php?p=1616421&postcount=366")

Also for:
```
Section "Device"
Identifier "Tarjeta de vídeo genérica"
Driver "nvidia"
BusID "PCI:0:5:0"
[COLOR="Red"]VideoRam 64000 <-- Most of the time this is not needed[/COLOR]
Option "RenderAccel""true"
Option "AllowGLXWithComposite" "true"
Option "TrippleBuffer" "false"

EndSection
```

---

### Post by handband2 on 2006-10-16
> **lammer said:**
> Someone on #ubuntu-xgl at freenode, has told me that the problem could be on my card, that is rather old, and it will possible fail to start beryl. He points to this phrase on my error message: **beryl-xgl: Support for non power of two textures missing** He thinks I need some video card with **GL_ARB_texture_non_power_of_two** :confused: 

He also post me this site: [http://www.worldwindcentral.com/wiki/Video_Card_Compatibility#nVidia](http://www.worldwindcentral.com/wiki/Video_Card_Compatibility#nVidia) where my video card is listed. On the site says that I need to "downgrade" my video driver to **45.23**, but it only list the Windows video driver: [http://www.nvidia.com/object/winxp-2k_45.23.html](http://www.nvidia.com/object/winxp-2k_45.23.html)

I have tried to look for a similar version in Linux, just to try, and I have found this one: [http://www.nvidia.com/object/linux_display_ia32_1.0-4496.html](http://www.nvidia.com/object/linux_display_ia32_1.0-4496.html) and this other one: [http://www.nvidia.com/object/linux_display_ia32_1.0-5328.html](http://www.nvidia.com/object/linux_display_ia32_1.0-5328.html)
The linux ones are about the same date as the windows ones, so I think I can try with them...

For sure, this is going to be my last workarround. 45€ is the market price of a "normal" Nvidia card with 256Mb, it is cheaper than all my *wasted* time .

I will post back the results as allways.

:-k

lammer,

Seems like you are like a lot of us, *you rather keep trying to get something to work rather than do the easy thing* ](*,) A lot of us like to figure things out even if it isn't the easiest way :)

For compatible cards I like this site, though I don't think your card is on the list:
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards")

Also, here is a great site to get your driver correctly installed:
[http://albertomilone.com/guides.html]("http://albertomilone.com/guides.html")

---

### Post by lammer on 2006-10-16
> **handband2 said:**
> lammer,

Seems like you are like a lot of us, *you rather keep trying to get something to work rather than do the easy thing* ](*,) A lot of us like to figure things out even if it isn't the easiest way :)


Hehehe ;) I think that there is still hope, even if this morning I was in a "Wallmart-like" shop, reading all the specs of several video cards...

> **handband2 said:**
> 
For compatible cards I like this site, though I don't think your card is on the list:
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#nVidia_Cards")


On that list, my card is the very first of Nvidia cards, so maybe someone has get it work...

> **handband2 said:**
> Also, here is a great site to get your driver correctly installed:
[http://albertomilone.com/guides.html]("http://albertomilone.com/guides.html")

Hey, thanks for the link. I think I have another reason to spend time with this dammed card... You know what? This morning I have also get a new (and expensive) computer chair, so I think that this afternoon will be loooooong :rolleyes: 

Thanks for all handband2!

---

### Post by jhenager on 2006-10-16
> **djRobbieF said:**
> WOW that's a nice monitor.  I thought I had it good  ;)

Are your Modes lines actually truncated like that, or is it just the way it got pasted?

... and why is the busid missing from your Device section?
I noticed that I didn't have that line either, but I don't see any problems.

---

### Post by jhenager on 2006-10-16
> **djRobbieF said:**
> Version 1.5
This will allow me to take advantage of the dual-core nature of the Pentium D processor by installing the optimized kernel. Once that kernel is installed, I restart the computer.


So typing uname -r will show me I am using that smp kernel?

---

### Post by ricdes on 2006-10-16
Hi all,

I just installed Beryl with this Howto, I got a Intel Centrino Duo.

I use Ubuntu 6.06, the newest Nvidia beta drivers and Gnome.

I Installed it like in this howto and everything worked until I tryed to start beryl.

when I right click on the Gem and I do -> Select Window Manager -> Beryl , the screen flashes for like 2 Seconds and then im still on Metacity...

Anyone knows that problem and can help me out with it? Everything updated and installed.

Greetings from cold switzerland.

---

### Post by lammer on 2006-10-16
> **ricdes said:**
> I Installed it like in this howto and everything worked until I tryed to start beryl.

when I right click on the Gem and I do -> Select Window Manager -> Beryl , the screen flashes for like 2 Seconds and then im still on Metacity...

Anyone knows that problem and can help me out with it? Everything updated and installed.

Greetings from cold switzerland.

Hi ricdes, post your /etc/X11/xorg.conf content, to check it's ok.

Also it would be useful in order to make sure that you have your latest video drivers to post the output of glxgears -info

And the content of the /etc/gdm/gdm.conf-custom file, or this couple of files if you are using [hadnband2 guide]("http://ubuntuforums.org/showpost.php?p=1564565&postcount=75") /usr/bin/startxgl.sh and /usr/share/xsessions/xgl.desktop

Greentings from the warm Spain ;)

---

### Post by wolf202 on 2006-10-16
Great guide, submitted to [wikitut.org]("http://www.wikitut.org")

[http://www.wikitut.org/index.php?title=How_to_Install_XGL/Beryl_on_GNOME_with_nVidia_Hardware](http://www.wikitut.org/index.php?title=How_to_Install_XGL/Beryl_on_GNOME_with_nVidia_Hardware)

-wolf

---

### Post by ricdes on 2006-10-17
> **lammer said:**
> Hi ricdes, post your /etc/X11/xorg.conf content, to check it's ok....

here you are:

**xorg.conf:**

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ch"
	Option		"XkbVariant"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"AIGLX"		 "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

**Output of GLXGEARS:**

GL_RENDERER   = GeForce Go 7900 GS/PCI/SSE2
GL_VERSION    = 2.0.2 NVIDIA 87.62
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_color_buffer_float GL_ARB_depth_texture GL_ARB_draw_buffers GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_non_power_of_two GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ATI_draw_buffers GL_ATI_texture_float GL_ATI_texture_mirror_once GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_depth_bounds_test GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_HP_occlusion_test GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_fragment_program2 GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_NV_vertex_program3 GL_NVX_conditional_render GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum
58915 frames in 5.0 seconds = 11782.882 FPS

**Gdm Conf Custom File:**

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=aiglx

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true:  


Thank you very much!

---

### Post by handband2 on 2006-10-17
> **ricdes said:**
> Thank you very much!

ricdes,

Try this, change your /etc/X11/xorg.conf:
```
Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver "nvidia"
BusID "PCI:1:0:0"  [COLOR="Red"]<-- Make sure this is correct by running $lspci -X | grep -i vga[/COLOR]
Option "RenderAccel" "True"
EndSection
```
Turn off DRI:
```
#Section "DRI"
#Mode 0666
#EndSection
```

Turn off Option AIGLX:
```
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
#Option "AIGLX" "true" [COLOR="Red"]<-- Turn this off[/COLOR]
EndSection
```

Also did you install aiglx?  If not change your etc/gdm/gdm.conf-custom:
```
**FROM**
0=aiglx [COLOR="Red"]<-- Change this to Xgl[/COLOR]

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true: [COLOR="Red"]<-- Remove the :[/COLOR]

**TO:** 
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

---

### Post by m.musashi on 2006-10-17
> **ricdes said:**
> here you are:

**xorg.conf:**

.
. (code deleted)
.


Thank you very much!
It sounds like beryl is trying to load and then failing for some reason and falling back to metacity. You might try adding the following to the xorg.conf under the device section.
```
Option "AllowGLXWithComposite" "true"
Option "TrippleBuffer" "false"
```
These don't seem to be required options but may help some people. I believe that handband2 had also suggested removing the ":0" from etc/gdm/gdm.conf-custom like this:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

Just some suggestions from others. Hope they are helpful.

EDIT: oops, too late. Follow Handband2's suggestions.

---

### Post by m.musashi on 2006-10-17
> **handband2 said:**
> ricdes,
Try this...


Wow, you are good. I missed all those. Of course, you've been my teacher through this so that is to be expected.

---

### Post by handband2 on 2006-10-17
[COLOR="black"][B][SIZE="4"]Install the NVIDIA driver script, thanks to [[COLOR="Black"]tseliot.[/COLOR]]("http://ubuntuforums.org/member.php?u=19388") [Website is here - Envy]("http://albertomilone.com/nvidia_scripts1.html")
[/SIZE][/B][/COLOR]
"Envy" is a script written in Python which will download the latest Nvidia driver or the Legacy driver (for older cards) from Nvidia's website and set it up for you handling dependencies (compilers, OpenGL, etc.) which are required in order to use the driver on Ubuntu Linux.

Brief explanation of the name of my script:
The Italian for "envy" is "invidia" ( I guess you can see the play on words)

This project is also registered on [Launchpad]("https://launchpad.net/products/envy")


[COLOR="Red"]**NOTE: **[/COLOR]Envy will REMOVE your RESTRICTED MODULES. Therefore if you need the restricted modules for a hardware device of yours (e.g. for your wireless card) DO NOT use Envy.


**STABLE VERSION** (0.4.2-1ubuntu10, released on September 20 2006)
(See my Blog for an explanation of Envy's features)

Licence: GPL

**Package for Ubuntu Dapper 6.06/Ubuntu Breezy Badger 5.10**
**[envy_0.4.2-1ubuntu10_all.deb]("http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu10_all.deb")**


**Source code**
(only developers might want to download this)

**[envy_0.4.2-1ubuntu10.dsc]("http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu10.dsc")**

**[envy_0.4.2-1ubuntu10.tar.gz]("http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu10.tar.gz")**

**[envy_0.4.2-1ubuntu10_i386.changes]("http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_0.4.2-1ubuntu10_i386.changes")**


____________________________________________


**Requirements**
[LIST]
[*]Ubuntu Breezy 5.10 or Ubuntu Dapper Drake 6.06 (32bit or 64bit)(PPC is NOT supported)
[/LIST]
[LIST]
[*]An Internet connection (better if broadband)
[/LIST]


**Instructions**
Select the script according to your CPU architecture (nvidia_script1 for x86 processors and 32 bit operative systems, nvidia_script_64 for 64bit operative systems)

[COLOR="Red"]**NOTE: **[/COLOR]Make sure you have all the repositories enabled (also universe and multiverse) in your /etc/apt/sources.list
If you do not know how to enable those repositories, please take a look at this page:
[enabling_extra_repositories]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")


**1) Download and install the deb package**

**2) Log out and press CTRL+ALT+F1 (so as to get out of the Desktop Environment, i.e. you'll see ONLY the command line)**

**3) Log in (if required)**

**4) Run "envy" by opening Terminal or Konsole and typing (quite obviously):**

```
envy
```
[B]
5) Choose to install or uninstall the driver (from the textual interface)[/B]


[COLOR="Red"]**Known Issues**[/COLOR]
A user reported that after typing "envy" and choosing the "install" option, envy hangs on Ubuntu's splash screen. To solve that problem press Ctrl+Alt+F1

**Support**
You can find more information and get support at the following address:
**[HOWTO: Latest Nvidia Drivers- Testers needed]("http://www.ubuntuforums.org/showthread.php?t=139264")**

---

### Post by PendragonUK on 2006-10-17
OK it's working, spinning cube and everything...

But and you that there would be a but...

How do I set up Beryl? As I type this every few seconds I have to click on the page just to get focus back so I can type. I can't click anything with my mouse unless I hold Ctrl. As you can imagine this is a little tiresome.

It all looks very cool but I can't live with it...

So please can someone please point me in the direction of some documentation.

---

### Post by m.musashi on 2006-10-17
> **PendragonUK said:**
> OK it's working, spinning cube and everything...

But and you that there would be a but...

How do I set up Beryl? As I type this every few seconds I have to click on the page just to get focus back so I can type. I can't click anything with my mouse unless I hold Ctrl. As you can imagine this is a little tiresome.

It all looks very cool but I can't live with it...

So please can someone please point me in the direction of some documentation.

Are you running conky? It seems to steal focus with beryl. There is a fix. If you have conky I'll try and find it. I'm not sure about the other issues you mentioned. You should have a gem icon on the top panel that will give you access to beryl manager. From there you can change a bunch of settings.

---

### Post by PendragonUK on 2006-10-17
I can access the Beryl control panel but it's a mine field of settings.

What I looking for is some documentation for those settings.

To add to my misery the scroll wheel on my mouse just zooms the screen in and out...

These post would be longer but I don't touch type, so I don't see when it loses focus and I have to type everything several times. Grrrrr...

---

### Post by m.musashi on 2006-10-17
> **PendragonUK said:**
> I can access the Beryl control panel but it's a mine field of settings.

What I looking for is some documentation for those settings.

To add to my misery the scroll wheel on my mouse just zooms the screen in and out...

These post would be longer but I don't touch type, so I don't see when it loses focus and I have to type everything several times. Grrrrr...

Click the gem and select "select window manager" and then choose metacity. That will turn beryl off so you can work out the problems without the typing hassles.

As for documentation, I have not found much. The beryl forums are at [http://forum.beryl-project.org/index.html](http://forum.beryl-project.org/index.html). That might get you started. It's a very new project and as yet there isn't a lot of documentation.

---

### Post by m.musashi on 2006-10-17
Here is another site with some info. I think it's the home site for the forum.

[http://wiki.beryl-project.org/index.php/Main_Page](http://wiki.beryl-project.org/index.php/Main_Page)

---

### Post by handband2 on 2006-10-17
> **m.musashi said:**
> Are you running conky? It seems to steal focus with beryl. There is a fix. If you have conky I'll try and find it. I'm not sure about the other issues you mentioned. You should have a gem icon on the top panel that will give you access to beryl manager. From there you can change a bunch of settings.

For people running Conky and Beryl go here:
[http://ubuntuforums.org/showpost.php?p=1569585&postcount=175]("http://ubuntuforums.org/showpost.php?p=1569585&postcount=175")

---

### Post by PendragonUK on 2006-10-17
OK the focus problem has been solved by removing "Conky" shame because I liked it. But if I can get this to work the way I want then it will be worth it.

Thanks for the tip.

I just have to get the mouse to behave the way I want, that is the way it would normally behave...

Left button, right button and the scroll wheel (center on the wheel click)

---

### Post by m.musashi on 2006-10-17
> **PendragonUK said:**
> OK the focus problem has been solved by removing "Conky" shame because I liked it. But if I can get this to work the way I want then it will be worth it.

Thanks for the tip.

I just have to get the mouse to behave the way I want, that is the way it would normally behave...

Left button, right button and the scroll wheel (center on the wheel click)
Check [here](http://ubuntuforums.org/showpost.php?p=1609809&postcount=2) for a suggestion on fixing conky to work with beryl. I think this is what I did. It is still hiding desktop icons but it no longer steals focus.

---

### Post by PendragonUK on 2006-10-19
I have found the weird mouse problem fix :) Disable the screen shot plug-in

---

### Post by arunabh on 2006-10-19
thanks...it worked of me....:)

---

### Post by m.musashi on 2006-10-20
> **handband2 said:**
> For people running Conky and Beryl go here:
[http://ubuntuforums.org/showpost.php?p=1569585&postcount=175]("http://ubuntuforums.org/showpost.php?p=1569585&postcount=175")

Thanks. The start up script worked well. Now my desktop icons are not hidden. Not sure why that would fix the problem but it did.

---

### Post by rykel on 2006-10-20
Hi,

I need some help... I followed the instructions here on page 1 WITHOUT setting the Acceleration in my nvidia config file, and now, when I log into Dapper, I see the NVIDIA splash screen flash 3 times, and then, NO SCREEN.

I know that below the blank monitor, the system should be up and running already, since I see hard disk activity.

I also CANNOT switch to other virtual desktops (Ctrl-Alt-F1 etc.), but I CAN reboot the PC by Ctrl-Alt-Del.

Please advise?

---

### Post by m.musashi on 2006-10-21
> **rykel said:**
> Hi,

I need some help... I followed the instructions here on page 1 WITHOUT setting the Acceleration in my nvidia config file, and now, when I log into Dapper, I see the NVIDIA splash screen flash 3 times, and then, NO SCREEN.

I know that below the blank monitor, the system should be up and running already, since I see hard disk activity.

I also CANNOT switch to other virtual desktops (Ctrl-Alt-F1 etc.), but I CAN reboot the PC by Ctrl-Alt-Del.

Please advise?
I suppose your fist step would be to be able to log in so that you can start to fix the problem. Is that what you are wanting to do? If so, you will have to edit some files from a comand prompt. It might also be possible to boot a live cd and edit the config files. I've not done it that way before but I think it's quite easy. Just boot the ubuntu install CD and open the xorg.conf file and undo the changes or add the "RenderAccel" line. From a command prompt type:
```
sudo vi /etc/X11/xorg.conf
you can also use:
sudo nano /etc/X11/xorg.conf
```
Undo what you did or add in what you think you need and reboot. If I missunderstood your goal, please let me know.

---

### Post by zomw on 2006-10-22
I'm having one major problem.  After following your helpful guide, I can't boot into Ubuntu.  The only step I didn't follow exactly was the very last one where I had to reboot (I instead just logged off and logged back in).  When I logged back in, it flashed me the desktop where I noticed the little beryl icon in the system tray for a sec, but then switched to a completely blank white screen.  I tried the beryl controls, and they worked just fine (I rotated the cube around, saw the big beryl logo on top, etc.), but once again I could see no desktop on the sides of the cube, just the big beryl logo on top.  I then rebooted, and as someone said before, it flashed the nvidia logo three times and then went to a screen that said my x server was messed up somehow.  It gave me the names of two logs/files:
Logfile- "/var/log/xorg.93.log"
Using Config file- "/etc/X11/xorg.conf"
and also told me to check [http://wiki.x.org](http://wiki.x.org) to make sure that I had the newest x server version.  Lastly it told me that it had temporarily disabled my x server and also something else about the GDM, then leading me to a terminal on a completely black screen.

really sorry about how long this is...but does anyone have any possible resolutions to this problem?...just got ubuntu 3 days ago and am completely puzzled.

---

### Post by zomw on 2006-10-22
oh yeah and three more things-

-how would I install a newer version of x server if i can't even successfully boot into ubuntu?

-If it's not the version of x server I have that's causing the problem and really what I typed in on one of the files I had to edit, how could I access those files to edit them correctly?

-I have the ubuntu live cd with me if I need it to fix the problem (I also can boot into windows xp)

---

### Post by rykel on 2006-10-22
> **m.musashi said:**
> I suppose your fist step would be to be able to log in so that you can start to fix the problem. Is that what you are wanting to do? If so, you will have to edit some files from a comand prompt. It might also be possible to boot a live cd and edit the config files. I've not done it that way before but I think it's quite easy. Just boot the ubuntu install CD and open the xorg.conf file and undo the changes or add the "RenderAccel" line. From a command prompt type:
```
sudo vi /etc/X11/xorg.conf
you can also use:
sudo nano /etc/X11/xorg.conf
```
Undo what you did or add in what you think you need and reboot. If I missunderstood your goal, please let me know.

hi musashi,

thanks for your reply... i managed to change my nvidia driver to the "nv" driver using Knoppix Root Shell, and upon rebooting into Ubuntu, I faced the following scenario...

GNOME never came back, but the system managed to get me to the command line, which is what i needed desperately. using "sudo killall gdm" and then "startx", i am able to get back into my not-so-fully-functional Desktop.

next, i used Synaptic Package Manager to remove anything related to beryl, emerald and compiz...

HOWEVER, i still cannot log into the Desktop upon another reboot, and had to kill GNOME Display Manager (gdm) and using "startx" again.

well, but at least i can now use the screen!

i will solve this problem later and if successful, i will post my experience here.

thank you!!!

---

### Post by m.musashi on 2006-10-22
> **rykel said:**
> hi musashi,

thanks for your reply... i managed to change my nvidia driver to the "nv" driver using Knoppix Root Shell, and upon rebooting into Ubuntu, I faced the following scenario...

GNOME never came back, but the system managed to get me to the command line, which is what i needed desperately. using "sudo killall gdm" and then "startx", i am able to get back into my not-so-fully-functional Desktop.

next, i used Synaptic Package Manager to remove anything related to beryl, emerald and compiz...

HOWEVER, i still cannot log into the Desktop upon another reboot, and had to kill GNOME Display Manager (gdm) and using "startx" again.

well, but at least i can now use the screen!

i will solve this problem later and if successful, i will post my experience here.

thank you!!!

Was the "nv" driver the only change you had to make to get back to an "original" set up? There are several other changes that should be made to the xorg.conf file according to the how to. You would have also made some changes to /etc/gdm/gdm.conf-custom. Did you undo those changes? Can you post the contents of xorg.conf and gdm.conf-custom? Perhaps someone here can find what might be causing the problem.

---

### Post by abu3abdalla on 2006-10-22
hi 
i am facing a big problem couse when i set xorg.conf to Nvidia insted of the defult " i810" the laptop cant log in GUI and tell me that thier is an error 
but when i am use the " i810 " i can log in but without 3D desktop and when i am update the system is give me : 

abu3abdalla@abu3abdalla-laptop:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  libwnck18 xserver-xgl
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

so i do not know what can i do ?????????


please tell me please :confused:

---

### Post by bennyj on 2006-10-22
> **m.musashi said:**
> Was the "nv" driver the only change you had to make to get back to an "original" set up? There are several other changes that should be made to the xorg.conf file according to the how to. You would have also made some changes to /etc/gdm/gdm.conf-custom. Did you undo those changes? Can you post the contents of xorg.conf and gdm.conf-custom? Perhaps someone here can find what might be causing the problem.

I had the same problem.your going to have to remove the lines you added at the bottom of your /etc/gdm/gdm.conf-custom under [server].I also removed the lines I added to /etc/X11/xorg.conf.That allowed me to boot up normaly.Just use nano from the command line to remove and then do a sudo reboot and you should be back in.

---

### Post by OpticalIllusion on 2006-10-24
Is anyone else having the same problem that I'm having with the newest version of Beryl?  

I'm having this same problem on my desktop (nvidia) and laptop (ati).  When I login, beryl-manager will start up normal and everything.  As soon as I open a window, the window borders will flash on and off really fast.  The only way I can make it stop is by quitting beryl-manager and restarting it.

I never had this problem on the previous version of Beryl.  It worked fine on my laptop and desktop.  This problem is with both of my computers with two totally different video cards.  Is it a bug or some configuration I need to fix?

---

### Post by m.musashi on 2006-10-24
> **OpticalIllusion said:**
> Is anyone else having the same problem that I'm having with the newest version of Beryl?  

I'm having this same problem on my desktop (nvidia) and laptop (ati).  When I login, beryl-manager will start up normal and everything.  As soon as I open a window, the window borders will flash on and off really fast.  The only way I can make it stop is by quitting beryl-manager and restarting it.

I never had this problem on the previous version of Beryl.  It worked fine on my laptop and desktop.  This problem is with both of my computers with two totally different video cards.  Is it a bug or some configuration I need to fix?
There was an update to beryl that seems to have caused some problems. Someone posted a new thread realated to the problems. [http://ubuntuforums.org/showthread.php?t=281497](http://ubuntuforums.org/showthread.php?t=281497). So far it seems there isn't a fix other than work arounds like stopping and restarting beryl.

---

### Post by OpticalIllusion on 2006-10-24
Thanks for the link.  Nice to know I'm not the only one having this problem.  I hope they get it fixed soon. :)

---

### Post by ldvader on 2006-10-25
I followed your steps to the "T" and got Beryl installed. The RED gem is present on my desktop, but I think Beryl is defaulting to Metacity. CTRL-ALT-Left or Right not doing anything. When I reboot and switch session to XGL, I get the following Error:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. "

***DETAILS***
/etc/gdm/PreSession/Default: Registering your session with wtmp....
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w .....
/etc/gdm/Xsession: Beginning session setup...
No matching visual for _GLcontextMode with visual class = 4,nplanes
Could not init font path element /usr/lib/X11/fonts/TTF/, rm from list.
/usr/bin/startxgl.sh: line2: 6141 Killed Xgl -fullscreen :1 .....
***       ***

](*,) It wasn't until afterwards did I realize I don't have a nVidia card. Ubuntu is running on my labtop which has a VGA compatible controller: S3 Inc. 86c270-294 Savage/IX-MV (rev 13) Do I have any chance of running Beryl with it? Any suggestions? 

I have just seen Beryl for the first time on a friend's PC and my tougne fell to the floor.

---

### Post by handband2 on 2006-10-25
> **ldvader said:**
> I followed your steps to the "T" and got Beryl installed. The RED gem is present on my desktop, but I think Beryl is defaulting to Metacity. CTRL-ALT-Left or Right not doing anything. When I reboot and switch session to XGL, I get the following Error:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. "

***DETAILS***
/etc/gdm/PreSession/Default: Registering your session with wtmp....
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w .....
/etc/gdm/Xsession: Beginning session setup...
No matching visual for _GLcontextMode with visual class = 4,nplanes
Could not init font path element /usr/lib/X11/fonts/TTF/, rm from list.
/usr/bin/startxgl.sh: line2: 6141 Killed Xgl -fullscreen :1 .....
***       ***

](*,) It wasn't until afterwards did I realize I don't have a nVidia card. Ubuntu is running on my labtop which has a VGA compatible controller: S3 Inc. 86c270-294 Savage/IX-MV (rev 13) Do I have any chance of running Beryl with it? Any suggestions? 

I have just seen Beryl for the first time on a friend's PC and my tougne fell to the floor.

ldvader,

Here are a couple sites which will answer your question about your graphic chipset:
[http://www.freesoftwaremagazine.com/node/1797]("http://www.freesoftwaremagazine.com/node/1797")
[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL")
[http://en.opensuse.org/Xgl#Hardware_Advisory]("http://en.opensuse.org/Xgl#Hardware_Advisory")

---

### Post by sumithar on 2006-10-27
Thanks.  These directions worked for me.  I have a relatively slow machine, AMD Sempron 1.54GHz and only 768MB RAM and my graphics adapter is only GEFORCE 5200 and was a bit concerned if it would work.  But work it does!

Now to play...

---

### Post by roncrump on 2006-10-28
I've got a problem. I was trying to uninstall beryl etc, so worked backwards through the instructions on the first page of this thread, and have made a mess. More details are [here]("http://ubuntuforums.org/showthread.php?t=286718").

Sorry for cross-posting, but I wasn't sure whether this very big thread was the appropriate place to ask my question, so I started a new thread.

I may well get a response over there, in time, but I am impatient as I wanted to get this sorted before making the jump to Edgy.

Thanks,
Ron

---

### Post by Mangamaniac on 2006-10-31
Hello!
I'm new here and I have the same problem as some people before me: 

```

$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

``` 

I have also tried to start beryl diectly through beryl-manager but it keeps falling back to compiz. 
What else can I do?

with kind regards Mangamaniac

---

### Post by DJ Wings on 2006-10-31
I'm trying Beryl on Xubuntu Dapper, and whenever I try to start Xgl, it says:
> 
Fatal server error:
no GLX visuals available

Advice? My xorg.conf doesn't have dri or GLCore loaded, but it does have GLX.
EDIT: I'm using an NVidia GeForce 5200FX.

---

### Post by BrunoMartin on 2006-11-15
> **lammer said:**
> Hehehe ;) I think that there is still hope, even if this morning I was in a "Wallmart-like" shop, reading all the specs of several video cards...



On that list, my card is the very first of Nvidia cards, so maybe someone has get it work...



Hey, thanks for the link. I think I have another reason to spend time with this dammed card... You know what? This morning I have also get a new (and expensive) computer chair, so I think that this afternoon will be loooooong :rolleyes: 

Thanks for all handband2!

Hi Lammer,

Just like you, I have tried a lot to configure beryl on RIVA TNT2 Model 64/Model 64 Pro. I follow all your step and I'm having the same error.

In my case, I can't buy a new one, so I have to make it work anyway.

Some points that maybe you didn't note:

The legacy driver doesn't support the 
Option         "AddARGBGLXVisuals" "true" 
in xorg.conf. See [http://download.nvidia.com/XFree86/Linux-x86/1.0-7184/README/readme.txt](http://download.nvidia.com/XFree86/Linux-x86/1.0-7184/README/readme.txt) 
for the available options in xorg.conf for the 7184 driver (legacy).
You can note this seeing de xorg log file on /var/log/

I wont post my steps because they are the same as lammer did.
When I turn on beryl manager (by gdm session), whitout beryl-manager, I have problems whit mouse pointer (it disturbs the image when it changes, like in menus). When I turn the beryl-manager on, the windows border disappears (no window manager loaded, I think) 

[http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL) is the only place I see someone saying that is possible to make my  RIVA TNT2 Model 64/Model 64 Pro work on beryl. 

well, please let me know if have success.

If Anyone find some use case of success using RIVA TNT2 Model 64/Model 64 Pro, pleeeeeeeeeeeeeeeeese, let me known.

Thanks,

Bruno Martin
From Brazil

---

### Post by Aeolian on 2006-11-17
> **abu3abdalla said:**
> hi 
i am facing a big problem couse when i set xorg.conf to Nvidia insted of the defult " i810" the laptop cant log in GUI and tell me that thier is an error 
but when i am use the " i810 " i can log in but without 3D desktop and when i am update the system is give me : 

abu3abdalla@abu3abdalla-laptop:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  libwnck18 xserver-xgl
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

so i do not know what can i do ?????????


please tell me please :confused:

I have the same annoying problem.... Nonone with an answer?

---

### Post by ittiam on 2006-11-17
Hi,

I installed berly and whenever i try to start the beryl i see the beryl's splash screen but after that it automatically logs me out of this session and brings me back to the login screen. I tried running beryl-xgl etc. everything has the same behaviour. Has anyone got ideas? Have been stuck with beryl for too long.
](*,)

---

### Post by HoMe_CaNiBaL on 2006-11-17
someone have tried Beryl 0.1.3 (released today) at [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) ???

i have problems with that release...no windows borders...

hugs

---

### Post by jdarvwill on 2006-11-21
same here! fustrating :)


> **ittiam said:**
> Hi,

I installed berly and whenever i try to start the beryl i see the beryl's splash screen but after that it automatically logs me out of this session and brings me back to the login screen. I tried running beryl-xgl etc. everything has the same behaviour. Has anyone got ideas? Have been stuck with beryl for too long.
](*,)

---

### Post by ojasvi rajpal on 2006-11-25
Hey I did exactly as you told me to but when I start Beryl manager It says 

" XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
"
](*,) 
and I have xgl installed is it that I have a newer version of XGl or what. Plz Help

---

### Post by misterjo on 2006-11-27
OK again i have also that problem of :

```

$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

```

Could it be because of my geforce 7900GS card in my laptop?
i checked the nvidia unix page and i didn't see support for the 7900GS card...

But i can play 3d games like tuxracer and others with a good fps and no lag... (installed the latest stable nvidia driver , maybe i should install a beta driver?

greetz,
       misterjo

---

### Post by PartisanEntity on 2006-12-08
Hello,

Someone on the Beryl forum told me that if I have an Nvidia card with **TurboCache** I would need to use Beryl with **AIGLX** (apparently to avoid black windows issues), can anyone confirm this?

Or, to put it differently, has anyone with a **TurboCache** enabled Nvidia card used this How To successfully? 

My graphics card is a Nvidia Go 6200.

Thanks

---

### Post by drjnet on 2006-12-10
> **heisters said:**
> Hmmm... doesn't quite work for me. Beryl falls back to Metacity. When I run beryl from the commandline I get:

```

$ beryl --replace
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
$

```

The [edgy/beryl thread](http://www.ubuntuforums.org/showthread.php?t=263851) has repos for some hacked kernel modules, perhaps dapper needs something equivalent? Anyway, :(
did you ever solve this problem dude? If so how... i need beryl badly!

---

### Post by mustang on 2006-12-17
Thank you very much for this guide. I am using a Geforce Ti200 and everything seems to work fine.

Although I did encounter the flickering windows issue which I remedied by adding "emerald" to the startup programs list.

---

### Post by diablostereo on 2007-01-07
I have a problem... I did all that's wrote in this guide but when i boot up my pc after the gdm startup i see X for one second and it crashes... so i do startx and it runs.. but without xgl and with beryl...what's appened?

---

### Post by dreadhead90 on 2007-01-09
> **drjnet said:**
> did you ever solve this problem dude? If so how... i need beryl badly!

i also have this problem...

---

### Post by dreadhead90 on 2007-01-09
hmmm... mine is working now :S

i just did some other stuff, and then rebooted, and it workt :S

---

### Post by dabl on 2007-01-09
I have Kubuntu Edgy, nVidia 7900GS and Intel Core 2 Extreme on Intel motherboard.  I have Beryl semi-working, but the window decorations aren't working correctly and some of the menu items on the Beryl settings manager are grayed out.  Here is the response from the console when I run Beryl:


> desktop:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

** (process:6368 WARNING **: get_setting_is_integrated not found in backend ini

** (process:6368 WARNING **: get_setting_is_read_only not found in backend ini

** (process:6368 WARNING **: get_setting_is_integrated not found in backend ini

** (process:6368 WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
Reloading all options.


I searched for this error both here and at Kubuntu, but can't find a prior example.   Ideas?

---

### Post by natetoshiba on 2007-01-11
didnt work, and now i cant boot,  im xp atm..

Everything seemed to go nice, after the instalation of beryl i could see it in the menu, so i rebooted like yuo said and now i get suck at the kubutu loading screen, it loads everything, the one withthe blue line, after that it goes to the same thing and nothing happens, whats the deal, is there away to boot in -v like osx so i can see where its stuck? this shits me, its the 3rd time, so now i have to re-install, re-update all over again..

does it matter i use the envy script for the drivers? it was all recongnised..

pc specs

Toshiba Satellite p100
intel duo 2ghz
2gb ram
nvidia 7900 512mb
ect..

---

### Post by ashmew2 on 2007-02-01
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```
I added that to the file :  /etc/gdm/gdm.conf-custom 
and i followed all of the other options , but when i rebooted , X could not start so i used the backup of the old untouched gdm.conf-custom (Luckily , i had backed it up) and then i started gdm and it works. The beryl icon is showing in the task bar but nothing is working and in WIndow Managers it shows : Compiz , Beryl , Compiz with Cow , Metacity
How do i remove Compiz and Compiz with Cow from that list and how do i get the features of Beryl ?!? Please tell me!!

---

### Post by PartisanEntity on 2007-02-01
These working for anyone: ?

> deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

---

### Post by ashmew2 on 2007-02-01
> **PartisanEntity said:**
> These working for anyone: ?

yeah it worked

---

### Post by SentientFluid on 2007-04-08
When I followed the steps and tried running sudo aptitude update I kept getting an error saying I didn't have the public key.  Running the following in Terminal solved it:

```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

May want to consider adding it to your instructions. :)

---

### Post by JawsThemeSwimming428 on 2007-04-17
I severely messed something up with the instructions. When I completed the steps I rebooted and came up with a bunch of errors with XGL (I think). Eventually I got to a command prompt and edited the files back to what they were originally. Is there maybe a more detailed guide on how to install beryl. I just want to get some themes going here! Thanks for your help.

---

### Post by KrIaXPaTaLa on 2007-05-03
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main aiglx

These dont work anymore I assume :\

Any other place to get beryl for dapper?

Regards.

KrIaX, Portugal

---

### Post by nooga on 2007-06-11
As above. Those repos doen't work. :(

---

### Post by Drpwn on 2007-06-18
Do these repositories require an hget key? I get this error after trying to install beryl and the lib files:
```
W: GPG error: http://media.blutkind.org dapper Release: **The following signatures  couldn't be verified because the public key is not availabl**e: NO_PUBKEY 31A5F97 FED8A569E
W: GPG error: http://mirror.ubuntulinux.nl dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBK EY 49A120FD1135D466
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/universe Packag es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-am d64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/multiverse Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binar y-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files** failed to download**, they have been ignored, or old ones used  instead.

```
I tried to proceed without those and I got this:
```
josh@josh-laptop:~$ sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
**E: Couldn't find package beryl**

```

after adding the deb's from this tutorial I also cannot update my system. I try to update and it can't locate this file
```
W: Failed to fetch http://media.blutkind.org/xgl/pool/main/libw/libwnck/libwnck-common_2.14.2-0ubuntu2_all.deb
  404 Not Found



```

[COLOR="SeaGreen"]After reading the thread I see those repos won't help me. Is there another place we can check?[/COLOR]

---

### Post by kablooee87 on 2007-08-25
hi, I'm having a problem going through this howto:

when i try to do sudo apt-get update after I have edited the sources.list file...it is unable to download all of the packages from the sources you provided. The error it gives me go along the lines of:

Err [http://www.beerorkid.com/dapper/main](http://www.beerorkid.com/dapper/main) Packages
    Bad header line
Err [http://www.beerorkid.com/dapperaiglx](http://www.beerorkid.com/dapperaiglx) Packages
    Bad header line
Err [http://www.beerorkid.com/dapper/main](http://www.beerorkid.com/dapper/main) Packages
    404 not found
Err [http://www.beerorkid.com/dapperaiglx](http://www.beerorkid.com/dapperaiglx) Packages
    404 not found


Then, when I try to install, the message I get is "Package libgl1-mesa is not available, but is referred to by another package. This may mean that the package is missing, has been obsolete, or is only available from another source."

Not exactly where to go from there....

---

### Post by forsen on 2007-09-22
I have the same problem as the people above. Those repos doesnt work. Any work around it?

---

### Post by tboandfshady on 2007-10-05
umm... im new and i get it wrong wen i edit the script all the time :(plz can u 
copy ur script so i can just use urs and aand del mine:)thanks i new ive just been using ubuntu umm for 4 days

---

### Post by tboandfshady on 2007-10-05
plz can i have r script code coz i dunno were to put the script so just lemmie copy and paste ur  1and dell mine???

---

### Post by SoftwareExplorer on 2008-05-11
I am having a problem: when i add the repositories to the sources.lst file and apt-get update I get 404 not found errors for beerorkid and it won't connect to media.blutkind.org. Is there a newer place that I should put it? I have hardy Heron by the way. Thanks in advance.

---

