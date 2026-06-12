---
title: "Steaming Media"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Inhumane on 2006-09-07
How can I enable steaming media support for WMVs in Ubuntu? When I click install plugin in Firefox it directs me to the microsoft.com website... which of course, has nothing for Linux.

I'd also like to know how to tell Ubuntu to change the application for Media, because when I instert my iPod it opens Rythembox instead of Banshee, and I'd like Banshee to be the media player to open up

---

### Post by jimbob on 2006-09-07
You can install the User Agent Switcher extension in FF.

In FF click tools,extensions, get more extensions and search for it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Inhumane on 2006-09-07
Agent Switcher just lies about what type of browser I'm using, it won't enable streaming, but installing w32codecs does :) Just found out about it, thanks anyway. 

Anyone who could help me with my assigning programs to certain problem?

---

### Post by macewan on 2006-09-07
[https://help.ubuntu.com/community/RestrictedFormats#w32codecs](https://help.ubuntu.com/community/RestrictedFormats#w32codecs)

**[SIZE=3]basicly do this:[/SIZE]**

[SIZE=2]Applications > Accessories > Terminal[/SIZE]

**[SIZE=3]When the terminal opens do this:[/SIZE]**
wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)

[SIZE=3][SIZE=3]**When it finishes downloading this file do this:**[/SIZE]

[/SIZE]sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

---

### Post by CatKiller on 2006-09-08
> **Inhumane said:**
> I'd also like to know how to tell Ubuntu to change the application for Media, because when I instert my iPod it opens Rythembox instead of Banshee, and I'd like Banshee to be the media player to open up

System -> Preferences -> Removable Drives and Media.
Click on the Multimedia tab.
Portable music players -> command: banshee
(I'd imagine - I don't have Banshee installed. Whatever the menu entry says, anyway.)

HTH.

---

### Post by jimbob on 2006-09-08
Sorry- I grabbed the wrong extension.

Should have been MediaPlayerConnectivity ver 0.5.5

Take a look at it if the other stuff doesn't work for you ...

---

