---
title: "Karmic won't boot Lucid"
date: 2010-06-19
forum: Desktop Environments
---

### Post by Pkirkham on 2010-06-19
As advised by oldfred I'm reposting my reply to 9477887 as a new thread.

Sometimes it's not so easy.
I installed Lucid 10.4 but then decided to fallback to Karmic 9.10 because Lucid currently has a problem with my Digium TDM400P card and won't boot. However the versions of grub 2 are different and grub 2 can't boot Lucid. I'm not sure it's because of the differences between 1.97 and 1.98. In the latter there are options on the menuentry line and a line which reads recordfail which apparently isn't present in 1.97.

---

### Post by wilee-nilee on 2010-06-19
> **Pkirkham said:**
> As advised by oldfred I'm reposting my reply to 9477887 as a new thread.

Sometimes it's not so easy.
I installed Lucid 10.4 but then decided to fallback to Karmic 9.10 because Lucid currently has a problem with my Digium TDM400P card and won't boot. However the versions of grub 2 are different and grub 2 can't boot Lucid. I'm not sure it's because of the differences between 1.97 and 1.98. In the latter there are options on the menuentry line and a line which reads recordfail which apparently isn't present in 1.97.

Post the script in my sig in code tags. When you say fallback what does that mean? Did you just change the repositories and try to downgrade or did you dual boot?

---

### Post by Pkirkham on 2010-06-19
I dual booted by installing 9.10 from a Live CD.

Sorry this is a false alert. 10.4 wouldn't boot for the same reason as before. I had reinserted the Digium TDM400P card which caused me to want to try 9.10 to see if the problem was there too which it isn't. Of course with the card in the machine it still won't boot in 10.4. That problem has been posted elsewhere.

---

### Post by phantom_ on 2010-07-05
i do confirm the above Lucid bug.

my system has a **Digium TDM400P PCI card** installed. Lucid Lynx 10.04 setup crashes.

however, i am able to install Lucid without the card installed. when i re-insert the card into the PCI bus and restart; system crashes thru boot process.

where should i report the above for Ubuntu development team's review?

---

### Post by tikismoke on 2011-11-27
Does anyone getmore info , i issue the same problem with debian and grub2. But i can boot with a rescue cd and card pligin.

---

### Post by oldos2er on 2011-11-27
Closed, necromancy.

For Debian questions, please use their forums. [http://forums.debian.net/](http://forums.debian.net/)

---

