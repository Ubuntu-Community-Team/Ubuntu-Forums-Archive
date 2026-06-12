---
title: "Firefox fonts different in Gusty compared to Fiesty"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by gungazoo on 2007-10-31
I just upgraded my Ubuntu to Gusty and immediately noticed that the fonts used in Firefox are different (and in my opinion not as good).  Where I primarily notice this is in Gmail.  Does anyone know what I can change to get the old fonts back?

Thanks,

Peter

---

### Post by timcredible on 2007-10-31
since you did an upgrade, there may be a setting that's messed up.  try quitting firefox, opening a terminal session and do ```
 mv .mozilla .mozilla-old
``` and then restart firefox.  if the fonts look good, then that means you had a setting messing things up.  the bad part of this is that if you had cookies and save passwords and bookmarks, you'll need to get them back, which is doable, but i don't remember the files you'd need to copy back into the .mozilla directory off the top of my head.

---

### Post by gungazoo on 2007-11-01
Actually for a test I did a clean install of Gusty on my home machine last night (although it was the 64bit version) and the fonts are different there as well.  And, by different, I mean different than they were for Feisty.

Is there an easy way to figure out what the settings were in Feisty so that I can set them on Gusty?

Peter

---

### Post by caldesign on 2007-11-10
Your not wrong. The fonts are very ugly under gusty. I have been looking for a fix, but have found no fix thus far. Ended up reinstalling feisty. :(

---

### Post by Happy_Man on 2007-11-10
Really? perhaps you guys forgot about msttcorefonts.....

```
sudo apt-get install msttcorefonts
```

---

### Post by gungazoo on 2007-11-14
I checked and did not have msttcorefonts installed.  I installed it, removed my .mozilla, restarted Firefox and had the same ugly fonts.  I assume that msttcorefonts was installed under Feisty but am not sure.  I did an upgrade of my Feisty so I would have thought that if it were there under Feisty it would have been there under Gusty.

I'm thinking about going back to Feisty as well but would much prefer to just figure it out.

Thanks for your help.

Peter

---

### Post by zdude on 2007-11-14
I too, had noticed poor fonts with the upgrade in FF. I them noticed in Edit>Preferences>Content you can choose a font - my default was blank. I am now close to where I was at in Fiesty. YMMV.

---

### Post by gungazoo on 2007-11-16
Ok -- I've reinstalled Feisty and have screenshots from both.  I'm sorry for the size but I didn't want to hit any compression issues w/ jpgs so I left them as png files.  I see a *very* significant difference in the two.  I'm hoping someone can help me setup Gusty to look as good as Feisty.

Here is Feisty showing an email and then Gusty: (be sure to click on the image to expand it)

[http://pjanderson.googlepages.com/Feisty-email.png/Feisty-email-full.jpg](http://pjanderson.googlepages.com/Feisty-email.png/Feisty-email-full.jpg)
[http://pjanderson.googlepages.com/Gusty-email.png/Gusty-email-full.jpg](http://pjanderson.googlepages.com/Gusty-email.png/Gusty-email-full.jpg)

Feisty then Gusty showing a search:

[http://pjanderson.googlepages.com/Feisty-search.png/Feisty-search-full.jpg](http://pjanderson.googlepages.com/Feisty-search.png/Feisty-search-full.jpg)
[http://pjanderson.googlepages.com/Gusty-Search.png/Gusty-Search-full.jpg](http://pjanderson.googlepages.com/Gusty-Search.png/Gusty-Search-full.jpg)

Feisty then Gusty on Gmail login page:

[http://pjanderson.googlepages.com/Feisty-Gmail.png/Feisty-Gmail-full.jpg](http://pjanderson.googlepages.com/Feisty-Gmail.png/Feisty-Gmail-full.jpg)
[http://pjanderson.googlepages.com/Gusty-Gmail.png/Gusty-Gmail-full.jpg](http://pjanderson.googlepages.com/Gusty-Gmail.png/Gusty-Gmail-full.jpg)

I would really appreciate any help in fixing this.

Thanks,

Peter

---

### Post by TreverT on 2007-11-18
I had to fiddle around a good bit to get my internet fonts looking good too.  Here's my solution:

```
Edit>Preferences>Content
```

My default font is actually left blank.  I got my biggest improvements from the advanced settings changes - Here is what mine is set to.  One crucial one is the "min size", because before setting that, FF was making many fonts just way too small to read.  Here are my current settings:

[[IMG]http://s226.photobucket.com/albums/dd25/serious_t2/th_fontsetting.png[/IMG]]("http://i226.photobucket.com/albums/dd25/serious_t2/fontsetting.png")

And here are a couple of sample page screen caps of Firefox on Ubuntu 7.10:

[[IMG]http://s226.photobucket.com/albums/dd25/serious_t2/th_samplepage.png[/IMG]]("http://i226.photobucket.com/albums/dd25/serious_t2/samplepage.png")

[[IMG]http://s226.photobucket.com/albums/dd25/serious_t2/th_sample2.png[/IMG]]("http://i226.photobucket.com/albums/dd25/serious_t2/sample2.png")

---

### Post by ElemonGW on 2007-11-18
At Firefox:

Edit-->Preferences-->Content-->Fonts & Colors-->Advanced

There select:

Proportional: Serif
Serif: serif
Sans-serif: sans-serif
Monospace: monospace

These are the defaults at Feisty (at least I think so)...

EDIT: You may also need to specify at:

Edit-->Preferences-->Content-->Fonts & Colors

serif as the default font

---

### Post by VuDu on 2007-11-20
Does anyone know a decent not too wide font for firefox?
The default ones on Ubuntu are just too wide compared to the ones on windows and many pages look ruined because of that.
I don't like using msttcorefonts because of the "ms" on their name :D
The ideal would be using a free "open" font that looked as smooth as ubuntu's native fonts and didn't mess up the webpages.

---

### Post by stunner on 2007-11-20
I unchecked "Allow pages to choose their own fonts" in Advanced and set sans-serif as my overall default font.  I left everything else untouched.  Google looked better immediately.

---

### Post by ColombianGold on 2007-12-09
I had a similar problem and the only way to solve it was to remove mstt fonts via synaptic, everything went back to normal...although I dont know what will happen to open office.

Hope it helps.

CG
:guitar:

---

