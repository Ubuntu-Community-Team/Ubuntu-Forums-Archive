---
title: "&quot;These files are on a Picture CD.&quot; No, they're not!"
date: 2009-04-02
forum: General Help
---

### Post by SkankinRatFink on 2009-04-02
Hello everyone. When I browse the partition of my hard drive that I use for file storage (NTFS format), it shows a bar at the top that reads "These files are on a Picture CD." There are many more file types on this partition--- music, video, documents, etc. in addition to my photos.

[IMG]http://i40.tinypic.com/262mjpj.png[/IMG]

How do I get rid of that bar? I don't use F-Spot, I manage my photos myself with a card reader. Thanks in advance for your help.

---

### Post by philinux on 2009-04-02
One thing to try.

Open your home folder.

Click on Edit>preferences. Then click the media tab.

Other Media type drop down box and choose picture cd. Choose your action to suit.

---

### Post by _Purple_ on 2009-04-02
This is a bug. It says "These files are on a Picture CD" because that partition contains the "Pictures" folder. See [this](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936).

---

### Post by philinux on 2009-04-02
> **_Purple_ said:**
> This is a bug. It says "These files are on a Picture CD" because that partition contains the "Pictures" folder. See [this](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258936).

Could be happenning cos of ntfs. Try renaming the folder from Pictures to say Photos or Pics.

---

