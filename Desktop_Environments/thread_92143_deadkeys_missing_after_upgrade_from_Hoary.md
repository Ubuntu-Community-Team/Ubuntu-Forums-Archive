---
title: "deadkeys missing after upgrade from Hoary"
date: 2005-11-18
forum: Desktop Environments
---

### Post by davidm on 2005-11-18
After upgrading from 5.4 to 5.10 I lost the US-deadkeys option in Control Panel=>Regional & Accessability=>Keyboard Layouts. I have to go to web pages to copy accented characters so I can write. I added a bunch of Latin American locales with dpkg-reconfigure locales. Can anyone offer suggestions?

Thanks!

---

### Post by easy_target on 2005-11-18
I am not being able to configure my keyboard for dead keys. I need the accents to write the portuguese characters. Can someone give us a hand?

---

### Post by davidm on 2005-11-19
easy_target, either you and I are the only Kubuntu users in the world who need to write accents with US keyboards, or everybody else already knows how and was just laughing at us. Some Googling led to this site

[http://www.valdyas.org/fading/index.cgi/software/keyboard.comments](http://www.valdyas.org/fading/index.cgi/software/keyboard.comments)

which points out that the us_intl data has been folded into the us file in etc/X11/xkb/symbols/, and also points out the new button in the control panel app called "Layout varient" which lets us choose from a (somewhat strange) variety of mods.

It works, though I miss being able to select deadkeys with the click of an icon on the taskbar.

---

### Post by easy_target on 2005-11-25
I am more of an "icon" guy. Can you tell me how to do this exactly? I feel so frustrated because I have a  lot of texts in Portuguese that need to be correctly accentuated. Thanks a lot!

---

