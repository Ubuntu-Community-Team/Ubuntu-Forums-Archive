---
title: "problem with hibernate kubuntu"
date: 2012-04-22
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-22
I didn't see hibernate button in kubuntu and when I use this command 
```

root@subhi-pc:/home/subhi# hibernate
hibernate:Warning: Tuxonice binary signature file not found.
```

how can I solve this problem ?

---

### Post by jbernardo on 2012-04-23
> **forsubhi said:**
> I didn't see hibernate button in kubuntu and when I use this command 
```

root@subhi-pc:/home/subhi# hibernate
hibernate:Warning: Tuxonice binary signature file not found.
```how can I solve this problem ?
Hibernate has been disabled by default in ubuntu. You need to edit a obscure policy file to get it to work. See the discussion [here]("http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html") and the "bugs" [here]("https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/812394") and [here]("https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/976654").

For me, this decision is one of the WTF moments of the year, but the ubuntu devs seem set on watering down ubuntu, and unfortunately that also breaks kubuntu and all the other derivatives.

---

### Post by forsubhi on 2012-04-24
I am beginner so I don't understand what I shall do , can you help me?

---

### Post by jbernardo on 2012-04-25
> **forsubhi said:**
> I am beginner so I don't understand what I shall do , can you help me?

In the discussion [here]("http://www.ubuntuvibes.com/2012/04/hibernation-disabled-by-default-in.html") you'll find the steps to test and enable hibernation. It involves editing a system policy file, so it might be a little complicated for a beginner.

---

