---
title: "Shutdown dumps to the login screen"
date: 2009-05-14
forum: General Help
---

### Post by linux_votary on 2009-05-14
Hey folks I am using Ubuntu 8.04. and whenever I click the Shut Down Button, it dumps me to the login screen... The same happens when i shut down using the login screen "Options". 
Ultimately I need to shut my system down using the terminal by the shutdown -h command.. Any suggestions??
Thanks in advance.

---

### Post by deepclutch on 2009-05-14
Try reinstalling upstart.

---

### Post by linux_votary on 2009-05-15
Thanks for the reply... But didnt work....!!

---

### Post by KhurramM on 2009-05-15
I had many faults in hardy when it was on a secondary based logical partition.

Make sure that the root is on primary partition.

SWAP is also better to be on primary.

Hope this helps.

---

### Post by JoshRobertson92 on 2009-05-15
I think the folder /etc/rc6.d holds the scripts for shutdown.
You could try find a non broken script somewhere and change it.

if not why not create a new item on taskbar and use the script
**shutdown -h now**
Which when clicked will shutdown anyway.

Apart from that im clueless.

---

### Post by linux_votary on 2009-05-15
> **KhurramM said:**
> I had many faults in hardy when it was on a secondary based logical partition.

Make sure that the root is on primary partition.

SWAP is also better to be on primary.

Hope this helps.


I didnt get u... I have a dual boot system with Xp... Did u mean that?

---

