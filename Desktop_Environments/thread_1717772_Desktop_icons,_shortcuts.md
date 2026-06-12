---
title: "Desktop icons, shortcuts"
date: 2011-03-30
forum: Desktop Environments
---

### Post by mrush336 on 2011-03-30
hello all. Im new to Ubuntu and have a simple question? When I open a places location and then close it there appears on my desktop an icon or shortcut rather of the place or hard drive where I was. Is there a way to stop this? To prevent the icon from showing up? I notice after shutting down and booting back up the icons are gone. its a minor inconvienence but I have looked everywhere in the settings and cannot find a way to turn this feature off. Any help will be much apprieciated thank you.

---

### Post by ~Plue on 2011-03-30
you mean you want to hide the partitions from the desktop?
if so, press alt+F2 to bring up the run dialog and enter *gconf-editor *
then, navigate to *apps > nautilus > desktop  *and uncheck 'volumes visible'

or, you could install [ubuntu-tweak]("http://ubuntu-tweak.com/") and use it to change the visibility of the icons (among many other things)

---

### Post by AndyCinDallas on 2011-03-30
Bear in mind that it's showing you that it's mounted a drive or partition or shared folder (or whatever) - so you can always right-click on the icon and click "unmount" - and it's gone ;)

---

### Post by mrush336 on 2011-03-31
Ok thank you. right clicking on the icon that looks like a hard drive and selecting unmount does make it disappear. but is there a way to prevent them from showing up in the first place? im a little ocd about my desktop being neat and organized and i go crazy when programs put shortcuts on my desktop that i did not want! lol thank you in advance

---

### Post by mrush336 on 2011-03-31
ok i installed ubuntu tweak and unchecked the show mounted volumes box and that took care of it. thank you all for the help.

---

### Post by sorrow413 on 2011-04-08
im have been useing linux for dayliy use for a about two years now and i love it the freedom the ability to find lots of free things and  the fact that since i have been useing linux i have goten alot better at doing alot of computery things any way  im not good at doing some of the more advance things in linux i  have a friend who knows loads more than me about ti but hes not around  and i have a hard time getting to talk to him so ill ask here plez forgive me if this is a moronic question but is their a terminal command for hiding everything on the desktop  temperately and hotkeying that to a button so that if you want to just hid it all you just push that button if so could someone plez tell me and before you bitch at the fact that i cant spell for the life of me  i have a hard time spelling and my spell check is like for what ever reason doesnt like me lol

---

### Post by Krytarik on 2011-04-08
Simply create a keyboard shortcut for this command, hoping you generally know how to do that:
```
gconftool-2 /apps/nautilus/desktop/volumes_visible --toggle
```
LOL:D Funny thing!

---

