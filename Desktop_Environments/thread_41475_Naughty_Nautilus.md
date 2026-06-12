---
title: "Naughty Nautilus"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-13
My Nautilus has no back button (or any other), menu bar, or address bar. I had a version once that did and it was very likable. There is nothing in any menu or control pannel to enable these crucial things.

Everytime i open a folder, the window re-sizes. This is annoying, as it always goes to hyper-small mode. I'd like nautilus to always run maximized, and to open every folder in the curent window. Can I do this?

I'd also like to turn off the coloured rows if that is possible. As a newbie, they're just a bit far from home at the moment.

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]My Nautilus has no back button (or any other), menu bar, or address bar. I had a version once that did and it was very likable. There is nothing in any menu or control pannel to enable these crucial things.

Everytime i open a folder, the window re-sizes. This is annoying, as it always goes to hyper-small mode. I'd like nautilus to always run maximized, and to open every folder in the curent window. Can I do this?

I'd also like to turn off the coloured rows if that is possible. As a newbie, they're just a bit far from home at the moment.[/QUOTE]
 For the old Nautilus look, use "Browse" rather then open. The other thing is called Spatial mode, and yes it can be switched off

To disable nautilus spatial: use gconf-editor and set **/apps/nautilus/preferences/always_use_browser** to true.

---

### Post by Dave_is_sexy on 2005-06-13
I don't have /aps in my filesystem... which is a shome cos i really miss an equivilent to 'program files'

can you give it to me, as navigate to X folder and change X file?

---

### Post by tread on 2005-06-13
> /apps/nautilus/preferences/always_use_browser 

refers to a key .. Go to APplications->System->Configuration Editor and follow the path.

---

### Post by Kimm on 2005-06-13
you dont quite understand what desdinova means..

Open the Configuration Editor (equailent to Windows regedit), browse to:

apps -> nautilus -> preferences

and set the value "always_use_browser" to true, its that simple

---

### Post by Dave_is_sexy on 2005-06-13
YAY! Oh thank goodness! We're getting there.... ^_^ :-)

---

### Post by Dave_is_sexy on 2005-06-13
OK,,, this is why I was root. On my user account, the gconf settings are the same as they are in root (weird since i never changed them as dave) but... even tho alwas use browser is checked, it doesn't work like that.  ](*,) 

root teminal now (surprisingly) says this:

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

which is practically what it says for everything

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]OK,,, this is why I was root. On my user account, the gconf settings are the same as they are in root (weird since i never changed them as dave) but... even tho alwas use browser is checked, it doesn't work like that.  ](*,) 

root teminal now (surprisingly) says this:

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

which is practically what it says for everything[/QUOTE]
 From a normal console, to run a graphical program as root

gksu program-name

---

### Post by Dave_is_sexy on 2005-06-13
Yeah i still get the message. And the always_use_browser is on.. but it does'n hae any effect. Is it broken already?

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]Yeah i still get the message. And the always_use_browser is on.. but it does'n hae any effect. Is it broken already?[/QUOTE]
 Out of interest try

xhost +

then try again

---

### Post by Dave_is_sexy on 2005-06-13
It says

root@D5:/home/dave # xhost +
access control disabled, clients can connect from any host
root@D5:/home/dave #

Is that good?

---

### Post by desdinova on 2005-06-13
For now yes - try running the same command line that got that error message before

---

### Post by Dave_is_sexy on 2005-06-13
Works now ^_^

let me re-phrase that... the error message is gone. I still don't have nice browser windows

---

