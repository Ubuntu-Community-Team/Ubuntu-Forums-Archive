---
title: "Does Anyone Know What This Means?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Mark76 on 2006-07-05
> E: lilypond-data: subprocess post-installation script returned error exit status 1


And is there a fix?

---

### Post by xyz on 2006-07-05
Hi
You don't tell us much about it so I'll take a guess...try this out
[http://www.ubuntuforums.org/showthread.php?t=103013&page=2](http://www.ubuntuforums.org/showthread.php?t=103013&page=2)

---

### Post by Mark76 on 2006-07-05
This is turning into a nightmare :(

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I tried doing that and all I get is a >

---

### Post by xyz on 2006-07-06
No matter what command you want to run (or what fixes you're trying to achieve), do it in 'Recovery Mode'...if you haven't already!
Like I said, you don't give us lots of info....
How about the link I indicated? Is it of any help? Is it what you're looking for?
I mean...do your fingertips hurt? Nobody here will be able to help if you don't participate!!!

---

### Post by az on 2006-07-06
[QUOTE=Mark76]And is there a fix?[/QUOTE]
Are you using only ubuntu apt sources?

try

sudo dpkg --configure -a 
as mentioned.

Try 

sudo apt-get -f install

If you got these packages from an outside source, remove them:

sudo dpkg -r lilypond lilypond-data

---

### Post by az on 2006-07-06
[QUOTE=Mark76]This is turning into a nightmare :(



I tried doing that and all I get is a >[/QUOTE]
You must have made a typo.

sudo dpkg --configure -a

---

### Post by Mark76 on 2006-07-06
Yep.  I thought it was all one long continuous string of characters.

Anyway, I've managed to sort out the lilypond problem.  Now, if only the non displaying Gnometab one would go away.

---

