---
title: "Is xfce really this unstable?"
date: 2014-08-14
forum: Desktop Environments
---

### Post by WB0HYQ on 2014-08-14
I've been giving xfce a chance as my desktop for a few days now (on 14.04) and have found that I like it very much but it seems very unstable to me.  I have a thread concerning the constant crashing of the Notification Area on the Panel so I won't get into that here.  Other things are now coming to the front.

1) No matter how small I make the desktop icons (they are now down to 10x10) in order to move them around on the desktop, xcfe provides an orange box to put them in.  However, this orange box is a HUGE box that runs 2 1/2 inches on a side, which, at my resolution of 1600x900 still only leave me a 5x4 matrix.  This is hardly sufficient enough to host more than 20 icons -- and I have around 35 I want to display.

2) I was intrigued by the Cairo Dock and gave it a try.  Yow!  This is really unstable!  I worked for over an hour, pruning and tuning it, only to have it totally disappear when I logged out and back on again.  It seems to be there (over on the left, where I put it) but I can't get the mouse to make it appear.  It was not hidden and whn I originally worked on it, it resided just fine over there.

3) No matter how I've set the colors and themes, I still get a totally black panel in certain windows where I should be seeing files and directories.  Each and every theme I've tried does this to me - and the NVIDIA driver seems to be very stable indeed under Ubuntu (default) theme.

4) I have tried my level best to create and insert other launchers into the Cairo Dock, but even though their "drop it here" animation appears, when I release the mouse, the icon goes up in a puff of smoke and I have to start all over again.  This may be the fault of Cairo Dock and not xfce per se.

So, is this a viable platform to be using for 14.04 or not?

Bill

---

### Post by ajgreeny on 2014-08-14
Yes, it is very stable in my opinion, and on my hardware.

I can't help with cairo-dock as I have never used it, but it may be disappearing on logout/login because you did not add it to the startup applications list.

See posts 8, 9 and 10 of [http://ubuntuforums.org/showthread.php?t=2239216&p=13097647#post13097647](http://ubuntuforums.org/showthread.php?t=2239216&p=13097647#post13097647) for a possible answer to your notification area in the panel crashing.

As to your query about desktop icons, I have no idea what you are talking about, but it sounds as if there is some display problem, perhaps related to nvidia driver or something, as changing the icon size to 10pixels on my system makes them pin-head sized and very close together, utterly useless as launchers. (see screenshot for what I see at 10px)

---

### Post by WB0HYQ on 2014-08-14
That's just it.  I do have Cairo Dock set to start with login, and it does start, it just isn't visible way way off to the left side of my monitor where I can't reach with the mouse.  If I press the mouse against the left side and click a key programs launch, so the Dock has to be there, just at negative pixels from the edge.

In my other thread concerning the crashing Notify Area, I found that solution and it does seem stable - so far.

In the xfce desktop, when you want to move an icon, you press and hold the left button of the mouse and drag the icon.  Under the icon as you drag it, there appears orange queares where yuou can drop the icon to a new location.  These squares are what I am talking about.  They are huge.  I normally don't run icons down that small either, and according to the Cairo Dock documentation, as you change the size of the icons, the "landing area" square SHOULD change size also, but it doesn't.

I have a feeling that I managed to get an incomplete install of xfce or something like that as my software update process tive me an error that "some repositories could not be checked" and refuses to proceed.  The "Details" tell me that the repositories belong to xcfe4.

I am about to remove the whole schmear from my computer.

Bill

---

### Post by ajgreeny on 2014-08-14
Yes, I think you may be correct about the installation either not being complete, or perhaps the installation medium was corrupt.  How did you install, and if from an iso file that you burned to DVD or put on a USB, did you check that it was a good download and md5sum matched with the published one?

On my desktop running 14.04 at a resolution of 1440x900 I can get 14 icons across the screen and 8 down the screen using an icon size of 34px, and the "orangebox" you talk of is about 1" square, not 2.5", so your display is definitely not behaving properly.  It sounds as if you are actually running at a very low resolution in low-graphic mode so have a look in Settings-manager ->Display to see what the screen resolution really is, as opposed to what the native screen resolution is.

What hardware do you have?  Have you now given up totally on Xubuntu 14.04?

---

### Post by kc1di on 2014-08-14
Hi WB0HYQ,

I've used xubuntu for serveral years now and recently installed xubuntu 14.04.1 it's working just great here , very stable. So something is amiss with your
install.  What is your video card?  that's where I would look first. 
73 Dave kc1di :)

---

### Post by WB0HYQ on 2014-08-14
I installed using the apt-get method and it seemed to install just fine.  When I logged off and clicked the Ubuntu button in the logon screen, xfce and xfce-fallback were both listed.  I have subsequently tried both of them and fallback is even more messed up than the normal xfce.

