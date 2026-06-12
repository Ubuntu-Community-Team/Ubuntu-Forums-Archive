---
title: "[SOLVED] desktop effects could not be enabled (Intel Corporation 82845G/GL Chipset)"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by arunvijay on 2008-01-23
hii ..
i'm a newbie to ubuntu..
first, i tried ubuntu 7.10 with a live cd..
everything worked fine!!
thn i installed ubuntu on my hard disk after a struggle..
but now the problem is - i cant enable "visual effects" it says

"desktop effects could not be enabled"

BUT
it worked fine when i tried with the live cd

i googled a lot.. but couldnt understand any thing..

ABOTHER problem is that .. when ubuntu starts its showing a blank screen with a small box running around saying "Hz ?"

SO somone plz help me .. plz explain in detail wat to do......

i m using Intel Corporation 82845G/GL Chipset Integrated Graphics Device.
1 gb ram

heres a screen shot of "desktop effects could not be enabled"
[http://picasaweb.google.com/arunnvijay/Junksz/photo#5157533360424538962](http://picasaweb.google.com/arunnvijay/Junksz/photo#5157533360424538962)

---

### Post by polmir on 2008-01-23
Connect your pc with Ubuntu to Internet
type in terminal
```
sudo update-pciids
```

after this operation please post out of this:

```
lspci
```

---

### Post by arunvijay on 2008-01-23
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by arunvijay on 2008-01-23
heyy!! comon people giv me a hand:mad::mad:

---

### Post by ronmarley1 on 2008-01-23
I had a similar problem with a new Macbook.  While running the live CD, compiz worked fine.  When I installed Ubuntu, compiz did not work.  For some reason, the live cd loaded a driver that worked, but the install used another driver.  I rebooted with the live cd, and went to System, Administration, Screens and Graphics and wrote down the name of the driver that worked.  I then rebooted to the install, went back into Screens and Graphics and changed the driver to the one that worked.  I rebooted X and all was well with compiz.
Sorry for the non-answer, but it is how I solved my similar problem.
Good luck!

---

### Post by arunvijay on 2008-01-24
heyy!! thanks bro!!
it worked!!

the driver with live cd was 'intel -experimental modesetting driver'
and that in system was 'VESA - GENERIC vesa'

i changed the driver in system to 'intel -experimental modesetting driver' , first it didnt work, i mean, it didnt change, after i click OK and open 'screen and graphics preferences' again, it showed the driver as 'VESA - GENERIC vesa' itself

thn i clicked som other driver and clicked OK, but at that point computer just hang up

when ubuntu reloaded it said "low graphics mode" and asked to select my graphics card.
at this point, i selected  'intel -experimental modesetting driver', and eurekka!! 

it worked!! :guitar:

**BUT** the effects appear to be slow.. i mean the effects are appearing jerky somtimes
may be due to my graphics card (its only 64 mb internal memory)
**but it works well within the live cd**
well just to know: is there any way to speed up things ??

---

### Post by ronmarley1 on 2008-01-24
I'm not sure why the effects work better for you using the live cd as opposed to the install.  I've read other threads asking about the same issue, but never really followed them up since it did not apply to me.  Try and search for those posts.  
Maybe it has to do with the fact that it's running compiz from RAM with the live cd as opposed to the install.  When running from the install, I'm sure some log files are generated somewhere, so maybe that's part of the issue?  Sorry just guessing here...

---

### Post by duo001 on 2008-04-01
I have attempted to change the Graphics Card driver back to the intel experimental driver, and I am unable to do so. No matter what I do, when I log back into the machine, it is set back to the intel 915 driver..


Any help would be greatly appreciated.

---

### Post by MikeKnoop on 2008-04-21
> **duo001 said:**
> I have attempted to change the Graphics Card driver back to the intel experimental driver, and I am unable to do so. No matter what I do, when I log back into the machine, it is set back to the intel 915 driver..


Any help would be greatly appreciated.

I found that in order to get my intel - experimental driver to stick, I had to first change the type of monitor I was using in the screen tab and hit OK (you could change it to anything, but change it to one you aren't going to actually use). Then, go back into the screens/graphics prefs and change the driver to the intel - experimental as well as change your monitor and resolution to what you want. If you get a dialog that says "You must log out then log back in to enable" you are on the right path.

-Mike

---

