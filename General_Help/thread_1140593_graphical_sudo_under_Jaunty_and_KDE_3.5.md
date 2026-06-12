---
title: "graphical sudo under Jaunty and KDE 3.5"
date: 2009-04-27
forum: General Help
---

### Post by TWO on 2009-04-27
versions:
Qt: 3.3.8b
KDE: 3.5.10
KdeSudo: 2.5.1

Just installed KDE 3.5 under Jaunty Jauntelope and have found that I can't use graphical sudo in the konsole.

I wanted to edit the sources.list file and needed graphical sudo to work with Kate text editor.

Any suggestions on a resolution would be greatly appreciated.

Thanks in advance

TWO

---

### Post by Gilabuugs on 2009-04-27
you could also just do sudo kate in konsole and enter your pass there it would work the same, check to see if the correct package is installed i don't know what it is for kde EDIT: I see you put kdesudo, make sure that it is indeed installed

---

### Post by TWO on 2009-04-28
> **Gilabuugs said:**
> you could also just do sudo kate in konsole and enter your pass there it would work the same, check to see if the correct package is installed i don't know what it is for kde EDIT: I see you put kdesudo, make sure that it is indeed installed

That is a possible way around, but I think that using ```
sudo
```with graphical applications is discouraged as there is the potential for file permissions to be messed up:

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

So, I'd like to avoid doing that one.

Thanks anyway though.

TWO

---

