---
title: "Fonts and Breezy"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Watter on 2005-10-20
**Warning: Long, but possibly instructive post ahead!**

I thought I'd share my font experience. There's some good font information [here]("http://ubuntuforums.org/showthread.php?t=20976&highlight=tahoma") that I followed when I installed Hoary, but, for me at least, Breezy was a little different. Before starting here's some facts about my setup so that you'll know whether or not the following might be useful for you:

[list]
[*]I'm using Kubuntu, not Ubuntu (not that relevant as .fonts.conf applies to both)
[*]I'm using an LCD monitor (Dell 2001FP), not a CRT
[*]I'm a real believer in simplicity; the fewer changes I need to make from the defaults to get where I want to be, the better I feel about it
[/list]

First off, kudos to the (K)ubuntu team on Breezy's default fonts setup. I had to screw with Hoary for days before I got the basic font setup looking good. Breezy came up after a fresh install looking fabulous. The fonts were extremely crisp but well hinted, with no bulkiness or fuzziness.

At this point my .fonts.conf looked like this (I think):
```

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
```

The problems began when I installed the standard msttcorefonts package. The only one I did any testing with was Verdana as displayed via Firefox on several web pages. It looked pretty bad. I'm not a guru when it comes to font terminology, but I believe the issue had to do with hinting. It was most noticeable on letters like &#8220;k&#8221; and &#8220;x&#8221;. It appears that parts of the letter are faded out to some degree. I'll call this the k/x effect from now on. Anyway, it looked bad. Considering how good the default fonts looked, I said, &#8220;screw it&#8221; and just uninstalled the msttcorefonts package. Everything look good again... well, almost.

The problem is that so many pages use the MS fonts by default and their spacing and layout almost rely on having those specific fonts in place. CNN is a good example. It's readable with DejaVu Sans or Bitstream Vera Sans (I know, I know, they're the same thing for English), but it really doesn't look &#8220;right&#8221;. A more serious problem is that the task I use my workstation for is the development of web applications, and I really need to see my pages the same way most of my users do. I use VMware to run IE for functionality testing along with Firefox on linux, but I didn't want to have to fire up VMware every few minutes just to check basic appearance.

So, after a few days of a Verdana-less system, I gave in and reinstalled msttcorefonts. I now had to figure out how to make them not look so crappy.

I don't know why the default fonts in Breezy look so good without autohinting, but they do. In any case, I recalled having turned on autohinting in Hoary so I gave it a shot here. My ~/.fonts.conf file now looked like:
```

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
  <edit mode="assign" name="autohint" >
    <bool>true</bool>
  </edit>
</match>
```

Hey! That seemed to work. Kind of. My test page containing lots of Verdana looked decent. The k/x effect seemed to be gone, but unfortunately there were some pretty nasty side effects. My beautiful default fonts were now all fuzzy and less distinct. It wasn't horrible, but it was a noticeable step back from their pre-autohinting crispness. The second problem, and one that sends shivers down the back of most LCD users, was that the Verdana font I was testing now had a little blue and red hinting around the edges. Yikes!

Ok, this was clearly unacceptable. I wasn't going to sacrifice the crsipness of my fonts just to get Verdana looking halfway decent. Fortunately, fonts.conf provides a mechanism to get around this. You can tell the font engine that you only want to apply a particular setting to a specific font. As my main concern was Verdana, I decided to focus on that. Here's what my ~/fonts.conf looked like after making this change (notice, I also simplified the setting text):
```

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
<match target="font">
  <test name="family">
    <string>Verdana</string>
  </test>
  <edit name="autohint">
    <bool>true</bool>
  </edit>
</match>
```

Well, that worked for the most part. Verdana still looked a little fat and indistinct, but it was far better than the choppy, k/e effect that it originally had. More importantly, my default fonts looked like their normal, great selves. So, now to address the second problem of blue and red hits around the letters. 

It took a ton of searching, but I finally found someone who had put up a how-to involving [linux fonts and LCDs]("http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=397"). While I disregarded most of his how-to, he did mention an interesting tidbit about disabling sub pixel ordering by setting "rgba" to "none". he claimed that X should already know the right sub pixel order and that overriding it can cause problem on LCDs. Sure enough, this worked beautifully. Again, as my original fonts were perfect as far as I was concerned, I only wanted to apply this to Verdana (in the future, I may do the same for any of the other MS fonts that appear to need it). 

My final ~/.fonts.conf ended up looking like this:
```

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
<match target="font">
  <test name="family">
    <string>Verdana</string>
  </test>
  <edit name="rgba">
    <const>none</const>
  </edit>
  <edit name="autohint">
    <bool>true</bool>
  </edit>
</match>

```

With these few changes I managed to preserve my good looking default fonts, and get an acceptable, if a little fuzzy looking, Verdana for those pages that need it. Will this be useful to you? Who knows, but hopefully, the descriptions of how I ended up with these settings and what their specific effects were (at least on my system) will help you figure out your own optimal setup.

**Questions Remain:** While I can certainly live with the above setup, I'm still a little troubled. I'd like for my Verdana and other MS fonts to look as nice and crisp as my default ones do. What's odd is that at larger sizes (with autohinting off) they do! It's only at small sizes that the the k/x effect comes into play. Why would that be? It seems like there are some rules being applied to those specific fonts at small sizes that aren't being applied at larger sizes, or vice-versa. I'd love to figure out what is happening there so that I can get the same level of crispness with Verdana as I do with DejaVu Sans and my other default fonts.

---

### Post by indusnecro on 2005-11-07
I got the same problem in Ubuntu.
But I got around this in Ubuntu using

**sudo dpkg-reconfigure fontconfig **
and selecting autohinter. 
I think this will not work in Kubuntu

---

### Post by Glauco on 2005-11-09
Yes, it works in Kubuntu.

---

### Post by GoldBuggie on 2005-11-09
hmm..if its perfect windows look you want then you have to change you dpi to 96. I currenlty have 108 which I think is sooo beautiful. But windows and many fonts are configured properly for 96, which also looks crisp on Linux. Changing the dpi also effects how sizes of the fonts look. dpi of 108 makes smaller fonts some what larger and with 96 its the other way around(hmmm I hope this one makes sence).

Anyway...

Check which dpi you are using by going to *KInfoCenter -> X-Server.*

To change dpi:
```
sudo kate /etc/X11/xorg.conf
```
then add
```
DisplaySize     270     203     #1024x768 - 96dpi
```
to the **Monitor** section.

---

