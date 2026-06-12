---
title: "Can't find MS fonts"
date: 2007-02-24
forum: Desktop Environments
---

### Post by allwin on 2007-02-24
I used Automatix to install the MS fonts.  However, in the Gnome FONTS preferences and Firefox, I don't see them anywhere.  I am using something like Freesans, but the characters are a little wider than MS and so web pages look strikingly different, and don't show as much info on the screen.

I presume the names changed and I just don't recognize them...OR...did I fail to take some step to turn them on fully?

---

### Post by yabbadabbadont on 2007-02-24
They should be installed in /usr/share/fonts/truetype/msttcorefonts

Do you see them there?

---

### Post by allwin on 2007-02-24
Yes, I see them there.  Now I see them in the drop downs.  I might have confused myself because I've installed and re-installed things.  HOWEVER...I have a KVM switch here, so I can browse a web page with XP on one machine and the same one under Ubuntu Gnome Firefox 2.  They don't look the same, switching back and forth.

I'm wondering if the choice of fonts on the web pages themselves are not being made differently on Ubuntu?  That is, how can I be sure that say, Firefox, isn't interpreting a request for an Arial font on a web page to resolve as simply something like SANS SERIF?  Where would that font subtitution table be?  Or to put it another way, if a web page just asks for a sans serif font, how can I make it choose ARIAL instead of something like freesans?

I'm not so much insisting that Ubuntu look just like XP...but I'd also like to learn where the levers are for changing these things.

---

### Post by yabbadabbadont on 2007-02-24
"man fonts-conf"  will provide some of the information for which you are looking.  You should also look around in the /etc/fonts directory tree.  Also, if you are using Gnome, I think it's font settings sometimes override the fonts that other applications would normally use.  It's all very messy and somewhat confusing as to exactly where the final decision is made.  :-?

Edit: I should have said, "It's all very messy and confusing to me"  ;)

---

### Post by kerry_s on 2007-02-24
open a terminal->
sudo su 
cd /usr/share/fonts/truetype/msttcorefonts
mkfontscale
mkfontdir
fc-cache -f
restart X (ctrl+alt+backspace)

---

