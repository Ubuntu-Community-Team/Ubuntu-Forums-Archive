---
title: "Terminal Emulators Fail to Locate Installed PCF Fonts"
date: 2009-02-08
forum: General Help
---

### Post by gfulton on 2009-02-08
Hi,

I have installed a pcf font, vga11x19, following the community font-howto - and some other posts on font issues. vim-gnome is able to see and use the font however I cannot seem to get any terminal emu's (rxvt, Eterm, xterm) to load the font using the -fn (or similar) flag. They just report "font not found - using fixed".

I have also enabled bitmap fonts. 

Thanks,
-gf

---

### Post by osirisgothra on 2013-02-23
I used the following when i put the font in, also, a side note, if you extract it using ark it will "appear" to be successful even when it is not, I had it extract directly to /usr/share/fonts/X11/misc and thought it worked, checked it, and it wasnt there! Found out that the permissions were denied, so I just extracted it to my home folder, went into the shell and used sudo to copy it to the right directory. "sudo cp vga11x19.pcf /usr/share/fonts/X11/misc" and then.. since it wasnt gzipped in the first place (it was in a tar with other files) i had to re-gzip it in its own file just using "sudo gzip vga11x19.pcf" which then renamed it to "vga11x19.pcf.gz" like the others in that dir. Ok, then i ran (from that same folder) just to be safe this:
"sudo xmkfontdir ."
and
"sudo xset fp rehash"
after that all i did was run rxvt (i just ran it from xterm just so i could see the commandline was indeed valid)
"rxvt -bg black -fg white -fn vga11x19"
without any problem, but only after i did all that... i of course jumped the gun and did it the fast way the first time and second and third, only to find out i was missing steps. Hope this helps, oh yeah btw my ubuntu version is 12.10 quantal (32-bit) but i also run a 64-bit version on my other machine so i verified it works on both 32 and 64 bit for me, i installed the minimal server installation and then manually installed all  my packages myself finding out that it works alot better to do that if you want a custom setup, otherwise reckless package installs ive found corrupt the system and confuse the package manager after a while (i avoided kubuntu-desktop like the plague and went with just kde-full, xorg-server, etc)... hopefully this with the above will give you some idea of what you need to do next if you still cant do it drop me a line i know alot of other people who could go into greater detail. Hope this helps all future readers as well!
- osirisgothra (website-less, zymic shut me down for no reason other than switching to linux from windows!!!???!)

---

### Post by matt_symes on 2013-02-23
Ancient thread so closed.

---

