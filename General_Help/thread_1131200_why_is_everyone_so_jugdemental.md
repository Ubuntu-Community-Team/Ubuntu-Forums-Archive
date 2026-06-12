---
title: "why is everyone so jugdemental?"
date: 2009-04-20
forum: General Help
---

### Post by Angerflst on 2009-04-20
i really dont understand. im just asking for help to reset our family laptop's password ( because no one can remember) and everyone instantly assumes i am making everything up. does everyone really think that if i am spending so much time "stealing this machine" wouldnt i just reformat it and be done with it? seriously, are people ready to help me or are they jsut going to sit there giving me vague answers and since i dont know everything about ubuntu im instantly a criminal?

---

### Post by ddrichardson on 2009-04-20
I don't think people are really accusing you of anything but no-one wants to be the one who told you how to do it had you not had permission - its a blame culture and that's the sort of thing that *might* be actionable.

That's quite a risk for a volunteer giving up their time.

There are other sites that [might]("http://www.psychocats.net/ubuntu/resetpassword") tell you (hint).

---

### Post by Angerflst on 2009-04-20
but its not like anyone cna give proof unless i get my parent to sign a full document stating that the internet is allowed to help me and then i can scan it and post here. seriously, im telling u my parent do not remember the password and my step brother doesnt remember the password. so i have come to this form for help. and no one wants to help. instead they feel like it is easier to just report me as a scammer.

---

### Post by Dougie187 on 2009-04-20
Well, as it has been said before, it is not that people don't believe you. It is just it is a very large risk. If you know anything about social engineering then you should be able to understand why people don't want to be the one to tell you how to do it. Don't take it personally, because its not personal.

---

### Post by ddrichardson on 2009-04-20
Dude, re-read my post particularly the last sentence.

---

### Post by Angerflst on 2009-04-20
> **Dougie187 said:**
> Well, as it has been said before, it is not that people don't believe you. It is just it is a very large risk. If you know anything about social engineering then you should be able to understand why people don't want to be the one to tell you how to do it. Don't take it personally, because its not personal.

ok, so why is their so many guide on google on how to do it? lol but when i try to do it it says give root password for maintenance instead of what they have. which is dumb cuz if this is the method for resetting your password, when why does it ask for ur password? lol all too confusing. 

what if people only say step by step. so that they are telling me the answer they are just saying a code.? lol im trying to find a loophole here.... help me trying to find people to help me lol.

---

### Post by Angerflst on 2009-04-20
> **ddrichardson said:**
> Dude, re-read my post particularly the last sentence.

ok thx for telling me.

edit: i know i was there but after root// drop to root shell prompt and it asks "give root password for maintenance"

---

### Post by swarsron on 2009-04-20
add "init=/bin/sh" to your kernel options if you're using grub. You'll get a root shell where you type passwd and change your password. If you don't have grub get a knoppix cd/dvd and boot that. Mount the root partition, go in there and do a chroot . /bin/sh
Then passwd etc.
Besides that i don't think that liability could be really a point here. No judge would sentence someone for answering such a trivial question.

---

### Post by Angerflst on 2009-04-20
> **swarsron said:**
> add "init=/bin/sh" to your kernel options if you're using grub. You'll get a root shell where you type passwd and change your password. If you don't have grub get a knoppix cd/dvd and boot that. Mount the root partition, go in there and do a chroot . /bin/sh
Then passwd etc.
Besides that i don't think that liability could be really a point here. No judge would sentence someone for answering such a trivial question.

how would i go about adding init=/bin/sh" options?

---

### Post by ddrichardson on 2009-04-20
> **swarsron said:**
> Besides that i don't think that liability could be really a point here. No judge would sentence someone for answering such a trivial question.
Really? Given some of the crazy decisions that are made, especially in civil cases?

It doesn't hurt to cover your ****.

---

### Post by cariboo on 2009-04-20
This is a least the third thread about this same issue, with a different story in each thread.

I'm going to close this thread for staff review.

Jim

---

