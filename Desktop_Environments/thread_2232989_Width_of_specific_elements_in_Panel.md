---
title: "Width of specific elements in Panel"
date: 2014-07-05
forum: Desktop Environments
---

### Post by r_avital on 2014-07-05
Hello all,

Using Mate 1.8 (under Ubuntu 14.04) -- I'm aware that  there is a MATE desktop forum, and I've posted this question there  without much success so far, so I'd like to see if I can get better  answers here.  Thank you in advance for your patience.

I have a  single panel, at the top of the screen. I would like to increase the  width of one specific "element" of the panel, namely the keyboard  indicator.

Right now it is square (I believe it's 22 pixels  square, I could be wrong), with "en" in it on a grey background. In  dconf-editor, I can easily turn the "show-flags" item to true and  display a flag. But then the flag is square, which is wrong, it should  be rectangular.

After looking extensively, I don't believe this "icon" is an image file of any kind. I'll explain:

When  I run under Unity, that particular icon does not have "en" in it, but  "En" -- see the difference? This is an *.svg image file. SVG files are  just XML files with or without image info in them (they can contain  "raw" image data in the form of long strings of characters, or a link to  an actual image file). In that SVG file, you can easily find the string  ">En<" plus height and width settings. Those files are usually in  "/usr/share/icons/ubuntu-mono-dark" -- or "ubuntu-mono-light" followed  by "/status/22/" and there's a whole bunch of them for each language.  They are NOT used under MATE.

I did not find either a text file  of any sort (xml, svg) with the string ">en<" -- which is what  this "icon" is displaying under MATE, or any true image file (png, jpg,  etc) that looks like it. If anyone knows of such a file, by all means,  please let me know.

As far as enlarging in gimp, sure, that's  easy enough, but you see, my image for, say, a U.S. keyboard (named  us.png) is ALREADY rectangular, but displaying it in that location  squeezes it (or crops it) so it's square, not rectangular, so stretching  it even more won't do a thing.

Somewhere in some panel  configuration file, there's probably a setting for an alloted space for  whatever displays in it, be it the string "en" or an image flag. I would  love to find out where that is and if it's possible to enlarge the  width a bit.

I did find /usr/share/mate-panel/layouts/default.layout, but it's not in that file either.

Any ideas, anyone? 

TIA :)

---

