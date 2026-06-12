---
title: "copy and save desktop themes hw?"
date: 2011-03-24
forum: Desktop Environments
---

### Post by ottosykora on 2011-03-24
How can I save desktop themes so I can use them on other computer?

Example: one older computer runs ubuntu 8.04 and I wouldlike to transfer one desktop themes from it to let say 10.04?

---

### Post by Copper Bezel on 2011-03-24
When you save a theme in Appearance Preferences, it's saved to a hidden folder in your home directory. Go to your home directory, hit Ctrl+H, and browse to .themes. Find the one you want to copy, and move it to the same location on the new computer. 

If it's using a specific icon theme or GTK/Metacity skin that isn't in the defaults, you'll have to copy those folders, too. The skins will be in the same .themes directory, and icons will be in .icons (also under your home directory.)

---

### Post by ottosykora on 2011-03-24
hmm, this unfortunately does not work on my side. The hidden folder themes is there, but nothing in it.
The aim is simply to set other computer to the same desktop theme. This was avaiable in 8.04 and not in 10.04, so I wanted to transfer it somehow with usb stick. But on all computers , the themes folders are empty, not single file i it.
So there must be some other place where those thigs arre hiding.

---

### Post by Copper Bezel on 2011-03-24
So you're using one of the default themes, then? They're in /usr/share/themes .

---

### Post by ottosykora on 2011-03-24
yes found them there, will try to transfer it from there

---

