---
title: "Japanese bold/blury, Western too bold. A Problem for the ages."
date: 2006-09-13
forum: Desktop Environments
---

### Post by tora201 on 2006-09-13
Sorry if this is the wrong forum. I have spent hours reading and trying all of the techniques in the forums (that I could find) in order to get the fonts up to scratch in Ubuntu, especially for the display of Japanese characters. With all my windows fonts (I did not really like the IP Japanese fonts mentioned in another post)installed and the original Ubuntu ones gone, things are still no better.

The problem is as follows:

ld. If you turn on hinting/smoothing etc, Western fonts are acceptable, but then the Japanese ones are too bold, and it is uncomfortable reading them. (I mean they are just blurry and you can't see detail as easily as in windows).
However, if you turn the settings to monochrome and smoothing completely off, the Japanese fonts (with windows MS P Mincho, MS Gothic, etc) become acceptable and smooth, but then the Western fonts become blocky. 

So, my question is: how to make both sets of fonts work together so that the Western ones are not blocky and the Japanese ones are not blurry/too bolded? :-k 

Cheers.

EDIT: SOLVED. install msfonts (you will also need MS P Mincho, MS P Gothic and MS Gothic from your Windows font directory) following instructions in this post. [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
It is also important to install the XML files as well.

Make sure that your Firefox font settings for Japanese are:

Serif
MS P Mincho
MS P Gothic
MS Gothic

Font sizes should all be 17. (16 was in the original windows version of Firefox, but 17 seems to work better in Ubuntu for some reason). To be absolutely sure I deleted ALL Ubuntu fonts before hand.

You should have an almost pefect display in both Western/Japanese fonts. This probably works for other Asian fonts too.

---

