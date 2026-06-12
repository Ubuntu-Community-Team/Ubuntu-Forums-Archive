---
title: "msttcorefonts dont show up in synaptic"
date: 2006-03-05
forum: Desktop Environments
---

### Post by OffHand on 2006-03-05
Hi

The MS fonts don't show up in my synaptic.
apt-get install msttcorefonts doesn't work either.
I got Universe and Multiverse repositories enabled.
Does anyone know what I am doing wrong or is there another way to do
this without too much hassle?
I prefer not to use Automatix.

Thanks in advance,
Subsonic

---

### Post by CallsignBaron on 2006-03-05
You may need to make sure you have all your repositories enabled and updated. I just ran Synaptic and searched msttcorefonts and the package is there.

---

### Post by OffHand on 2006-03-05
Thanks for your reply but like I said in my first post I got Universe and Multiverse repositories enabled  ;) 
To be sure I unchecked them, reloaded the list, checked them again and reloaded again. There is def way more fonts with Universe and Multiverse repositories enabled but msttcorefonts isn't in the list.

---

### Post by OffHand on 2006-03-05
This is the error message if it helps: 

Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

---

### Post by Spano on 2006-03-05
Replace your /etc/apt/sources.list file with one from this page:[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by OffHand on 2006-03-05
That worked, thnx. Should I replace the new list with my backup again or is it ok to keep using that list?

---

### Post by Ramses de Norre on 2006-03-05
Those servers work better then most local servers, so I'd keep using them.

---

### Post by OffHand on 2006-03-05
Ok, I will keep those then  :)
BTW: will the synaptic also use this list now? (after reload?)

---

### Post by Ramses de Norre on 2006-03-05
Yes, sources.list is used by apt, synaptic and update manager (and maybe others?).

---

### Post by Spano on 2006-03-05
> That worked, thnx. Should I replace the new list with my backup again or is it ok to keep using that list?

That's a good question.  Psychocat was/is a moderator on this forum and I have been running with this sources.list for 3 months without problems.  I think it's fine.  Don't really know the difference between Psychocats sources.list and the official version.    
Can someone enlighten me?
If you go back to your originl list the installer and fonts will still be on your machine and I think they still show up in Synaptic should you decide to remove them.

---

