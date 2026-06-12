---
title: "Issue with reboot after install"
date: 2007-04-10
forum: Desktop Environments
---

### Post by tehmilk on 2007-04-10
Hi guys,
    Recently I had gotten tired of windows x64 and wanted to try out some new stuff, So I went out and got a 160GB hdd and an 80GB hdd.  The 160 I installed vista on and we wont even go there.  The 80 I installed ubuntu 6.10.

    The problem I'm having is:  whenever installation completes, and it goes back to the ubuntu loading screen, it says in the corner to "Eject the disc and press ENTER to continue"  and the cd drive opens.  I press enter, and nothing happens.  Thinking maybe it just needs some time to process, I leave it alone and happen to fall asleep.  I wake up this morning, 3 hours later, and still sitting on that screen.
    Annoyed, I simply hit the reboot button on the tower thinking it might work.  I check my BIOS to make sure all the boot orders are correct and reboot.  Successful boot beep, computer posts, and everything goes fine until it tries to boot.  Goes past the boot from CD part, and then just sits there.

Everything works fine on my HDD with x64, and when I had installed windows 32-bit on that HDD, it worked fine as well.



My hardware is:
DFI LanParty UT SLI-D
2GB OCZ PLatinum PC3200 ram
AMD Athlon X2 4400
nVidia GeForce 7950 512MB
Creative Soundblaster Audigy 2
Ultra X-Connect 2 550W modular PSU

---

### Post by mister_p_1998 on 2007-04-11
Did you install grub after the main Ubuntu installer finished?
If not it wont boot.
Steve

---

### Post by tehmilk on 2007-04-11
Oh wow, I feel like a complete moron.  I forgot to install grub.  

Well actually I didnt forget, I just figured that a boot loader wouldnt be necessary if I wasn't dual booting

---

### Post by tehmilk on 2007-04-12
Everything running fine now.  Just powered off and unplugged my terabyte storage drives and it went perfectly.  I guess the way I had drive letters assigned was installing GRUB to on of those drives, which arent even in the boot list.

---

