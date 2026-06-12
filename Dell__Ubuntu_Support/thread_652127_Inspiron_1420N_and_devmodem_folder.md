---
title: "Inspiron 1420N and /dev/modem folder"
date: 2007-12-28
forum: Dell  Ubuntu Support
---

### Post by duanekf2jc on 2007-12-28
Hello,
   I bought my son a new 1420N laptop. We got the modem working before he went back to college in November. He used the wireless network while at school. Now he's back home, and the modem doesn't work - no sounds coming out of speaker to indicate that it is even dialing out. I checked all the modem connection information in the Network Settings folder - everything seems to be correct - no changes made. I went to the /dev/modem folder and clicked on it. I got this reply:  Cannot open dev/modem, no application is known for this type of file. What should I check next? Thanks in advance for your help.

Duane

---

### Post by natehall on 2007-12-28
Don't know if this helps or not but I have a 1420N also and the file dev/modem is a symbolic link to /dev/ttySHSF0 on my computer.

---

### Post by fragos on 2007-12-28
> **duanekf2jc said:**
> Hello,
   I bought my son a new 1420N laptop. We got the modem working before he went back to college in November. He used the wireless network while at school. Now he's back home, and the modem doesn't work - no sounds coming out of speaker to indicate that it is even dialing out. I checked all the modem connection information in the Network Settings folder - everything seems to be correct - no changes made. I went to the /dev/modem folder and clicked on it. I got this reply:  Cannot open dev/modem, no application is known for this type of file. What should I check next? Thanks in advance for your help.

Duane

That error message is the correct behavior because there is no application.  The fact that you see /dev/modem means that the system sees the modem and has mounted it.  Getting sound from the modem is normally controlled by an AT command that's sent to the modem for initialization.  It's been so long I don't remember what the command is.  These used to be called Hayes commands.

---

### Post by skillllllz on 2007-12-28
> **fragos said:**
> ...These used to be called Hayes commands.

Okay, wow! Sorry for straying off topic, but that just triggered a flashback in my brain that made me cringe. I do not at all miss that technology one bit; that and setting IRQs via DIP switches... <insert_vomit_sound_here>

---

