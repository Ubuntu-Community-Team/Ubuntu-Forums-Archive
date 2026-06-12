---
title: "wierd memory loss?"
date: 2009-03-29
forum: General Help
---

### Post by wubiubiubi on 2009-03-29
so i just installed wubi last night (thinking about wiping xp and switching to ubuntu altogether) and everything went great. I installed flash, java, internet settings, and the first update package (282 files, like 4MB). So I looked on filesystem properties because I wanted to see how much space I had. It said I only had 5 GB free space left. Then it took around a half hour to count number of files and how many GB I already used. It came to about 45 GB. Is it normal to have it take up so much space, even though I've installed almost nothing? It seems to be running like a new computer, it's really fast. If I only had 5 GB of space left, I would think it would be running incredibly slow. If anyone could give me advice or a reason why this is happening, I'd be grateful.

P.S.,sorry if the prefix is wrong, I'm new and didn't know if wubi counted as Ubuntu.

---

### Post by sdennie on 2009-03-29
> **wubiubiubi said:**
> so i just installed wubi last night (thinking about wiping xp and switching to ubuntu altogether) and everything went great. I installed flash, java, internet settings, and the first update package (282 files, like 4MB). So I looked on filesystem properties because I wanted to see how much space I had. It said I only had 5 GB free space left. Then it took around a half hour to count number of files and how many GB I already used. It came to about 45 GB. Is it normal to have it take up so much space, even though I've installed almost nothing? It seems to be running like a new computer, it's really fast. If I only had 5 GB of space left, I would think it would be running incredibly slow. If anyone could give me advice or a reason why this is happening, I'd be grateful.

P.S.,sorry if the prefix is wrong, I'm new and didn't know if wubi counted as Ubuntu.

If your update was 282 packages, it was certainly a lot more than 4MB.  Wubi is a tricky installation.  If you told the disk analyzer to count used disk space, it probably recursed through your Windows installation (which is directly mounted in a Wubi install) and counted that information as well.  To get actual disk usage information, open a terminal and type, "df -H".  I don't have a Wubi install to tell you what you need to look at but, if you think you have 5GB left on the "disk", you probably do.  The default install is only about 3 or 4G if I remember right.  If you set your Wubi install to have 10G of free space, the situation you are describing sounds normal to me and is not something to worry about.

---

### Post by wubiubiubi on 2009-03-29
Thanks, I think i get it now. What is the 45GB coming from then, when I open properties on the filesystem and it counts all the files? And is it possible to re-install wubi with a bigger amount of space? I remember when I was downloading wubi to begin with, It put it all in a folder in "program files" which was 10Gb. When I went to start up Wubi for the first time, it basically did everything on its own, it didn't even ask me to choose a size to dedicate to wubi.

---

### Post by sdennie on 2009-03-29
I don't know.  I've only ever seen a wubi install.  If I remember correctly, the host filesystem (Windows) was accessible via /host.  If you told the disk usage analyzer to analyze your entire disk, it probably went through /host (at a relatively slow speed) and counted that towards your used disk space.  

I have an odd setup with various things mounted as encfs or tmpfs and the disk usage analyzer thinks my 200G disk is actually 355G.  Basically, I'm saying, trust what is says when it tells you that directory X is using Y amounts of disk space but, don't trust it to tell you how much disk space you have.

(Also note that Wubi installs are measurably slower than proper installs for disk access.  If you think Ubuntu in Wubi is fast, it will likely be noticeably faster if natively installed).

---

