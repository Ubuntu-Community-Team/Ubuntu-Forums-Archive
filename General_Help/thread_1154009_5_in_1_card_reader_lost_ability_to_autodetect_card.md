---
title: "5 in 1 card reader lost ability to autodetect cards but not usb in 9.04"
date: 2009-05-09
forum: General Help
---

### Post by alanwalterthomas on 2009-05-09
I have a fairly generic 5 in 1 card +1 USB internal card reader (see it at [www.ngear.ca](www.ngear.ca)) that worked under 8.04 with whatever card I threw at it (SD, XD, CF) & the usb. I would put in a card, ubuntu mounted it, & a little window popped up showing its contents. Now with 9.04 that only happens with the USB entry. The cards are good & work in other devices. If you look at the ngear site you'll see the card reader has 2 LEDs. One red, to indicate power, which stays on, & another green, which indicates a card is inserted. (I think it blinked too when transferring data with 8.04) With 9.04 the green light goes on with the card in it, but that's all. Ubuntu doesn't seem to recognize it.
dmesg | tail didn't change when putting it in, taking it out.

Ok, now I've played with it a little more since I started writing & made it work by chance, but it still doesn't work as it should. I got it to work by putting in a SD card (nothing happened) then putting in a USB stick (both detected at the same time). Afterwards, I could put the card in & take it out & it would behave as it should, so long as I kept the usb stick in as well.
I also found that if both usb drive & SD card are attached neither is detected (appears on the desktop) when ubuntu loads. Reinserting the USB drive results in detection of both. The USB alone also isn't detected at startup - reinsertion needed. I don't know how to probe for it.

I can't make sense of every line of lspci, but nothing changed from when it didn't autodetect to when it did.

dmesg | tail showed
alan@alan-desktop:~$ dmesg | tail
[ 1830.730849]  sde: sde1
[ 1924.698075] sd 8:0:0:2: [sde] 3842048 512-byte hardware sectors: (1.96 GB/1.83 GiB)
[ 1924.698921] sd 8:0:0:2: [sde] Write Protect is off
[ 1924.698927] sd 8:0:0:2: [sde] Mode Sense: 03 00 00 00
[ 1924.698932] sd 8:0:0:2: [sde] Assuming drive cache: write through
[ 1924.699548] sd 8:0:0:2: [sde] 3842048 512-byte hardware sectors: (1.96 GB/1.83 GiB)
[ 1924.701105] sd 8:0:0:2: [sde] Write Protect is off
[ 1924.701110] sd 8:0:0:2: [sde] Mode Sense: 03 00 00 00
[ 1924.701113] sd 8:0:0:2: [sde] Assuming drive cache: write through
[ 1924.701122]  sde: sde1

This might have something to do with it: During boot, right after grub says Starting up... , "modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory" appears, twice if I have the USB stick inserted.

Any ideas? Thanks

---

### Post by silentviper324 on 2009-05-22
I have a similar card reader to yours and I also have the same problem you're having. Sometimes, when I view Computer, the drives will be listed and it will work fine while most of the time nothing appears there at all. Hopefully, someone can find a solution to this soon because its a pain to boot into windows 7 jus to transfer files to the SD card.

---

