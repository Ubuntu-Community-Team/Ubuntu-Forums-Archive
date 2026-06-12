---
title: "root control"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Zingomoos135 on 2006-07-15
I'm pretty new to linux, and i really want to learn more, so i kinda need some help with this.

i've got a compaq proliant server that was surplussed off from a business, and i've installed ubuntu on it. The entire operating system went into one of its scsi harddisks, and i want to use the other three as well. i can create a partition on the other drives, but i can't use them because i'm not root and i don't have permission.

if anyone has any suggestions, please let me know!

---

### Post by jimbob on 2006-07-15
Open a terminal window and issue all your commands preceeded by 'sudo' (without the tick marks.)

You will be asked for YOUR password once in the window.

This executes your commands in a root shell.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Zingomoos135 on 2006-07-15
i basically don't know any commands for linux yet. i've got the second harddisk set up with the Disks tool in System > administration > Disks but the folder that i've assigned to it is write protected, and only root can use it.

---

### Post by Zingomoos135 on 2006-07-15
never mind, i figured it out

i used

"sudo chown -R michael /" etc etc...

thanks for your help!

---

