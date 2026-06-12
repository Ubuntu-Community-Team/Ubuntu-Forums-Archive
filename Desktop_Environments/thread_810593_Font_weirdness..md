---
title: "Font weirdness."
date: 2008-05-28
forum: Desktop Environments
---

### Post by walkeraj on 2008-05-28
I just upgraded to Hardy, and I'm noticing some strange behavior with some of my fonts.

In particular, when the characters "fi" are typed together, there is some strange deformation in certain fonts.  In this case, it seems to be the "sans" font, but there are lots of examples.  This is best described visually, so I've included a screenshot.  The firefox session on the right shows the differences clearly.  Please note that I'm not changing the font or anything like that.  Look also at the "n" in the gedit window.  Both it and my lowercase "m"s are deformed.  The "Unfiled" in tomboy notes is pretty evidently wrong, too.  This appears all over my system.

---

### Post by Zorael on 2008-05-28
I'm actually getting something similar though not as severe. On [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm), search for an occurence of 'different'. Two f:s together makes it intrude upon the following characters. Also, selecting the text makes the fonts grow/shrink somehow.

Tagging thread for interest.

---

### Post by walkeraj on 2008-05-28
Update: scrolling through the generic font preferences dialog, I have shown this problem to occur with the following fonts:

DejaVu Serif
Dingbat (and similar fonts like opensymbol, so it's whatever is being used to fill in for the missing characters)
"sans"
sawasdee
"serif"

Soo... it's looking like some kind of font mapping problem.  Something to do with fontconfig?  I deleted ~/.fontconfig to no avail.  It seems to have changed other fonts gnome is using, but not those.

---

### Post by netron on 2008-05-29
i too have been having font issues with Hardy

here's a screenshot of site in firefox
[http://i29.tinypic.com/2wd66fp.png](http://i29.tinypic.com/2wd66fp.png)

this was publicised on the Drupal website , which has a screenshot of how it should be rendered:
[http://drupal.org/node/261340](http://drupal.org/node/261340)

has anyone figured out WHY hardy is having so many font issues?  this simply was not a problem in Gutsy.  

Ubuntu has gone backwards with this release.

( i've tried completely fresh installs too - and the same font issues are occuring...)

---

### Post by walkeraj on 2008-06-02
Bump.

---

### Post by mcduck on 2008-06-02
That combining of 2 (or more) letters together is called "ligature" and it's actually considered to be a good thing, something that computer fonts have lacked until recent times when modern fonts and font rendering has developed to a stage where it's possible to do ligatures..

[http://en.wikipedia.org/wiki/Ligature_(typography)]("http://en.wikipedia.org/wiki/Ligature_(typography)")

The reason why you only see it with some fonts is that these are the most "advanced" fonts and others just do not support ligatures yet.

---

### Post by L815 on 2008-06-02
I used to have the same issues even after installing msttcorefonts.

How I fixed my problem:
-If you have a windows partition, copy all the fonts to your /home/user/.fonts directory 
-Press ctrl+h to see if the folder already exists, if not create it
-Open terminal, type fc-cache

And then I went to Preferences -> Appearance -> fonts -> details
-Changed Smoothing to Subpixel (for lcd) and hinting to slight or medium, whichever you like best.

That made my fonts look so much better :)

---

### Post by walkeraj on 2008-06-02
Excellent reply.  I didn't even think about ligatures!  However, considering as ligatures exist for a similar purpose as kerning (increased readability), they shouldn't fundamentally alter the letter-form, and in this case the difference really is quite jarring.  Please see the following screenshot (and annotation) from a thunderbird session.

The first line is the glyphs as they appear individually.  The second is the ligature-ized (for lack of a better word) appearance, followed by one that I made in the gimp from the individual letter-forms by removing the tittle from the 'i' and kerning them together.  You can see that they're quite different,  and they really shouldn't be.

---

### Post by mcduck on 2008-06-03
The way I've understood ligatures the point really is to alter the shape of the letters to combine them smoothly together, not just to adjust the spacing of letters. Of course it's always the font designer's choice how to do that and how much to change the shape..

---

### Post by walkeraj on 2008-06-03
Sure thing, there is a lot of leeway in how the glyph looks, but take a look at the screenshot attached to my first post.  It's pretty evident in a couple of examples that these ligatures are breaking the line metrics.  In the lefthand example, the glyph goes below the baseline.  In the righthand example, it's pretty obvious that something somewhere is wrong with the ascender metric, as identical letterforms are not as high as each other when made into a ligature.  Look at the difference between the f letterform and its height in the 'ff' ligature.  Something looks wrong, which is why I wrote this post in the first place.  It almost looks like it's pulling the ligatures from some other font.

---

### Post by mcduck on 2008-06-03
I suppose that would be just because ligatures are still so new on computer use, so there's lots of room for improvement in their rendering.. And probably in the fonts themselves as well.

I agree that the example on the right on your first post looks really horrible :D

I suppose using italic font doesn't really help, and if the font used happens to be a "fake" italic that would break things even more.. Fake italics are quite common in web use anyway, as usually people just use italic tags instead of actually defining some italic version of a font..

---

### Post by hugmenot on 2008-06-04
The deformation is due to the hinting process. Ligatures are made by the typographer when two letters would collide in the natural setting. Some fonts need this, some don't (e.g., if the hood of the f is short). The proper way to gauge how the letter shape looks is to really increase the text size. It should look all natural. When using small text size kerning is not natural but snapped to integer pixels. An unresolved fi may have 1px distance, but the fi ligature may have a fractional bearing (say 1.6) and the hinting will snap this to 2px distance. Could be improved by usng less strong hinting.

---

### Post by EricDB on 2009-05-30
This has been driving me nuts for a long time, too.  I can confirm that it's related to hinting, but changing from full to medium or slight did nothing to help--only disabling hinting completely got rid of the problem.

When I do set hinting to "None", I notice that the ligatures always look the same, and it's the "regular" text that now matches the ligatures.  This leads me to guess that ligatures are not being hinted, regardless of the chosen level of hinting.

---

