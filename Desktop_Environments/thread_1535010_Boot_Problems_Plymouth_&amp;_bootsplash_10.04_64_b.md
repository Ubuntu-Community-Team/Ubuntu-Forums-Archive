---
title: "Boot Problems: Plymouth &amp; bootsplash 10.04 64 bit"
date: 2010-07-20
forum: Desktop Environments
---

### Post by K_REY_C on 2010-07-20
I’m on a Dell XPS M1530 running Ubuntu 10.04 64 bit and I can’t boot into my GUI (and my non-GUI is so pixelated I can’t tell what is going on). It stems from trying to fix the resolution of my boot splash (which has always been off on my 1440x900 monitor).

These are the commands I used to attempt to fix the problem (and cause it?)

I used these instructions to download a new theme (from here: [http://tinyurl.com/28283l6]("http://tinyurl.com/28283l6") ):
sudo apt-get install plymouth-theme (though I installed themes via synaptic)
and then used
sudo update-alternatives --config default.plymouth (via the terminal)
in order to change to a newly downloaded theme (and I did).

Then I rebooted and could see things during the boot splash but it was doubled and totally pixelated. When I used CTRL+ALT+F2 and logged-in without a GUI it was still pixelated and I couldn’t see what I was typing.

Does anyone know how I can fix this?

This site seemed to suggest possible problems: [http://tinyurl.com/29coa9g]("http://tinyurl.com/29coa9g") but I’m unsure how to fix them. They suggest booting into recovery mode (which I did try by holding down SHIFT while booting) but I still had the non-GUI resolution problem (and the GUI black screen if I tried that).

I’ve also tried this (though I couldn’t see what I was typing or what the output was) to fix the problem (but it didn’t): sudo dpkg-reconfigure plymouth && update-initramfs -u

Any help appreciated. I’ll by trying more things on my own but I’d love it if someone who understands the problem might be able to shed some light. Thanks much. KYLE ~from a Knoppix Live CD

---

### Post by K_REY_C on 2010-07-20
I fixed the boot issue (for GUI) by:

Boot
CTRL+ALT+F2
login (username, password)
sudo update-alternatives --config default.plymouth
0 #this is a zero, then hit ENTER
sudo update-initramfs -u

Then a rebooted and it went to my GUI.

Still have the double vision in non-GUI and on the bootsplash screen. Any ideas how to fix those issues?

Thanks again. KYLE ~from my ubuntu 10.04 install

---

### Post by K_REY_C on 2010-10-11
If anyone stumbles upon this old thread --- I upgraded to 10.10 and followed the info here: [http://ubuntuforums.org/showthread.php?p=9954835#post9954835](http://ubuntuforums.org/showthread.php?p=9954835#post9954835)

All is well now. I hesitate to call this "solved" (it might not work for 10.04) but it certainly works for 10.10.

---

