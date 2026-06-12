---
title: "1080p tv not showing correct resolution"
date: 2010-01-19
forum: Desktop Environments
---

### Post by Quake3DeathGod on 2010-01-19
I've asked this question in another forum as well, this is the c/p from that posting. Since it fails in any version of Ubuntu as well, I'm asking here. Not to many people have been able to offer suggestions, so here goes:

I have a computer setting on my TV that is running windows. I have been trying to get it to run linux for months now, and I'm about done trying. Here is the deal.... In windows nvidia will allow you to "adjust" the resolution to anything you want, via the sliders in the nvidia control panel. The resolution that works out to fit on the tv is 1795x1010.
Now I'd think that if I told the same nvidia control panel in mint 7 to do the same resolution, it would fit. It dont even come close. As I adjust the resolution in the nv control panel, the icons get HUGE, but the actual space on the screen does not change. Then windows dont fit on the screen, and you cant hit "ok" or "cancel" or anything. What actually fits on the screen is about 1080x400, but the icon for "computer" is about 12 inches tall! :lol: Again, you cant hit any "ok" buttons, they are WAY out of the viewing area! I've tried to manually add this to x config file, and it will crash out, in low res mode. I can add it via the nv control panel, but it still does not fit on the screen. I cant see the start bars, or the default icons on the screen, they are out of the viewing area. Is there anyway I can run this and make it fit on the screen pretty and nice? I've literally been working on this for months, and I'm am admitting defeat. I'm VERY hard headed. Am I stuck in windows?

Ok, edid come back with a bunch of symbols, and ends with "your edid info is probably invalid."

Now, what both windows and linux tries to make default for my tv is 1920 x 1080p. Now there had to be a way to change the DPI of the screen some where. Follow me here: ON install, vesa drivers will default to 800x600, which ALMOST fits. (it has a 1 inch black section on left and right, 1/2 inch top and bottom of unused screen) If the vesa driver was fast enough to play videos full screen I'd not be here. So, I load the nvidia drivers, and it defaults to 1900x1080. Oddly, it almost fits too. (it goes beyond the screen about 1 inch left and right, 1/2 top and bottom) If after loading the correct nvidia drivers, I switch to 800x600, it no longer fits, its so huge, you cant do ANYTHING with it, and have to go in and edit the xconfig file to get it going again. I think there is a difference in what the vesa driver is saying is resolution, and what nvidia is saying is the resolution. Vesa drivers are changing the amount of space on the screen, where nvidia is changing the actual dot size on the screen, I think :roll: Am I making any since here? Clear as mudd?? :? I swear, I thought I could go into the xorg file, MAKE it go to 1795x1010, and it would work, not so easy though... I need help :cry:

---

### Post by andrewc6l on 2010-01-19
Here's a good doc on setting up your monitor the way you want it:

[http://howto-pages.org/ModeLines/](http://howto-pages.org/ModeLines/)

---

### Post by mcduck on 2010-01-19
Assuming that it's LCD or Plasma screen (anything else than CRT, really), what you *really* want to do is to set the resolution to 1920x1080 (which is the native resolution of your display) and then set the display itself to run in pixel-per-pixel mode, meaning that all image scaling should be disabled. If you need to move the image your display should have setting for that. 

Using the display's native resolution will always fit perfectly (assuming your display's own settings are right), and is also the only way to get a clear picture.

If you then need to adjust how large fonts etc appear use the DPI setting calculated from your display's size and resolution. Just like the resolution, DPI as an absolute setting for any LCD/Plasma panels, there is only one correct value.

If you after that need to adjust how large your fonts etc are just use the font size settings.

---

### Post by Quake3DeathGod on 2010-01-19
Im gonna read what andrew has linked me to, see whats in there. My problem is, I know I need to make it the default resolution, but there is a trim around the screen, and I guess the screen continues under that trim a bit. What I can fit on the screen where I can see everything is 1795x1010, in windows. So I guess I am missing 70 pixels in one direction , little better than 50 on either side. Oddly enough, it does not do that via the TV, or the wii, or the xbox. I dont know why a PC is the only thing it seems to have trouble with. I'm going at this through an HDMI port from an nvidia card... if that makes any difference. Its a Sanyo, and as far as I can remember there is very little adjustment in the menu for anything other than balance of colors. I'll look again, but if its in there, I'm going to be embarrassed!

---

### Post by Quake3DeathGod on 2010-01-21
xvidtune will not work on this setup, runs to an error about not being able to make changes.

Im about done trying.... Its just one little computer... : ( I dont think its linux fault per say, but the nvidia control panel does not have the same options we have in windows. If it did, I would not have any of this trouble. Besides, I may upgrade the nvidia card to an ati card soon. It has onboard hd decoding, where the nvidia hands it off to the cpu. Thanks for all your help, at least it makes me think I'm not completely stupid, and it wasnt as easy as I was afraid it was going to be.

---

