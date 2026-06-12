---
title: "hp device manager - invisible menu fonts"
date: 2009-04-22
forum: General Help
---

### Post by kasl33 on 2009-04-22
I have Ubuntu 8.10 and I constantly send faxes through the HP Device Manager - Send Fax.

When that window opens after I go to print and select my hp all in one fax printer, the window pops up and you can see text on the buttons, but no where else.

For example, in the list where my outgoing faxes are stored or the lists of who i am sending the faxes to, it is blank. However, if i click on the list, you can see a flicker of what's there, but then it goes away (in a split second). See the picture below to know what I'm talking about:

Where you see the line highlighted in blue, there is supposed to be text there - and there is, but you can't see it.

This happened in Ubuntu 8.04 as well and somebody had a simple fix for it that works, but after extensive Googling, I cannot seem to find an answer anymore.

[IMG]http://outklaw.com/images/random_web_pic_storage/pic.png[/IMG]

---

### Post by Irony on 2009-04-22
This is just a guess but whenever I come across these sort of things I just delete the configuration folder. i.e. right click on the device manager icon and quit out of it. Locate the folder;

```
~/.hplip
```

Delete it (or rename it), then start the device manager;

```
System > Preferences > HPLIP toolbox
```

---

