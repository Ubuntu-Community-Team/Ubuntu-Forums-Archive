---
title: "GDM Screen Login is Huge"
date: 2008-08-03
forum: Desktop Environments
---

### Post by kh1116 on 2008-08-03
This is weird, when i log into my computer, the login screen is so big that i can barely see the input box, it ends up being in the bottom right corner of the screen. Anyone know a fix?

---

### Post by K2712 on 2008-08-03
Check your xorg.conf for a Virtual line, and see if it has your correct resolution.

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by kh1116 on 2008-08-06
sorry i forgot to specify-- when im logged in, the screen resoulution is fine, its only at login when its like that

---

### Post by pauper on 2008-08-06
In case you're using custom Greeter theme, check XML file in
/usr/share/gdm/<current_theme>/*.xml

[php]<item type="pixmap">
  <normal file="background.png"/>
  <pos x="0" y="0" width="100%" height="100%"/>
</item>[/php]

If W×H differs from 100% scale, make an adjustment. Other than that--there is a
chance that the original theme were made for a different resolution than yours,
or it's simply poorly written, so you end up with misaligned objects. Edit your
XML file to fix that.

Try other themes--same behavior?

---

### Post by kh1116 on 2008-08-06
Yes all themes, plain or themed, including the default ubuntu login screen have this problem. idk if this helps anything, but when i move my mouse to the edge of the screen, it changes the point of view so i can view the whole login screen, but its not all on my monitor at the same time

---

### Post by Sniqs on 2008-08-07
I had the exact same problem you have and I fixed it by editing the Virtual line of my xorg.conf (what K2712 said). Open a terminal and type:

```
gksudo gedit /etc/X11/xorg.conf
```

Find the Screen section, mine looks like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
```

My problem was that the last line (Virtual) had way too high values (1792 1344). Check if those values are the same as your desktop resolution. If they're not then edit them so that they are the same. This should solve your problem. It solved mine :)

---

### Post by kh1116 on 2008-08-07
nope sorry guys  i changed the resoulution to 1024 768 and the problem is still occuring... could it be a problem with restricted drivers not loading until login? idk just a guess

---

### Post by kh1116 on 2008-08-07
bump

---

### Post by kh1116 on 2008-08-10
anyone know?

---

### Post by atpat on 2008-08-27
Bump indeed.  I have this problem too, and I can add the following observation: I changed the "virtual" values to something sensible, and it limited my available resolutions after login (as listed by the Preferences/Screen Resolution tool) down to a maximum of the one I'd specified in "virtual".  I had to change "virtual" again to "1600 1200" to make my monitor's maximum resolution available again; but of course the login screen size enlarged again without the actual resolution changing from what looks to me to be bog-standard 480*600 or something.  If I do figure something out, I'll post again.

---

### Post by mali2297 on 2008-08-27
My suggestion is to add the line
```

Option  "DDC"  "false"

```
in Section "Device" in /etc/X11/xorg.conf.

---

### Post by wightghost on 2008-08-28
> **Sniqs said:**
> I had the exact same problem you have and I fixed it by editing the Virtual line of my xorg.conf (what K2712 said). Open a terminal and type:

```
gksudo gedit /etc/X11/xorg.conf
```

Find the Screen section, mine looks like this:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
```

My problem was that the last line (Virtual) had way too high values (1792 1344). Check if those values are the same as your desktop resolution. If they're not then edit them so that they are the same. This should solve your problem. It solved mine :)

I don't mean to hijack the thread but I had the same problem as KJ1116.  This suggestion fixed my problem.  The "Virtual" line had setting that were too high for my screen.  Now the login box is in the centre of the screen.  Although for some reason when I logged in again I had to reset the screen refresh rate back to what it was.  But other than that it works fine.  Thanks.

---

### Post by atpat on 2008-08-28
I have fixed this problem for myself :KS.  Here is what I've learned.

_The Quick Answer:_ in xorg.conf, section "Screen", subsection "Display", the element "Virtual" has to set the same resolution as the resolution of the screen mode at the left-hand end of the list in the element "Modes".  Note that (1) this will also determine the maximum resolution available through the Preferences/Screen Resolution tool, and (2) the mode which needs to match "Virtual" is the first on from the left in "Modes" which actually works for your monitor and graphics card.

As an example of a successful configuration, here are the relevant lines from my xorg.conf file:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual 1792	1344
			Modes	"1792x1344@60"	"640x480@60"	"640x480@72"	"640x480@75"	"640x480@85"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@85"	"800x600@60"	"832x624@75"	"1024x768@85"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1024x768@43"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x960@85"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"	"1856x1392@60"
	EndSubSection
EndSection
```

If I wanted to have a login page with slightly less microscopic text, and could bear to sacrifice the rare occasions where I need the really high resolution, I'd perhaps set Virtual to 1600 1200 and move "1600x1200@60", which I know works on my equipment, to the head of the Modes list.

_The detailed answer_

In xorg.conf, section "Screen" binds your graphics card to your monitor.  Within Screen there is a subsection "Display", which appears to determine what resolutions are available to you on your desktop and what resolution the GUI login page will use.

The element "Modes" within subsection "Display" contains a list of possible screen modes.  When deciding which mode to use for the login screen, the system reads this list from the left and uses the first mode which works on your card & monitor.  This means that you can prioritize which mode to use by changing the order of the list.  The system does this, however, regardless of the size of the login page itself, so if the login screen is 1600x1200 and the first compatible screen mode is 640x480 then you're only going to see the top left corner when you go to log in.

So you can take control of which screen mode is used at login; but what controls the size of the login page itself?  Obviously you want these two things to be the same, so that the login page fills the screen but you can also see all of it.  This is where "Virtual" comes in.  This value seems to have two effects:
[LIST=1]
[*]the system chooses which size of login screen to try to display based on it;
[*]the system uses it as a limit on your available screen modes in the GUI: if you have "Virtual 1280	1024" then the highest resolution you will have available for your desktop will be 1280x1024.
[/LIST]
If you delete "Virtual" altogether, you'll have all the screen resolutions available to you in the GUI, but the system will default to the largest possible login page and the mode used to display it is likely to be somewhat smaller, depending on the order of the "Modes" list.

The answer, therefore, is to decide what the biggest resolution is that you'll want to use, set "Virtual" to that, and make sure that a compatible screen mode at that resolution is at the head of your "Modes" list.  This is ok, except that I'd like to have my maximum possible resolution available for some things like viewing hi-res pictures, but not to have microscopic text on my login screen.  If anyone finds out a third factor which lets this happen, please post it!

Please do make a backup of xorg.conf before you start hacking it around, and please do make sure you can log in without actually being able to see the text box!  (I suppose you must be able to do that if you have come to read this thread...)

One more thing: there is something odd about the translation of the screen mode frequencies in xorg.conf to the list available in the GUI preferences/screen resolution tool.  For example, according to xorg.conf, for 1024x768 my monitor can do 43, 60, 70, 75 and 85Hz.  According to the GUI tool, 88Hz and anything from 60Hz to 64Hz are available; and they do seem to work.  Eh?

Oh, and after all this fiddling about, displayconfig.gtk doesn't work anymore, despite my reinstalling it.  Oh well.

---

### Post by lister171254 on 2008-10-28
I have the same issue. I have added a question in Launchpad:
[https://answers.launchpad.net/ubuntu/+question/49337](https://answers.launchpad.net/ubuntu/+question/49337)

Cheers,

Leo

---

