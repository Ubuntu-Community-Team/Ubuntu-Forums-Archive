---
title: "First time user question's . . ."
date: 2005-03-20
forum: Desktop Environments
---

### Post by Crash5291 on 2005-03-20
Hey all

i have spent the last while looking through the boards for helpful topics and i have found a few that helped out but i have a few that i haven't had any luck with

this is my first time with Linux, its its installed dual boot on my machine
my hardware is

Asus K8V SE Deluxe (socket 754) 
AMD Athlon 64 3000+ 2.0Ghz (10x200) currently (10X230)
Corsair XMS PC3200 1GB (two 512MB sticks) 3-3-3-8 (currently 2.5-3-3-6)
Plextor 712A dvd burner
Maxtor HDD 160GB, 8MB, 7200PRM, ULTRA ATA133 (this is my windows drive)
Fjitsu   10GB, 512kb (my Ubuntu drive)
ATI All In Wonder 9600XT
Intel 537 56K modem

My problems
any advise on how to get the modem to work? since the cd included has only windows drivers  :-(  (currently have to use windows for the net and i use the net for 7-9hrs a day)

and is there a way to run dual monitors like i have windows setup for? (first mointor is 1024x768 fixed at 0x0, second is 1024x768 fixed at 1024x0. so i have a seamless transfer from left to right i have gotten way to used to useing the right for referance while writing articals and editing images ect.)

was going to ask about mounting the NTFS drive but i found and artical for that  8) 

Thanks All
Joe

---

### Post by flaming_monkey on 2005-03-20
Your modem is a WinModem, or Soft modem.  This basically means it uses windows software, therefore, doesn't work with Linux.

There is some software that can purchase that will get your modem working, but  it cost money and can be difficult to install.  The alternative is to buy a Linux compatible modem.  Seeing how most people are moving over to ADSL and cabel, you should be able to pick up a cheap Linux modem on ebay.

Good luck.

---

### Post by bored2k on 2005-03-20
[QUOTE=flaming_monkey]Your modem is a WinModem, or Soft modem.  This basically means it uses windows software, therefore, doesn't work with Linux.

There is some software that can purchase that will get your modem working, but  it cost money and can be difficult to install.  The alternative is to buy a Linux compatible modem.  Seeing how most people are moving over to ADSL and cabel, you should be able to pick up a cheap Linux modem on ebay.

Good luck.[/QUOTE]
 Not necessarily it means it won't work [modem] /.

My old PC-Tel Winmodem [prior DSL] worked on Xandros and Mandrake.

---

### Post by flaming_monkey on 2005-03-20
It's true that not all winmodems fail on linux, but the majority have problems i.e. don't work.

For more information on winmodems, check out the great HOWTO over at TLDP > [http://www.tldp.org/HOWTO/Winmodems-and-Linux-HOWTO.html](http://www.tldp.org/HOWTO/Winmodems-and-Linux-HOWTO.html)

---

### Post by az on 2005-03-20
[QUOTE=flaming_monkey]It's true that not all winmodems fail on linux, but the majority have problems i.e. don't work.

For more information on winmodems, check out the great HOWTO over at TLDP > [http://www.tldp.org/HOWTO/Winmodems-and-Linux-HOWTO.html](http://www.tldp.org/HOWTO/Winmodems-and-Linux-HOWTO.html)[/QUOTE]


Most work, actually, but with proprietairy and close-source binary-olnt drivers.  Only the Conexant ones have drivers for sale, the others are available for free.

You will need the sl-modem drivers for your modem.

---

### Post by gnutux on 2005-03-20
For dual monitors, you must configure your xorg.conf in /etc/X11 folder.

gnutux

---

### Post by Crash5291 on 2005-03-20
[QUOTE=azz]Most work, actually, but with proprietairy and close-source binary-olnt drivers.  Only the Conexant ones have drivers for sale, the others are available for free.

You will need the sl-modem drivers for your modem.[/QUOTE]
 Ok thanks for the info on the modem, any thoughts on the display configuration?

Joe

---

### Post by Crash5291 on 2005-03-20
[QUOTE=gnutux]For dual monitors, you must configure your xorg.conf in /etc/X11 folder.

gnutux[/QUOTE]
 didn't see your post before i posted the above thanks for the info

Joe

---

