---
title: "messing with pSX broke package manager"
date: 2009-08-22
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2009-08-22
Dear All, 

I have sent myself up s*** creek, though I don't know how. I downloaded doing this .deb from a user known as rfrayer, who supplied a very convenient package that bypassed the pulseaudio error that was so common in pSX. However, it turned out that one of my games had only limited compatibility, so rather than use the command line, I decided to use Ultima's pSX front-end. Trying to configure that program should've worked, but there was a permissions conflict with pulse, and I added myself to pulse-rt. No dice. I tried undoing what I had done, only to find that pSX wasn't working. Dismayed, I attempted to purge it using Synaptic, but even that wouldn't work. Now Package Manager won't work at all. I used -f, and it said that psx needed to be reinstalled, but that an archive for it couldn't be found. Any help at all would be appreciated. I just got into the groove with this recent installation, and a system wipe would only be last resort. And sorry for all the text, but I'm scared out of my wits.

---

### Post by BoyOfDestiny on 2009-08-23
Are you getting an error only when you are trying "resinstall" some package in synaptic? 

If so, is it that one you got the package for? In that case, just mark it for removal. Then do what you need for the fix, and reinstall that deb you got manually (probably why synaptic is complaining about a missing package)

---

### Post by MEGAMANULTIMATE on 2009-08-23
Thanks for your reply. I actually can't access Synaptic at all. Here's what happens:

---

### Post by BoyOfDestiny on 2009-08-23
You're welcome.
Sadly never encountered an error like that.

Just a guess, close Synaptic. From terminal do a 

sudo apt-get update

sudo apt-get install bb

(or just pick an app to install, bb is a cool ascii art demo)

See if it gives a better error, and maybe advises a command to try to let it correct itself...

Best of luck!

---

### Post by MEGAMANULTIMATE on 2009-08-23
Tried installing bb, got the same message via terminal: 

```

```E: The package psx needs to be reinstalled, but I can't find an archive for it.

Any other suggestions? I'm getting pretty worried now.

---

### Post by MEGAMANULTIMATE on 2009-08-23
I don't mean to bump only after half a day, but I fear that any more personal work on this will break my system. I mean, I already can't install anything. If anybody has any ideas, don't hesitate to offer suggestions.

---

### Post by ELD on 2009-08-24
This is why you don't ever use random .deb files people send you! That should have been a given for your own security and stability.

Only thing i would know to do is a fresh install.

Although before that try this:
"sudo apt-get autoclean"

In terminal, since it mentions it can't open the cache, wipe it.

---

### Post by MEGAMANULTIMATE on 2009-08-24
Well, I guess I'll have to reinstall. Thanks for your help.

---

