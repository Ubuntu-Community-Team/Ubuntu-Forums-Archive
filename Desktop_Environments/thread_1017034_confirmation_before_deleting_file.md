---
title: "confirmation before deleting file"
date: 2008-12-20
forum: Desktop Environments
---

### Post by twallstr on 2008-12-20
I wonder how to configure Nautilus to ask me to confirm that I want to delete a file before it actually does it. Now I just click delete and file is gone.
Ubuntu 8.10
Nautilus 2.24.1

Thanks!

---

### Post by 73ckn797 on 2008-12-20
> **twallstr said:**
> I wonder how to configure Nautilus to ask me to confirm that I want to delete a file before it actually does it. Now I just click delete and file is gone.
Ubuntu 8.10
Nautilus 2.24.1

Thanks!


Open file manager. Places/Computer

Click edit/Preferences/Behavior

check off "Ask before emptying trash or deleting files." (if it is not checked)

---

### Post by twallstr on 2008-12-22
Tried it but it does not work. Files are still deleted without any warning/confirmation.

/twallstr

---

### Post by jonobr on 2008-12-22
one mans trash is another mans treasure.

I always liked the way linux and unix in general assumed I was sure of what I was doing that it didnt ask then reask.

Anyway, the options outlined previously will only prompt you once you go to empty the trash , uncheck it will just empty trash unprompted.

Im wondering, if you delete and you have confirmation in the trash, would that not be good enough?
Ie if you delete, its not really gone, just moved to a different location which you can recover from?

---

### Post by twallstr on 2008-12-25
jonobr, I guess you have a point there. Just that I am use to the Windows way.
Anyway I gues sI&#314;l have to live with that.

Thanks!

twallstr

---

### Post by tudor_victor on 2009-02-22
I know this is an old thread but I'm also looking for a solution to this problem.

this is a very serious issue because
#1 you can accidentally hit the "del" key and this will delete whatever file is selected and
#2 if you delete a file on an NTFS partition it is gone forever, not moved to trash.

so if you have multiple partitions that you share with Windows and you accidentaly hit del while you're browsing one of these partitions, you just lost that file for good.

---

### Post by 73ckn797 on 2009-02-23
Do not know of any way to do what you are asking. You will just have to make certain that what you delete is something that you know you will no longer need.

---

### Post by jonobr on 2009-02-23
HI..

This discussion has been going on in a lot of places and wont be solved or addressed here.


There are two sides to the debate, 
You can be sure that if it was changed to have a confirm delete, there would be an equal number of people who dont like that.

If Im wrong, then I think you have grounds to start a poll or movement to get this implemented.
In the interim, I would recommend you perform all removals via command line and set up an alias for all remove commands to have a '-i' switch,
This way, any time you execute rm, it does it interactively

---

