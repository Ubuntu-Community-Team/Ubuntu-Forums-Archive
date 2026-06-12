---
title: "Installing Enlightenment"
date: 2009-01-22
forum: Desktop Environments
---

### Post by JordyD on 2009-01-22
So I heard some nice things about Enlightenment and wanted to install it. My first thought is to type into the terminal, 'sudo apt-get install enlightenment' and supply my password for sudo. I get this for output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment has no installation candidate[/B]

```

Is there some sort of repository that I need to enable? Any help would be appreciated.

Thanks,
Jordy

---

### Post by gjoellee on 2009-01-22
> **JordyD said:**
> So I heard some nice things about Enlightenment and wanted to install it. My first thought is to type into the terminal, 'sudo apt-get install enlightenment' and supply my password for sudo. I get this for output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment has no installation candidate[/B]

```Is there some sort of repository that I need to enable? Any help would be appreciated.

Thanks,
Jordy

lets try to get E17 (Enlightment 17). Follow this guide: [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

---

### Post by JordyD on 2009-01-22
> **gjoellee said:**
> lets try to get E17 (Enlightment 17). Follow this guide: [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

Well, after following this guide, I get this:

```
Package e17-cvs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  e17-svn
E: Package e17-cvs has no installation candidate

```

Should I try the e17-svn package?

---

### Post by Tux Aubrey on 2009-01-22
> **JordyD said:**
> Well, after following this guide, I get this: ......

Should I try the e17-svn package?

Absolutely - e17_cvs is "no longer with us"

The thread you should be following is [http://ubuntuforums.org/showthread.php?t=916690](http://ubuntuforums.org/showthread.php?t=916690) (referenced in the old cvs one)

If you strike any issues, post in that new thread - several e17 users monitor it regularly.

---

### Post by JordyD on 2009-01-22
Thank you, it seems to have worked and I think I'll be logging into Enlightenment in a little bit now.

---

