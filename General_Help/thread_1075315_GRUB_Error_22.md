---
title: "GRUB Error 22"
date: 2009-02-20
forum: General Help
---

### Post by tum0r on 2009-02-20
Hi! I know there are already alot of threads around the web on this topic, but mine is deffinetly unique! but not in a good way. :(

A few months ago when i tried to uninstall ubuntu off of my dual booted machine. I went into Windows partition manager, and deleted the ubuntu partition. I restarted and got..

Loading GRUB...
GRUB error 22


so, naturally i went straight for my xp re-install disc (i don't have a ubuntu live cd btw,) and i got..

Loading disc...
error
Loading GRUB...
GRUB error 22

I then decided to try and install ubuntu with a flash drive (thinking that the dvd drive is disfunctional (i still do)) and of course i get an error..

this is where i am stuck. I have $60.00 and am going to try and buy a dvd burner later next week. I hop I don't have to though :P

P.S. my DVD burner couldn't burn DVD's, nor re-install windows when the system was running smoothly. also, my BIOS now takes FOREVER to load:-({|=, will this pass once my hard drive is re-formatted?

Thank you in advance!

---

### Post by caljohnsmith on 2009-02-20
When you tried to install Ubuntu from the flash drive, what error did you get? If you can boot to the Ubuntu desktop using the Ubuntu on your flash drive, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

