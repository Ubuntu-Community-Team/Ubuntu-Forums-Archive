---
title: "Grub, XP First?"
date: 2009-02-27
forum: General Help
---

### Post by bouncer5 on 2009-02-27
Was looking at editing my grub file so XP is first on the list and therefor it will boot after a certain peroid of time, Could someone edit it for me? I Dont want to mess it up.

---

### Post by brokenLockpick on 2009-02-27
it is not too difficult to edit

The number after the word "default" controls which is picked automatically you count starting from 0 down the list of possible choices, in your case 3 should point it to windows.

---

### Post by Slim Odds on 2009-02-27
> **bouncer5 said:**
> Was looking at editing my grub file so XP is first on the list and therefor it will boot after a certain peroid of time, Could someone edit it for me? I Dont want to mess it up.

Where it is in the list does not matter.

There is a line with "default". This is the index of the entry that is used by default. Just change that.

---

### Post by howefield on 2009-02-27
I am sure someone will take a look, but another easy way of changing the default boot order is to install startupmanager.

Do a search in Synaptic, (can't remember if I got it through the default repository or medibuntu)

Video on this site will give you an idea of what it is about.

[http://www.getdeb.net/app/Startup+Manager](http://www.getdeb.net/app/Startup+Manager)

---

### Post by bouncer5 on 2009-02-27
I've dont it before but I can't remember, It looks differnt from last time, That's why I asked someone to edit for me :P

---

