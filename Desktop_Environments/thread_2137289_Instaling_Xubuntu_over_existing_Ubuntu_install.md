---
title: "Instaling Xubuntu over existing Ubuntu install?"
date: 2013-04-20
forum: Desktop Environments
---

### Post by NanakiXIII on 2013-04-20
I really like Xubuntu and greatly prefer it to the regular Ubuntu/Unity setup. The problem is, I have a computer that runs Ubuntu with a lot of stuff set up that I don't want to have to reinstall. I just want to have Xfce instead of Unity, but keep the rest of the installation.

Now, I'm aware that one can just install Xfce or xubuntu-desktop from the repositories, but the problem is that they are not completely the same as the regular Xubuntu installation I use on my laptop. Those packages don't come with the same themes, keyboard shortcuts, etc. I suppose I could configure all of that myself, but it shouldn't be that much of a hassle.

The second problem I have is that the computer is set up with two monitors. This works without a hitch in Ubuntu, but Xubuntu doesn't seem to support multiple screens out of the box. I've worked with several solutions (such as ARandR), but nothing has really been satisfactory. Since everything works fine under Unity, can't Xfce just use the same drivers to control the screens somehow? The necessary software is obviously on the machine.

---

### Post by Elfy on 2013-04-20
Other than an odd wallpaper issue I have with 2 screens I've not had any issues with arandr.

You could install xubuntu-desktop then remove the ubuntu-desktop files.

```
sudo apt-get install xubuntu-desktop
```

[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

sudo apt-get install xubuntu-desktop
Which 

> they are not completely the same as the regular Xubuntu installation I use on my laptop

bits do you mean?

It's entirely possible you'd be able to backup and copy those configuration changes you've done across to a clean install.

---

### Post by NanakiXIII on 2013-04-20
I've had a lot of trouble with ARandR, at least on my laptop when connecting that to a second screen. It would regularly forget my settings after a reboot or completely mess up the resolution on the second screen.

> Which bits do you mean?

Mainly the Greybird theme that comes with Xubuntu when you install it from the CD. It looks sleek and polished; everything that comes with xubuntu-desktop looks terrible. Also, Xubuntu from the CD is preconfigured with some useful keyboard shortcuts for Firefox, Thunderbird, etc. The CD version just seems more like a finished product; it works out of the box. These are just the differences I noticed within the few minutes I spent mucking about, there might be more. 

This is going to sound super lazy, but while I could of course go and set these things up myself or maybe copy it all from my laptop or something, the CD gave me all this without any hassle and I want to know if there's any way I can get the same thing here. Can I maybe install the desktop environment from the Xubuntu CD?

---

### Post by Elfy on 2013-04-20
The shortcuts on the cd should exactly the same as an installed version. I assume you mean things like super+w for browser. The greybird on the cd is the same as the one I have here.

When you install from the cd - all it's basically doing is copying the image to a partition. 

As far as arandr goes - I read you as having 2 monitors - not 2 monitors sometimes :) I've seen issues with that here.

---

### Post by NanakiXIII on 2013-04-20
> **Elfy said:**
> The shortcuts on the cd should exactly the same as an installed version. I assume you mean things like super+w for browser. The greybird on the cd is the same as the one I have here.

Really? Because I tried installing xubuntu-desktop only yesterday and it looks completely different (I think it did have a theme called Greybird, but it looked different) and doesn't have any of the shortcuts.

---

