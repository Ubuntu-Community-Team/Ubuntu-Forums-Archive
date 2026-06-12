---
title: "Fonts suddenly become ugly when switching to high resolution"
date: 2008-12-22
forum: Desktop Environments
---

### Post by torne on 2008-12-22
On a freshly installed 8.10 machine, fonts look fantastic at 1024x768 or 1360x768 (smooth and antialiased), but when I set my desktop resolution to 1920x1080 suddenly they become horribly ugly, in all programs: horizontal and vertical lines acquire irregular bumps and vary in width, and generally it looks like a very poor rendering :)

It only affects smallish font sizes, large text looks fine. No combination of the antialiasing or hinting options in the Appearance control panel makes it look significantly better, but dropping the resolution back down to anything smaller immediately looks fantastic again.

The HDTV I'm outputting to is rendering 1:1 pixel mapped: if I display a checkerboard or similar images they match up perfectly under a magnifying glass. Line art and photographs likewise look fine, so it definitely looks like a font rendering issue. I have a pretty recent ATI card, but the fonts render the same with the open source driver or with fglrx.

Any guesses what could cause it to only go wrong at the higher resolution? What I could do to fix it?

---

### Post by gettinoriginal on 2008-12-22
Try this:   

System > Pref > Appearance > Fonts set rendering to "subpixel smoothing" then go to details set smoothing to "subpixel" and hinting to full

---

### Post by kostkon on 2008-12-22
Try changing the DPI used. 

You could use a DPI calculator (for example, like [this]("http://members.ping.de/~sven/dpi.html")) to find which is the most appropriate DPI for your monitor.

---

### Post by torne on 2008-12-23
> **gettinoriginal said:**
> Try this:   

System > Pref > Appearance > Fonts set rendering to "subpixel smoothing" then go to details set smoothing to "subpixel" and hinting to full
Already tried every combination of those options, nothing helps.

> **kostkon said:**
> Try changing the DPI used. 

You could use a DPI calculator (for example, like [this]("http://members.ping.de/~sven/dpi.html")) to find which is the most appropriate DPI for your monitor.
The DPI of the TV is 60, which makes fonts even *smaller* and uglier than they already are (as it defaults to 96). Setting it to a huge value masks the problem a bit as the renderer gets more pixels to work with but it still does a bad job: letters are anything but smooth.

If I set the resolution back down to 1360x768, the font rendering is *always* good, with or without antialiasing, with any hinting level, and at any DPI.

Anything else I can try? :)

---

### Post by s3gfault on 2008-12-23
i think you've hit a bug.  report it at launchpad.net and then test other versions of the font packages.

---

### Post by s3gfault on 2008-12-23
delete me

---

### Post by PascalGR on 2009-02-08
Same problem here. I just bought a full HD monitor and I was very dissapointed by the display of windows, fonts etc. Its like stretching vertically the contents. Its very weird I know, but that's how I see the whole desktop.

I've tried changing the fonts rendering (subpixel smoothing), the DPI (96), the hinting (Slight), even the subpixel order but nothing. Evrything is displayed really ugly.

Its a pity that I have to switch to a lower resolution (1680x1050, this resolution shows things much better).

Any ideas on this subject? Am I missing something?

---

### Post by torne on 2009-02-09
I did fix this problem in the end: turns out it *was* a pixel mapping issue with the TV and not an issue with rendering. It just happened that whatever scaling process the TV was applying didn't distort a moire pattern noticably, but did distort character shapes. The fix was to use the other HDMI port on the TV: it promptly offered a switch to "PC mode" which had not previously shown up and caused scaling artifacts to vanish.

If your whole desktop looks wrong then it's definitely not anything to do with font rendering: you need to stop your TV from rescaling the picture. Look for a 1:1 or PC mode in the options, and try a different HDMI port if there are several. [http://pixelmapping.wikispaces.com/](http://pixelmapping.wikispaces.com/) has loads of details about this. Some TVs cannot ever display a 1:1 mapped image: it's just tough.

---

### Post by PascalGR on 2009-02-17
Hi Torne & thanks for your advice.

I'll have a look on the link you provided but for the moment I don't think this is the issue. The monitor is connected through DVI (it also has the normal analog PC input plus 2 HDMI ports) and when I boot from Windows the same resolution (1920x1080) displays perfect from the same source (DVI).

I've changed the fonts DPI (set to 91) and the fonts rendering are now improved a bit, but it still needs inprovements in order to be considered as perfect. :(

---

### Post by torne on 2009-02-17
Just because Windows and Linux are using the same resolution doesn't mean they're using the same display parameters: the modeline might not be identical and thus the display could still be doing something different :(

---

### Post by nfnaaron on 2009-03-24
Yes! Yes! Someone else has my problem! I think.

OP quoted in full to contrast with my particular details, but it sounds like the same symptoms if not the same cause.

See attached screenClip.png.

Installed 8.10 (gnome), all looks great, except my laptop screen and my external screen are tied together.

Untied them using System/.../Screen Resolution, looks great-ish, but both screens are at 1024x768.

Used System/.../Screen Resolution to set both screens to their maximum:
LVDS: 1280x800 (laptop)
VGA: 1680x1050 (external LCD)

Looks great for awhile but then progressively deteriorates as shown in attached screenClip.png.

Note that for every obscured character, almost all instances of that character are obscured, and in exactly the same pattern.

And the longer you go, the more characters will be obscured.

Also if you go long enough the text in the menus in the panel will virtually disappear (can still faintly see them as ghostly grey/white), but will come back visible but still disfigured if you click on the menu. Same for menu sub-items.

Although it's not shown here, text within a web page IS affected.

Also, I'm pretty sure that text within a terminal window is NOT affected, but that's a three in the morning type of observation, and I'm on WinXP at the moment.

This does not happen in Kubuntu or Xubuntu, only Ubuntu. I'm not sure if dual screen is relevant, or if it's just high-resolution.

I also installed Fedora 10 in gnome and kde versions, and got the same results on Fedora gnome except worse and quicker.

No version of KDE, or Xubuntu, shows this problem with font degradation. Unfortunately I can't get dual screens working in [X|K]ubuntu.

None of the subpixel smoothing type of suggestions (fiddling with setting values) has any effect.

Here's what I have (info from WinXP System info):
Compaq Presario V6000 laptop.
Chip Type: Mobile Intel(R) 965 Exress Chipset family.
Memory Size: 128 MB
Adapter String: Mobile Intel(R) GMA X3100.
Bios Information: Intel Video BIOS.

External Monitor: Samsung SyncMaster 2053BW.

Laptop and External are both 32 bit color.

I would like to solve this but I have no idea where to look, I'm not familiar with Linux architecture.

Suggestions or pointers? thanks.


> **torne said:**
> On a freshly installed 8.10 machine, fonts look fantastic at 1024x768 or 1360x768 (smooth and antialiased), but when I set my desktop resolution to 1920x1080 suddenly they become horribly ugly, in all programs: horizontal and vertical lines acquire irregular bumps and vary in width, and generally it looks like a very poor rendering :)

It only affects smallish font sizes, large text looks fine. No combination of the antialiasing or hinting options in the Appearance control panel makes it look significantly better, but dropping the resolution back down to anything smaller immediately looks fantastic again.

The HDTV I'm outputting to is rendering 1:1 pixel mapped: if I display a checkerboard or similar images they match up perfectly under a magnifying glass. Line art and photographs likewise look fine, so it definitely looks like a font rendering issue. I have a pretty recent ATI card, but the fonts render the same with the open source driver or with fglrx.

Any guesses what could cause it to only go wrong at the higher resolution? What I could do to fix it?

---

