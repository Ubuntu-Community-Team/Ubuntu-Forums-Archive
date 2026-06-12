---
title: "I cannot access my computer!"
date: 2008-12-31
forum: General Help
---

### Post by bengreer on 2008-12-31
I recently removed ubuntu dual booted with windows xp from my hard drive. I still cannot access windows!  

GRUB Loading stage1.5

GRUB loading, please wait...
Error 22

I know that when I removed ubuntu, I didn't remove the boot loader and that I need to fix the mbr.  I don't have the windows installation disk. I do have the ubuntu live cd. Is there a way that I can fix the mbr off of the live cd.

Your help is much appreciated, if any other details are needed, just ask.  I am checking back every few minutes!

---

### Post by melojo on 2008-12-31
Boot from your XP cd and go to recovery console and type
```
fixmbr
```

and then

```
fixboot
```

---

### Post by b3n0 on 2008-12-31
Shame Ubuntu didnt work out for you. Grab your win XP CD.... that you had to purchase, and do this. Run the Windows XP CD and go for 'recovery console' and at the prompt type
'fixmbr' you can try 'fixboot' as well.

Hope this helps.

EDIT: Blast I was beat to it. ;)

---

### Post by bengreer on 2008-12-31
I don't have the xp cd, this computer was bought in 2004 and my parents probably lost it!

---

### Post by melojo on 2008-12-31
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

this will do it

---

