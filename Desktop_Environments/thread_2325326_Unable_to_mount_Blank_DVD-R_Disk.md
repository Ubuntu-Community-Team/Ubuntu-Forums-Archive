---
title: "Unable to mount Blank DVD-R Disk"
date: 2016-05-21
forum: Desktop Environments
---

### Post by asigurnjak on 2016-05-21
This is copy of my post from Mate forum     whitch  got no solution so far . If anyone here can help   that would be great ! 
Mate 16.04 Ubuntu , when i put in  dvd for burning this is  message i get  :
Unable to mount Blank DVD-R Disk 
Also when trying to associate app with  blank dvd  options are grayed out  like in 14.04 .
I have Brasero  installed  , it works  fine , so far  no problem burning data on dvd or blue-ray dvd . 
Just do not like   warning and not being able to set  default app in  file manager preferences . 

Any idea  will be apprecciated . 

Also after initial  install of Ubuntu Mate   in menu bar  places were not  populated , should i report that as a bug .
Fix was easy , but still ,  it would be better  if i  did not need to fix it .
Here are screenshots for  dvd issue and places  before and after fix

Addendum :
Well , i just installed fresh Ubuntu Mate on spare laptop  and i got same results .  Unable to mount  blank dvd  and unpopulated places in a top bar. 
It does not seems to be  happening only on one pc  and few folk on google plus say they experience exactly same issue .  I now think these are bugs in Mate  and do not know if this is limited to Ubuntu version . 
Next i will download non-Debian-Ubuntu Mate install to confirm this  and  if still  i get same results , i suppose   it  will be time for bug report . 
Mate desktop is so sweet that these few little niggles  should be  ironed out   so  there will be no complaints "But this does not happen in OS X or Win  X " ! 
Of to next step  !
Just  installed  current Sabayon Mate and same  situation ,  can not mount  blank dvd and unpopulated places . 
Of to figure out how to  place bug report with Mate developers  if there is not one  already .
Any workarounds   are welcome !

---

### Post by mcduck on 2016-05-21
Well, the message is correct, you can't mount blank discs, as you mount filesystems, not devices or media, and a blank disc doesn't contain a filesystem.

That being said, getting a message about that seems pretty pointless, the blank disc should be ignored by everything else than a program capable of burning optical media.

---

### Post by kansasnoob on 2016-05-21
It's a bug that's been ignored since 12.10:

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1069964](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1069964)

---

### Post by asigurnjak on 2016-05-21
Well that make sense ,  thank you .:D
[COLOR=#333333][FONT=monospace] I loaded up dconf-editor and searched for media handling in gnome and mate section. I deselected all of the automount features and the annoying message has gone away (for now at least)..
This is quite  , well , rude ! Ubuntu devs know  there is something broken  in gvfs, or gio  , but have no intention of fixing it .
Maybe instead  reinventing the wheel  with Unity they could  spend some time  catching up with bug reports and sqashing them . 
Having   this as one of many issues  they choose not to fix will not help  Linux gain wider popularity . [/FONT][/COLOR]

---

### Post by mc4man on 2016-05-22
> **asigurnjak said:**
> Well that make sense ,  thank you .:D
[COLOR=#333333][FONT=monospace] I loaded up dconf-editor and searched for media handling in gnome and mate section. I deselected all of the automount features and the annoying message has gone away (for now at least)..
This is quite  , well , rude ! Ubuntu devs know  there is something broken  in gvfs, or gio  , but have no intention of fixing it .
Maybe instead  reinventing the wheel  with Unity they could  spend some time  catching up with bug reports and sqashing them . 
Having   this as one of many issues  they choose not to fix will not help  Linux gain wider popularity . [/FONT][/COLOR]

This is a Gnome issue - try filing an upstream bug if you'd like some action on it.

---

### Post by asigurnjak on 2016-05-22
I suppose that is next step . It is same behaviour across distributions .

---

