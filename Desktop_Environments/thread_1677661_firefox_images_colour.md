---
title: "firefox images colour"
date: 2011-01-29
forum: Desktop Environments
---

### Post by snisarg on 2011-01-29
the default browser that came with ubuntu, firefox, has a problem with displaying images.

for some reason, at times, it just inverts the colour of the images (blue is shown as pink, bright white is displayed as pitch black). I have tried reinstalling firefox, (and had even reinstalled ubuntu once, and this problem still persists). 

Is it something to do with my Ubuntu CD? is there a solution?

---

### Post by Frogs Hair on 2011-01-29
This happened to me a couple of times and I thought it may have had something to do  with hitting a key combination . Each time I had made a mistake on the keyboard , but have not  been able figure out what caused it. and it hasn't happened  since .

---

### Post by H-Racky on 2011-01-29
It happens whey you press Winkey + M

Used to happen to me when I wanted to minimize the open windows. :lolflag:

---

### Post by Frogs Hair on 2011-01-29
> **H-Racky said:**
> It happens whey you press Winkey + M

Used to happen to me when I wanted to minimize the open windows. :lolflag:

Thanks! since it hasn't happened more than twice so I never put much effort into figuring it out.

---

### Post by snisarg on 2011-01-29
NO NO!

you all are mistaken. winkey + M is the command to actually invert everything.

i said, only the images are having the problem. Text colour and other components are normal. I haven't inverted or changed any other settings for that matter. Also, its not direct inversion that would have normally, just something like a distortion.

---

### Post by Frogs Hair on 2011-01-29
Sorry , misunderstood I had something possibly similar that affected font only in Firefox and I was able to correct it by changing the rendering settings in Appearance Preferences > Fonts .

I had strange colored halo on the edge of the black fonts and when I changed the settings for best contrast it disappeared . That was on 10.04 , my previous release.

As for the images I don't Know the answer. If it is only in Firefox I would check the error console for warnings or errors.

---

### Post by Frogs Hair on 2011-01-29
The Mozilla forum has a large number of posts on this problem from different versions of Firefox with no solutions.

The link has a possible work around , but seems unrelated given you have reinstalled Ubuntu removing the user profile.
[http://pleasemakeanote.blogspot.com/2008/09/firefox-blurry-images.html](http://pleasemakeanote.blogspot.com/2008/09/firefox-blurry-images.html)

---

### Post by hardclip on 2011-03-01
Hi,

I had the same issue.......presumed it was something to do with firefox 3.6.x until this morning when I jumped to the 4.0 beta and the issue was still present.....

there is an entry under about:config called "gfx.color_management.mode" with a value of 2 set (presume this is the default setting) -> setting this value to 0 and restarting firefox worked for me....unable to comment on any undesirable side effects as yet, will post if I notice any....

---

### Post by Frogs Hair on 2011-03-01
> **hardclip said:**
> Hi,

I had the same issue.......presumed it was something to do with firefox 3.6.x until this morning when I jumped to the 4.0 beta and the issue was still present.....

there is an entry under about:config called "gfx.color_management.mode" with a value of 2 set (presume this is the default setting) -> setting this value to 0 and restarting firefox worked for me....unable to comment on any undesirable side effects as yet, will post if I notice any....

Good to know , thanks !

---

