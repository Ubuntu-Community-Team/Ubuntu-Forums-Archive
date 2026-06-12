---
title: "Making a copy of Home folder"
date: 2009-02-19
forum: General Help
---

### Post by Felessen on 2009-02-19
What I want to accomplish here is copy my Settings and UI effects from one machine to another, was told all I needed to do was copy my /home folder.  All my attempts at getting this done have failed.  I either can't have access even if I sudo nautilus, or the copy fails too many files due to access rights or w/e.  If its even possible which I'm sure it is, some help on accomplishing this would be nice.  BTW, the only way I can get this off the host machine to the other is by means of DVD.

---

### Post by Therion on 2009-02-19
Take a look at **Quickstart**.  This tool will allow you to backup your /Home folder quickly and easily, plus a whole lot more.
Be sure to follow the instructions for intstalling; it's easy-peasy lemon-squeezy but you DO need to follow the very basic instructions.

[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

---

### Post by perrti-y02 on 2009-02-19
from my experience of trying to do this the major problem is that it tries to copy a huge number of meaningless files that live in the ".Trash" folder.
I think in theory you could copy each folder the you think you will need individually; a bit tedious but you can choose which you want.

---

### Post by grndslm on 2009-02-19
> **perrti-y02 said:**
> from my experience of trying to do this the major problem is that it tries to copy a huge number of meaningless files that live in the ".Trash" folder.Or to not be tedious, just delete the trash and go about copying the rest of your /home folder, which you should mostly need all of.  You can go in the trash app and select "Empty Trash" or you can simply "rm -r .Trash/" from a terminal.

Not rocket science by any means.

---

### Post by dcstar on 2009-02-19
> **Felessen said:**
> What I want to accomplish here is copy my Settings and UI effects from one machine to another, was told all I needed to do was copy my /home folder.  All my attempts at getting this done have failed.  I either can't have access even if I sudo nautilus, or the copy fails too many files due to access rights or w/e.  If its even possible which I'm sure it is, some help on accomplishing this would be nice.  BTW, the only way I can get this off the host machine to the other is by means of DVD.

You can just burn a DVD of your /home folder - or more specifically your user folder inside /home. I use k3b as my burner program, it seems a bit more flexible then the others.

BTW, all of your settings etc will be in (hidden) "." folders and files in your home directory, if you just want these then the data won't be that much at all.

---

