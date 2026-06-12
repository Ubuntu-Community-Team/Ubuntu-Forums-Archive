---
title: "Update Manager - Need Advice"
date: 2005-05-20
forum: Desktop Environments
---

### Post by ahood on 2005-05-20
We upgraded to from Warty (4.10) to Hoary5.05 and it seems to be successful. After several weeks of use there is a red icon in the task bar that informs us that there are updates available. 

The following message appears after we click on the red Update icon...

> There is a new release of Ubuntu available!"

A new release with the codename 'hoary' is available. Please see [http://www.ubuntulinux.org/](http://www.ubuntulinux.org/) for upgrade instructions.

I would love to know why this message appears.

However, in the end, what really matters is...

What is the most appropriate action to take?

Thanks in advance for any suggestion.

---

### Post by Xian on 2005-05-20
[QUOTE=ahood]We upgraded to from Warty (4.10) to Hoary5.05 and it seems to be successful. After several weeks of use there is a red icon in the task bar that informs us that there are updates available. [/QUOTE]
What method did you use to upgrade to Hoary? 
For example, did you change the repo sources and perform an 'apt-get dist-upgrade'?

---

### Post by ahood on 2005-05-20
Thanks for replying.

Yes, I originally did the

> sudo gedit /etc/apt/sources.list

Change any reference of Warty to Hoary
     From: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

      To: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

sudo apt-get update

sudo apt-get dist-upgrade

sudo apt-get install base

sudo apt-get install desktop

see [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

---

### Post by Xian on 2005-05-20
Open a temial and issue the command below.
What is the output?

```
$ cat /etc/issue
```

---

### Post by ahood on 2005-05-21
[QUOTE=Xian]Open a temial and issue the command below.
What is the output?

```
$ cat /etc/issue
```[/QUOTE]

Thanks for replying,

I issued the command it the following message was returned.

> Ubuntu 5.04 "Hoary Hedgehog" \n \l

---

### Post by Xian on 2005-05-21
You upgraded per the Ubuntu guidelines and it is obviously showing the current Hoary version on your machine, so you might want to search for and/or report a [bug](https://bugzilla.ubuntu.com/).

---

### Post by ahood on 2005-05-21
[QUOTE=Xian]You upgraded per the Ubuntu guidelines and it is obviously showing the current Hoary version on your machine, so you might want to search for and/or report a [bug](https://bugzilla.ubuntu.com/).[/QUOTE]

Xian,

Thank you for the input. Quick question.

Do you think re-doing the command in a terminal

'sudo apt-get update && apt-get upgrade'

mess up the machine?

---

### Post by Xian on 2005-05-21
[QUOTE=ahood]Do you think re-doing the command in a terminal
'sudo apt-get update && apt-get upgrade'
mess up the machine?[/QUOTE]
That is an incorrect command. Try the one listed below.
It is appropriate to run, although I'd substitute 'sudo apt-get dist-upgrade'.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ahood on 2005-05-21
Xian,

Thank you much for the help and advice. Will give it a go.

---

