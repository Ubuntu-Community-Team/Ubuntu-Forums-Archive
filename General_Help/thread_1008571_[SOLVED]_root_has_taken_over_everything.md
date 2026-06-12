---
title: "[SOLVED] root has taken over everything"
date: 2008-12-11
forum: General Help
---

### Post by sydbat on 2008-12-11
Seriously. Not sure what I did (or maybe didn't do) but now everything seems to be owned by root and I cannot change the permissions in Nautilus (sudo nautilus). This seems to have happened after updating yesterday via update manager, although I just noticed it now.

I know I am missing something. Any suggestions?

EDIT - I also notice that all my partitions have "unknown" as the owner, but show root when checking properties. Never had anything listed under their designations before.

EDIT2 - It seems as though I can still access and use the partitions like before. I wrote a test page in Ooo and saved, then opened it and edited it, then saved again and opened it with no problems. Am I simply going loopy?

---

### Post by |{urse on 2008-12-11
does "sudo su" give you the ability to set the permissions back to what they should be?

Try checking your console history and see what you may have done to cause this.

type 

> history

press enter

---

### Post by sydbat on 2008-12-11
I did sudo nautilus a few days ago to put a couple of MS office fonts into the Ooo fonts folder. That's about it.

And should I sudo su nautilus?

---

### Post by sydbat on 2008-12-11
Did sudo su and now it gives me ```
root@my-desktop:/home/me#
```

---

### Post by bodhi.zazen on 2008-12-11
What do you mean "everything is owned by root"

What directories and files re off ?

---

### Post by |{urse on 2008-12-11
yeah "sudo su" allows you to become root to administer the system. BE VERY CAREFUL WITH THIS COMMAND (okay, maybe that didnt warrant all caps lol).

---

### Post by sydbat on 2008-12-11
Oh it does require all caps. Really.

So now that I have the root prompt, how do I change the permissions back to me?

---

### Post by sydbat on 2008-12-11
> **bodhi.zazen said:**
> What do you mean "everything is owned by root"

What directories and files re off ?The best way I can describe it is, if I were to check the permissions of my partitions yesterday, they belonged to me. Today they have root or, as in the image below, 'unknown' in blue letters underneath the partition names.
[ATTACH]96069[/ATTACH]
On my desktop I have 2 folders that link to a partition and they have root underneath the name of the folder.

I hope this makes sense.

---

### Post by sydbat on 2008-12-11
I don't think i will worry about this yet...unless I cannot access things. It might just be a glitch?? Might need a reboot to clear it up?? Oh well, I have the 8.04 Live CD if anything borks...

---

### Post by sydbat on 2008-12-12
I feel like I need to wear a helmet! Turns out that I had changed a setting in File Management Preferences the other day that I totally forgot about. In the 'Display' tab I chose 'Owner' from one of the drop down boxes and that is why [COLOR="Blue"]root[/COLOR] started showing up everywhere.

Please flame me now. I deserve it.

---

