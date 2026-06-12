---
title: "gnome-settings-daemon -- what does it do?"
date: 2008-02-06
forum: Desktop Environments
---

### Post by BattlePanic on 2008-02-06
I'm having a hard time finding information on the gnome-settings-daemon.  I don't have a very good understanding of what it does or why it's required.

I've been playing around with the Openbox and Fluxbox window managers.  I'm just running them on their own, not under GNOME.  I've noticed that running the gnome-settings-daemon while in Fluxbox seems to restore my fonts to what they look like under GNOME.  Once the gnome-settings-daemon is running, the correct fonts are used in menus and although my fonts were antialiased before I ran the gnome-settings-daemon, they look even smoother to my eye once the gnome-settings-daemon is running.
Other than fixing my fonts to my GNOME preferences, I can't tell what else this daemon is doing.

Can anyone clarify what exactly gnome-settings-daemon does or point me to some documentation.  Is there a means of achieving the same results in Fluxbox without having to resort to gnome programs?

---

### Post by tcommbee on 2008-02-09
You're right, there's poor documentation about that in the net, but from what i have found it seems that it bundles several daemons from older versions of gnome-control-center. this means it enforces that your gtk-theme is set, keyboard shortcuts work etc. I would assume that it's generally used to apply the settings made in the several gnome-*-properties dialogs (including the one about font rendering).

---

### Post by BattlePanic on 2008-02-09
thanks for the reply tcommbee,

I've been experimenting with Fluxbox a bit more since my orignal post and I've learned that I can restore my fonts to what they would look like with the gnome-settings-daemon running.  It seems that the file ~/.gtkrc-2.0 holds a configuration for my current gtk 2.0 theme.

Oddly, there seems to be a slight problem with how the fonts are rendered in Fluxbox.  It's a very subtle glitch, but it seems that on certain dialogs and in certain programs the text will jump around by a pixel if it's selected or hovered over with the mouse.  I have mostly noticed it in the firefox dialog asking if I want to restore a previous firefox session or start a new one.  I also noticed it on the Firefox tabs.  It will occasionally happen with selected text on web pages as well.  What's strange is that this rendering problem only seems to occur in Fluxbox and not under GNOME.

---

### Post by ejket on 2008-02-09
> **BattlePanic said:**
> Oddly, there seems to be a slight problem with how the fonts are rendered in Fluxbox.  It's a very subtle glitch, but it seems that on certain dialogs and in certain programs the text will jump around by a pixel if it's selected or hovered over with the mouse.  I have mostly noticed it in the firefox dialog asking if I want to restore a previous firefox session or start a new one.  I also noticed it on the Firefox tabs.  It will occasionally happen with selected text on web pages as well.  What's strange is that this rendering problem only seems to occur in Fluxbox and not under GNOME.

This sounds like a problem that I had, only it was related to the vertical refresh rate in xorg.  It was more like the text flickered thicker and then thinner, triggered by mouse movement ... but it was twitchy-looking and annoying.  I fiddled it somehow in Gnome so that it went away, but then I had to get a [**modeline**](http://www.bohne-lang.de/spec/linux/modeline/) to fix it for Openbox.  (My vertical refresh rate was 75 Hz and needed to be 60 Hz).

Also, Gnome failed to report the refresh rate accurately: it said it was 50 when it was 75, and then said it was 51 when it was 60.  I used nvidia-settings to see what the actual values were.

---

### Post by BattlePanic on 2008-02-10
> **ejket said:**
> Also, Gnome failed to report the refresh rate accurately: it said it was 50 when it was 75, and then said it was 51 when it was 60.  I used nvidia-settings to see what the actual values were.

This sounds interesting.  The problem only seems to affect one or two lines of text at a time and in my case an entire word will shift upwards or downwards by a pixel so I'm really not sure if this is the same problem but I think it may be worth investigating.  I happen to have an nvidia graphics card as well.  Can you tell me where in nvidia-settings it reports the refresh rates?

---

### Post by ejket on 2008-02-10
> **BattlePanic said:**
> This sounds interesting.  The problem only seems to affect one or two lines of text at a time and in my case an entire word will shift upwards or downwards by a pixel so I'm really not sure if this is the same problem but I think it may be worth investigating.  I happen to have an nvidia graphics card as well.  Can you tell me where in nvidia-settings it reports the refresh rates?

The second menu item from the bottom reports refresh rates (just above the prog config which is the last line).

This may not be a solution for you, but it wouldn't hurt to optimize your xorg.conf a bit, anyway.  There are some nice tricks for the nvidia driver, like setting the DPI:

```
Section "Device"
    ...
    Option      "UseEdidDpi" "false"
    Option      "DPI" "90 x 90"
    ...
EndSection
```

That's a bit of a drift off-topic, but all of this stuff contributes to making things look good ...

---

### Post by BattlePanic on 2008-02-10
> **ejket said:**
> This may not be a solution for you, but it wouldn't hurt to optimize your xorg.conf a bit, anyway.  There are some nice tricks for the nvidia driver, like setting the DPI:

...

That's a bit of a drift off-topic, but all of this stuff contributes to making things look good ...

I think I may have figured out what is going on and your mention of DPI settings in xorg.conf was actually quite fortuitous.

I noticed that nvidia-settings reported my screen to be at 1280 x 800 pixels at a DPI of 101x101 dots per inch.  The only other time had seen DPI mentioned was under GNOME's font settings, where it was set to 96 dpi.  I wondered if this inconsistency was perhaps why fonts in Fluxbox and GNOME were rendering differently.  Fluxbox was using 101dpi whereas GNOME was somehow overriding this X11 setting and using 96 dpi instead.  I read up on [editing xorg.conf]("http://www.linux.com/feature/118108") and added the two lines you mentioned.  The relevant section now reads:

```

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"UseEdidDpi"	"false"
	Option		"DPI" "96 x 96"
	Option		"NoLogo"	"True"
EndSection

```

I logged out to the GDM login window and immediately noticed that the fonts were now slightly smaller in GDM.  I logged in into a Fluxbox session and the font weirdness was gone.  nvidia-settings is also now reporting 96 x 96 dpi as it's now explicitly stated in my xorg.conf.  As for where 101 dpi was coming from, I'm guessing that the display hardware was reporting this number to my graphics card via [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data").  101 is probably the true dpi of my display but certain desktop elements weren't handling fonts gracefully at 101 dpi and this caused little hiccups in how fonts were being positioned.  96 dpi seems to do a better job with fonts, for whatever reason.

Thanks ejket, you pointed me in the right direction.  If you know of any other nvidia driver tweaks be sure to send them my way.

---

### Post by ejket on 2008-02-10
You're welcome -- glad it worked out.

Yes, sometimes you have to take control and skip the automated stuff.  Even though Gnome can put a bandaid on some problems, it's best to solve them at a more basic level, I think.  Then they're really solved :)

---

### Post by tcommbee on 2008-02-10
i would argue that the monitors EDID is much more basic than xorg.conf...

---

### Post by ejket on 2008-02-10
It's just one part of the equation, though.  You have the monitor, card, and software -- they all have to work together.  An EDID can't guarantee good settings.

Though I see your point and won't argue back :)

---

