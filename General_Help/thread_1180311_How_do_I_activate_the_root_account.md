---
title: "How do I activate the root account?"
date: 2009-06-06
forum: General Help
---

### Post by Mend and Defend on 2009-06-06
Sorry for this likely simple question, I'd like to know how to activate the root account since it is not done during installation in Ubuntu.

---

### Post by Legace on 2009-06-06
> **Mend and Defend said:**
> Sorry for this likely simple question, I'd like to know how to activate the root account since it is not done during installation in Ubuntu.

It is NOT reccomended to activate the root account.
Use sudo instead:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Mend and Defend on 2009-06-06
I know that it's not recommended, but I'd prefer to activate it, it makes me feel better.

---

### Post by posburn on 2009-06-06
Not to be rude, but Google it.  AFAIK, it's against Forum policy to reveal how that's done here.

---

### Post by Mend and Defend on 2009-06-06
Really? Why the hell would it be against forum policy? It's not like it's illegal. Most, if not all non-Ubuntu derivative distros have it set up during installation...

---

### Post by Legace on 2009-06-06
> **Mend and Defend said:**
> Really? Why the hell would it be against the policy?

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by michy99 on 2009-06-06
> **Mend and Defend said:**
> Really? Why the hell would it be against the policy?

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

EDIT: What he said.

---

### Post by Legace on 2009-06-06
> **michy99 said:**
> [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Too slow :tongue:

---

### Post by posburn on 2009-06-06
It is this Forum's policy to uphold the Ubuntu security model; the use of sudo as opposed to the root account is a crucial element of that model.

---

### Post by Mend and Defend on 2009-06-06
That's insane....

---

### Post by Legace on 2009-06-06
> **Mend and Defend said:**
> That's insane....

No its not.
The majority of the "noobs" that use Linux use Ubuntu.

If they were to accidentally execute a "bad" command as root, they could potentially destroy their filesystem.

For more experienced people (like you?) root should be fine, but for beginners, using their computer as root could lead to unwanted trouble.

---

### Post by ddrichardson on 2009-06-06
> **Legace said:**
> No its not.
The majority of the "noobs" that use Linux use Ubuntu.

If they were to accidentally execute a "bad" command as root, they could potentially destroy their filesystem.

For more experienced people (like you?) root should be fine, but for beginners, using their computer as root could lead to unwanted trouble.
While there may be truth to this, you could argue that we are teaching people to prepend everything they type with "sudo".

---

### Post by posburn on 2009-06-06
...

No, it's just a policy.  It's easy enough to find the info you want - you just won't find it here.;)

---

### Post by Tribulation on 2009-06-06
sudo passwd root

---

### Post by cmost on 2009-06-06
> **Legace said:**
> It is NOT reccomended to activate the root account.
Use sudo instead:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It really irks me when someone asks a perfectly reasonable question and someone else responds with "Why do you want to do that anyway, do this instead..." or some variation.

Obviously this guy has some legitimate reason for wanting to activate the root account.  Either explain how to do it or don't bother posting.

---

### Post by xenosaga456 on 2009-06-06
wow thats stupid as hell y dont u just tell him?????

---

### Post by ddrichardson on 2009-06-06
> **cmost said:**
> It really irks me when someone asks a perfectly reasonable question and someone else responds with "Why do you want to do that anyway, do this instead..." or some variation.

Obviously this guy has some legitimate reason for wanting to activate the root account.  Either explain how to do it or don't bother posting.
To be fair, the community help document he links to does say how to enable the root account.

---

### Post by Rocket2DMn on 2009-06-06
Almost everything that you need to do as root can be done using sudo - it is part of Ubuntu's security model, which is why we have the policy in place.  It's sort of one of those things that goes like this: If you don't know how to do it, you probably shouldn't be.

The answer is out there, all over google, we just don't support enabling the root account on these forums.  We could carry on this discussion all day, but it's one that has been had many times, so let's not turn this into such a recurring discussion thread.  Thanks.

---

### Post by Tribulation on 2009-06-06
I don't think it wise to treat the users like idiots. Microsoft does that, do we really want to give Ubuntu users the same experience? As long as people are warned of the dangers, it's fine. If someone screws up their system by doing something they didn't pay attention to the warnings then they have no one to blame but themself.

---

### Post by Rocket2DMn on 2009-06-06
> **Tribulation said:**
> I don't think it wise to treat the users like idiots. Microsoft does that, do we really want to give Ubuntu users the same experience? As long as people are warned of the dangers, it's fine. If someone screws up their system by doing something they didn't pay attention to the warnings then they have no one to blame but themself.

It is a misconception to say that just because we don't support enabling the root account, that we are treating users like idiots when they ask and we decline.  We are providing advice based on Ubuntu's security model, which happens to be safer than the original idea - we are here not only to provide support for users, but to educate them in the Ubuntu way of doing things which might be different than their previous methods or their expectations.  Also, as was said earlier, the Community Doc site at help.ubuntu.com which was linked to a few posts ago does explain how to enable root, with all the warnings and exclamations points attached as you suggested.

As you may know, many problems that plague windows (like viruses) are made worse by the fact that Windows has historically allowed users (and thus malware) to execute as Administrator, even without the end user knowing it.  But I digress.

To address your last point, we don't want users to screw up their system, because then we aren't providing a very valuable service.  It is much better to prevent data loss and have users make the best use of a functioning and secure system than to have to troubleshoot problems that arise as a result from previous advice given/received here.

---

### Post by xenosaga456 on 2010-07-15
ya i guess ur all right

---

### Post by lisati on 2010-07-15
[LIST=1]
[*]Thread closed, necromancy
[*]See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[/LIST]

---

