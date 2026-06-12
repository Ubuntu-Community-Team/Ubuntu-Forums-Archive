---
title: "Get ride of GRUB - the easy way. Make this a sticky!"
date: 2008-03-26
forum: Desktop Environments
---

### Post by solaceinsilence9 on 2008-03-26
[COLOR="Blue"][SIZE="3"]OK well I am in the process of reinstalling my Ubuntu system on my 1501. But before I did that I deleted my Ubuntu Partitions and swap Partitions. I wanted to have a completely Linux free hd; including no GRUB. So after I did some research and what not, reading about fdisk and MBR I came across this zip file. So I thought I'd give it a try, worse come to worse the system crashes and I just do a fresh install which would get rid of GRUB anyway. But it actually worked without any problems. I attached the file in this post. Please scan for viruses, I didnt have the opportunity because I DONT have antivirus on Vista yet. (sue me.) Anyway heres how to do it:

1: Download .zip file
2: Unzip it and save to your desktop
3: Open up command, make sure you are running it as admin
4: Navigate it to the mbrfix folder (*cd* then your directory path)
5: type *MbrFix /drive 0 fixmbr /vista*
6: Reboot

That should get rid of GRUB altogether. I just tested it on my Vista machine and worked perfect. So, if this works for others would an admin please make this a sticky? It will save other people alot of time and searching on google. Thoughts anyone?

:guitar::):guitar:[/SIZE][/COLOR]

---

### Post by Blacklife08 on 2008-03-26
excuse my ignorance, but this is to get rid of grub?  not vista?

---

### Post by solaceinsilence9 on 2008-03-26
Nooooo, NOT Vista. This replaces your existing Master Boot Record (the one that has the GRUB on it) with a copy of your MBR WITHOUT the GRUB loader. The reason for this is because if you delete your Linux partitions you still have the GRUB loader on your MBR. This gets rid of that so you boot directly to your Windows Vista OS instead of the GRUB loader then the OS. Got it?

---

