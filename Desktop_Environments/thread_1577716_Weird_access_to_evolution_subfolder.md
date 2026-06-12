---
title: "Weird access to evolution subfolder"
date: 2010-09-19
forum: Desktop Environments
---

### Post by kaspar_silas on 2010-09-19
Hi,

Just discovered a strange issue with my evolution. I don't seem to be able to always navigate into sub folders using the directory tree on the left. More precisely I just cannot expand the tree as the little plus buttons aren't doing anything. 

Well almost nothing I somewhat randomly discovered I can open any non responsive sub folder with the following procedure:

1/ Selecting any another folder
2/ Clicking "Send / Receive" 
3/ Expanding one folder (other than the currently selected one)
n.b. I can't select the newly expanded sub folders at this stage or they vanish
4/ Clicking "Send / Receive" again
 
In other words I get one non accumulating expansion per Send/Receive pair. Weird, eh? Especially step 3 in which the sub folders collapse if I try and interact with them. Very quantum mechanical.

Anyway, so it is clearly not that serious but does anyone know what it might it. I checked the data and file permissions but that all seems okay and evolution doesn't print any warning to the terminal.

---

### Post by eltama on 2010-09-20
What version of Ubuntu/Evolution are you using?

I'm trying Maverick Meerkat and sometimes I cannot see my subfolders at all.

---

### Post by eltama on 2010-09-20
I have filled in this bug report [https://bugs.launchpad.net/bugs/643446]("https://bugs.launchpad.net/bugs/643446").

---

### Post by kaspar_silas on 2010-09-21
I am using:
Evolution 2.28.3
and OS
Ubuntu 10.04.1 LTS
2.6.32-24-generic

cheers for opening the bug.

---

### Post by eltama on 2010-09-22
I think the bug I am experiencing is a bit different because I don't see the arrow for the subfolders at all.
But maybe the same workaround works for you: try disabling and enabling the account.

---

### Post by kaspar_silas on 2010-09-27
As my sub folders are not on the account but in the local computer I didn't think messing with an account would have any difference. 

However I tried it and it now works. Not sure that was the solution but hey. Cheers

---

### Post by kaspar_silas on 2010-09-29
Actually it turns out that wasn't the solution. It only seemed to work as changing the accounts led to the send/receive fix happening.

---

### Post by hutch120 on 2010-10-10
Thanks for the tip, I've just started getting the exact same problem. Send/Receive allows me to expand a folder. Very strange, quite annoying.

Evolution 2.28.3
Ubuntu 64bit 10.04 LTS

---

### Post by kaspar_silas on 2011-02-09
Incidentally this problem went away when I (accidentally) upgraded to the development version of Natty Narwhal. Possibly it was just the evolution upgrade.

Either way all is well now, for me anyway.

---

