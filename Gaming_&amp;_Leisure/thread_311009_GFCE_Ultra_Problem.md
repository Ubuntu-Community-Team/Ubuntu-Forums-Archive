---
title: "GFCE Ultra Problem"
date: 2006-12-02
forum: Gaming &amp; Leisure
---

### Post by Sandman32 on 2006-12-02
Hey all, I have run into a bit of a problem running roms in GFCE Ultra.  I'll pick a ROM to load and it will just do nothing for a long time.  The options portion will go off the screen but nothing will happen.  

I have noticed that if I go into my directory where I keep all of the my ROMs and I modify a file it will instantly trigger the rom I tried to start into running.  

So for now, as a work around I have one file that I will delete and then restore when I am done.  So I can still use GFCE Ultra, I just need to delete a rom each time to get the one I want to work to run.

Anyone have a clue what could be causing this wierd behaviour?  Or any idea where I'd even start the trouble shooting process?

Thanks for any tips you can give!

Edit: Resolved, I installed the bleeding edge version from svn and it all of a sudden works now, not sure how or why, but at least it works.

---

### Post by Canguçu on 2007-01-10
It also happens to me. See the bug report @ launchpad:
[https://launchpad.net/ubuntu/+source/gfceu/+bug/71161](https://launchpad.net/ubuntu/+source/gfceu/+bug/71161)

---

### Post by SparcMan on 2007-05-23
> **Canguçu said:**
> It also happens to me. See the bug report @ launchpad:
[https://launchpad.net/ubuntu/+source/gfceu/+bug/71161](https://launchpad.net/ubuntu/+source/gfceu/+bug/71161)

The patch in the bug report worked for me.

---

### Post by tareksobh on 2010-03-19
> **SparcMan said:**
> The patch in the bug report worked for me.

Can you help us with applying the patch? GFCE Ultra emulator loads games very slow, but runs perfectly with sound disabled.

> You can apply this patch as well.
 1. save patch in /tmp
2. start terminal
3. cd /usr/bin
4. sudo patch gfceu /tmp/gfceu-0.5.0-slowstartup.patch


I'm getting this error: "sudo: patch: command not found"

---

### Post by soryu on 2010-08-04
my GFCE also runs perfectly without sound.
anyone know how to fix this? 
need some sound.



HEYnOw!

---

