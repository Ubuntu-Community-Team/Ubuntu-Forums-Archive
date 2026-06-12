---
title: "Change font antialising outside gnome session"
date: 2009-07-22
forum: Desktop Environments
---

### Post by Andreas1 on 2009-07-22
hi,
i am using the "awesome" window manager and i was wondering how i could change the font rendering settings for applications. so far i created a .gtkrc-2.0 file that says ```
gtk-font-name="Sans 8"

```
because it seems by default the dpi is way bigger than 96.

what i would like to do now is change the dpi to 96 (like gnome session default) so i can use font size 10 again and also change antialising from strong hinting to slight hinting or none.

---

### Post by Zorael on 2009-07-22
As for DPI, I think one way would be to edit your **/etc/gdm/gdm.conf** file, find the line with the actual command called to start the X server, and add a -dpi argument to it. I don't have a GNOME system available so I'm just googling for an example here; yours might look a bit different.
```
*<snip>*

[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 **[COLOR="RoyalBlue"]-dpi 96[/COLOR]**

*</snip>*
```

As for antialiasing, have you tried adding the option to your ~/.fonts.conf file?
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>true</bool>
 </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="**antialias**" >
   <bool>**true**</bool>
  </edit>
 </match>
</fontconfig>
```
Omit the non-antialiasing options if you don't want them, obviously. That's my file for getting rgb subpixel rendering with full hinting for my laptop's LCD screen. It might look bad on CRT screens. Embedded bitmaps are what make complex unicode fonts such as Japanese kanji even remotely legible, so unless you read a lot of CJK characters, it's a very optional setting. (With it disabled, they become *very* fuzzy at lower font sizes.)

Alternatively, check what files in /etc/fonts/conf.available are symlinked into /etc/fonts/conf.d to get the same effect(s) for all users.

Oh, and at least for kdm, there is an option in /etc/kde4/kdm/kdmrc to enable antialiasing at the actual greeter (login screen). Likely there's something similar in GNOME's gdm.conf.

---

### Post by Andreas1 on 2009-07-23
editing gdm.conf didn't work, but something else did:
i created .Xresources in my home directory that says:
```
Xft.dpi: 96
```

the .fonts.conf partially works: the different degrees of hinting are not discerned: "hintnone" makes no hinting, which is ok, but "hintslight", "hintmedium" and "hintfull" all look the same (about what "hintfull" should look like, i guess). any ideas?

basically i just want the default font rendering that is used in ubuntu, for my awesome session. starting the gnome-settings-daemon is also a way to achive this, but this also loads other settings that i do not want, like the human gtk theme.

---

### Post by geoffp on 2009-07-28
Thanks for the tip, although my issue was unrelated!  Every time I install a GTK app not from the repos, the font hinting doesn't match the rest of my desktop, but using:

```

 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
```

in .fonts.conf makes it match my font preference closely enough that it doesn't drive me crazy.

I found the full reference for all the things you can stick in this file here: [http://www.fontconfig.org/fontconfig-user.html](http://www.fontconfig.org/fontconfig-user.html)

---

