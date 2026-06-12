---
title: "Kubuntu wont load"
date: 2009-05-04
forum: General Help
---

### Post by shaneg-nz on 2009-05-04
Hi, first off, hi everyone..
I have been using Kubuntu for about 3-4 months and love it, a few learning curves and a couple of re-installs on the way but flying along great now, Double booting Vista and Kubuntu Jaunty atm.
Havnt used vista in about 3 months, a lot slower compared to Kubuntu...
And slowly spreading the linux love to a few friends/family once the see how easy and useable it is.
 
Anyway, i was creating a virtualbox to load up Backtrack 3 so i could test my wireless around my house as there are a few around my area and dont want people getting into it (internet is really expensive in nz, adsl2 is just arriving) and cant be bothered rebooting all the time as its on a usb stick, and it was gonna be my tester vbox as i havent used it before, and was gonna do a vista vbox after that..
 
So created a new box, the *.vdi was created under /home/shane/backtrack3/backtrack_boot.vdi mistakenly created it at 8gig
and it was all going well until about 43% into it it froze, nothing would work
ctrl+alt+f12 ctrl+alt+del .... nothing, so held down my power button to turn off
went to restart and selected my kubuntu from the boot menu
and it goes straight to /grub gives a few options press tab etc...
 
push "e" on fallback 1, which is the kubuntu/boot/menu.lst option
and i get error 15
 
none of the other fallbacks work
halt halts the system
reboot suprisingly reboots
but cant get past there
vista is still fine, so its only kubuntu thats affected
 
im guessing when i created the vbox it may have deleted some files? but not sure
any ideas or another fresh re-install, i dont mind i like learning from mistakes
 
and any tips about the vbox incident, i.e dont make it 8gig??

---

### Post by Bindsa on 2009-05-04
Try this reference guide:
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#15"]
GRUB error 15[/URL]

---

