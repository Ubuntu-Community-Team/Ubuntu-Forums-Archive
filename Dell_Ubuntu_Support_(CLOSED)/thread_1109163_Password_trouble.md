---
title: "Password trouble"
date: 2009-03-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rchapin38 on 2009-03-28
I just got a Mini 9 from Dell. When I set name and password I thought everythng was fine. As it turned out, the system authentication does recognize my password. My question is, what can I do to fix this issue, short of reinstalling Ubuntu 8.04? I hope someone can help me with this problem. I am a rank beginner when it comes to Ubuntu/Linux. Thanks in advance.

---

### Post by ugm6hr on 2009-03-28
> **rchapin38 said:**
> As it turned out, the system authentication does recognize my password. 

I'm assuming that was a mis-type, and Ubuntu does **not** recognise the password.

There are ways to recover this, including boooting into the Recovery Console to create a new username and password.

However, just double-check you haven't got caps-lock on; Ubuntu is case sensitive.  There is no light for the capslock on the Mini 9 - I get caught out a lot with that.

---

### Post by Dr Small on 2009-03-28
If all else fails, boot into recovery mode (from the GRUB menu), and run:
```
passwd *username*
```

Where *username*, put in your account username. You can then set your new UNIX password.

---

### Post by ugm6hr on 2009-03-28
> **Dr Small said:**
> If all else fails, boot into recovery mode (from the GRUB menu)

On the Dell Mini, to do this, you have to press Escape repeatedly while it boots (just at the end of the Dell image screen), since the delay is set to 0 seconds before it defaults to the standard Ubuntu.

---