In the default Ubuntu my screen resolution is 1600x900 (the native for the monitor) and when I checked xfce it was at the same resolution.

The very first time I set up xfce, I had those smaller orange squares also and I created and moved my icons around just where I wanted them.  I di a lot of cosmetic maintenance and then, as a final move, I logged out and logged back in.  That's where my troubles began.  Each subsequent login has reduced the whole xfce desktop to a shade of it's former self - almost like it was slowly divesting itself of usable parts.

I am wondering if a complete uninstall and reinstall might help?  I would really like to use xfce for another important reason: I need to connect from several Windows 7 machines and RDP will not connect in Ubuntu 14.04 - I get a grey cross-hatched screen and nothing more (but that is another story).

Bill

---

### Post by WB0HYQ on 2014-08-14
Okay.  A bit of red-face here.  I did add Cairo Dock to my startup group, but for some reason it didn't take.  I did it again and NOW the dock shows up every time I logout/in.  So, that's taken care of.

The attached screenshot is rather large, but it does indicate that my display in xfce is running 1600x900.  Note the icons.  They have been shrunk down to as small as I really want them, but note also how far apart they are spaced.  This is because the orange square extends from the top of one icon to the next higher one.  The same spacing is for horizontal also.  I simply cannot get them closer than they are right in this shot.

Bill

---

### Post by WB0HYQ on 2014-08-14
Dave.  Sorry I missed your question about video card.  It is an NVIDIA GeForce 8400GS with 1G of RAM.  According to the NVIDIA display tweaker, I am running 1600x900 using NVIDIA driver set 331.38.  If I could just get those icons to behave, I'd be happy.

Bill

---

### Post by PJs Ronin on 2014-08-15
Is 1600x900 the default resolution for your monitor?   As a test I would recommend setting the resolution to, say 1920x1080 and see how it goes.

Edit: Would also suggest you check to see if compositor option is active:  Whisker Menu > Settings > Window Manager Tweaks > Compositor

---

### Post by kc1di on 2014-08-15
Hi Again Bill, At this point I think I'd try the 304 legacy driver for your card.

go to a terminal and type the following:```
sudo apt-get purge nvidia-331 && sudo apt-get install nvidia-304
```

Reboot and see what happens if it does not work you can always go back to the 331.  But i'm thinking 331 is not the correct driver for you card.
Let us know what happens. 

Good Luck

---

### Post by WB0HYQ on 2014-08-15
@PJs Ronin: 1600x900 is the default for the display and what I run in Windows7 on my other computers.  I use a 4-port KVM switch to go between computers here in my office.  To eliminate the possibility of the KVM interfering, I bypassed it.  Same thing.  Upping the resolution actually made the display get a little worse.  It did shrink desktop items (as expected) but they got a little fuzzy also.  Back to 1600x900.  When I turned Compositor off (it was checked) the desktop blinked, but nothing really changed.  When I re-checked it, Cairo Dock shut down and I had to restart it.  More in the next response.

@KC1DI: Dave, I've replaced the video driver with one from 304 and didn't get 1600x900 as a settable resolution (which is the monitor default).  So I went back to my 331.  Now that I know how Cairo Dock works, and can restart it when I need to, I find that I don't NEED icons on the desktop so the size of the orange squares doesn't matter at all.  In fact, I tried to create a desktop icon for VLC, and when I did, it immediately nestled itself into the Cairo Dock instead of popping up on the actual desktop.  When I switch desktop environments, I just go back to the Ubuntu default and in that configuration icons can be put wherever I want them with no restrictions.

So, I have now convinced myself that the xfce simply overwhelmed me initially and I retract my 4 original observations as being a little hasty in the face of something new.  In fact, I've grown to like the customizations possible with xfce/Cairo that just don't exist in other desktop environments.

Thanks for everyone's help here with a new guy.

Bill

---

### Post by The Cog on 2014-08-15
Those icon locating squares (blue on my PC) do change size as I change the icon size. At 8x8 they all huddle together in an area no bigger than a postage stamp. So there really is something fishy with your install. I wonder if it is because you added XFCE to Ubuntu and have a lot of leftover stuff. Can I suggest you try an Xubuntu live CD?

---

### Post by WB0HYQ on 2014-08-15
@The Cog: Your explanation may very well be the reason.  I added xfce through the apt-get mechanism into Ubuntu 14.04 other than an actual live disk install of Xubuntu.  There is a very good chance that some things didn't get copied, or didn't get initialized correctly.  But, I am a very firm believer in "if it isn't broken, don't mess with it".  I do fall back to the default Ubuntu desktop from time to time for various reasons and like to have that capability simply by logging off, changing the session, and logging back in.

I'm going to go with what I have right now.  Thanks for your input.

Bill

---

