---
title: "Mouse problems in Ubuntu 11.04 (dead zones on the screen)"
date: 2011-05-02
forum: Desktop Environments
---

### Post by dumitru on 2011-05-02
I've installed Ubuntu 11.04 and observed that I have problems with mouse. Often, while clicking or making selection in different areas the mouse doesn't respond. It has like dead zones (dead spots) on the screen. I have to mouse-scroll or touchpad-scroll several times to make it working.

I first thought that's because my mouse is discharging, because in previous 10.10 I didn't encounter this problem. But later I checked it in Windows and it works perfect.

I have Logitech wireless mouse.

---

### Post by sunshinekid on 2011-05-03
Same problem here with 11.04. It's very nerving while playing flashgames.

I use the touchpad of my Acer laptop and various mouses...

---

### Post by keltic dave on 2011-05-03
Hi I'm having the same issue when I'm browsing websites if I don't have the window full-screen there are like dead-zones which no matter how much I click on them just wont. 

It's getting a bit annoying I found though and I don't know if this is related to the issue or not by changing the theme the problem seems to get a bit better ?

---

### Post by sco on 2011-05-03
Same issue with my xps m1330 using evolution  and  when i try to double click on windows borders.

---

### Post by Eversmann on 2011-05-03
Same problem here, i didn't know where to search or how to describe the problem. That's true: dead zones, because if we have a button in there, moving the window the button goes to a place that's not dead and I can click on it.

---

### Post by keltic dave on 2011-05-03
no one with a solution or reason for the problem ? 

Does anyone get it if they run Ubuntu classic ?

---

### Post by frmdstryr on 2011-05-03
I'm having the same problem. Makes graphic editing really difficult... Anyone else having random clicking noises coming from the speakers?

---

### Post by RasH on 2011-05-03
I have the same problem both with unity and ubuntu classic. I'm not sure about this but it feels like the dead zone area is not always in the same place.

---

### Post by dfrossar on 2011-05-04
Same problem. In apps like Libre Office, parts of the editing window are dead, others are clickable. Clicking near the part of text I wish to edit, I can then use the computer's arrow keys to get to the place I wish to edit.

More difficult (in apps like Chrome) is clicking pull-down menus, acknowledgement buttons, and the like. It works or it doesn't. If it doesn't, I try to click somewhere in the window and use the Tab key to finally get to the Cancel or Okay button (where I hit the Enter key).

I'm using Gnome and Ubuntu Classic, not Unity.

An Update: I've installed Gnome3 and the problem disappeared. Make of that what you will.

---

### Post by Eversmann on 2011-05-04
One thing (i don't think it can resolve anything, but at least, it's good try).

I was in the process to make the cube work again, so i login in classic without effects. Then on ccsm, i clicked on expo and cube and, of course, the bug appeared so every option in ccsm turned off. 

I took some patience and then i clicked on every option that is needed for compiz to work properly (opengl, composite, move, static switches, expo, cube, rotate cube, grid... you know), so this way i have a compiz profile with everything enabled the way i want.

