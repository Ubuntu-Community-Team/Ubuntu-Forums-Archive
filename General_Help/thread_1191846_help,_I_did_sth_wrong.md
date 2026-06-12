---
title: "help, I did sth wrong"
date: 2009-06-19
forum: General Help
---

### Post by Kasra97 on 2009-06-19
I had vista and ubuntu 8.10. I wanted to remove the ubuntu so I went to my c drive and deleted the folder named ubuntu and two other files about wubi. When I restarted my laptop I saw that there was still one ubuntu and one vista. When I wanted to go to my ubuntu it sayd file not found. What should I do to remove ubuntu completely and instal new one?

---

### Post by DeMus on 2009-06-19
> **Kasra97 said:**
> I had vista and ubuntu 8.10. I wanted to remove the ubuntu so I went to my c drive and deleted the folder named ubuntu and two other files about wubi. When I restarted my laptop I saw that there was still one ubuntu and one vista. When I wanted to go to my ubuntu it sayd file not found. What should I do to remove ubuntu completely and instal new one?

It looks to me you installed through Wubi and just deleted the Ubuntu files inside Windows, right?
Now, when you boot, the boot menu still says there is a Ubuntu installation (which there is not anymore since you deleted it).
I'm not familiar with Wubi but it looks to me you should boot into Windows and find the bootmenu, probably on the C:\ drive. See if you can edit the bootmenu, delete the line with Ubuntu.

---

### Post by Penguin Guy on 2009-06-19
Try booting Windows in recovery mode or from the live CD (if you have one) and type 'fixmbr'. Then you will want to delete your /boot partition (if any). I'm not an expert on WUBI though, so you might want to wait for conformation before doing anything.

---

### Post by hibliss on 2009-06-19
It is gone, you just need to remove it from the boot menu. The boot.ini is gone in Vista. There are some simple instructions here - [http://www.jimmah.com/vista/content.aspx?id=15]("http://www.jimmah.com/vista/content.aspx?id=15")

Here is the Microsoft page explaining the new system, called BCDedit - [http://technet.microsoft.com/en-us/library/cc709667.aspx]("http://technet.microsoft.com/en-us/library/cc709667.aspx")

There are several graphical third party applications that can make it easier if you like. Take a look around google for BCDedit, or use the one in the first link. You just need to remove the Ubuntu entry.

One more thing, did you uninstall Wubi through Add/Remove programs as well?

---

### Post by wojox on 2009-06-19
You can't just delete files and folders from windows. You have to uninstall them through add/remove programs. You need to edit the boot menu. You could try to modify the boot menu via ControlPanel > System > Advanced >
StartUp_and_Recovery and press edit. Look for instances off ubuntu.

open run type regedit
go to 

HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

Delete Wubi registry key

---

