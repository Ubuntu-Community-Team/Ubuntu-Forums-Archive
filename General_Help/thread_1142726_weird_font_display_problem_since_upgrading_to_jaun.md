---
title: "weird font display problem since upgrading to jaunty jackalope"
date: 2009-04-29
forum: General Help
---

### Post by prickos on 2009-04-29
Hey guys,

I'm having a major problem since upgrading to jaunty jackalope, various programs now display fonts in a manner that I can not read it. I've seen it popping up in Skype, Sun VM Virtualbox and KeePassX. I've attached screenshots so you can see what I see. Any ideas? I have already tried to turn off the advanced effects and such but it didn't change..... 

Weird and really hard to use!

Justin

---

### Post by cmisub on 2009-04-29
I have seen the same thing.  I have a 7-year old HP laptop on which I previously had installed Ubuntu 8.04, which did _not_ display this same weird behavior.  I have installed both Xubuntu and Ubuntu 9.04 in the past few days, and noticed this font corruption on both the installed versions as well as the Live CD versions!!  I have noted that by playing with the font display parameters in the Preferences->Display dialog you can sometimes clear up the problem, but in a short time the corrupt display returns.  My suspicion is that it is a problem with font rendering in the X server, that is particular to my system.  I've tried to figure out what graphics chipset is installed on this old laptop, but cannot find any admin application that displays it.  I don't have any other ideas as to how to fix it.:(

---

### Post by johnthemong on 2009-05-02
I have just upgraded to xubuntu 9.04 and have run into a major problem with Thunderbird (so far the only ap I've found with the problem anyway). The font throughout the application is way to small to be read. Everywhere else it seems ok so far. Could really do with a bit of help from anyone out there who can fix it. Tried mucking with display stuff but that brings problems everywhere else. If someone finds and answer, I'd love to hear it.

---

### Post by Yashiro on 2009-05-02
It's a QT bug. Go into your font preferences and try changing the LCD/font smoothing options.
(don't select vrgb based options)

---

### Post by johnthemong on 2009-05-02
> **Yashiro said:**
> It's a QT bug. Go into your font preferences and try changing the LCD/font smoothing options.

Thanks so much for getting back to me Yashiro. Unfortunately and sorry for being lame but I've looked on the QT configuration thing and couldn't see anything about LCD or font smoothing. Nor when I looked under display and appearance in the xfce settings manager. Any other suggestions?

---

### Post by Yashiro on 2009-05-03
If you disable all font smoothing and LCD optimizations does this not correct the display problem?

I'm talking about your generic xfce display settings not anything specifically relating to QT widgets.

---

### Post by johnthemong on 2009-05-03
Ok so this is what I tried. I went into the Settings manager and looked under display. That let me alter the screen size, refresh rate and rotation. Didn't think any of them were what you were talking about so I went into the appearance part. There I could 
[LIST]
[*]enable/disable anti-aliasing (and I have no idea what that means)
[*]select a level of hinting
[*]change sub-pixel order 
[*]apply a custom dpi setting (is that fact that I am using my tv (720p flat screen tv made by LG relevent here?)
[/LIST]

I had a play with all of the above and got nowhere with them. Try as I might, I can't find anything anywhere about 'font smoothing' or 'LCD optimisation'. Everything worked fine under Xubuntu 8.04. Kinda wishing I hadn't upgraded.

Hardware info if it's any help.#
System is based on a Nano ITX VIA embedded board (1Ghz + 1gb ddr)
Monitor as described above is a PAL 720p TV through a RGB (or is it VGA connection)

Thank for getting back to me again by the way. Sorry for my rather wordy reply.

---

### Post by Yashiro on 2009-05-03
If changing those options (No hinting, no anti aliasing, rgb sub pixel order) and logging out then in changed nothing then I have no more ideas.

---