After that, i'm using my computer since i did that and i'm not noticing any dead spot around. (but i can't tell you doing that can be used as a workaround).

Give it a try if you're in the mood ;-)

---

### Post by keltic dave on 2011-05-04
took the advice of the second last post and so far so good. Gnome 3 is a definite improvement over Unity/Gnome

---

### Post by Eversmann on 2011-05-04
I read it because i'm subscribed to smspillaz blog. But looks like the bug is known and he's working hard on it.

[https://bugs.launchpad.net/unity/+bug/709461](https://bugs.launchpad.net/unity/+bug/709461)

---

### Post by keltic dave on 2011-05-05
I'll go back to unity then once it's fixed.

---

### Post by Eversmann on 2011-05-05
I added the xorg-edgers ppa and dist-upgraded from it, and after 2 hours i'm not having dead zones (and btw, i feel the desktop smoother, but you know...)

It's a good try. You can always ppa-purge it ;-)

---

### Post by fnog on 2011-05-06
> I added the xorg-edgers ppa and dist-upgraded from it, and after 2 hours i'm not having dead zones (and btw, i feel the desktop smoother, but you know...)

Very good tip! Thanks!

Made the change 3 hours ago and you know what?
No more dead zones (yet) ;-)

I can work again without this stress. (Now, I'll just have to find the solution for evolution hangups. - I regret having gone through with this upgrade so soon :-/ )

Thanks again!

Francisco Nogueira

---

### Post by ShadowKyuzo on 2011-05-06
Same problem here, im glad i found this thread, i was thinking that my new mouse was broken...

Gonna try the solutions in this thread!

---

### Post by Eversmann on 2011-05-06
You're welcome ;-)

After working all evening and part of the night, i didn't get dead zones, so looks like the bug is inside xorg (or the video driver).

If it stays this way, i'll post this in launchpad.

---

### Post by muratakbas on 2011-05-06
> **Eversmann said:**
> I added the xorg-edgers ppa and dist-upgraded from it, and after 2 hours i'm not having dead zones (and btw, i feel the desktop smoother, but you know...)

It's a good try. You can always ppa-purge it ;-)

It's work for me.
Thanks a lot..

---

### Post by ShadowKyuzo on 2011-05-06
xorg-edgers didn't work for me, i had to purge it and reinstall my driver's card to be able to boot again :(
I must have done something wrong...

I think i'll try installing Gnome3 later...

---

### Post by ricsi-pontaz on 2011-05-06
Launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/741112](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/741112)

Screencast: [https://launchpadlibrarian.net/71145309/deadzone.mpg](https://launchpadlibrarian.net/71145309/deadzone.mpg)

---

### Post by keltic dave on 2011-05-06
just thought I would say that so far using that ppa is working thanks man. 

I had to reformat back to unity as there is no way of downgraded gnome :P but it's worth it. definite improvement.

---

### Post by CallsignBaron on 2011-05-07
I had this same problem as well. FWIW, removing xserver-xorg-video-nouveau seems to have done the trick for me so far. Been about an hour or so and no dead spots yet. If anyone else tries this and it works, please post back. This xserver is marked experimental in synaptic, don't know why it was included in my default Natty install. I don't think it's completely stable.

---

### Post by behrouz.seyedi on 2011-05-09
same problem here! it is ... ](*,)

---

### Post by cliffemu on 2011-05-09
autoremove xserver-xorg-video-nouveau
and a restart worked for me.  No stuck/dead mouse issues in firefox4 since.  I'm not sure the consequence of removing that, though :)

---

### Post by zm_caglar on 2011-05-09
&#305; have a problem .. &#305; download compiz fasion..and &#305; change something..when &#305; change something on compiz then &#305; can not see my toolbar on my desktop .there is nobody on my desktop.because of that &#305; can not firefoñ , command screen ... ect. 
please help me..

---

### Post by keltic dave on 2011-05-09
maybe once again in English I have no idea what you're saying

---

### Post by sdgreen on 2011-05-10
Same here. I am convinced 11.04 needs more work. I have it working but with many issues with the Desktop UI.

---

### Post by zarbam on 2011-05-12
> **cliffemu said:**
> autoremove xserver-xorg-video-nouveau
and a restart worked for me.  No stuck/dead mouse issues in firefox4 since.  I'm not sure the consequence of removing that, though :)
\\didnt work here

---

### Post by keltic dave on 2011-05-12
> **Eversmann said:**
> I added the xorg-edgers ppa and dist-upgraded from it, and after 2 hours i'm not having dead zones (and btw, i feel the desktop smoother, but you know...)

It's a good try. You can always ppa-purge it ;-)

This solves the issue just fine.

---

### Post by humanisfood on 2011-05-12
> **keltic dave said:**
> This solves the issue just fine.
worked for me too.

---

### Post by danielelias22 on 2011-05-15
> **keltic dave said:**
> This solves the issue just fine.

How you did that, this is my second day in Ubuntu, i am very noob.
Can you help me?

Regards and thank you for your time

Daniel

---

### Post by magicalplug on 2011-05-15
sudo apt-get autoremove xserver-xorg-video-nouveau

in the Terminal seems to have fixed the problem for me.

Was most evident in dialogue boxes and in unresponsive hyperlinks in Google Chrome. A few hours in and it seems ok thus far, hasn't happened yet. Will report back if the problem reappears.

---

### Post by xtknight on 2011-05-16
Wow, I'm not the only one with this problem? I thought I was nuts.

One time I looked at my desktop (it might have been after some everyday catastrophe like gnome-settings-daemon or the window decorator crashed and spilled its guts) and there actually were small white boxes. I'm about 99.999999% sure that those boxes were the regions I couldn't click, and suspected it was application windows that weren't getting freed.

It might have something to do with apps like Eclipse that create windows spontaneously (like for Intellisense/autocomplete method lists) and then somehow those don't get destroyed.

I'm going to install GNOME 3. Let's see how badly I regret this.

Let's find a way to tag the original post with some other helpful keywords. I was lucky to have picked "dead zones" as my vocabulary when Googling this problem. Other possible tags might be "natty click problems", "natty unclickable".......hope this helps someone.

---

### Post by magicalplug on 2011-05-16
It's a bit of a crap bug :)

Anyway, I've been going strong for over a day now without any problems reoccuring, so the:

sudo apt-get autoremove xserver-xorg-video-nouveau

terminal command I posted fixed it for me! On a side note, besides this bug, Natty has been awesome for me. My M-Audio 2496 works out the box properly, unlike in Maverick, and the whole thing seems a lot more polished and enjoyable through Unity. Roll on the Oneiric Ocelot! :D

---

### Post by BugA_ on 2011-05-17
```
sudo apt-get autoremove xserver-xorg-video-nouveau
```A true life saver :D I was getting really annoyed with being unable to click where I needed to, and when I needed, but luckily it looks like that one fixed the problem. So far so good, thanks :)

EDIT: Not fixed after all... :( I`ll reboot and see if it helps.

---

### Post by teachop on 2011-05-17
This just started happening to me too, took a while to realize what was going on.  I first noticed the zones because they eat the mouse scroll wheel events.

I have Intel integrated graphics on this laptop.  You folks that are autoremoving xserver-xorg-video-nouveau, do you have nVidia video hardware? 

Man is this an annoying bug.

---

### Post by BugA_ on 2011-05-18
I have ATI (Mobility Radeon 5650), and it looks like this helped in the end. I won`t say that it solved the problem for good, but now it is much better. For example, when I used to edit something in gedit before, there were spots on the screen on which mouse cursor would change to normal arrow cursor (instead of text editing one) and clicking just wouldn`t work - luckily, this doesn`t happen any more :)

---

### Post by teachop on 2011-05-19
There is a request on this bug:
[https://bugs.launchpad.net/unity/+bug/709461]("https://bugs.launchpad.net/unity/+bug/709461")

For help in being able to reproduce the problem, so they can get it debugged and fixed.  So if you can get to a repeatable way to trigger this, follow the link and try to help them out.

---

### Post by Podex on 2011-05-19
> **Eversmann said:**
> I read it because i'm subscribed to smspillaz blog. But looks like the bug is known and he's working hard on it.

[https://bugs.launchpad.net/unity/+bug/709461](https://bugs.launchpad.net/unity/+bug/709461)

It's funny. I was going to click this link, but a dead zone appeared on it... :S

This bug is happening on my Intel laptop right now also. First it just happened on my Nvidia desktop computer. I did have xserver-xorg-video-nouveau installed on my laptop too strangely enough. I have autoremoved it and will see if that fixes my problem.

---

### Post by just_fancy on 2011-05-20
:confused: I have the same problem...
Anyone help?

---

### Post by magicalplug on 2011-05-20
It's still happening for me, despite my message earlier.

I find if I reboot, and then only use my installed applications, its much less likely to come back. It seems to start happening more frequently in sessions where I'm tweaking things, or installing things in the Software Centre.

Going to use my machine all day and only use installed software, and not do anything 'system related' and see if it still happens...

Hope this gets nailed soon, it's highly annoying!

---

### Post by teachop on 2011-05-20
> **magicalplug said:**
> It seems to start happening more frequently in sessions where I'm tweaking things
I was suspecting this as well.  Ubuntu seems very fragile at this stage to even looking sideways on Compiz settings.

The first day I noticed the dead zone, I had been assigning a spare mouse button to a window management function in CCSM.  But I cannot repeat that, so it may be coincidence.

We need to find a reproducible way to cause this, so they can debug it.

---

### Post by magicalplug on 2011-05-21
Used for over 12 hours without any symptoms.
Didn't do anything technical during this time, simply used already installed programs. Didn't even go into the Control Centre.

There's something that triggers it by messing with the system configuration somewhere it seems. Hopefully it will come to light soon exactly what that is, so the bug can be easily reproduced and then quashed :)

---

### Post by jacklsw2008 on 2011-05-21
i encounter this issue of my mouse's primary click not working out of sudden. it happens at random but when it does, only the primary click is not working while scrolling wheel and secondary click are still ok. heck, are they even working on the stability in release after release? i kinda feel that ubuntu is getting worse.

---

### Post by darinmiller on 2011-05-22
This does not work:
```
sudo apt-get autoremove xserver-xorg-video-nouveau
```

(it does remove Compiz Setting manager though, :()


Restarting Compiz does fix it implying Compiz may have a role:

```
metacity --replace &
compiz --replace &
```

or in a script:

```
#!/bin/sh
# compiz toggle
pid=`ps -A | grep compiz | nawk '{print $1}'`
if [ $pid ]; then
	metacity --replace &
	# Sometimes compiz does not die...
	pid=`ps -A | grep compiz | nawk '{print $1}'`
	if [ $pid ]; then
		kill -9 $pid &
	fi
	cz=1
 else
	compiz --replace &	
fi
```

---

### Post by d0ti5 on 2011-05-24
I don't have the dead spot issue - but my mouse has lost his mind.  I click once, get two or three clicks.  I can not drag things around - like windows, or when highlighting text or selecting a portion of an image.  

I also get the clicking in the speakers - sometimes it overwhelms the sound.

I am running an AMD 64bit Phenom triple-core, running the 64 bit 11.04, everything is up-to-date.  I also have Logitech, albeit wired, trackball mouse.

This is driving me nuts.  (Granted, short trip, that...)

---

### Post by magicalplug on 2011-05-25
Apparently the problem is with the 'Static Application Switcher' in Compiz. If you use CCSM to untick that plugin, the problem should go away.

Of course you lose Alt-Tab, but there are enough alternatives to swap between applications, especially the All Window picker (ALT+SHIFT+Up).

Hopefully now it's been narrowed down, it can be fixed anyway...

---

### Post by andersgb1 on 2011-05-25
> **magicalplug said:**
> Apparently the problem is with the 'Static Application Switcher' in Compiz. If you use CCSM to untick that plugin, the problem should go away.


Do you have an URL for the bug?

---

### Post by magicalplug on 2011-05-25
I got the information from here:

[https://bugs.launchpad.net/ubuntu/natty/+source/unity/+bug/709461](https://bugs.launchpad.net/ubuntu/natty/+source/unity/+bug/709461)

---

### Post by andersgb1 on 2011-05-25
Thanks

---

### Post by smcrossman on 2011-05-30
Hmmm...I thought it was a problem with FF 4/ Flash upgrades and my damned 64 bit setup!  Gaming has been torturous....been looking at other browsers!  I'll try the application switcher and see if that helps....I suppose I can always program a hot key command or such for the Alt+Tab since that is like breathing to me after years of Windows multitasking!  I know it isn't installed on my netbook (which I'm on now) and it's been driving me crazy today...especially since I'm still trying to work kinks out of desktop environment with Unity....

Glad it wasn't another Logitech driver issue....one is more than enough!

---

### Post by kojl on 2011-06-05
*autoremove xserver-xorg-video-nouveau*
worked fine for me! :KS

---

### Post by grekhss on 2011-06-29
It seems that I have the same problem with the mouse on Ubuntu Classic. The following actions worked for me:
1) uninstall xserver-xorg-input-all, xserver-xorg-input-mouse, xserver-xorg-input-vmmouse, xserver-xorg-video-nouveau
2) reboot
3) install xserver-xorg-input-all, xserver-xorg-input-mouse, xserver-xorg-input-vmmouse
4) reboot

Somewhere between 1 and 3 I have installed xfce4, but I don't think that it influenced anything, since mouse also did not work properly for this desktop.

UPDATE.
Sorry, guys, it did not work for second time. Maybe I did something else - I do not remember.

---

### Post by thexder31 on 2011-06-30
Awesome catch people!  It already appears to be better.  This has been severely irritating.  Actually, I find just about anything having to do with compiz to be rather irritating (nice when it works, but at a lower stability level I have come to expect).  yea, yea, if I want stability I should be on the LTS releases.

Am using Classic (god I hate the new UI).

Anyways, thanks!

Linux UbuntuLab02 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

---

### Post by grekhss on 2011-07-04
Installed xubuntu after a number of attempts to fix this mouse trouble. =)

---

### Post by LordDelta on 2011-07-11
I don't know that this is the same issue, but occasionally I get VERY erratic behavior with the mouse (since 11.04).

I'll end up clicking through to other apps, perhaps this is the deadzones behavior people've been talking about?

Also the mouse is just un-cooperative in general, it sometimes requires me to click twice to perform a single click, or when dragging it randomly "releases" the pointer.

I guess I'll uninstall nouveau, see if that makes any difference.

EDIT: Doesn't seem like it fixed sqat...

---

### Post by Paper Bag on 2011-07-19
It is/was an issue with the Static Application Switcher. Was fixed in compiz - 1:0.9.4+bzr20110606-0ubuntu1~natty1.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/789580](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/789580)

