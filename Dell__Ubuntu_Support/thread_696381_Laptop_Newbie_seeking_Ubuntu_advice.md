---
title: "Laptop Newbie seeking Ubuntu advice"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by Beloch on 2008-02-13
Greetings!  I've lurked for a bit, but this is my first time posting here.  I'm not new to Ubuntu, but I've never actually owned a laptop before.  I just ordered a Dell m1330 since the hardware appears to be well supported, and I'm too excited to just wait for it to arrive so I can start messing around!  As such, I'm hoping the members of this forum can offer a little advice.  If all goes well, this thread might be useful for others in a similar boat as me.  (i.e. Laptop newbies)  As such, I'll be gathering in links that might be obvious to many just to have them in one place.  
[LIST=1]
[*]First off, the installation.  Dell has made an Ubuntu installation image for the m1330 available, which can be found [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO").  [This thread]("http://ubuntuforums.org/showthread.php?t=653627") seems to indicate that the pre-installed version of Ubuntu, and hence, the images, don't install any special software.  Just all the required drivers, proprietary or not.  As such, I am currently leaning towards doing a fresh install with standard images.  Does this assessment ring true? 

[*]Now, I do prefer KDE to gnome (Please, let's leave it at that!) so I was planning to install Kubuntu.  Does Kubuntu have any laptop deficiencies or quirks I should be aware of?  Would I be better off installing KDE on top of Ubuntu?  Is my irrational KDE preference going to cause me grief in the laptop world no matter what I do?  

[*]What are the must-have utilities, applications, etc. for laptop linux?  e.g. [This wiki page]("https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330") suggests a few apps, such as powertop, that might be important to extend battery life, reduce fan noise, etc..
[/LIST]

That's all for now, although I'll probably think of more questions later...

---

### Post by Beloch on 2008-02-14
Well... That didn't take long.  More questions! 
[LIST=1]
[*]How well do the capacitive media buttons work of the m1330 work by default?  What's the easiest way to customize their behavior?  (You can tell the suspense is killing me.  I could really save a lot of time by just forgetting all this until the laptop arrives and I can just try things out.)  

[*]How about the various other switches, knobs, bells and whistles on this new-fangled lap-top dee-vice?  Will buttons for sending output to a projector, disabling wireless, etc. all work irregardless of the OS, or does the OS have to be configured to work with them properly?  

[*]The fingerprint reader (another first for me) reportedly works with [ThinkFinger]("https://wiki.ubuntu.com/ThinkFinger").  If I understand correctly, that just provides driver support, and you have to use something like [PAM]("http://www.kernel.org/pub/linux/libs/pam/modules.html")?    I haven't really dug into that yet, but I like the idea of being able to log in with a finger swipe and have different apps pop up depending on the finger you use...  Am I on the right track for that?

[*]I ordered a Bluetooth chip and a Bluetooth travel mouse.  Will switching back and forth between it and the pad work by default?  

[*]The m1330 has areas on it's track-pad that do scrolling.  (I tried this out on a demo unit at a Dell kiosk)  This seemed like a spiffy feature.  What is necessary for it to work in Ubuntu?

[*]I read somewhere that the m1330's slot-loading DVD drive is rather noisy when trying to suck in a disk, which it tries to do on booting.  You can apparently quiet that down by just leaving a disc in it at all times.  Is there a better way to avoid embarrassing yourself when you start your laptop?  i.e. Will just taking it out of the boot-sequence in the BIOS work?
 [/LIST]

---

### Post by natehall on 2008-02-14
My 1420N was my first Linux machine. I've since loaded Ubuntu on an old HP Paviillion and I've yet to notice any differances. (I hear the scrollpad has some extra settings but  I always l plug in a mouse so I don't care.) Since I've messed with the power settings I've had some issues shutting down in my fresh Dell DVD Gutsy install , so perhaps KDE will work better on that score.

---

### Post by Beloch on 2008-02-16
A couple more...  

[LIST=1]
[*]I expect running Compiz with all the bells and whistles will suck more power and reduce battery life since the Nvidia 8400M will be stuck in 3D mode.  How much of an impact will this have on battery life?  

[*]Is there an easy way to set up two profiles that have the same browser history, files, etc. but different Compiz settings, etc.?  i.e. High and low power profiles?
[/LIST]

---

### Post by natehall on 2008-02-16
I'm not sure what files store those histories but you can always use [B[]chmod]("http://www.linuxcommand.org/lts0070.php#chmod")[/B] to let a common group have access  to any particular file.

---

### Post by Qray on 2008-02-17
> 
Now, I do prefer KDE to gnome (Please, let's leave it at that!) so I was planning to install Kubuntu.  Does Kubuntu have any laptop deficiencies or quirks I should be aware of?  Would I be better off installing KDE on top of Ubuntu?  Is my irrational KDE preference going to cause me grief in the laptop world no matter what I do?  


I have a Inspiron 6400 which was delivered with Ubuntu.  Since I use KDE at work (no Gnome avail. there), I wanted to use it on my laptop too and just installed KDE in addition. Till now no problems with it (started with feisty and upgraded to gutsy), except not working Brightnessup/down after the upgrade. But that could be fixed partially and does not seem to be a special KDE problem.
So from my experience KDE works as well as Gnome.

> 
Will buttons for sending output to a projector, disabling wireless, etc. all work irregardless of the OS, or does the OS have to be configured to work with them properly?


The button for the projector does not work properly for me, but I dont need it usually. Just attach the projector and switch to a appropriate screen resolution (the tool krandrtray is very usefull for that! I usually use 1024x768 ). Then for me automatically it works without any switching.
Only a few projectors make a bit trouble(artefacts in the picture), but after they are connected a quick restart of X helps with them.

All other buttons (except  Brightnessup/down, see above) worked out of the box.

> 
I expect running Compiz with all the bells and whistles will suck more power and reduce battery life since the Nvidia 8400M will be stuck in 3D mode. How much of an impact will this have on battery life?

The effect on battery is barely noticable as far as I could notice. But I have a built in graphic chip (intel), so I can't say for sure how it is with a real graphics card.

> 
Is there an easy way to set up two profiles that have the same browser history, files, etc. but different Compiz settings, etc.? i.e. High and low power profiles?

You can always switch by using "kwin --replace" to disable compiz and "compiz --replace" to re-enable it. So there is no real need for two profiles.

Hope this helped a bit, although my experiences are made with another laptop.

---

### Post by Beloch on 2008-02-17
Thanks for the responses guys!

[quote=Natehall]I'm not sure what files store those histories but you can always use **chmod** to let a common group have access to any particular file.[/quote]
Sharing files between two different accounts was what I was trying to avoid.  It's doable, but a hassle.


[quote=Qray]You can always switch by using "kwin --replace" to disable compiz and "compiz --replace" to re-enable it. So there is no real need for two profiles.[/quote]
Good tip.  Thanks!  Hopefully I can find a power profile manager that will let me just add those lines in if needed so it switches automatically.  If it does suck too much power, I'll probably try underclocking the 8400M first since I don't imagine compiz will need every last bit of power to run half decently. 
 
[quote=Qray]The button for the projector does not work properly for me, but I dont need it usually. Just attach the projector and switch to a appropriate screen resolution (the tool krandrtray is very usefull for that! I usually use 1024x768 ). Then for me automatically it works without any switching.
Only a few projectors make a bit trouble(artefacts in the picture), but after they are connected a quick restart of X helps with them.[/quote]

There must be some way to output a resolution different than your desktop...  A second monitor configuration or something.  I haven't really messed around with multiple monitors under Linux before.  I'll have to start I guess!  (I just don't want to be the guy who makes everyone wait while he's trying to get his laptop to work with the projector.)

---

### Post by Beloch on 2008-02-29
Well, the laptop has arrived.  I think I can answer some of my own questions, but I still have outstanding questions.

_**Outstanding**_

**Finger Print Reader**
>  The fingerprint reader (another first for me) reportedly works with ThinkFinger. If I understand correctly, that just provides driver support, and you have to use something like PAM? I haven't really dug into that yet, but I like the idea of being able to log in with a finger swipe and have different apps pop up depending on the finger you use... Am I on the right track for that?

I followed [this guide](https://wiki.ubuntu.com/ThinkFinger) to install thinkfinger.  I can use the  tf-tool commands to scan and verify prints, but changing the /etc/pam.d/common-auth did nothing.  (i.e. At no point does scanning my finger work in lieu of entering a password)

The finger print reader software in Vista lets you login with a simple finger swipe, which is very quick once you get the hang of doing it consistently.  (This may take a minute or two with the practice program.)  I think this would be a great feature...  if it worked.

I'm stuck on this one.

**Slow Graphical Performance in Compiz:**
The Nvidia 8400M chipset throttles itself *agressively* to minimize power consumption.  It will literally underclock itself to wuss-levels within seconds of being idle.  As such, Compiz runs rather herky-jerky.   If you keep doing graphically intensive stuff it's just fine, but, anytime you stop doing fancy whiz-bang effects for more than a couple seconds the 8400m throttles itself down and then you get jerks when you, for example, rotate your Compiz cube. It actually doesn't go to full speed immediately either.  It dicks around for a few seconds in 2nd-gear before getting down to business.

You can run nvidia-settings to see what's causing this.  It's powermizer.  You can watch the chipset underclock itself seconds after you stop doing stuff.  I haven't found any way to adjust any of the underclocking frequencies or even just turn powermizer off, which is pretty bloody annoying.

[This thread](http://ubuntuforums.org/archive/index.php/t-594593.html) contains a script you can use to turn off powermizer, but the wait time in it is 20 seconds, which is actually way too long.  (i.e. Powermizer will underclock the 8400m in much less time)  You may need to reduce the time.  This is a really ugly solution.  Ideally I'd like a way to configure the Nvidia settings directly.  I haven't really come across one yet.  

The .nvidia-settings-rc in your root user directory (i.e. ~/) contains a couple suggestive lines:  

```
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
.
.
.
0/GPUScaling[DFP-0]=131073
```

The first line probably just lets you turn of monitoring of powermizer, not powermizer itself, but I haven't tried messing with it.  The second line is probably totally irrelevant, but it's not totally impossible that it could do something...

Any thoughts?

**Stuck Adept Notifier Window in Compiz**
Sometimes, when I log in, an uncloseable blank black Adept Notifier window will be up.  Double click on it says there are no updates, but that's about all you can do with it.  How do I get rid of the thing?  Sometimes it doesn't show up, but it comes up with enough frequency to be annoying.

**_Partially Answered**_
**KDE vs Gnome:**
> Now, I do prefer KDE to gnome (Please, let's leave it at that!) so I was planning to install Kubuntu. Does Kubuntu have any laptop deficiencies or quirks I should be aware of? Would I be better off installing KDE on top of Ubuntu? Is my irrational KDE preference going to cause me grief in the laptop world no matter what I do?

First off, the fingerprint reader is supposed to work in gnome (I haven't confirmed this), but I haven't found a way to make it work in KDE yet.  

If you want to use the Dell images so you don't have to round up drivers, you have to install Ubuntu and then replace the desktop environment with KDE.  It's pretty easy to get to a near Kubuntu state actually.  The following will do it:

```
sudo apt-get install kubuntu-desktop
(select kdm as your window manager)
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```

There's still some gnome packages kicking around after this though.  e.g. The gnome power management app is still installed, although it doesn't run by default.  I haven't really looked into finding a list of all the gnome stuff that you have to clean out, but  autoremove certainly doesn't do it. 
 

**Various button functions:**
> How about the various other switches, knobs, bells and whistles on this new-fangled lap-top dee-vice? Will buttons for sending output to a projector, disabling wireless, etc. all work irregardless of the OS, or does the OS have to be configured to work with them properly?

The switch to disable wireless is purely in hardware and works, but I always leave it on since it also controls bluetooth, and I use a bluetooth mouse most of the time.  The Function combos (e.g. FN-up-arrow to increase monitor brightness) work by default in KDE.   I haven't tried to hook up the m1330 to a projector yet.

**Power Profiles**
> Is there an easy way to set up two profiles that have the same browser history, files, etc. but different Compiz settings, etc.? i.e. High and low power profiles?

The KDE power management utility will let you set some things that will depend on whether the laptop is plugged in or not, such as default brightness and behaviour such as suspending/hibernating when the laptop is closed or after a certain period of time.  I haven't looked into making compiz turn off automatically though.  I still think Qray's commands should work, although I haven't looked for the scripts that change power settings.  (I assume they exist somewhere...)

**_Answered:_**

**Dell Installation Images:**
> First off, the installation. Dell has made an Ubuntu installation image for the m1330 available, which can be found here. This thread seems to indicate that the pre-installed version of Ubuntu, and hence, the images, don't install any special software. Just all the required drivers, proprietary or not. As such, I am currently leaning towards doing a fresh install with standard images. Does this assessment ring true?

The images from Dell's site can be used as a live-cd the same as any other Ubuntu discs, but they do seem to include all the needed hardware packages.  It doesn't install them automatically however.  e.g. You have to install the Nvidia drivers yourself.  It can also do some kind of factory image install, but I didn't try that.

Bottom line, the Dell disks just make it easier to find some of the drivers, but you still have to install some of them.

**Noisy DVD Drive:**
> I read somewhere that the m1330's slot-loading DVD drive is rather noisy when trying to suck in a disk, which it tries to do on booting. You can apparently quiet that down by just leaving a disc in it at all times. Is there a better way to avoid embarrassing yourself when you start your laptop? i.e. Will just taking it out of the boot-sequence in the BIOS work?

Either the people writing the reviews that talk about the m1330 having an annoyingly loud DVD drive mechanism are smoking something, or later versions of this laptop are much quieter.   You can hear the drive when it attempts to suck in a disk, but it's not loud at all.  

This drive, however, does sound like a hoover when reading data discs at high speed.  (e.g. during installation)  However, it's about what you would expect from any desktop DVD drive.  There's not much you can do about this other than to limit the drive speed and put up with the slowness.  (Not worth it, IMHO)  

**Bluetooth Mouse:**
> I ordered a Bluetooth chip and a Bluetooth travel mouse. Will switching back and forth between it and the pad work by default?

No, it won't work by default.  [This howto](http://ubuntuforums.org/showthread.php?t=227057) is what you need to make it work.  (This should also work with a Bluetooth keyboard, but I don't have one to test.)

Once you do this, your Bluetooth mouse will be detected automatically and just work.  

Update:  I was wrong about the need for this hack.  KBluetooth (which will run in your KMenu by default) can actually get the BT mouse working.  The interface is just utter crap, and I didn't realize how to do it the first few times I tried.  Give it a go,  but if you get stuck just use the above hack.  The results are identical. 

**Trackpad Scrolling Regions:**
> The m1330 has areas on it's track-pad that do scrolling. (I tried this out on a demo unit at a Dell kiosk) This seemed like a spiffy feature. What is necessary for it to work in Ubuntu?

Works by default.  

**Capacitive Buttons:**
> How well do the capacitive media buttons work of the m1330 work by default? What's the easiest way to customize their behavior? (You can tell the suspense is killing me. I could really save a lot of time by just forgetting all this until the laptop arrives and I can just try things out.)

The capacitive buttons (volume, mute, eject,etc) all seem to work by default.  

**Compiz**
> I expect running Compiz with all the bells and whistles will suck more power and reduce battery life since the Nvidia 8400M will be stuck in 3D mode. How much of an impact will this have on battery life?

As I said before, to get Compiz to run smoothly we need to find a way to keep the 8400m from throttling itself so aggressively.  That means the power useage is going to be a bit higher.  However, I have no plans to run tests on this because I just don't care.  (i.e. I am rarely away from a power outlet for more than an hour.)  

I do have one tip on installing Compiz though...  You'll probably want to install the 8400m drivers using envy, but envy doesn't always (not in my case at least) enable the Nvidia proprietary driver after installing it.  You have to do that yourself.  

i.e. In the Kmenu, go to System_Settings/Advanced/Restricted_Drivers and check off the Nvidia driver.  

If you use envy to install the Nvidia drivers but do not enable them, then Compiz will not work properly.   In my case, compiz was starting, but Emerald wasn't, and I was getting no window controls.

---

### Post by oskar-swe on 2008-03-02
Thank you very much for your useful contributions. I'm still waiting for my 1330 to arrive. Did your laptop come pre-installed with vista? If so, how did you deal with media direct?

---

### Post by Beloch on 2008-03-02
Hi Oskar,
      It did indeed come with Vista.  Dell started offering ubuntu in Canada just after I ordered.  Oh well.   

As for mediadirect, I actually just got rid of it.  It didn't look like something I'd ever actually use.  Other people have apparently gotten Ubuntu to boot from the media direct button, so I might do that in the future.  Strangely enough, the mediadirect button was bound to Amarok by default in Kubuntu.

Dell was really conscientious about including backup disks of all the programs that came with this laptop.  You'll get a media-direct installation disk that you can use to restore it if needed, so you can play around without too much fear.  The Vista disk is capable of installing a fresh copy and not just restoring a factory image, which was also very nice.

---

### Post by oskar-swe on 2008-03-09
Ok,

Thank you for the information!

---

