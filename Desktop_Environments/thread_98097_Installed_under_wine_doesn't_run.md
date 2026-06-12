---
title: "Installed under wine doesn't run"
date: 2005-12-02
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-02
Hey, I just installed Finale under wine, but when clicking on the icon on my desktop - nothing happens.

What's wrong?

Thanx

Gabriel

---

### Post by welsh_spud on 2005-12-02
Any number of things. Wine doesn't run all windows programs perfectly.

To see the error message, go into terminal and change to the directory where the actually binary is kept (not the shortcut on your desktop) and type 

```
wine <program>.exe
```


keep the terminal window open and see what it says, however it is probably unlikeley we will be able to fix the problem; wine is still in beta and can't run everything

spud

---

### Post by bluevoodoo1 on 2005-12-03
I got Finale 2003 to run on wine, but I'm getting a Midimap.cfg error... telling me that I need to add it to my windows/system folder. I'm not very good with MIDI. Any ideas?

---