In the description there is an easy way to reproduce it.

---

### Post by hannon on 2011-07-24
Not sure if this helps anyone but I'm only having these mouse click issues with 32-bit machines, I don't know if it's a 32 vs 64 bit issue in general or it just happens to be my particular hardware. I was wondering if anyone else has had similar experiences? I tried all the fixes previously mentioned with no luck. I tried 10.04 and 11.04, I've tried Xubuntu, Kubuntu and Gnome 3 with the same disappointing results, so I guess it's back to windows on these machines until a fix is in, or this could be a good excuse to try out something else for a while.

---

### Post by jivanyatra on 2011-07-31
I've been having this issue with 64-bit as well, not just in 32-bit.

For anyone who's too lazy to visit the bug tracker page ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/789580]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/789580")), the solution is in enabling the "proposed" updates.

Applications > Ubuntu Software Center.

Edit > Software Sources...

Updates > Check the box next to "proposed"

Compiz should update and things should be fixed. I'm not sure if this needs to be done, or if the fix trickled into the normal updates yet. This worked for me.

---

### Post by hannon on 2011-07-31
> **jivanyatra said:**
> I've been having this issue with 64-bit as well, not just in 32-bit.

For anyone who's too lazy to visit the bug tracker page ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/789580]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/789580")), the solution is in enabling the "proposed" updates.

