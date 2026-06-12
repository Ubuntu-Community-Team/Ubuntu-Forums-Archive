---
title: "Upgrade to lastest kernel crippled boot up"
date: 2008-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chamlyn on 2008-07-01
I installed all regular updates, then installed the new kernel update on my Dell.  Now when it boots I get this repeating indefinitely:

[4917.195740] ata2.00:Exception EMask 0x0 SErr 0x0 action 0x2 Frozen
[4917.195740] ata2.00:Cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
[4917.195740] ata2.00:Status: {DRDY}

That above keeps repeating with the left most numbers changing each time.  

I am able to hit esc and enter the GRUB boot menu and have this list:

Ubuntu 8.04, kernel 2.6.24-18-generic
""----------------------------------- (Recovery mode)
""----------------- 2.6.22-15-generic
""----------------------------------- (Recovery mode)
""---------- memtest86+
Reinstall Operating System (Will erase blah blah)

If I try 2.6.24-18 recovery mode it gets to this point and pauses:
[2176.872367] sd 2:0:0:0: attached scsi generic sg1 type 0

Then this repeats twice:
ata1.00: qc timeout (cmd 0x27)
ata1.00: failed to read native max address (err_mask=0x4)
ata1.00: revalidation failed (errno=5)
ata1.00: failed to recover some devices, retrying in 5 seconds

Then it looks like it's moving forward but ends up repeating this:
ata2.00: Status: {DRDY}
ata2: soft resetting link
ata2.00: configured for UDMA/33
ata2: EH Complete
ata2:00: exception Emask... (same info from that first error at the top of this post)


I am able to start "2.6.22-15-generic" and everything appears normal, but if I try to add/remove programs or use the update manager they both hang.  Eventually the whole system will hang.

Anyone know what is going on?  Any advice?

---

### Post by chamlyn on 2008-07-01
No ideas?  Can I provide more information or anything?  I'm also trying Dell but so far it's been a gauntlet of unanswered e-mail and mysteriously disconnected phone calls.

