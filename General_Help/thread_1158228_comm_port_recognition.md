---
title: "comm port recognition"
date: 2009-05-13
forum: General Help
---

### Post by mario1 on 2009-05-13
ive installed ubuntu on my new machine and i noticed that its not recognizing all of the com ports, ive asked the manufacturer for instructions on how to get them to recognize and they respnded below, but im just not sure exactly what to type in terminal or what to edit, if someone could please help me ide appreciate it greatly, im very new to linux

[manufactureres reponse]
Now the solution on how to make the internal serial interface to work under Linux -- All you have to do is to
configure the Linux kernel to recognize more than 4 serial ports. Add the following kernel boot option to /boot/grub/menu.lst file.  $$$[how do i edit this?]$$$

8250.nr_uarts=6        $$$[where does this go? anywhere?]$$$

 Also add the followings to /etc/rc.local:

setserial /dev/ttyS4 port 0X2F0 irq 11 uart 16550A baud_base 115200
setserial /dev/ttyS5 port 0X2E0 irq 10 uart 16550A baud_base 115200


xorg.conf and make sure under InputDevice section you see this line : 

Option "Device" "/dev/ttyS4" $$$[does this go anywhere in the file?]$$$

---

### Post by FlaHAM on 2009-11-18
Did anyone answer this Question?
Better late than never!

The string 8250.nr_uarts=6
is added to /boot/grub/menu.lst

Example:
title           Ubuntu 8.10, kernel 2.6.27.7
uuid            8bb3bbfc-63cd-4a1b-9c78-218bfd13ccd5
kernel          /boot/vmlinuz-2.6.27.7 root=UUID=8bb3bbfc-63cd-4a1b-9c78-218bfd1
3ccd5 [COLOR="Wheat"]8250.nr_uarts=6[/COLOR] ro quiet splash
initrd          /boot/initrd.img-2.6.27.7
quiet

---

