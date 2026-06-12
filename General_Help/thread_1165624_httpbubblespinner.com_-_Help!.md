---
title: "http://bubblespinner.com/ - Help!"
date: 2009-05-20
forum: General Help
---

### Post by ConnorIRL on 2009-05-20
When I go on this site on my brother's computer, it runs quick and doesn't lag at all, but when I play it on mine, the balls shoot slow and it is very "choppy".  Is this a result of Ubuntu, or something else?  Thanks!

---

### Post by geraldvillorente on 2009-05-20
Your specs please!

---

### Post by ConnorIRL on 2009-05-20
Are there any specific ones you're looking for that would help diagnose this? I just did this one command and it made a myhardware.html and it's a ton of info, I don't want to completely load this page up with useless info. :P Is there any simple thing to type in to get the info I need?

---

### Post by emarkay on 2009-05-20
What kind of PC - how much RAM, what kind of video card (if one was added-  as opposed what came originally)  We can look up the specs if you give mfg. and model number.

Also on the other one - and I presume they are all using the same release of Ubuntu?

EDIT: That's a FLASH game - ensure you have the latest release of flash from adobe.com, and, what browser are you using?

---

### Post by geraldvillorente on 2009-05-20
Your problem is either you are running out of resource(memory, & CPU) or try to update your flash player

---

### Post by ConnorIRL on 2009-05-20
> **emarkay said:**
> What kind of PC - how much RAM, what kind of video card (if one was added-  as opposed what came originally)  We can look up the specs if you give mfg. and model number.

Also on the other one - and I presume they are all using the same release of Ubuntu?

EDIT: That's a FLASH game - ensure you have the latest release of flash from adobe.com, and, what browser are you using?

It's a Toshiba Satellite laptop, with 1 GB of RAM.  It's just the stock video card.  

On my brother's computer, he has 2 GB of RAM running on Windows XP, with FireFox.

I just checked it, and I do have the most recent release.  I'm using FireFox too. Could it just be the ram difference?

---

### Post by geraldvillorente on 2009-05-20
> 
Could it just be the ram difference?

No! Run "top" command and check the behaviour of your system...e.i cpu usage, & memory....
Lets check if who uses a very big amount of resources...

Try the "htop" command...more detailed than "top"
Before you can use this you have to install it first..
```

sudo apt-get install htop

```

---

