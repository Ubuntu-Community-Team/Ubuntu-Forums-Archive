---
title: "MS Briefcase equivalent or other file sync SW"
date: 2009-04-08
forum: General Help
---

### Post by dpatel on 2009-04-08
Hi All –

I’m looking for a utility in Linux similar to the functionality I remember of MS Briefcase. Basically what I want it to allow me to do is:

•	Copy a file(s) onto my USB memory stick from my PC/laptop
•	Remember the location of where those files are on my PC
•	I take the USB to another computer, change them etc
•	Plug my USB stick back into the original PC, click ‘Sync’ or whatever and the programme will update the files on my PC with the changed ones from my USB.

I am NOT looking to backup to my whole folder structure to my USB (wouldn’t fit anyway). I just want to be able to do this for the few files I need.

I don’t know if this can be done with rsync/Unison – as I understand it these utilities backup entire folders/folder structures so not really for synchronising a few files.

Anyone know of anything that can do this?

---

### Post by dpatel on 2009-04-17
Any ideas anyone please?

---

### Post by ushills on 2009-04-17
Try unison and the graphical interface in synaptic it will do what you want.

---

### Post by reeseslover531 on 2009-04-17
You can use the GUI or via commandline it is very easy.  Just type: 
```
unison /directory/one /directory/two
```
and that will sync the two directories.  Is that kinda what you were looking for?

---

### Post by ushills on 2009-04-17
You could sync a new folder with links (symbolic?) to the files you want.  Then unison this to a usb drive.

---

### Post by dpatel on 2009-05-04
Sorry for late reply. Thanks for your posts.

I've tried Unison - it's not really what I'm looking for. Say I copy 5 different files from 5 **different** locations on my PC to my usb drive; I want to be able to sync these back. Unison just compares one directory to another.

Any other thoughts?

---

