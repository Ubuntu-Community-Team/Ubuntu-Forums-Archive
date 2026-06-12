---
title: "Ubuntu text mode."
date: 2009-04-24
forum: General Help
---

### Post by ebobby on 2009-04-24
Is is possible to install ubuntu in just text mode and then choose my desktop accordingly? (I personally want to use fluxbox).

Installing the normal desktop and then trying to get rid of all the other packages is a pain.

Thanks for your help!

---

### Post by dcstar on 2009-04-24
> **ebobby said:**
> Is is possible to install ubuntu in just text mode and then choose my desktop accordingly? (I personally want to use fluxbox).

Installing the normal desktop and then trying to get rid of all the other packages is a pain.

Thanks for your help!

Use the Server or Alternate install CDs.

---

### Post by RedSquirrel on 2009-04-25
> **ebobby said:**
> Is is possible to install ubuntu in just text mode and then choose my desktop accordingly? (I personally want to use fluxbox).

Installing the normal desktop and then trying to get rid of all the other packages is a pain.

Thanks for your help!

The [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") is good for this.

After you install the command-line system and reboot without the CD, just run:

```
sudo apt-get update
sudo apt-get install xorg fluxbox
startx

```

---

