---
title: "Dell Wireless 355 Bluetooth for Inspiron 1420"
date: 2007-11-02
forum: Dell  Ubuntu Support
---

### Post by RobertGloverJr on 2007-11-02
There was no option when I recently bought my Inspiron 1420 with Unbuntu 7.04 on it to ask for bluetooth.  I read in forums that it used to be offered but was taken off the purchaseable options recently to save Dell from the work of figuring out the correct drivers needed.

   So I called Dell and bought the Dell Wireless 355 Bluetooth Module, for Inspiron 1420 and it arrived by mail a few days ago.  

   It has no instructions except for a "drivers CD" which I assume only works on Windows and has nothing whatsoever on the CD that refers to Linux or Ubuntu.

   I have no idea how to install this tiny little circuit board into the Dell Inspiron 1420 laptop.  And if I ever figure out how to put the little circuit board into the laptop,  I have no idea how to make it work in unbuntu.

   Suggestions  very much appreciated.

postscript:  I actually don't even know what I will use bluetooth for, if I ever get it working.  I bought every possible upgrade option, so it seemed a shame not to spend another $20 and get bluetooth too.
Does anyone have any suggestion what to do with my bluetooth?

---

### Post by ymo on 2007-11-09
> **RobertGloverJr said:**
> 
   I have no idea how to install this tiny little circuit board into the Dell Inspiron 1420 laptop. 

Instructions for installing the Bluetooth module can be found in the 1420 Owner's Manual on the Dell Support Web Site.

[http://support.ap.dell.com/support/edocs/systems/ins1420/en/OM/parts.htm#wp1130573](http://support.ap.dell.com/support/edocs/systems/ins1420/en/OM/parts.htm#wp1130573)

Scroll down to "Internal Card with Bluetooth(R) Wireless Technology". The card will reside in the memory module compartment according to the manual.

I have no idea what you might use it for - a single Bluetooth device is not much use. Interfacing to mobile phones seems quite popular, as do cordless mice and keyboards.

---

### Post by RobertGloverJr on 2007-11-09
> **ymo said:**
> Instructions for installing the Bluetooth module can be found in the 1420 Owner's Manual on the Dell Support Web Site.

[http://support.ap.dell.com/support/edocs/systems/ins1420/en/OM/parts.htm#wp1130573](http://support.ap.dell.com/support/edocs/systems/ins1420/en/OM/parts.htm#wp1130573)


  I spent two hours last night with Dell support trying install the Bluetooth card.  They insisted all I had to do was read that exact section of the manual you refer to.

   However I was able to prove to them that the picture at that link it totally meaningless and that it is impossible to install the bluetooth based on that meaningless picture and the nonsensical directions in the user manual.
  
   Dell support then emailed me 4 pictures of the the actual process which were enough for me to figure out how to do it.  Without the 4 pictures  Dell support emailed me, nobody could ever possibly install that bluetooth card.  I would post all 4 pictures to this forum if it was allowed.  They really help.  But even with the pictures it requires a good deal of ingenuity to figure out how to install that card because the wire in the Dell laptop with the mail socket-plug is lodged into the middle of the bluetooth frame and you have to remove the socket from the frame before you can snap the bluetooth card into the frame.  That is not explained anywhere in the Dell user guide or in the additional 4 pictures they sent me.  Also, the Dell user guide you refer to does not mention anywhere that it is impossible to install the bluetooth unless you use a screwdriver to remove the bluetooth holder that is held in by a single screw, inside the memory compartment.

    I now have the Bluetooth card installed correctly and it is recognized okay by unbuntu 7.04.

---

### Post by ymo on 2007-11-09
Glad you managed to install it. I don't have a 1420 so was unaware that the instructions in the manual were so poor. I have a 6000 and while I have not tried to install the Bluetooth module I have opened the little door inside the battery compartment and seen how easy it would be to plug the module into the cable.

---

### Post by locky28 on 2008-02-05
I'm looking to do this myself on my 1420 as I didn't think I needed bluetooth when I first got my lappy but I've been in several situations were I wish I had it, the main one being the USB connector for my Sony Erricson Mobile is sh*thouse and I'd like to be able to transfer files to and from it with fiddling with the cable or having to carry around a MicroSD adapter.

Just wanted to know how much you payed for it Robert? I know they're $20 when you select them to be installed when you first get it and that it should cost less since a Dell tech doesn't have to install it but you know what companies are like with post sale parts.

I rang Dell to order parts and they said they won't have any in stock until February 15th and they can't give me a price until they had them in stock, however he said it will definetely be under $100 :O I was thinking $40 at the most!!!

---

### Post by Packrat73 on 2008-02-06
I would like to know how you got it to work under Ubuntu? I have tried 4-5 different tutorials and none has worked for me.

---

### Post by dicecca112 on 2008-02-06
should be recongized automatically.  I have found that it doesn't recognize devices automatically.  You have to make the Item you want to use discoverable then enter
 
sudo hidd --search
 
It'll find and connect your item

---

### Post by master5o1 on 2008-02-13
> **dicecca112 said:**
> should be recongized automatically.  I have found that it doesn't recognize devices automatically.  You have to make the Item you want to use discoverable then enter
 
sudo hidd --search
 
It'll find and connect your item


```

jason@meinDell:~$ sudo hidd --search
sudo: hidd: command not found
jason@meinDell:~$ hidd --search
The program 'hidd' is currently not installed.  You can install it by typing:
sudo apt-get install bluez-utils
bash: hidd: command not found
jason@meinDell:~$ sudo apt-get install hidd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hidd

```

Hardy Heron alpha 4.

---

### Post by dicecca112 on 2008-02-13
Your answer is in your post, hidd is part of 

sudo apt-get install bluez-utils

run that, and it should install hidd

---

### Post by hardawayd on 2008-02-13
It says the bluez-utils is already installed but still can not find the hidd command.

---

### Post by rapolas on 2008-03-11
I have the same problem. hidd is not found, and bluez-utils is installed..

---

### Post by delca5 on 2008-03-11
I have a similar problem with my dell 1420 (no N), and i solved it :
[http://ubuntuforums.org/showthread.php?t=715732](http://ubuntuforums.org/showthread.php?t=715732)

---

### Post by locky28 on 2008-03-11
Hi all,

I got my module a while ago, installation was a breeze and I just re-enabled it in Bios and Ubuntu detected and installed it straight away. 

However I couldn't see any bluetooth devices at first and after some googleing I installed **gnome-vfs-obexftp** and now it works! Mostly anyway.
After I create a partnership with my Mobile I can now view all the files on it and pull them across to my laptop. My phone can see my laptop but isn't able to access  it for some reason :S but I'm not to fussed as long as my Laptop can send to/receive from my phone. Haven't tested any other bluetooth devices just yet.

Thanks for all the help on this one,

---

### Post by yeowzuhx3 on 2008-03-12
I just got a 1420. I thought the bluetooth was an option,ordered it, was told it was not an option with Ubuntu, and ended up with Bluetooth anyway. I bought a Microsoft Bluetooth mouse, read the directions and it worked.  And I'm an absolutely absolute beginner.

---

