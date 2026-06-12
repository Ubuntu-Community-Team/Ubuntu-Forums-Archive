---
title: "Install Kubuntu with WinXP and SUSE"
date: 2005-05-03
forum: Desktop Environments
---

### Post by Padmal on 2005-05-03
This is my first post here.

I just installed kubuntu in my laptop. i had WinXp and SUSE 9.2 before. I installed kubuntu as the second linux distro. But I didn't have an option to install GRUB, and it just installed GRUB in MBR (which i did not want).  Then I couldn't boot to WinXP or SUSE. I anyhow managed to get WinXP and SUSE back. Now I want to install Kubuntu using hda6 as root partition. Is there any way to install Kubuntu without installing GRUB (later on I want to add Kubuntu to SUSE GRUB)?

Thanks in advance.

Padmal

---

### Post by defkewl on 2005-05-03
Just skip the boot loader installation :)

---

### Post by Padmal on 2005-05-03
Thanks for the reply. I will try that.

Then how to add Kubuntu to SUSE GRUB (kind of SUSE question)?  :-? 

Thanks,

Padmal

---

### Post by jtsai256 on 2005-05-03
You can probably edit your GRUB config file, if SUSE is using Grub as its boot loader. If it's using LILO, then edit your Lilo config file to include Ubuntu as one of your choices.

---

