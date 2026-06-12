---
title: "Beep at shutdown (Jaunty)"
date: 2009-05-25
forum: General Help
---

### Post by 0per4t0r on 2009-05-25
I know there are already threads on this, but few of them seemed to help. I hear a large beep as soon as it starts to shut down, and I was wondering if anyone knew how to fix it.

---

### Post by s.fox on 2009-05-25
Hi,

Yes,  it seems to be a common problem for many people.  One of my friends solved it by following [this]("http://ubuntuforums.org/showpost.php?p=7162033&postcount=12") post and black listing,  though by the sounds of things you have tried many different things.  I really hope this bug gets sorted out soon!

-Ash R

---

### Post by chenguo4 on 2009-05-25
An easier way might be to go into volume control and just muting the PC speaker.

---

### Post by rehilliard on 2009-05-25
Muting doesn't do it on my installation. It's annoying...

---

### Post by 0per4t0r on 2009-05-25
> **Ash R said:**
> Hi,

Yes,  it seems to be a common problem for many people.  One of my friends solved it by following [this]("http://ubuntuforums.org/showpost.php?p=7162033&postcount=12") post and black listing,  though by the sounds of things you have tried many different things.  I really hope this bug gets sorted out soon!

-Ash R
Tried it, sorry, it didn't work.

---

### Post by cmost on 2009-05-25
Is it really that annoying?  Yeah, it's there, but really!?  It only happens for a second or so and then the machine shuts down.  No big whoop.  Worry about the graphic regressions for Intel users, now that's a problem on which the devs should be spending time.  Not this minor beep on shutdown issue.  Sorry.  :(

---

### Post by rehilliard on 2009-05-25
> **Ash R said:**
> Hi,

Yes,  it seems to be a common problem for many people.  One of my friends solved it by following [this]("http://ubuntuforums.org/showpost.php?p=7162033&postcount=12") post and black listing,  though by the sounds of things you have tried many different things.  I really hope this bug gets sorted out soon!

-Ash R
but...this solution did work. I agree with 'cmost" about the severity level, but annoying isn't that harsh a word...

---

### Post by meeples on 2009-05-25
whats worrying is that beep actually comes from the computer rather than the speakers...

and thats the beep i used to get when trying to install incompatiible ram cards on my motherboard.

---

### Post by 0per4t0r on 2009-05-25
> **cmost said:**
> Is it really that annoying?  Yeah, it's there, but really!?  It only happens for a second or so and then the machine shuts down.  No big whoop.  Worry about the graphic regressions for Intel users, now that's a problem on which the devs should be spending time.  Not this minor beep on shutdown issue.  Sorry.  :(
Yes, it's very loud, and if I have my computer in public, it will attract much attention to my computer, and it makes linux just look bad to other people.

---

### Post by 0per4t0r on 2009-05-26
> **Ash R said:**
> Hi,

Yes,  it seems to be a common problem for many people.  One of my friends solved it by following [this]("http://ubuntuforums.org/showpost.php?p=7162033&postcount=12") post and black listing,  though by the sounds of things you have tried many different things.  I really hope this bug gets sorted out soon!

-Ash R
Actually, that fixed the beep, I just had to restart the computer first!

---

### Post by nandemonai on 2009-05-31
The beep is because of a broadcast to all ttys that a shutdown is taking place. If it really annoys you blacklist the pc speaker module.

/etc/modprobe.d/blacklist.conf

```
# Disable PC Speaker
blacklist pcspkr
```

---

