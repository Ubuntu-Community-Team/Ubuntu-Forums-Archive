---
title: "Help needed: Evolution IMAP folders do not show up. Mails neither."
date: 2009-01-03
forum: Desktop Environments
---

### Post by jesuspresley on 2009-01-03
Hi, 

I set up my IMAP account on Evolution in a fresh Hardy install - worked just fine for a few days.
After a few tweaks to the system the complete folder tree is gone. Evolution fetches mails and connects to the server, but nothing is displayed:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98544&stc=1&d=1230984713[/IMG]

What I possibly did before was installing some plugins for Nautilus, but because I was setting up a lot of software I can't really judge when the error occurred. 

I tried downgrading Evolution, I removed most of the optional plugins - no effect.
I therefore also removed all the Nautilus plugins.

[INDENT]
My evolution version is: 
Evolution 2.22.2 
My Nautilus version is:
Nautilus 2.22.5.1[/INDENT]

I will use Thunderbird meanwhile, but it would be nice to have a decent evolution installation running. 
Can anyone help me debugging this?

---

### Post by jesuspresley on 2009-01-04
Funny enough, "Add/Remove..." has also stopped displaying folders. 
Synaptic still works fine, so I assume it's not a bug in package management.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98708&stc=1&d=1231102475[/IMG]

That's way too much. I need help!

---

### Post by jesuspresley on 2009-01-06
Maybe I have to move this thing - or give it a [Ubuntu] prefix. No one seems to have an idea.

The problem gets really annoying. 
Isn't there anyone who knows how to get rid of all this?

---

### Post by jesuspresley on 2009-01-10
I solved the "Add/Remove..." issue using [this post]("http://ubuntuforums.org/showthread.php?t=1035402"):

> **namdung said:**
> ```
sudo apt-get --reinstall install gnome-app-install
```

But evolution is still the same. 
I will try with a similar command.

---

### Post by jesuspresley on 2009-01-14
OK, problem solved. I reinstalled Evolution and all of the packages. This was not necessary at all. Why?

The sidebar [where the folders are displayed] was completely hidden. I could have just switched it back on by clicking > View > Layout > Show sidebar Then of course, I have to maximize the width of the sidebar which was reduced to zero before.

---