I'm getting concerned and may have to reinstall the OS from scratch.  The only real problem is that it's my wife's computer and I've been talking up Ubuntu for months.  So admitting defeat now and telling her she needs to set everything up again is going to be painful :(

---

### Post by gbrainin on 2008-07-01
First off, Dell won't help you.  This is clearly a software problem.

Second, the most current kernel I have is -19, not -18, so perhaps you can use the update manager to get the -19 kernel?

Third, there's nothing wrong with using a slightly older kernel if that's what works on your machine.

---

### Post by chamlyn on 2008-07-02
>First off, Dell won't help you. This is clearly a software problem.

They support Windows as part of their OEM licensing agreement.  I can't imagine they'd try selling any PC without having some sort of basic OS support.  Besides, they have a dedicated Ubuntu support telephone number, which seems pretty silly if they only support hardware issues.  Do you have any basis for your claim?  Did I miss something?  I'm not trying to be a jerk but that's a pretty big claim to make without any research on your part.  If Dell responds to my e-mail in a helpful way I'll let you know. :)

>Second, the most current kernel I have is -19, not -18, so perhaps you can use the update manager to get the -19 kernel?

-18 will not load.  Only -15.  While in -15, the Add Programs and the update manager both hang if run.  So no dice there :(

>Third, there's nothing wrong with using a slightly older kernel if that's what works on your machine.

-15 works, but it's superficial.  I can check e-mail, surf the web, do an office document, but I am unable to do any kind of updating, can not add/remove any programs, and randomly Evolution or Firefox will just hang.  

So it looks like I'm going to have to reformat the system.  A perfect way to spend the holiday weekend :(

Thanks for responding.  Sorry to be so down, it's the situation, not your reply.

---

### Post by gbrainin on 2008-07-02
> **chamlyn said:**
> >First off, Dell won't help you. This is clearly a software problem.

They support Windows as part of their OEM licensing agreement.  I can't imagine they'd try selling any PC without having some sort of basic OS support.  Besides, they have a dedicated Ubuntu support telephone number, which seems pretty silly if they only support hardware issues.  Do you have any basis for your claim?  Did I miss something?  I'm not trying to be a jerk but that's a pretty big claim to make without any research on your part.  If Dell responds to my e-mail in a helpful way I'll let you know. :)

Software support is provided (as an extra-cost item) by Canonical; Dell provides only hardware support.  See, for example, [http://linux.dell.com/wiki/index.php/Products/Consumer]("http://linux.dell.com/wiki/index.php/Products/Consumer")

> >Second, the most current kernel I have is -19, not -18, so perhaps you can use the update manager to get the -19 kernel?

-18 will not load.  Only -15.  While in -15, the Add Programs and the update manager both hang if run.  So no dice there :(

Annoying, I agree, but at least you know that there's a newer version out there.  So once you do get it working, you can upgrade to the newest kernel.

> >Third, there's nothing wrong with using a slightly older kernel if that's what works on your machine.

-15 works, but it's superficial.  I can check e-mail, surf the web, do an office document, but I am unable to do any kind of updating, can not add/remove any programs, and randomly Evolution or Firefox will just hang.

Hmm, sounds like the problem is not just with the kernel, then.  Unfortunately, I have no better answer than to reinstall (someone with more technical savvy than I have might have another suggestion).  Be sure to back up your data first.

---

### Post by chamlyn on 2008-07-02
Thanks for clarifying that Dell thing.  Wow, no support huh?  That's kind of dumb.  that Conocal company seems pretty pricey.  Well thanks for letting me know.  I'll stop calling them.

Yeah, well that's the good thing about getting it at least partially working, I can at least back up her stuff.  I think she probably had a virus (I had one on my Ubuntu machine recently), which started me down this whole road.

I'll reinstall. 

Thanks again for responding.

Take care

---

### Post by gbrainin on 2008-07-03
> **chamlyn said:**
> Thanks for clarifying that Dell thing.  Wow, no support huh?  That's kind of dumb.  that Conocal company seems pretty pricey.  Well thanks for letting me know.  I'll stop calling them.

Well, there's no _telephone_ support.  There are things like, for example, this forum, that seem to do a pretty good job of taking its place for a lot of people.

> Yeah, well that's the good thing about getting it at least partially working, I can at least back up her stuff.  I think she probably had a virus (I had one on my Ubuntu machine recently), which started me down this whole road.

Are you sure?  Viruses are pretty unusual in the Linux world.  Not saying it isn't, just that it's farther down my guess list than it would be if I were diagnosing a problem in Windows.

> I'll reinstall. 

Have you considered putting the /home directory on a separate partition?  It makes it a lot easier to reinstall without losing personal data.  Instructions are [here]("http://www.psychocats.net/ubuntu/separatehome"), if you're unfamiliar with the process.

> Thanks again for responding.

You're welcome.  I wish I had better answers for you.

---

### Post by chamlyn on 2008-07-03
Virus:

I know what you mean.  I've been running my Ubuntu PC for almost a year with no anti-virus software, which is kind of dumb, but I only use it to do "work" stuff (Open Office and Web Design), not surf the web or anything all that often.

So I got my wife her PC and didn't think too much about viruses.  But my PC got all sluggish and strange, so I installed the community supported anti-virus program and it found one (didn't think to write down the name darn it).  So I cleaned it, rebooted, ran it again and it found the same one still there.  Rebooted again and it was gone.  So that's when I decided to get anti-virus on my wife's PC, which is what lead to this updating fiasco.

In looking for a solution I came across that Home directory on a separate partition thing and you can bet I'll be doing that this time :)

Thanks again for everything.  I'll check my anti-virus history and see if I can get a name for you (if you're curious, cause now I am)

---

### Post by checksum_101 on 2008-07-03
I got similar probs - im using a dell m1330 laptop and my USB is dead since that update.

---

