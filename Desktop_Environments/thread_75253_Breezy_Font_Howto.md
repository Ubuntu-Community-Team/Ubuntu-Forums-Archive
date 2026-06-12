---
title: "Breezy Font Howto"
date: 2005-10-13
forum: Desktop Environments
---

### Post by BIGtrouble77 on 2005-10-13
Hopefully someone knowlegable can write a good font howto for breezy.  I still can't get aliased 96dpi ms fonts to look right.  Honestly, I think most people have screwed up fonts, they just don't know it because the antialiasing covers it up.

-BT

---

### Post by nooky59 on 2005-10-13
You know, MS TT Core Fonts looks better not antialiased at small size and it's better for reading.

But at higher size, MS TT Core Fonts renders better anti-aliased.

The perfect deal is to do this. The problem is I don't know to do this on Gnome (so I disable antialising) bot on KDE you can give a range of fonts size that should not be antialiased

---

### Post by nicolas314 on 2005-10-14
I could not agree more. The first thing you see after upgrading to Breezy
is that all fonts are screwed up. Not badly, just enough to strain your eyes
and make web pages unbrowsable after 5 minutes. Fixed-sized fonts are Ok.

I am using Terminus for fixed-size and Tahoma for the desktop, following
a description made on this forum for Warty. Unfortunately the Breezy upgrade
broke it. Just spent half a day modifying one after another all configuration
files I could lay my hands on, without success. If anybody succeeds in
making anti-aliasing actually work, it would be appreciated.

---

### Post by bin on 2005-10-14
[QUOTE=BIGtrouble77]Hopefully someone knowlegable can write a good font howto for breezy.  I still can't get aliased 96dpi ms fonts to look right.  Honestly, I think most people have screwed up fonts, they just don't know it because the antialiasing covers it up.

-BT[/QUOTE]

Ummm - does your monitor run naturally at 96dpi?

I know it's a silly question, but not all do by any means. Provided you've got your DisplaySize set in xorg, run xdpyinfo in a terminal and near the top it'll show you the resulting dpi. You acn alos use the font tool in Mozilla to set to custom and see what it comes back with. 

EG my lappy looks ok at 96 dpi but it actaully runs at 92 dpi. Result - very clear fonts - and trust me I am picky to the point that I will only run Debian cos all other distros produce fuzzy fonts on LCD's and I cannot be bothered to go and recompile half a dozen bits an pieces to get what should 'just work' in 21st C

in light

bin

---

### Post by BIGtrouble77 on 2005-10-14
[QUOTE=bin]Ummm - does your monitor run naturally at 96dpi?

I know it's a silly question, but not all do by any means. Provided you've got your DisplaySize set in xorg, run xdpyinfo in a terminal and near the top it'll show you the resulting dpi. You acn alos use the font tool in Mozilla to set to custom and see what it comes back with. 

EG my lappy looks ok at 96 dpi but it actaully runs at 92 dpi. Result - very clear fonts - and trust me I am picky to the point that I will only run Debian cos all other distros produce fuzzy fonts on LCD's and I cannot be bothered to go and recompile half a dozen bits an pieces to get what should 'just work' in 21st C

in light

bin[/QUOTE]

I believe that the msttcore fonts are designed to run at 96dpi.  It's critical that those fonts are correctly represented because I do web development and need to know exactly how my pages will look on a windows machine.

To answer your question, I know the fonts look fine at 96 dpi on my laptop because that what I had hoary set to.  I just need the fonts to look exactly the same as they do on a windows machine.  I know this is possible because that's how I had hoary setup.

-BT

---

### Post by jobezone on 2005-10-15
[QUOTE=BIGtrouble77]I believe that the msttcore fonts are designed to run at 96dpi.  It's critical that those fonts are correctly represented because I do web development and need to know exactly how my pages will look on a windows machine.

To answer your question, I know the fonts look fine at 96 dpi on my laptop because that what I had hoary set to.  I just need the fonts to look exactly the same as they do on a windows machine.  I know this is possible because that's how I had hoary setup.

-BT[/QUOTE]
Here's a screenshot of my desktop (using all the LCD features in font properties of Gnome). Is this how you want it to look, or is it suboptimal to you? If so, why? Because I use gnu/linux for some years, and while in the begining fonts were really screwed up (only existed free bitmap fonts at the time, no outline ones), for the last 2/3 years they have improved and look fine to me.

---

### Post by cowlip on 2005-10-15
I've found that making hinting "none" makes fonts looks nicer and more like Mac OSX, it's under "details" in the font preference

---

### Post by BIGtrouble77 on 2005-10-23
I thought I'd conclude this thread now that I finally fixed the problem.  Issue was my font paths were not set to unscaled.  Here's what I needed to input in the "Files" section in my xorg.conf:
	```

        FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/truetype/msttcorefonts/:unscaled"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"


```
This will ensure that all the fonts will be properly scaled while aliased.  If you want it to behave like windows and antialias larger fonts then you'll have to edit your fonts.conf.  Fortunately there's a ton of howto's here that will explain how to do that.

It's also important that hinting is turned on.
Here's a screenshot if anyone's confused by what I was trying to accomplish: [http://bob.bah.net/mullet/Screenshot2.png]("http://bob.bah.net/mullet/Screenshot2.png")

I wanna thank everyone for their suggestions.
-BT

---

### Post by kod on 2005-10-25
[QUOTE=BIGtrouble77]
It's also important that hinting is turned on.
-BT[/QUOTE]

Are you using the native hinting, or autohinter?

thanks for noticing the unscaled thing - my fonts are looking better . . .

---

### Post by BIGtrouble77 on 2005-10-27
[QUOTE=kod]Are you using the native hinting, or autohinter?

thanks for noticing the unscaled thing - my fonts are looking better . . .[/QUOTE]
I'm pretty sure I have it set to native, but I'm not sure there's much of a difference.  I use the msttcorefonts for virtually everything, so I used native because that's what's recommended. 

If hinting isn't enabled in the "Font Rendering Details" they will look messed up.  I didn't notice any difference between slight, medium and full.

---

