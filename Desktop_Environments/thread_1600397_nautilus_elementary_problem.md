---
title: "nautilus elementary problem"
date: 2010-10-18
forum: Desktop Environments
---

### Post by atul007 on 2010-10-18
hello i want help regarding nautilus elementary.i installed it on ubuntu  10.10 and it didn't work as expected so i removed it using software  center and now i'm unable to log in to my system,it hangs on boot  screen.please tell me what to do?:sad:

---

### Post by ankspo71 on 2010-10-19
Hi,
I think removing nautilus-elementary left you with no original nautilus.

First, start your computer, then when you are about to see "Grub Loading...", rapidly press on your Esc key so you can access the Grub Menu. If you are able to stop grub from loading in time, it will show you the Grub menu, but if not you will have to restart and try it again. When you look at the Grub menu, look for the most current version of ubuntu  where it says "(Recovery Mode). Select the newest (Recovery Mode) and press Enter. Now it is going to load the base Ubuntu system and then show you another menu. It will be the recovery menu. Choose "netroot" in this menu and press Enter. Now it will bring you to a black screen where you can type commands. I don't think you will be asked for your username and password, but if it does, then enter them when it asks for them.

Okay let's try to fix the Ubuntu. Run this command to refresh the repositories:
```
sudo apt-get update
```
Now use this command to install Ubuntu:
```
sudo apt-get install ubuntu-desktop
```
If it says it is already installed try this:
```
sudo apt-get install --reinstall ubuntu-desktop 
```

This should be enough to get ubuntu working again. When it is done installing you will be able to restart your computer and check to see if Ubuntu works again. You can use this command to restart your computer:
```
sudo reboot
```.

If Ubuntu works, I recommend removing the nautilus-elementary repository so that no packages from this repository gets reinstalled again when you try to install something else. Then, if you see nautilus-elementary installed again, you can remove it again, **BUT** before before you do, make sure that you removed the repository first, and do not turn off your computer yet. Before turning off the computer again, use the same command that you used before. Go to applications > accessories > terminal. Now use the same command to reinstall Ubuntu (again):
```
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
```
Enter your username and password when asked, and say yes to reinstall ubuntu-desktop and all of the other packages.
When it is complete, it will be safe to turn off your computer.

Hope this helps.

---

### Post by nilarimogard on 2010-10-19
This is the proper way of removing Nautilus Elementary (it disables the PPA and downgrades Nautilus to the official version in the Ubuntu repositories) in Ubuntu 10.10:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```

---

### Post by lungten on 2011-01-07
> **nilarimogard said:**
> This is the proper way of removing Nautilus Elementary (it disables the PPA and downgrades Nautilus to the official version in the Ubuntu repositories) in Ubuntu 10.10:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```

Thanks. This helped.

---

### Post by WEGIII on 2011-04-01
> **nilarimogard said:**
> This is the proper way of removing Nautilus Elementary (it disables the PPA and downgrades Nautilus to the official version in the Ubuntu repositories) in Ubuntu 10.10:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```


Thanks!! Your the man! Fixed my issue :)

---

### Post by Ronalddig on 2011-06-21
thx for the commands for removing elementary , worked fine

---

