---
title: "Dell's plans for 10.04 LTS"
date: 2010-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by HTML-insane on 2010-01-10
'Lo everyone!

Just a quicky: Dell's custom repositories (pointing to [http://dell-mini.archive.canonical.com/ubuntu](http://dell-mini.archive.canonical.com/ubuntu)) on the Inspiron Mini 10v that I got only a few days ago don't allow to upgrade to later major releases from the 8.04 LTS release that comes with it. Does anyone know if Dell is planning to allow upgrades to the next Ubuntu LTS release from these repositories? Would be glad to hear that this will be a painless process and supported by Dell...

Thanks in advance.

---

### Post by winjeel on 2010-01-10
I'm in a similar boat. Also keep an eye on this link for an eventual reply: [http://ubuntuforums.org/showthread.php?t=1377047](http://ubuntuforums.org/showthread.php?t=1377047)

---

### Post by HTML-insane on 2010-01-10
Ah. Well, in your case, I suppose it might work (but also might be a bit dangerous) to back up your current /etc/apt/sources.list somewhere, take an existing sources.list from your other computer, change the, "intrepid" bits to, "hardy" and stick that in /etc/apt. Then you can (theoretically) upgrade to the next version of Ubuntu.

Still, that's kinda ugly and I can't guarantee that it'll work flawlessly... it's also kinda different to the question I'm asking, which isn't whether it will be possible, but whether it will be supported by Dell in their repositories. (will post this in your thread as well.)

---

### Post by peterthewolf on 2010-01-10
Today I have just installed Karmic for a friend as a dual boot on the mini. Everything just worked out of the box.

---

### Post by HTML-insane on 2010-01-10
> **peterthewolf said:**
> Today I have just installed Karmic for a friend as a dual boot on the mini. Everything just worked out of the box.

Yeah, but what I'm asking is, "I've bought a Dell laptop with Ubuntu 8.04 on it. Will Dell let you upgrade to 10.04 (the next LTS) in the future?".

---

### Post by snowpine on 2010-01-10
"Dellbuntu" 8.04 is *not* standard Ubuntu, and has no upgrade capability to later releases. It also uses the obsolete lpia (Low Power Intel Architecture) instead of the more common i386 architecture. (Canonical will no longer support the lpia architecture starting with 10.04.)

In other words, it's extremely unlikely you'll be able to upgrade Dellbuntu to a new release when support for 8.04 ends in April 2011. Your best bet is a fresh reinstall of a newer Ubuntu release. (I've done this with both 9.04 and 9.10, no major problems.) Some good tutorials on this site: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by HTML-insane on 2010-01-11
Hmm. Thing is, I've got a bootable Kubuntu 9.10 Netbook Edition USB stick, but when I boot into it and X starts it goes all funky. Dunno what's up with it, and since this is the only computer I have that can actually boot from USB...

I'll leave it until the LTS anyway. I've got a home FTP server up so I can back up my files nicely. Then I'll do a clean install. :)

---

