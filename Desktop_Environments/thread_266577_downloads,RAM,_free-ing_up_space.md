---
title: "downloads,RAM, free-ing up space"
date: 2006-09-27
forum: Desktop Environments
---

### Post by IusedTObeSOMEONEelse on 2006-09-27
Question is regarding downloads. I have downloade some linux os's to burn. Among downloading other thing, I want to free up some RAM and how mdo I find whats taking up RAM space and get rid of it. Please be mind-full that I'm "Not the brightest bulb on the tree" so please give me simple terms. But I am enjoying this learning exp. and I have not crashed the box in about a week!!

---

### Post by lagagnon on 2006-09-28
The key commands you need to learn to help you manage RAM are:
free
ps aux
top

Read the man pages for each. "ps aux" will show you all running processes and how much RAM they are consuming, "free" shows you your RAM status, including swap at an instant in time, while "top" tells you what processes are consuming CPU and memory.

The easiest way to free up RAM are:
1) use a different desktop environment, ie try fluxbox or xfce instead of Gnome-KDE
2) use lighterweight applications, ie AbiWord instead of OpenOffice Writer, Dillo instead of Firefox, Sylpheed instead of Thunderbird or Evolution
3) remove unused daemons (ie remove sshd, nmbd, others) if you don't use them. You need BUM (boot-up manager) and you need to do a bit of research as to what you should and should not remove.

---

