---
title: "Installed fonts not working"
date: 2009-05-12
forum: General Help
---

### Post by Nima1972 on 2009-05-12
I've installed some foreign, non-Roman, fonts but they work neither in OpenOffice word processor nor Scribus.  The new font can be selected but it just displays typed text in regular English i.e. Roman characters.

Any ideas?  

Thanks.
-Nima

---

### Post by Irihapeti on 2009-05-12
It sounds as though you need to enable a method for inputting non-Latin characters. Scim is already installed in Ubuntu but sometimes needs to be specially setup, particularly if your locale isn't en_US.

So we can help you better, could you tell us: what version of Ubuntu you are running, what your locale is (where you live would be a good indication) and what language(s) you are wanting to use.

Irihapeti

---

### Post by Nima1972 on 2009-05-12
I'm running Ubuntu 9.04 from the US.  I've installed Persian fonts but the other non-Roman fonts don't work either e.g. Japanese.

I switched to Persian (aka Farsi) in the Language Support which changed the OS's language but I don't think that changed the locale.  It wasn't working before the switch.

---

### Post by Irihapeti on 2009-05-12
You can check your locale by entering a command in the terminal: (applications -> accessories -> terminal)

```
locale | grep 'LANG='
```

What output does that give?

If you go to a website written in Farsi or Japanese, do the characters display properly? What happens if you copy some text and paste it into OpenOffice? Does it display properly there, too?

---

### Post by Nima1972 on 2009-05-12
[FONT=monospace]It returns: [/FONT]LANG=fa_IR.UTF-8

The Persian and Japanese websites both display characters properly.  If I copy and paste into openoffice word processor it's in the correct font (Persian).  However when I type in using keyboard I have roman letters.

BTW, from the list to select fonts I see all the fonts in their own shapes.  But the Persian is in English ie courier new is displayed using courier new font.

---

### Post by Irihapeti on 2009-05-12
Everything looks good so far. The next step is to get Scim working.

Again, it's a terminal command:

```
im-switch -z fa_IR.UTF-8 -s scim-bridge
```

Then log out and log in again. You should have a small keyboard icon in your system notification area, next to the loudspeaker icon.

The next thing is to install some software for inputting in Farsi and Japanese.

In the repositories, there are scim-anthy and scim-canna for Japanese, and scim-tables-additional and scim-m17n for Farsi. I know very little about these languages, so I can't suggest which ones will work best. Experimenting is probably the best way.

Then you can configure Scim to use the input methods you want. There's a step-by-step set of instructions here: [http://www.puppylinux.org/wiki/multi-lingual-puppy/technical-how-tos/getting-scim-working-after-its-installed](http://www.puppylinux.org/wiki/multi-lingual-puppy/technical-how-tos/getting-scim-working-after-its-installed)  It's written for another variety of Linux (by me, by the way), but the actual setting up of Scim is the same.

You should then be able to type in the language you've chosen.

If you need further help, please ask.

Irihapeti

---

### Post by Nima1972 on 2009-05-12
There's no option to use Persian (Farsi) in scim.  I looked in Synaptic Package Manager but there are no packages for it.  There are one for other languages which I don't need.

How can I find a Persian input method for scim?

---

### Post by Irihapeti on 2009-05-12
Try scim-m17n. It has an option for Farsi (under Persian). (It has about 40 languages altogether; you can disable the ones you don't need.)

---

### Post by Nima1972 on 2009-05-20
I installed scim-m17n.  I can't find how to bring it up.  It's not automatically in the menus.

---

### Post by Irihapeti on 2009-05-20
> **Nima1972 said:**
> I installed scim-m17n.  I can't find how to bring it up.  It's not automatically in the menus.

None of the Scim packages are automatically in the menus. You need to choose System-> Preferences-> Scim Input Method Setup, and click on the Global Setup under IMEngine. That shows all the language options you have installed.

I've attached a screenshot to illustrate what I mean.

I think it's a good idea to first click on Disable All, and then go back and choose the options you want. You'll need to log out and in again to have your new options working.

To actually input in another script, you need to press control-space. Then a small panel appears in the bottom right-hand corner of the screen.

---

### Post by Nima1972 on 2009-05-21
Actually I got to work.  All I needed to do was to go into keyboard preferences, choose the layout tab and add a new keyboard layout.

---

### Post by Irihapeti on 2009-05-21
> **Nima1972 said:**
> Actually I got to work.  All I needed to do was to go into keyboard preferences, choose the layout tab and add a new keyboard layout.

That would have been my next suggestion if things still weren't working. I once had to add another keyboard for Arabic in another variety of Linux. I didn't need to in Hardy for Farsi, so didn't believe it would be necessary. 

I have to say that scim isn't the most user-friendly program for beginners to set up (and even not-so-beginners).

Anyway, it's great that you've got it working now.

Irihapeti

---

