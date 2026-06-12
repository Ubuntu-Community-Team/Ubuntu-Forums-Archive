---
title: "Lilo vs grub ?"
date: 2005-04-27
forum: Desktop Environments
---

### Post by frs-design on 2005-04-27
Hi all,

Before talking, sorry for my english, i'm french  :smile: 

I'd like to know if we can reinstall lilo to replace grub after the installation of the kubuntu ?

I currently have a system which is perfectly turning, and i don't want to crash it.

Also, if it's sure i can do a such manipulation, please tell me how to do  :razz: 

I was thinking of installing lilo with apt-get install lilo, then editing lilo.conf and typing lilo at the prompt.

Is that right ?

Kubuntu rules !

Bye @+

---

### Post by siebzehn on 2005-04-27
[QUOTE=frs-design]Hi all,

Before talking, sorry for my english, i'm french  :smile: 

I'd like to know if we can reinstall lilo to replace grub after the installation of the kubuntu ?

I currently have a system which is perfectly turning, and i don't want to crash it.

Also, if it's sure i can do a such manipulation, please tell me how to do  :razz: 

I was thinking of installing lilo with apt-get install lilo, then editing lilo.conf and typing lilo at the prompt.

Is that right ?

Kubuntu rules !

Bye @+[/QUOTE]
 Once I did the oppossite, Installed Grub to replace Lilo, and it was as simple as   apt-get install grub.  For me GRUB is a lot better than LILO, let's start by saying that it autoconfigures itself when you upgradse the kernel, no need to run any command.

Anyway, I think you can just apt-get install LILO, I would give it a try...

---

### Post by brk3 on 2005-04-27
On the subject of grub, is there a way to make it display a nice picture when loading instead of all the boot messages like on some other distros? (You know the one where it just shows a progress bar and some text saying Press escape to view text mode.. or something like that)
I was hoping the developers would have had this done on hoary..  :???:

---

### Post by zupermanz on 2005-04-27
[QUOTE=brk3]On the subject of grub, is there a way to make it display a nice picture when loading instead of all the boot messages like on some other distros? (You know the one where it just shows a progress bar and some text saying Press escape to view text mode.. or something like that)
I was hoping the developers would have had this done on hoary..  :???:[/QUOTE]

I dont think it has to do with grub.... Anyway ive solved this using splashy (or somathing like that...) its easy to install and use.....

---

### Post by jodef on 2005-04-27
> I was thinking of installing lilo with apt-get install lilo, then editing lilo.conf and typing lilo at the prompt.

Apt-get install lilo : yes
edit lilo.conf         : yes

The final command would be **sudo sbin/lilo** this will write the lilo.conf to the MBR. The good thing here is that you will get an error message if any of the info contained in the .conf file is incorrect.

HTH

---

### Post by thecrimsonking on 2005-04-27
Can somebody tell me how to do this when Ubuntu is on my 2nd hd (hdb) instead of hda?

running liloconfig wont let me change from hdb to hda.

thanks.

---

### Post by frs-design on 2005-04-28
Thank you for your replies, i'll try that this evening !

Bye !

---

### Post by zupermanz on 2005-04-29
[QUOTE=thecrimsonking]Can somebody tell me how to do this when Ubuntu is on my 2nd hd (hdb) instead of hda?

[/QUOTE]

can you post your lilo.conf?

---

### Post by thecrimsonking on 2005-04-29
[QUOTE=zupermanz]can you post your lilo.conf?[/QUOTE]

If I go ahead and tell liloconfig to put lilo on hdb it crashes, says it failed to write the mbr and my system may not be bootable.  No lilo.conf is created.

Of course my system IS bootable because my mbr is on hda.

Rebooting brings up grub with no errors.

---

### Post by zupermanz on 2005-05-01
have you tried grubconf?

---

### Post by thecrimsonking on 2005-05-02
What am I supposed to try with grubconf?

I have always used Lilo until Ubuntu and I am not familiar with Grub.

---

### Post by zupermanz on 2005-05-02
try (i think so)
sudo apt-gei install grubconf 
sudo grubconf


i ve set up mine with grubconf

---

### Post by thecrimsonking on 2005-05-03
I can't find grubconf in any of the repositories i have enabled.  Anyway, farkit.
I will just look at it as an opportunity to learn about a part of linux I have previously neglected.
Thanks for the replies zupermanz, and sorry for jacking this thread.

---

