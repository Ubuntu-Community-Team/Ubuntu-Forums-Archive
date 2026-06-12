---
title: "matlab fonts"
date: 2013-06-25
forum: Education &amp; Science
---

### Post by kalyp on 2013-06-25
Hello,

I know that lots of people have posted about the problem with font sizes in matlab and how to solve it by installing xfonts-100dpi and xfonts-75dpi (e.g. [this thread]("http://ubuntuforums.org/showthread.php?t=1762805")). Which worked for me. 
The issue is that those fonts are not high enough resolution. I attach 2 figures generated with the exact same code in my ubuntu (12.04) and from a colleague on windows (I think) - saved as tiff then cropped & converted to jpg for upload here. The first is the ubuntu one - very pixelated. I imagine because those fonts are 100 dpi and I saved at 300 dpi resolution (needed for publications standards...).
[ATTACH=CONFIG]244169[/ATTACH][ATTACH=CONFIG]244170[/ATTACH]

Anybody has any solution for this??? like, higher resolution fonts, ways to go around this? (I know I can save as ps and then convert, but it's kind of a pain).

Thanks a lot in advance...

PS in case someone has matlab running on a later version, I'm interested to know if the same problem exists. I don't really want to upgrade if it doesn't fix the issue since I'd rather stay LTS.

---

### Post by LCollins on 2013-10-06
Yes, I would love an answer to this as well.

---

### Post by kalyp on 2013-10-09
I actually ended up asking the Matlab support - they were very good about it (I didn't actually believe they could solve that but they did!). Basically there was no truetype fonts in my path for whatever reason. He could tell that from the command
```
xset -q | grep font
```
As for adding truetype font he pointed me towards [this link]("http://forums.debian.net/viewtopic.php?f=5&t=103877#p496207") and it worked using DejaVu (standard font in the /usr/share/fonts/truetype folder).

I actually didn't fully solve the issue because DejaVu is not that great of a font (but didn't have the pixellation problem) and I got stuck at the next step which was download and install a truetype helvetica font. Somehow matlab was still using his helvetica when I was trying to call the new one. Also, in the link above they create /usr/share/X11/xorg.conf.d/04-fonts.conf to add the font permanently and that didn't seem to work. At that point I gave up :) - if you solve that further I'm more than interested as that would still make my life easier! For now I keep the pixelation for the figures I don't care about, and for publication figures I save them as .ps and then open them in gimp to convert to tiff / jpg.

Let me know if you have any questions about this - if you pm me I can forward the emails I exchanged with matlab support.

---

### Post by roland65 on 2013-11-14
Thanks for this great tip! It worked and I even was able to install all my truetype fonts and let them recognized by Matlab R2011a on Ubuntu 13.10.
Here is the way :

1. Copy all your truetype fonts (*.ttf files) to /usr/local/fonts/truetype

2. Create a fonts.scale and a fonts.dir in that directory:

sudo mkfontscale /usr/local/fonts/truetype/
sudo mkfontdir /usr/local/fonts/truetype/

3. Create the file  /etc/X11/xorg.conf.d/04-fonts.conf with the following content:

Section "Files"
  FontPath "/usr/local/fonts/truetype"
EndSection

4. Logout and then login.

You can check that your fonts are available with:

xset -q |grep font
xlsfonts |grep <your-font-name>

And then, all the fonts from the truetype dir are available for Matlab graphics.

---

### Post by kalyp on 2013-11-14
Awesome, I'm glad you got it to work! 

Did you manage to install a truetype helvetica? that's the one I was after... Thanks!

---

### Post by Balinus on 2014-04-28
To have "beautiful" fonts, you also need:
gsfonts-X11
gsfonts-other

on top of xfonts-100dpi and xfonts-75dpi.

Reboot and labels should be much better.

---

### Post by kalyp on 2014-05-06
This totally solved the problem (that I still had) for me. Thanks a bunch!!!

---

### Post by mörgæs on 2014-05-06
Good, please mark the thread 'solved' using 'thread tools'.

---

