---
title: "urxvt Font Width"
date: 2008-12-13
forum: General Help
---

### Post by gladstone on 2008-12-13
Anyone know why urxvt has weird font width spacing? i.e. 

[IMG]http://i35.tinypic.com/qsmp.png[/IMG]

(DejaVu Sans Mono, Size 8 ) -- Image from an ArchLinux forum post, which I seem to have lost.

Someone also seems to have mentioned it on [Best terminal font](http://ubuntuforums.org/showthread.php?t=824487#8) thread.

Is there a fix for this?

My *.Xdefaults* looks like this:
```

urxvt.font:                 xft:Monospace:size=9
! Also tried the following with no luck:
urxvt.font:                 xft:DejaVu Sans Mono:size=9

```

---

### Post by urukrama on 2008-12-13
I use the following:

> URxvt*font: xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:hinting=true

Which looks like this:

---

### Post by gladstone on 2008-12-14
Using
```
URxvt*font: xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:hinting=true
```
for me, gives (in comparison with your image) the following. Notice the difference in spacing.

---

### Post by urukrama on 2008-12-14
Interesting.

I wouldn't know what else could change the font spacing. 

Perhaps it is due to my ~/.fonts.conf file? This is what I have in there:

> <?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
 [http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098](http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098) -->

<fontconfig>

<!-- Disable sub-pixel rendering.
 X detects it anyway, and if you set this as well, it just looks really horrible  -->
<match target="font" >
	<edit mode="assign" name="rgba" >
	 <const>none</const>
	</edit>
 </match>
 <match target="font" >
	<edit mode="assign" name="hinting">
	 <bool>true</bool>
	</edit>
 </match>
 <match target="font" >
	<edit mode="assign" name="hintstyle">
	 <const>hintfull</const>
	</edit>
 </match>

<!-- The first part of the 'magic.'
 This makes the fonts start to look nice,
 but some of the shapes will be distorted, so hinting is needed still -->
 <match target="font" >
	<edit mode="assign" name="antialias">
	 <bool>true</bool>
	</edit>
 </match>

<!-- Autohinter is not turned on automatically.
 Only disable this if you have recompiled Freetype with the bytecode interpreter,
 which is run automatically.<br />  -->
 <match target="pattern" >
	<edit mode="assign" name="autohint">
	 <bool>true</bool>
	</edit>
 </match>
 <match target="font">
		 <test name="weight" compare="more">
				 <const>medium</const>
		 </test>
		 <edit name="autohint" mode="assign">
				 <bool>false</bool>
		 </edit>
 </match>
<!-- Helvetica is a non true type font, and will look bad.
 This replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
	<test name="family" qual="any" >
	 <string>Helvetica</string>
	</test>
	<edit mode="assign" name="family" >
	 <string>sans-serif</string>
	</edit>
 </match>
<match target="font" >
  <test compare="more" name="pixelsize" qual="any" >
   <double>12</double>
  </test>
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="pattern" >
  <test name="family" qual="any" >
   <string>Bitstream Vera Sans</string>
  </test>
  <edit mode="assign" name="family" >
   <string>Arial</string>
  </edit>
 </match>
 <match target="pattern" >
  <test name="family" qual="any" >
   <string>Helvetica</string>
  </test>
  <edit mode="assign" name="family" >
   <string>Arial</string>
  </edit>
 </match>
 <match target="pattern" >
  <test name="family" qual="any" >
   <string>Palatino</string>
  </test>
  <edit mode="assign" name="family" >
   <string>Georgia</string>
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
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>

---

### Post by gladstone on 2008-12-15
Thanks, I tried the *.fonts.conf* file, but still hasn't made a difference :(

Here's some relevant posts on the Arch Linux forums:

[urxvt font behaviour](http://bbs.archlinux.org/viewtopic.php?id=38607)
[Urxvt fonts](http://bbs.archlinux.org/viewtopic.php?id=44800)
[urxvt font widths](http://bbs.archlinux.org/viewtopic.php?id=55634)

Within one, they do mention [a patch](http://lists.schmorp.de/pipermail/rxvt-unicode/2007q4/000514.html), which seems interesting...

---

### Post by Micand on 2009-02-17
Thank you for the hint regarding ~/.fonts.conf -- removing my ~/.fonts.conf resolved the issue of excessively wide horizontal character spacing in urxvt. My ~/.fonts.conf was hanging around from an installation of Gentoo, and contained the following:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
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
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Now, with no ~/.fonts.conf, all is well.

---

### Post by gladstone on 2009-02-17
Good to hear its working as expected for you.

I don't use a ~/.fonts.conf on my Ubuntu system but I still have this issue. My Arch Linux system does not have problem, leading me to believe the fault here is something to do with Ubuntu's default font settings.

---

