---
title: "Can't get 1440x900 with drivers enabled"
date: 2007-11-02
forum: Desktop Environments
---

### Post by 4Play on 2007-11-02
Hello, I recently upgraded from Fiesty (7.04) to Gusty (7.10) and am kind of repenting that decision, here is why:

I installed the latest restricted nvidia drivers (I have a Geforce 6800 GS), but I didn't get the 1440x900 resolution option (my monitor is a Acer AL1916W widescreen). This had also happened with fiesty and edgy, so no problems there, I edited /etc/X11/xorg.conf as I always did, in order to add the new resolutions, but there were no resolutions listed under the "screen" section of xorg.cong, or any other section for that matter. Anyway, to make a (very) long story short, adding new lines, pertaining the desired resolutions did nothing, the only thing that got my resolution up and running was:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
However, this disabled the hardware acceleration (no fancy graphics, no games, no nothing). After several hours of meddling, I came to the conclusion that when the drivers are enabled, it must get it's resolutions from somewhere else, other then xorg.conf, since the available resolutions when the graphics driver is on are nowhere to be seen in the xorg.conf file. Only when the drivers are off do the resolutions I added show up as an option.

I did manage to choose 1440x900 with the drivers on, by changing the settings on the System>Administration>Screens and Graphics menu, but it showed 1440x900 all wrong (you know when the resolution is too big for the monitor, so you have to scroll around the screen to be able to see the whole desktop).

I have already ran sudo nvidia-settings, and it only shows the resolutions I don't want. One thing I found to be curious was that when I placed
```
	SubSection "Display"
		Modes		"1440x900" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
```
under the Monitor section (it should go under screen), upon restarting X, with the drivers enabled, I get an error message, and X prompts me to reconfigure my monitor, which I do, but when it comes back up, the 1440x900 resolution I chose is not there, it defaults to 1280x768 (or something close to that)

Anyway, sorry for the long post, but since I have been working(aka: banging my head on the table) with the xorg.conf file since Edgy Eft, I thought I had it all figured out...6+ hours of frustration just proved me wrong. But I believe this has more to do with Gusty then my inability, since I read on more then one post, that adding resolution lines to xorg.conf in Gusty didn't resolve the issue (the appropriate solution was never mentioned)

Thanks for any advice:)

---

### Post by 4Play on 2007-11-02
I found the solution, it was posted on this very forum @ [HTML]http://ubuntuforums.org/showthread.php?t=583825&page=2[/HTML]

I didn't find it earlier because I was serching for Gusty insted of Gutsy (you know when you start reading a word and your brain automatically completes the rest of the word without you actually reading the letters)

The solution, as described in the above mentioned link was to do the following:

> i had the same issue (same monitor) and it was fixed with these two lines:

you dont need modelines at all to get this working. remove those and under the screen section, just put in "1400x900" under the 24 bit section and you should be ok.

add them under the device section of the xorg.conf

Option "ExactModeTimingsDVI"
Option "ModeValidation" "NoDFPNativeResolutionCheck"

Worked like a charm. Mods can delete this post if they judge necessary, since it's already been discussed in another thread.

Thanks

---

