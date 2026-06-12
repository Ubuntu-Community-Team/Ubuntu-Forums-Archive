---
title: "Xubuntu application fonts"
date: 2006-05-12
forum: Desktop Environments
---

### Post by Jason-X on 2006-05-12
I have Xubuntu Dapper installed on my iMac. It works really well and I want to stick with it. I have just one problem and that is with the application fonts. They looked just fine when I first installed it but after and update they have gone a bit small.

I could always change the size in the "User Interface Settings" but it then makes the application fonts for Firefox too big. Firefox is one of my most used applications and I am happy with the fonts just the way they are.

Has anybody else had this problem and if so is there a fix for this. 

Many thanks Jason

[ATTACH]9378[/ATTACH]

---

### Post by K.Mandla on 2006-05-12
I've had  a similar problem on an Inspiron 8000 laptop. I generally set the system fonts how I like them, then use the advanced fonts settings to make Firefox behave properly.

In Firefox, click on Edit > Preferences > Content > Fonts & Colors Advanced. I use the Other setting on Display Resolution, then measure the line they show and give it your answer. From there it scales the fonts much more accurately.

Good luck! ;)

---

### Post by Jason-X on 2006-05-12
Thanks for the reply.

I've tried this and it only seems to effect the web page text. The problem I have is the Firefox interface font. I have increased the size of the XFCE interface font a bit so that it is not too small, but this has made the interface font on firefox bigger.

I suppose I can live with it, but it would be nice to have some consistancy between applications.

Cheers Jason

---

### Post by darkolo on 2006-05-19
Read this page:
[http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

---

### Post by Jason-X on 2006-05-19
Brilliant it worked! Thanks for the link.

If anybody else has this problem, heres what I did:

In the terminal type:

$ xdpyinfo | grep dimensions
$ xdpyinfo | grep resolution

to find out your resolution and DPI. My DPI turned out to be 75dpi.

Next type "about:config" in the address bar of Firefox. Scroll down to "browser.display.screen_resolution". Mine was set to 96, So I changed it to 75.

Restart Firefox and the fonts are the same as the system fonts. Although now some of the webpage fonts looked a bit small so I went to Preferences > Content >Fonts & Colours > Advanced. I set the "Display resolution" to "System setting" and "Minimum Font Size" the 11.

Everything now looks sweet:)

---

### Post by darkolo on 2006-05-20
I used this:
For example, if you use a 17" CRT display, your viewable screen dimensions will be approximately 328 mm wide by 246 mm tall. This actual size can usually be forced by adding:

	DisplaySize	328	246

to

	Section "Monitor"

in /etc/X11/XF86Config or /etc/X11/xorg.conf, as applicable on your system. If you are running a 1400 X 1050 resolution with a 328 mm X 246 mm display, your system will be running at an actual 108 DPI. In most cases, this change will be sufficient to correct your problem.

If the above change improves your system, but the result is less than 100% to your satisfaction, you can tweak sizes up or down by making the DisplaySize dimensions slightly larger or smaller than actual.

Unfortunately, variations in the implementations of X mean display size reconciliation as above won't be a solution on every system. Failure here seems to be common on newer systems using fontconfig instead of legacy xfs.

Many systems using fontconfig have the regular file /etc/X11/Xresources. On many of these systems, adding to this file a line:

	Xft.dpi: 108

The solution was found putting Xft.dpi: 96  ~/.Xresources.

---