Applications > Ubuntu Software Center.

Edit > Software Sources...

Updates > Check the box next to "proposed"

Compiz should update and things should be fixed. I'm not sure if this needs to be done, or if the fix trickled into the normal updates yet. This worked for me.

I'm no expert but I think it has to do with xorg configs and drivers in my case, some people say compiz, some say nouveau video driver and it may be all or none of them

Here's what I did to correct this problem:

1) I ran 'sudo lshw' in a terminal and read through the output to see what driver my video was calling for, in my case it was intel i815

2) I installed this package to make sure the right driver was in the system(which wasn't): xserver-xorg-video-intel

3) I checked to make sure it was running that driver and it was still running the nouveau driver 

4) After googleing all morning and reading through a bunch of wikis and forums, I came to believe the newer versions of xorg in ubuntu are setup to configure inputs and outputs automagically. It was then that I learned if I wanted a custom configuration I would have to create a file named xorg.conf in /etc/X11 with this text:

# Minimal xorg.conf for the intel driver

Section "Device"
	Identifier	"Default screen"
      	Driver		"intel"
EndSection


5) reboot and same problem but I knew the video driver has been ruled out (I heard that the video driver can cause issues like this but that's beyond my knowledge), it did how ever behave a little differently while booting so I know it did something. 

6) I unistalled compiz and rebooted, it still didn't work but one more thing ruled out

