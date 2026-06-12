---
title: "Exporting an installed package list to a file"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Master Goodheart on 2006-08-31
I recently started using Ubuntu on one of my computers and have been loving it. I'd been meaning to try Linux properly, so when I had the chance I insalled the latest distro I had, with was Ubuntu 6.06. I'd used Live CDs a lot in the past, and learned a lot from some bonus video tutorials from some magazine cover disks. So I now I have it on an oldish computer (1.6GHz Pentium 4, 16MB GPU, 512 MB Ram, etc.) which I didn't use that much. Its been great, but the only thing is that computer isn't connected to the Interent (and my computer that is has a 28.8kbps connection). So when I want to install something, I go to the [Ubuntu Packages]("http://packages.ubuntu.com") site and find it there. Its really great, but it can be annoying to keep checking back between computers to see if I have all the packages required for the app I want to install.

So what I'm asking is if there is a way of exporting a list of all the packages I have installed into a file so I can just check it instead.

Thanks a lot in advance,

M-G

---

### Post by Jussi Kukkonen on 2006-08-31
It's possible (can't remember the command though, sorry). 

Have tried running *apt-get install <packagename>*? That should give you a list of all the files that would be installed if you had a connection...

---

### Post by elettronicha on 2006-08-31
> **Master Goodheart said:**
> So what I'm asking is if there is a way of exporting a list of all the packages I have installed into a file so I can just check it instead.

Maybe this could be helpful:
$ dpkg -l > packagesList.txt

---

### Post by Master Goodheart on 2006-09-09
Thanks a lot! That works really well. Its much easier to download things now :D

---

