---
title: "How do I access Samba shares from a terminal?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by xp_newbie on 2006-06-22
Using the desktop to access the so called "Windows Network" is a breeze. No problem there.

However, I am trying to access the same Share (accessible via the GUI), using a terminal session, but I cannot find any mount or path that refers to that accessible share.

How do I do that?

Do I have to use smbmount to mount once again that samba share although it is already "mounted"?

Thanks!
Alex

---

### Post by kzutter on 2006-06-23
You have two primary choices, depending on what you want to do with the shared resource.
You can access resources with a ftp-like interface called smbclient.
Or you can mount the share with the smbmount package.

BTW- the share is NOT already 'mounted' - Your GUI tool does not mount the share in the usual fashion - ( the details are too technical to explain here).

Have fun!

---

### Post by xp_newbie on 2006-06-23
OK - thanks. That's what I suspected, but since I am not knowledgeable in the way Ubuntuo did the magic of making everything accessible and easy through the GUI I wasn't sure.

I am familiar with both smbclient and smbmount. I can continue from here.

Thanks!
Alex

---

### Post by hayesey on 2006-06-23
The best way is to edit the /etc/fstab file and mount the smb shares on boot.  Then they're available through the GUI and the terminal just as any other folder is.  Also programs like mplayer wont kick up a fuss when you try playing an MP3/video on one of the shares.

---

### Post by xp_newbie on 2006-06-23
[QUOTE=hayesey]The best way is to edit the /etc/fstab file and mount the smb shares on boot.  Then they're available through the GUI and the terminal just as any other folder is.[/QUOTE]

Actually, I like the fact that the shares are **not** accessible on boot - for data security reasons.

Now I am curious regarding how the Ubuntu desktop achieves the magic of accessing the smb shares **without** using smbmount or smbclient. Is there an online article somewhere that explains that?

Thanks,
Alex

---

### Post by Thund3rstruck on 2006-06-23
Of course I'm not expert but Windows computers (smb) broadcast their shares on port 139 (if I remember correctly). This is how network browser application methods such as the ones in Xbox Media Center and Network Neighboorhood identify workgroups and shares.  

Linux used to (and maybe still does) have a program called LinNeighborhood and from what I remember that's how it determined shares as well.

---

