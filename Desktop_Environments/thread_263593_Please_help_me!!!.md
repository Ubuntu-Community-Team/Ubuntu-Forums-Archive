---
title: "Please help me!!!"
date: 2006-09-23
forum: Desktop Environments
---

### Post by hvaughn on 2006-09-23
I'm totally new to this, so bear with me. I have a dell that I got from a friend. The hard drive was fried. So I bought a new one and replace the bad one. I then installed ubuntu from the cd. When I reboot, I get the F1 to reboot, F2 to setup message. :mad:  If I reboot and hit PF12 and then pick the option to "load to partition utility" ubuntu will load and everything seems to work. :)  What did I miss when I ran the install? I think it has something to do with the master boot record. I've searched thru the forums and on the web, but haven't been able to find anything to assist me. 

Can someone please help me???  [-o< 

thanks

---

### Post by kesomir on 2006-09-23
Silly question from me but did you remove the cd? Otherwise when the computer boots if the CD is before the HHD in the boot sequence it will load from the cd on every startup.

---

### Post by crossedout on 2006-09-23
It sounds as though you installed GRUB somewhere other than the MBR.  Do you know where you installed it?

-Xout

---

### Post by hvaughn on 2006-09-23
i have removed the cd
is grub automatically installed when I run the cd?

---

### Post by crossedout on 2006-09-23
Yes GRUB is needed to get to Ubunutu.
Follow [this]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub") link for an explanation on restoring your GRUB.


The other suggestion would be to reinstall but make sure you have GRUB install to the MBR.

-Xout

---

### Post by hvaughn on 2006-09-23
i used the link and ran the grub commands.
however, i still have the same problem.](*,) 
get the f1 to reboot f2 to setup. i have to
ctrl alt delete and hit f12 to boot to utility 
partition. i just don't get it. i have no problem
wiping out the drive and reinstalling. but i didn't
see anything the first time i installed about grub.
if i reinstall, where do i look to do this "grub"
thing. 

sooo confused......

---

### Post by Orestes on 2006-09-23
Sounds to me like you've installed ubuntu, and grub, into the restore partition!

Could you post your partition layout?

```
sudo cfdisk -Ps /dev/hda
```

will print a list of partitions to the console.

Good luck!

---

### Post by hvaughn on 2006-09-24
partition table:

cfdisk - P {r|s|t} [options] device

is this what you need?

---

### Post by Orestes on 2006-09-24
> partition table:

cfdisk - P {r|s|t} [options] device

is this what you need?
Reply With Quote 

There's an echo in here!! :)
in here...
in here...
here...
here...
...

---

### Post by wombat20 on 2006-09-24
He means yes.  :)

---

### Post by hvaughn on 2006-09-24
i'm confused
did i provide the correct info?

---

### Post by crossedout on 2006-09-24
You need to run the command that Orestes gave.  You need to run it from a terminal and paste the output here.

-Xout

---

### Post by hvaughn on 2006-09-24
first    last   
# type     sector   sector  offset length 'filesystem type(id) flag
1 primary         0 486898019 63 486898020 linux (83)          boot
2 primary 486898020 488392064  0   1494045 extended (05)       none
5 logical 486898020 488392064 63   1494045 linux swap / so (82)none

sorry, but I coulnd't paste b/c I'm using the forums with my laptop. I hope this is the info you need[-o<

---

