---
title: "subpixel hinting"
date: 2009-06-06
forum: General Help
---

### Post by fred6633 on 2009-06-06
Hello,

There is no difference when I use full hinting or medium hinting in Ubuntu 9.04.

Have I missed anything?

thanks

Fred

---

### Post by learningcurb on 2009-06-06
Full and medium hinting look the same on my display as well.  I don't exactly why though. :)

By the way in the XFCE settings manager, it says that regarding subpixel hinting, you can choose whichever option looks best to you.  It also mentions that the subpixel order option is the one that needs to be specific to your monitor.

---

### Post by sdennie on 2009-06-06
Medium and full look the same on my non-Ubuntu machine as well.  It's possible that they are just so close that the human eye can't tell the difference without examining them extremely closely (like, pixel by pixel).

---

### Post by fred6633 on 2009-06-07
Hello,
There is this thread
[http://ubuntuforums.org/showthread.php?p=16896](http://ubuntuforums.org/showthread.php?p=16896)

If I enter these lines in /etc/fonts/local.conf, there is a difference between medium and full hinting.

<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>

But this post is from 2004 and I don't know if it has any relevance anymore and I can't say I notice any particular improvements with these lines.

I think it has got something to with the freetype font engine.

Fred

---

### Post by sdennie on 2009-06-07
The ~/.fonts.conf file is still valid but I'm not sure if gnome-settings-daemon overrides those values with Xft resources or not.  There is also the system wide /etc/fonts/conf.d that contains the same sorts of things that exist in ~/.fonts.conf.  Here is an example .fonts.conf I use for non-gnome machines:

```

<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
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

---

### Post by fred6633 on 2009-06-08
I googled a bit and found that Ubuntu has disabled auto-hinting by defalut.

To enble:
sudo ln /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/. -s

Now slight, medium and full hinting make difference.

But I can't say I think the fonts are better looking with auto-hinting enabled.

It seems to be a patent issue with Apple.

I attach three samples. I prefer number 2.

Fred

---

