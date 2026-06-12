---
title: "Thunderbird doesn't move spam to the Junk folder"
date: 2010-06-11
forum: Desktop Environments
---

### Post by arrange on 2010-06-11
Hello all,

I cannot make TB move spam to the respective Junk folder automatically. I've enabled Junk mail control, and TB marks the mail as *Junk*, but it does not move it to *Junk* folder.

[[IMG]http://img813.imageshack.us/img813/4652/tbinbox.png[/IMG]](http://img813.imageshack.us/i/tbinbox.png/)

The problem is that when I want to set the folder in *Account Settings*, all the changes are not saved and always stay the way you can see in the attached screenshot.

[[IMG]http://img815.imageshack.us/img815/4424/screenshotaccountsettin.png[/IMG]](http://img815.imageshack.us/i/screenshotaccountsettin.png/)

I'm using a generic *Local Folders* account which comprises all my email accounts. I'm sure it's not a permissions issue as all the files in *~/.thunderbird* are writable and owned by me.
Do you have a suggestion on how I could resolve this?

Thank you.

---

### Post by arrange on 2010-06-11
I know this is not a matter of life and death, but still I would like to know, so I'm kindly bumping this... :P

---

### Post by azertyh on 2010-06-12
hi,
there are two "junk settings" folders, one in your account and the other in local folders. is the "move new junk ..." ticked in these 2 folders?

---

### Post by arrange on 2010-06-12
Hello *azertyh*, thanks for your reply.
The problem is that WHATEVER I (un)tick on the second screenshot (*Junk settings)*, it always moves back to what you can see in there. Also, there is no other *Junk* folder present than the one in *Local folders* (I can clearly see it when I unfold the tree in *Move new junk messages to - Other* (for this option see the same screenshot again).

---

### Post by azertyh on 2010-06-12
the other "junk settings" folder is in the account samozrejmost@...

---

### Post by arrange on 2010-06-13
The options are the same for all my email accounts and behave in exactly the same way as I described before. The junk settings cannot be changed for any of them.

---

### Post by Ecip on 2010-11-29
This here:
[http://kb.mozillazine.org/Compacting_folders](http://kb.mozillazine.org/Compacting_folders)

---

### Post by arrange on 2010-11-29
Thank you, I've just tried it now, and it didn't help either...

---

### Post by azertyh on 2010-11-29
hello,
in your screenshot, the ""junk" folder on" doesn't specify an account (???).
read that doc [http://kb.mozillazine.org/Junk_messages_not_moved](http://kb.mozillazine.org/Junk_messages_not_moved)

---

### Post by arrange on 2010-11-29
> **azertyh said:**
> hello,
in your screenshot, the ""junk" folder on" doesn't specify an account (???).
read that doc [http://kb.mozillazine.org/Junk_messages_not_moved](http://kb.mozillazine.org/Junk_messages_not_moved)

Hi,

it doesn't specify an account because I'm unable to specify it (and this is my main problem here): whatever I choose from the drop-down menu gets lost after I close (by clicking OK) and re-open the Preferences window. The setting is not saved, but TB doesn't give me any error messages (even if I run TB from the Terminal).

Thanks for the link, I gave all the tips there a try, but still no dice..

---

### Post by azertyh on 2010-11-30
hello,
post your problem on [http://forums.mozillazine.org/viewforum.php?f=39](http://forums.mozillazine.org/viewforum.php?f=39)
i can post there without to be registred.

---

### Post by arrange on 2010-11-30
I'll give it a try. Thanks man :)

---

### Post by arrange on 2010-12-07
Solved. For details see
[http://forums.mozillazine.org/viewtopic.php?f=39&t=2046515](http://forums.mozillazine.org/viewtopic.php?f=39&t=2046515)

---

