---
title: "main user desktop broken in 9.10"
date: 2009-11-03
forum: Desktop Environments
---

### Post by cw1035 on 2009-11-03
I upgraded to 9.10 from 9.04 yesterday. At first everything seemed to be working, but now when I try to login to the main user account using gnome,
nothing works. The logo appears, the strobe bar runs for a while, then both disappear, and I'm left with the background image from the login screen, and nothing else. No menu bars, no status bars, no normal desktop background image, alt+F2 doesn't work, right clicking doesn't work, ctl+alt+del doesn't work. The only thing I can do is crl+alt+F2 to get to another login screen, where I can reboot the system.

When I use another user account, everything works fine. Can anyone help me?
Thanks.

---

### Post by avb on 2009-11-03
> **cw1035 said:**
> I upgraded to 9.10 from 9.04 yesterday. At first everything seemed to be working, but now when I try to login to the main user account using gnome,
nothing works. The logo appears, the strobe bar runs for a while, then both disappear, and I'm left with the background image from the login screen, and nothing else. No menu bars, no status bars, no normal desktop background image, alt+F2 doesn't work, right clicking doesn't work, ctl+alt+del doesn't work. The only thing I can do is crl+alt+F2 to get to another login screen, where I can reboot the system.

When I use another user account, everything works fine. Can anyone help me?
Thanks.


login with your username in the text console, and do 'less ~/.xsession-errors'. Examine errors noted there and then i think you will be fine.

If you dont understand whats in the file, try to paste it to here, from your another account. You can open it with su your_username -c 'gedit /home/your_username/.xsession-errors'

---

### Post by cw1035 on 2009-11-03
> **avb said:**
> login with your username in the text console, and do 'less ~/.xsession-errors'. Examine errors noted there and then i think you will be fine.

If you dont understand whats in the file, try to paste it to here, from your another account. You can open it with su your_username -c 'gedit /home/your_username/.xsession-errors'

I have attached the file. I could not find any locks in .gconf or .gconfd and this account is not normally an NFS client machine. The only other suggestion involves TCP/IP networking for ORBit. But that should already be setup since the desktop is working in the other accounts. 

Do you have any other suggestions?

---

### Post by cw1035 on 2009-11-04
I found this answer in another thread: 
> I stumbled across this thread, and just renamed the "saved_state" (mv .gconfd/saved_state .gconfd/.saved_state) file in the .gconfd folder to something else and restarted GDM (sudo /etc/init.d/gdm restart). Everything came back up the way I had it.
I deleted the .saved_state file and everything came back.
"avb" Thanks for pointing me in the right direction to find the error log.

---

