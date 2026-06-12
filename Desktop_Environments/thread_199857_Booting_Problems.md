---
title: "Booting Problems"
date: 2006-06-19
forum: Desktop Environments
---

### Post by nickgzzjr on 2006-06-19
I had installed windows previous from this, and then I installed ubuntu to check it out. But now when i turn on the computer, i cant boot to windows and my little bro is getting on my nerves because he wants to play this titanic game he has.  I tried using gag and it didnt work, what can i do?

---

### Post by Maelstrm on 2006-06-19
edit /boot/grub/menu.lst with a text editor

Add

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

under where it says

### END DEBIAN AUTOMAGIC KERNELS LIST

:)

---

### Post by Irony on 2006-06-19
That's right, do in terminal;

[PHP]sudo gedit /boot/grub/menu.lst[/PHP]

and add this to the end of your boot list;

[PHP]# This entry by your goodself for a non-linux OS
# on /dev/hda1
title		XP Home SP2, hda1
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/PHP]

---

### Post by nickgzzjr on 2006-06-19
Well I tried except that Windows in not in (hd0,0) because Ubuntu is in there, so i tried (hd0,5) becuase the windows partition comes out in ubuntu as hda5. So when i did that an error came out "Error12:Invalid device request". So then I tried other numbers but non of them worked. Can You Please HElp Me !!!

---

### Post by deboring21 on 2006-06-20
I had this issue a while back when I tried dual booting, it is definately something with the grub loader, but I fixed mine through the rescue terminal.... I'm trying to remember what I did, but I'm drawing a blank here... what I did was reinstall the Grub loader on the main partition, which might be your WinXP one or your Ubuntu.. I'll find the papers about it when I get home tonight...
-Ryan

---

### Post by nickgzzjr on 2006-06-20
[QUOTE=deboring21]I had this issue a while back when I tried dual booting, it is definately something with the grub loader, but I fixed mine through the rescue terminal.... I'm trying to remember what I did, but I'm drawing a blank here... what I did was reinstall the Grub loader on the main partition, which might be your WinXP one or your Ubuntu.. I'll find the papers about it when I get home tonight...
-Ryan[/QUOTE]

Hey Thank You that would be really nice if you can tell me how you did. :D

---

