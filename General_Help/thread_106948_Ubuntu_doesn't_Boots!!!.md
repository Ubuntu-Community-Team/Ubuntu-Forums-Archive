---
title: "Ubuntu doesn't Boots!!!"
date: 2005-12-21
forum: General Help
---

### Post by inlogic on 2005-12-21
Hail!
I've followed this [wiki]("http://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29") on how to setup ndiswrapper so I could use my linksys wusb11, everything okay according to the wiki, the hardware was identified has present, and I added 'ndiswrapper' to the modules under etc/modules, now everytime Ubuntu starts to load, on that part "Calculating Module Dependencies etc..." it gives an error relationed with the ndiswrapper module, something like "load_drivers(321), too many .sys for driver xpto", and it stops there, the system doesn't loads :confused:  I could fix it if I could change the 'module' file, but I can't access it because ubuntu doesn't boots :shock:  need help, been searching on the forums but didn't find anything on these lines :|

My question is, is there anyway to skip that 'module' loading part, or anyhow have access to root through command line or something, so I could edit the 'module' file and make it work again? :S

thanks in advance!

---

### Post by joshuapurcell on 2005-12-21
You can either hit CTRL-C when you get to that portion of the boot process, or just use the grub menu to select the recover option to boot up in single user mode. Once you are logged in and at a command prompt, then edit /etc/modules and take the line out that says ndiswrapper:```
sudo vi /etc/modules
```

You can manually bring up the ndiswrapper module by typing this at a command prompt to see if you continue to get errors:```
sudo modprobe ndiswrapper
```
If you get any errors when doing this post what it says here.

---

