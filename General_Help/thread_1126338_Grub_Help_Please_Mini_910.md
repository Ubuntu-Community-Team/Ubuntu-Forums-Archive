---
title: "Grub Help Please Mini 910"
date: 2009-04-15
forum: General Help
---

### Post by anti_s0cialx on 2009-04-15
I don't know what happen but every time I sign on to my laptop I they ask me to enter a password and then they ask me to enter an HDD password then it goes to MBR_ Grub Loading Grub 2 and it takes me to a screen that has 
[Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]
grub> _


I dont know what to do cab anyone help me

---

### Post by LowSky on 2009-04-15
> **anti_s0cialx said:**
> I don't know what happen but every time I sign on to my laptop I they ask me to enter a password and then they ask me to enter an HDD password then it goes to MBR_ Grub Loading Grub 2 and it takes me to a screen that has 
[Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]
grub> _
  

To help we will need more informatuion on what you did or were doing before these errors popped up.
Second was the Dell Mini9 prchased with Ubuntu? Dell does give you tech support for Ubuntu machines, they might be able to get the ball rolling quicker than the forums can.

---

### Post by anti_s0cialx on 2009-04-15
I went into the PhoenixBios Setup Utility and went to Security there it told me to set a Supervisor Passowrd and A User Password and also a password for my HDD so after I did that I saved it and it restarted my computer and thats when the 
[Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]
grub> _
 message started coming up I tried to call dell and they said that the only thing they could do was have me send my mini back and have them reboot my computer but I dont want to send it in and wait for 8 days if there is away I can fix my computer myself.

---

### Post by Colochine on 2010-01-01
> **anti_s0cialx said:**
> I went into the PhoenixBios Setup Utility and went to Security there it told me to set a Supervisor Passowrd and A User Password and also a password for my HDD so after I did that I saved it and it restarted my computer and thats when the 
[Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]
grub> _
 message started coming up I tried to call dell and they said that the only thing they could do was have me send my mini back and have them reboot my computer but I dont want to send it in and wait for 8 days if there is away I can fix my computer myself.
  

Same Problem can anyone help with this issue??

thanks
Colochine

---

### Post by drs305 on 2010-01-01
1. Well, can you go back into BIOS and remove the security settings?

2. Grub 2 has password protection if you really feel you need it. It's not fully developed but it offers at least minimal protection. You can set it up for specific kernels, specific user access, etc. It's not fully scripted but I just finished a guide on how to set it up.  

I know what you want to do is get back into your system, I just offer the second paragraph as an alternative if you solve paragraph 1.  [Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019")

---

### Post by Leppie on 2010-01-01
try booting with a livecd, [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt

---

