---
title: "new to ubuntu and wont boot after upbate, please help me..."
date: 2010-02-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yakekaj on 2010-02-19
After the latest update I have been unable to boot ubuntu, I am left with this message before I select which Kernal I want to use:

GNU Grub Version 1.97~Beta4

[Minimal BASH- Like line editing is supported.  For the first word, TAB Lists possible command completions.  Anywhere else this TAB list possible device/file completions]

sh: grub>



Please help me....

---

### Post by mörgæs on 2010-02-20
So, does this mean that everything worked fine before a recent update, and you have always been on 9.10?

---

### Post by oldfred on 2010-02-20
Is this a wubi install? Suggested solutions here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by yakekaj on 2010-02-22
9.10 was working fine, after a bit of hassle sorting out the wireless internet.  I installed from a disc through windows vista and have the option of booting either ubuntu or vista.  Vista works fine (well as good as it ever worked), but when I select to run ubuntu it gives me the message above....:confused:

---

### Post by yakekaj on 2010-02-22
> **oldfred said:**
> Is this a wubi install? Suggested solutions here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


OK yes this is a Wubi install, I wanted to try ubuntu be fore fully committing since my computer skills are limited.

I have taken a look at the solutions through the above link, but dont seem to be able to move the download to 'C:'

When I click on the link it ask if I want to open or save so I select save.  The download window opens, but I cant seem to get any further as clicking on wubildr just asks which programme I want to open it with....

Like I said, my computer skills are limited.... Where should I go from here???:confused::confused::confused:

---

### Post by mörgæs on 2010-02-22
Sorry, can't help. I dropped Windoze completely and have never tried Wubi.

Maybe you could add Wubi in the title of the thread to get the right attention.

---

### Post by oldfred on 2010-02-22
The instructions say not to try to open it but just move it.

Don't try to open the file. Move the file to "C:\" to replace the faulty "C:\wubildr". (to get to "C:\" go to "My Computer" or "Computer" and double click the "C:\" drive) 
Note here, that wubildr needs to be placed into the partition containing Wubi. So if Wubi is not on the C:\drive, the above instruction need to be modified: Use the drive letter of the partition containing Wubi in place of "C:".

---

### Post by yakekaj on 2010-02-23
Thank you... Yes I see that you aren't supposed to open it, but using I'm Firefox and there seems to be no option that I can see to just move the download to C: or replace the existing faulty one...  This is the bit I am stuck with now, how to actually move the new download to replace the faulty on.  I have checked with Firefox help, but that just shows how to open the downloads...

---

### Post by yakekaj on 2010-02-23
OK, just realised that I have been really stupid and have managed to move the new download to  C: in the very simple way that you move any other files around... DOH!

Thank you for your help, the problem is solved and I am now writing this from Ubuntu....

---

