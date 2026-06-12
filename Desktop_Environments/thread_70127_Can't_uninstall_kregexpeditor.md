---
title: "Can't uninstall kregexpeditor?"
date: 2005-09-28
forum: Desktop Environments
---

### Post by thulben on 2005-09-28
Hi all,
I don't know why, but it seems that for whatever reason kregexpeditor has a bad configuration file on my system.  It's preventing me from doing apt-get upgrade.  The error is:
files list file for package `kregexpeditor' is missing final newline
So, I figured I'd uninstall it since I don't really care about it.  Unfortunately, it want's to uninstall most of KDE when I do this.  How do I work around this?
Thanks in advance,
Ben

---

### Post by mlomker on 2005-09-29
> 
files list file for package `kregexpeditor' is missing final newline


That is probably a file in /var/cache/apt/archives.  Take a look in there for a file with a similar name and delete it.

---

### Post by thulben on 2005-10-02
[QUOTE=mlomker]That is probably a file in /var/cache/apt/archives.  Take a look in there for a file with a similar name and delete it.[/QUOTE]
Unfortunately, this doesn't work.  I deleted everything in that directory just to be safe and it the problem still happens.

---

### Post by mlomker on 2005-10-02
Try looking for files in /var/lib/dpkg/info/ with a similar name (you definitely do not want to delete everything in there).

---

### Post by thulben on 2005-10-02
[QUOTE=mlomker]Try looking for files in /var/lib/dpkg/info/ with a similar name (you definitely do not want to delete everything in there).[/QUOTE]

Alright...this looks promising.  Check this out:

```

thulben@charlie:/var/lib/dpkg/info$ file *list | grep -v ASCII
console-tools.list:                         UTF-8 Unicode text
kregexpeditor.list:                         data
thulben@charlie:/var/lib/dpkg/info$ 

```

Looks like the kregexpeditor.list file is junk.  It's not intelligible <sp?>...I opened it in vim and it's complete garbage.  The question is: now what?

---

### Post by mlomker on 2005-10-02
>  The question is: now what?

Delete it.

---

### Post by thulben on 2005-10-10
Sorry I haven't gotten back until now...life keeps popping up. :)  Anyways,  I removed the list file and am now able to upgrade my system.  Yey...thanks!  However, I now get the following message whenever I do any install/upgrade operations:

dpkg: serious warning: files list file for package `kregexpeditor' missing, assu
ming package has no files currently installed.

It allows me to proceed, but the words "serious warning" don't give me a warm feeling...

---

### Post by mlomker on 2005-10-10
I'd do this:

```

sudo updatedb
locate kregexpeditor

```

You could chose to delete what it finds.

---

