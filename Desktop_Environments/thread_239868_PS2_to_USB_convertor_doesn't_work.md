---
title: "PS2 to USB convertor doesn't work"
date: 2006-08-19
forum: Desktop Environments
---

### Post by jenred on 2006-08-19
Using a PS2 convertor to connect a legacy keyboard to a system w/no ps2 ports.

Keyboard does work not in Ubuntu (Dapper Drake). Keyboard lights flash on boot and when Ubuntu is loading but keyboard does not work w/GRUB or when I log into my desktop.

Works fine in Windows after the hardware wizard adds the ps2 convertor.

Any suggestions?

Thanks,
Jen

---

### Post by tribaal on 2006-08-19
I'm not sure I understand: your keyboard is a ps2 keyboard and you have an adapter to plug it into usb? Or the other way around?

- trib'

---

### Post by jenred on 2006-08-20
Right. Sorry left out the usb part.  ps2 to usb convertor.

---

### Post by der_joachim on 2006-08-21
I have the same problem with my laptop occasionally. Try to unplug your PS2 connector and immediately plug it in again. If you see your keyboard's leds flash, you should be good.

---

### Post by claypole on 2006-08-24
I have the same problem.  This link sounds to me like why...

[http://www.clickykeyboards.com/index.cfm/fa/items.main/parentcat/11298/subcatid/0/id/124184](http://www.clickykeyboards.com/index.cfm/fa/items.main/parentcat/11298/subcatid/0/id/124184)

I have a 3 year old Dell Multimedia keyboard with a passive PS2 to USB convertor.  It does not work with my Windows XP work laptop or my Ubuntu PC.  I am looking into buying an active PS2 to USB adaptor and will post my progress!

---

### Post by claypole on 2006-08-24
Ok, I have bought one of these [http://kryton.clickandbuild.com/cnb/shop/directusbstore?productID=456&search=pro+usb+ps2&op=catalogue-product_info-null](http://kryton.clickandbuild.com/cnb/shop/directusbstore?productID=456&search=pro+usb+ps2&op=catalogue-product_info-null)

Very helpful when I spoke to them, this also works with KVM's (which many do not).

PLEASE NOTE THAT I HAVE NOT TESTED THIS YET

I will post an update once I have installed and tested.

---

### Post by claypole on 2006-08-25
I received the adaptor today and it works perfectly.  Problem solved!

---

### Post by jenred on 2006-08-26
Hmmm. Thanks I'll give the suggested USB adaptor a try.  

Although, my clickey keyboard with adaptor works in Windows (after the ps2 adaptor is installed) and the keyboard lights go on when the computer boots up AND when I unplug/replug in when I'm in Ubuntu.  But, alas, doesn't function in Ubuntu.

---

### Post by infoseeker on 2006-08-26
Hi
My son has a P4 PC which he is having problems with, so I decided to check his memory with the memtest option with a Gentoo live CD that I have.
On first boot I could not select the memtest option as the keyboard was non-responsive, but I later found that in his PC's CMOS setup that there was an option to enable USB-keyboard support (he has a USB keyboard).  I enabled this and the keyboard awoke on next bootup....just my 2c :rolleyes:

---

