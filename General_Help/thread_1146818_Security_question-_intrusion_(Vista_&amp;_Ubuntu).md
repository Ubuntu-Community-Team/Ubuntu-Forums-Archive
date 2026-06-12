---
title: "Security question- intrusion? (Vista &amp; Ubuntu)"
date: 2009-05-02
forum: General Help
---

### Post by Gizenshya on 2009-05-02
I was fiddling around in Vista (I use it for gaming) earlier and I noticed something that shocked me...

When modifying permissions, I noticed an "Unknwon Account" has, at some point, had access to files in Vista.  I have file sharing and tons of other potential security holes disabled (as I oinly use it for gaming), and I've only ever had one account on there.

After some googling, That Unknown Account means that, at some point, there was an account on the computer that had access to that folder, but that Vista cannot resolve the "SID" to an active account.  Generally, this happens after a Vista account has been deleted.. But there has only ever been one account.

So, my question is, Could this be caused by me accessing my Vista files from Ubuntu? (8.10, if that matters)  Some files I copied over form Ubuntu have a little icon in the bottom left that piqued my curiousity about security (which is how I found this out).  That also leads me to think that the culprit may be myself.

I just want to make sure that this is possible, to be sure I don't have some sort of virus or something that has breached my computer.

Thanks in Advance.

---

### Post by garythegoth on 2009-05-02
> **Gizenshya said:**
> I was fiddling around in Vista (I use it for gaming) earlier and I noticed something that shocked me...

When modifying permissions, I noticed an "Unknwon Account" has, at some point, had access to files in Vista.  I have file sharing and tons of other potential security holes disabled (as I oinly use it for gaming), and I've only ever had one account on there.

After some googling, That Unknown Account means that, at some point, there was an account on the computer that had access to that folder, but that Vista cannot resolve the "SID" to an active account.  Generally, this happens after a Vista account has been deleted.. But there has only ever been one account.

So, my question is, Could this be caused by me accessing my Vista files from Ubuntu? (8.10, if that matters)  Some files I copied over form Ubuntu have a little icon in the bottom left that piqued my curiousity about security (which is how I found this out).  That also leads me to think that the culprit may be myself.

I just want to make sure that this is possible, to be sure I don't have some sort of virus or something that has breached my computer.

Thanks in Advance.

Is it the hidden Administrator account that Windows uses?

---

### Post by BslBryan on 2009-05-02
Sounds right to me.  However, it could also be possible that this is on every Vista machine, because any time the UAC (User Account Control) prompt comes up and asks for administrative rights, you are using Vista's version of root.  This account is hidden, and is on every Vista machine.  It is a supersecret administrator that is actually you, but that most users don't even know about.  To unlock it, you run cmd as an administrator, and in the prompt, type
```
Net user administrator /active:yes
```

Anyway, either way it seems you are the culprit. :)

---

### Post by garythegoth on 2009-05-02
> **BslBryan said:**
> Sounds right to me.  However, it could also be possible that this is on every Vista machine, because any time the UAC (User Account Control) prompt comes up and asks for administrative rights, you are using Vista's version of root.  This account is hidden, and is on every Vista machine.  It is a supersecret administrator that is actually you, but that most users don't even know about.  To unlock it, you run cmd as an administrator, and in the prompt, type
```
Net user administrator /active:yes
```Anyway, either way it seems you are the culprit. :)

"User Account Control" *shudders* :-&

---

### Post by 3Miro on 2009-05-02
Quite possible it was the Ubuntu/Vista interaction. Makes sense to me (not that I am an expert or something).

Also I have to say that create and account -> do damage/steal information -> delete the account, is a fairly sophisticated attack. If this were an attach, it would not be caused by a random virus/trojan/whatever you call it. Therefore, it is unlikely to be a (random) attack.

---

### Post by Gizenshya on 2009-05-02
wow, thanks for the quick responses!

*sighs in relief*

*thinks maybe I'm just not giving microsoft enough credit on their security* .... naaaah :p

---

### Post by doas777 on 2009-05-02
> **Gizenshya said:**
> I was fiddling around in Vista (I use it for gaming) earlier and I noticed something that shocked me...

When modifying permissions, I noticed an "Unknwon Account" has, at some point, had access to files in Vista.  I have file sharing and tons of other potential security holes disabled (as I oinly use it for gaming), and I've only ever had one account on there.

After some googling, That Unknown Account means that, at some point, there was an account on the computer that had access to that folder, but that Vista cannot resolve the "SID" to an active account.  Generally, this happens after a Vista account has been deleted.. But there has only ever been one account.

So, my question is, Could this be caused by me accessing my Vista files from Ubuntu? (8.10, if that matters)  Some files I copied over form Ubuntu have a little icon in the bottom left that piqued my curiousity about security (which is how I found this out).  That also leads me to think that the culprit may be myself.

I just want to make sure that this is possible, to be sure I don't have some sort of virus or something that has breached my computer.

Thanks in Advance.

I usually see this when I have rebuilt my system, when looking at files on my data partition. my users SID is differant than it was on the last instance, so it appears to have been changed by an "unknown user".

---

### Post by lisati on 2009-05-02
> **doas777 said:**
> I usually see this when I have rebuilt my system, when looking at files on my data partition. my users SID is differant than it was on the last instance, so it appears to have been changed by an "unknown user".

I've occasionally noticed similar on XP when I've had to reinstall for some reason, gone to do something with  files on an external HDD, and "Permission denied".

---

### Post by BslBryan on 2009-05-03
This is a little off-topic, but lisati, did you know that there's a glitch with your Linux counter avatar?  I think it might update with every user counted, because you registered long before 30,000 others did. :P

---

### Post by pg-13(prostitute) on 2009-05-03
usually when i copy files or mess with files on my vista partition a little icon shows up on them to show there are "shared",,, but the only security risk i see on a home system is hackers gettiing ur docccs or personal info and using it to harass you or try to perform id theft

---

