---
title: "Colour display randomly switches to nonsense"
date: 2016-09-25
forum: Desktop Environments
---

### Post by remsirems on 2016-09-25
Hello everyone,

Since I re-installed Ubuntu on my laptop to upgrade it to version 16.04, I am facing an occasional problem with colour display. Most of the time, display is just fine. However, from time to time it switches suddenly to something completely nonsense. As an illustration, see what I should expect to observe on an arbitrary example:

[http://s22.postimg.org/gdwpbe7dt/capture.png](http://s22.postimg.org/gdwpbe7dt/capture.png)

In normal time, I actually get the following, which is just fine:

[http://s22.postimg.org/43rl36cs1/good.jpg](http://s22.postimg.org/43rl36cs1/good.jpg)

And here is what I get when something bugs (photograph taken for the same image in the same conditions):

[http://s12.postimg.org/9ttwhpu31/bad.jpg](http://s12.postimg.org/9ttwhpu31/bad.jpg)

I believe that the problem comes from software rather than hardware, because the problem disappears as soon as I unlog and relog onto my session; moreover, the start of the problem has nothing to do with moving the computer or anything that could disturb hardware.

Here are a few facts on this bug:
*** The bugged image is consistent from time to time: image appears to go wrong exactly the same way each time.**
*** Unlogging and relogging onto my session re-gives a normal image.**
* The image get by taking a screenshot is always the “good” one, even when the display is actually bugging.
* The time before the problem occurs is apparently random, but roughly of the order of 20 minutes.
* I could not link the problem with any specific application (but Thunderbird or Firefox might be involved too, since I have tese applications open virtually all the time).
* Whichever triggers the bug does not seem to be linked with any hardware handling either: most of the time, the bug triggers while I am doing absolutely nothing special.

I could not find any forum post referring to a problem alike :(, so I am asking to you help…

At least, has one any idea of the part of the system which may be involved in this bug? Maybe I should de-install or re-install some packages, but which?…

Do not hesitate to ask me for any software/hardware information for a better diagnosis :)

Thanks in advance,
Rémi

--------------------------------
**IMPORTANT EDIT: THE WRONG COLOURS CORRESPOND TO A 1-LEFT BIT-SHIFT IN THE COLOUR RGB VALUES** (see detailed explanation below)

After further investigation, it turns out that the “nonsensical” colours actually corresponds to a 1-left bit-shift in each of the values of the R, G and B canals. Assume for instance that the colour of a given pixel should correspond to a dark Caucasian skin: (R, G, B) = (231, 158, 109). These are in binary (11100111, 10011110, 01101101). Then the actually displayed colour will be (1100111*, 0011110*, 1101101*) (I am not sure of what the lowest-weight bits are: it could be either the highest-weight bit of the corresponding canal, or the highest-weight bit of the following canal, or always 0, or always 1…—of course I could not make the difference by the naked eye), that is, (206, 60, 218), which corresponds to a kind of lilac!

This precision being given, maybe you have some clues about the reasons for this phenomenon?

(By the way, I was so fed up with this anarchic behaviour of colour that I finally switched from Ubuntu to Debian! (and the problem does indeed not occur under Debian). So I guess that many other Ubuntu users could see this issue as most serious…).

---

### Post by oldrocker99 on 2016-09-25
Welcome to the forums!

I have observed that the screen will dim when the system is busy. It doesn't seem to be connected to CPU activity. It goes away for me within ~10-20 seconds as a rule. You do have some weird color changes, but I have no idea what causes it. If you had no problem running Unity before, it may not be that you don't have enough horsepower in you laptop. However, you might try Ubuntu MATE, Lubuntu or Xubuntu, which have lighter-weight desktops.

---

### Post by remsirems on 2017-01-10
I up my question ;), also adding an important precision on how exactly the colours get wrong! (see the edit above) :)

---