7) I made sure these packages were installed and reinstalled them:
xserver-xorg-input-synaptics
xserver-xorg-input-evdev
xserver-xorg-input-mouse

8) Reboot and still nothing but yet again one more thing ruled out(lol, I just previewed the post and my eight is an emocon, I'm so easily amused) 

9) I found a package called xserver-xorg-video-geode checked off in synaptic package manager, it said it had something to do with video input features so I marked it for removal(I'm not sure if it was even being used). Now here's were I went wrong, I lost my patients and uninstalled at second package at the same time(makes it harder to narrow down) called xserver-xorg-input-all, I think this may have something to do with the automagic setup but I don't really know.

10) Reboot and it worked perfectly, I rebooted several more times and tried just about every app, copied and pasted, clicked on textboxes, right and left clicked, ran several browsers and tested every icon in my tool bars. I used this machine all afternoon so far with no clicking problems at all. 

Now if I had to try this again I would start at step ten and I wish the second machine I had with this problem would be a good test to my meddling with drivers and X but it's identical(they were on sale,lol) and I just followed the same procedure and they both work. Maybe this may help someone or not but it got two of our laptops clicking away again

---

### Post by Paper Bag on 2011-08-02
Actually (also related to hannon's post above) there were at least two bug reports (I think it was this one: [709461]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/709461")) and they were unrelated but the problem was similar, so much that the bug reports got mixed up. In the bug report which I and you linked ([789580]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/789580")) there is an extremely easy way to reproduce it. If you can reproduce it that way, then updating Compiz (to 1:0.9.4+bzr20110606) will fix it.

---

### Post by Shekoufa on 2011-08-18
My problem is being just temporarily solved by running "compiz --replace" every time it happens! Actually it's not a complete workaround yet it solves this problem whenever I face it, until the problem comes back to life again!! :S And I tell you, for a programmer, working in an IDE, it's the most annoying bug! I hope there is a better solution to solve it!

---

### Post by exedzy on 2011-08-26
I found a solution, atleast it worked for me..

Open System => preferences => Startup Applications and add this command

```

gnome-panel --replace

```

Hope this helps someone :)

---

