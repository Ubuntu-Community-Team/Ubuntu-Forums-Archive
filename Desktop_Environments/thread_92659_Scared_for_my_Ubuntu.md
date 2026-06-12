---
title: "Scared for my Ubuntu"
date: 2005-11-20
forum: Desktop Environments
---

### Post by bathini on 2005-11-20
Hello friends

I am scared I am going to mess up my ubuntu OS. I have a dual boot Ubuntu OS and Windows XP. Yesterday evening I decided to boot to Windows XP after a long time.I use Ubuntu most of the time. I got there (XP)to check out certain files (pdfs), a message from avast antivirus came up for update. I updated and it prompt me to restart. When I restarted and went to XP, it hung on "Windows is starting up"

Now if I start fiddling with XP I will end up messing up my Cool Ubuntu breezy 5.10. Any suggestions friends? I was thinking of a utility which can write to windows drive within Ubuntu? Please help. Thanks

Bathini

---

### Post by Haegin on 2005-11-20
Im not 100% sure but I think that the only thing you can mess up is the bootmanager so you will be stuck booting into windows. While this is a terrible thing it is also fixable and I'm pretty sure there are various guides on this forum or on the wiki that can explain how to restore grub again. (Assuming your using grub)

Hope this helps, please somebody correct me if I'm wrong

---

### Post by bathini on 2005-11-20
Thanks Human for  your response, I will try to look for these guides, though up to now, I have not found guides how to go about fixing this problems.

---

### Post by drummer on 2005-11-20
Your Ubuntu partition should be safe from windows, unless you have the windows ext3 fs drivers installed, windows doesn't even know Ubuntu exists! And if windows writes over the MBR, it is fixable I believe, I just can't remember where I saw the how to reinstall grub thread.. somewhere in this forum.

---

### Post by bathini on 2005-11-20
Drummer

Thanks for this, I am taking out my windows cd and start rewriting the windows boot sector. 

Cheers

---

### Post by drummer on 2005-11-20
Found it - [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bathini on 2005-11-20
This is even better, Thanks :p

---

### Post by Olli on 2005-11-20
I understand that you can boot to Ubuntu, right?

If your MBR (Master Boot Record) is damaged, you can always refresh it by commanding

sudo grub-update dev/hda

(I recommend to check this [man grub-update], as I am not working in Linux environment at present and cannot check it myself.)

I have been using avast! antivirus for years, and it has never caused me any trouble, contarary to the commercial antivirus programmes have, several times.

---

### Post by Olli on 2005-11-20
[QUOTE=bathini]Drummer

Thanks for this, I am taking out my windows cd and start rewriting the windows boot sector. 

Cheers[/QUOTE]

If you rewrite your Windows boot sector, you'll lose access to Ubuntu partition - correct me - and soon - if I am wrong. To get to Ubuntu, you'll have then to reboot with Ubuntu installation CD in rescue mode and continue then as I wrote in my previoius message.

---

### Post by Chayak on 2005-11-20
You don't have to worry about it. Windows can turn itself inside out and not work at all and not be able to touch Ubuntu unless you let it format your partition or affect the MBR which I've never seen do on it's own... but it's windows and I'll not be surprised at the lengths it will go to...

---

### Post by bathini on 2005-11-20
Hello

I have been trying to troubleshoot this problem since this morning. Apparently I left my Windows XP CD at my old place.I am thinking I should boot XP in safe mode that is if I do not mess up Ubuntu? Now how do I boot to safe mode in a dual boot (Ubuntu and XP)?
Thanks

Bathini

---

### Post by Olli on 2005-11-20
[QUOTE=bathini]Hello

I have been trying to troubleshoot this problem since this morning. Apparently I left my Windows XP CD at my old place.I am thinking I should boot XP in safe mode that is if I do not mess up Ubuntu? Now how do I boot to safe mode in a dual boot (Ubuntu and XP)?
Thanks

Bathini[/QUOTE]

It dependes on your computer's BIOS Settings. In my computer I have to press F8 while connecting the power on.

---

