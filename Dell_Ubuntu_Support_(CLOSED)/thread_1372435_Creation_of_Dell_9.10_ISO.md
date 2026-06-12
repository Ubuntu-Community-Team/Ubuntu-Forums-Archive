---
title: "Creation of Dell 9.10 ISO"
date: 2010-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jaybop on 2010-01-04
Just curious if anyone has successfully created the Ubuntu 9.10 Dell ISO [ubuntu-9.10-dell_XXX.iso] by following instructions detailed here, using the dell-recovery tool and base iso: [Building Base Ubuntu Factory ISO]("http://en.community.dell.com/wikis/linux/building-base-ubuntu-factory-iso.aspx")?

I followed the steps and built my Dell ISO (A01) using ubuntu-9.10-desktop-amd64, but the weird thing is.. my output ISO is actually **smaller** in size than the base!

```
-rw-r--r-- 1 718878720 2010-01-04 12:16 ubuntu-9.10-dell_A01.iso
-rw-r--r-- 1 724353024 2010-01-04 09:18 ubuntu-9.10-desktop-amd64.iso
```

I assume the generated file should be similar to the size of ubuntu-9.04-dell_A01.iso (~1.8GB) or at least larger than desktop-amd64.

During the creation of the ISO, when using the dell-recovery tool, the only questionable behaviour I noticed was that as I was fetching the GIT tree, there was never a prompt informing me that this process completed.  If I run the tool again and re-attempt to fetch, it appears that all data was downloaded:

```
From http://linux.dell.com/git/ubuntu-fid
 = [up to date] 9.04 -> origin/9.04
 = [up to date] 9.04-Welchs -> origin/9.04-Welchs
 = [up to date] 9.10 -> origin/9.10
 = [up to date] anakin -> origin/anakin
 = [up to date] master -> origin/master
```

Any insight is appreciated.

---

### Post by Jaybop on 2010-01-04
Hmmm.. maybe the problem here is that there hasn't been a Overlay Framework release for the Base Image that I chose, ubuntu-9.10-desktop-amd64.iso.

It's strange though because the directions don't explicitly state which Base Images are supported, so I assumed that I could choose any image I desire pending any errors received duration creation.  Plus, the instructions also say:

[COLOR="DarkRed"][INDENT]_Overlay Framework_

Next, you'll need a copy of the Dell factory content.  If your base image already contains this, you can use it from there.  Otherwise, it can be fetched using GIT.  Keep in mind that the GIT tree is fairly large, so it may take a short period of time for it to fetch.

**If Dell has any support for this OS version, you will see it in the list of tags.  If it's not yet supported, you can use the origin/master tag, but keep in mind this is least likely to work as it represents the latest development.**[/INDENT][/COLOR]

.. which made me believe that creation of a Dell Desktop-AMD64 ISO at this time is possible. :-k

---

