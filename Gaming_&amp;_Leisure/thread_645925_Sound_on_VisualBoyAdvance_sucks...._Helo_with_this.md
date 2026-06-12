---
title: "Sound on VisualBoyAdvance sucks.... Helo with this would be appreciated"
date: 2007-12-20
forum: Gaming &amp; Leisure
---

### Post by Espreon on 2007-12-20
In addition it is sooo slow.... Why is this, I set the sound quality to 44KHZ and it stil sucks. Why does this occur? And How do I make it not suck?

Any help would be appreciated.

---

### Post by chronusdark on 2007-12-20
i had similar problems try mednafen it has the visualboy advance engine in it and no sound problems

plus you can play nes gameboy sms and tg16 roms too

its in the repos

---

### Post by Espreon on 2007-12-20
Thanks but:

1. It has no sound

2. Is there a GUI for mednafen?

---

### Post by DoktorSeven on 2007-12-20
I use the following script as a very simple "GUI" for mednafen, since many things are set up in the emulator (shift-alt-1 to set up controller 1 for example):
```

#!/bin/bash
# following should point wherever you want the file selector to point to by default
cd /mnt/wing/emulation
while /bin/true;
do
GAME=$(zenity --title "Select a game or Cancel to exit" --file-selection)
if [ -n "$GAME" ]; then mednafen "$GAME";
else exit
fi
done

```

Just be sure you have "zenity" installed; I believe it's installed by default in the latest versions of Ubuntu.

---

### Post by SyntheticXTC on 2007-12-20
Pretty much any emulation has bad sound issues.  I think alot of it depends on the quality of the rip.  About the only thing you can do with it would be to play around with the settings and see which one works best with your system.  Good Luck.

---

### Post by chronusdark on 2007-12-20
i have zero sound issues with mednafen do you have compiz turned on that can effect it
also make sure your color depth is 24 NOT 16

P.S. are you getting any console output about sound post that if you are

---

### Post by Espreon on 2007-12-20
@SyntheticXTC:

Actually My ROMs play perfectly (perfect sound) on the M$ Winblow$ version of VBA.

@DoktorSeven:

Thanks for the script

@chronusdark:

Thanks for recommending mednafen, even though I experimented with the Windows version of VBA to run in WINE, I got full speed and sound to become perfect after following a tutorial that allows you to run games in a separate X session simeltaneoulsy. I can still use mednafen for emulating NES ROMs if I decide to do so.

And I will try to run mednafen w/o CF running via this method I spoke of.

---

### Post by DoktorSeven on 2007-12-20
VBA runs slowly in Linux because it doesn't use hardware acceleration to draw the screen directly to the card.  Mednafen uses DirectFB to do so, so it's faster.

Edit: Oddly enough, vba seems to use directfb, but it's still slow.  I don't think it used to.

---

### Post by chronusdark on 2008-01-22
i am starting to think its an SDL issue because SDL/Direct X is the only difference between the windows/linux version plus if people are getting it to run faster in wine that adds more to my suspision

---

### Post by Sockerdrickan on 2008-01-22
Obviously you can't blame SDL.

Go to my website if you wan't a GB/C emu with working sound

---

### Post by disturbedite on 2008-01-22
i had somewhat poor performance with VBA on linux but perfect performance on winxp.

---

### Post by Diogo90 on 2009-05-10
Is there any command for "no sound" in VisualBoyAdvance ???

---

### Post by markg48 on 2009-05-11
cud always use no$gba but ull have to run it throught wine tho runs perfect

---

