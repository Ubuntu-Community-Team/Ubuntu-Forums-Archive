---
title: "Need help making Ubuntu Hebrew enabled...not localized"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Ingla on 2005-10-23
Hello.

I'm running Ubuntu 5.10. I'm almost totally new to Linux and this is the first distro I've actually tried to get running.

I need to be able to use Hebrew (and other languages...but I'm concentrating on this one on the assumption that European languages have been more thoroughly discussed and will be relatively simple if I can get the Hebrew up).

I've installed every Hebrew support pack I could find. However, I see no Hebrew fonts anywhere. I have no idea how to make a changeable keyboard such as one finds in Windows. I don't mind if it's somewhat more complicated to change languages, but so far see no way to do it AT ALL.

I installed Lyx, which CAN write Hebrew, but this won't help with e-mail or other tasks.

I followed a link to something called Kazit. It looks however like an all Hebrew localized distro. I can't find anything about making Ubuntu Hebrew enabled without changing the entire thing to Hebrew. I don't want to do that.

I know someone (not available at the moment) who is running some distro using KDE who says he has Hebrew functionality...I don't know how total.

From the little I understood reading up on Open Office, it seems to be separate from the general environment and would need to be specifically enabled for other languages.

Also, I installed Abi writer because it is supposed to be able to write in numerous languages. I can't see any way to get it to write anything but English.

I really need to be able to write documents, type in Gimp (or whatever), write e-mails, and just about anything else in Hebrew.

I've seen posts here and there suggesting I have to make different users with different default languages. I have no idea how to do that either as I see no sign anywhere that the languages packs I installed had any effect at all on anything.

Is it possible that Gnome can't handle this? Would Kubuntu be a better distro (because of KDE)? Can KDE be added to Ubuntu? As you can see, I'm pretty much totally in the dark.

Any help would be very much appreciated. 

Thank you very much.

---

### Post by LorenzoD on 2005-10-23
I'm sure you can get Gnome to work. But am sadly very ignorant about Hebrew. You need to have Hebrew fonts installed as well as a Hebrew keymap. I'd love to help you but the truth is I've got to get just a few hours of rest. If you don't give up on Ubuntu for another few hours I promise that I'll get you all the answers you need first thing when I wake up.

---

### Post by 3david on 2005-10-27
to add the ability to write hebrew in all (well.. most) applications in gnome:

- goto System\Preferences\Keyboard\Layouts
- press "Add", and select "Israel" (don't expand the israel item, just press it)
- goto the "Layout Options" tab and under "Group Shift/Lock behavior mark "Alt+Shift changes group"

to see which language you're using, right click the panel, and add the "Keyboard Indicator" applet

this will let you write in hebrew in firefox, gaim, openoffice, abiword, gnumeric, ...

---

### Post by Ingla on 2005-10-28
Hi.

Thank you. Got all that working. One problem remains. There don't seem to be any Hebrew fonts available to OpenOffice (except one). 

I installed the Culmus font package and...after a lot of attempts...got most programs to read them (but not Open Office). I saw somewhere that there's supposed to be a bug fix for this but haven't found anything useful.

Other programs seem to have no problem accessing the new fonts, so I don't think there's anything wrong with how I installed them.

Any idea how to get some regular Hebrew fonts in?

Thanks very much.

---

### Post by parktownprawn on 2005-10-28
hi
don't have any presonal experience with using hebrew on ubuntu but
according to [https://wiki.ubuntu.com/HebrewLocalizationHowto]("https://wiki.ubuntu.com/HebrewLocalizationHowto")  there is a hebrew localization package for openoffice.
try
```
 sudo apt-get install openoffice.org-l10n-he
```

---

### Post by Moonbuzz on 2005-10-28
Which does remind me to test Open Office for Hebrew.

Speaking of which, does anyone know how to make the hebrew fonts in Opera a bit less horrible? They look like a bad horror movie titles.

---

### Post by bgalan on 2005-11-15
[QUOTE=Ingla]Hi.

Thank you. Got all that working. One problem remains. There don't seem to be any Hebrew fonts available to OpenOffice (except one). 

I installed the Culmus font package and...after a lot of attempts...got most programs to read them (but not Open Office). I saw somewhere that there's supposed to be a bug fix for this but haven't found anything useful.

Other programs seem to have no problem accessing the new fonts, so I don't think there's anything wrong with how I installed them.

Any idea how to get some regular Hebrew fonts in?

Thanks very much.[/QUOTE]

Hey Ingla,

i write hebrew in openoffice using the font from the society of biblical literature, you can find it here: [http://www.sbl-site.org/TechResearch/TechResearch_SBLFontFoundation.aspx](http://www.sbl-site.org/TechResearch/TechResearch_SBLFontFoundation.aspx)

I can only write consonants since the font is unicode and vowels look really crazy (it works like a charm in windows, but i'm trying to leave windows behind...).

i install the font in /usr/X11R6/lib/X11/fonts/truetype/openoffice, where i have other truetype fonts that i use with openoffice (like greek, ugaritic, moabite, etc).

i hope this is helpful for you :) 

benjamin

---

### Post by Ingla on 2005-11-16
Thanks for the reply.

I've since learned there is some sort of problem with Open Office reading the Culmus fonts from the file they install themselves in. I put them in ~/.fonts and all programs can read them. Also put some TTF fonts there, with no other installation.

It seems all writing programs look for fonts in several places, but they all seem to look in ~/.fonts.

Thanks again.

---

