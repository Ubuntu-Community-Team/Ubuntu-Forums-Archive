---
title: "Problem with Graphics Driver"
date: 2011-03-01
forum: Desktop Environments
---

### Post by arjunbajaj on 2011-03-01
Hi,

I had installed Ubuntu 10.10. Then I installed Unity from the software center and then I installed a driver(poulsbo) for Unity.

I ended up in making my laptop not even start.

Then I removed the driver and Unity through safe mode.

But my computer doesnt even starts. Not even in safe mode.

When I start it, it shows a blue screen with this black strips in it. Then it hangs forever. If I do something before that hang, it hangs on "Checking Battery State" forever... And in the safe mode, it just shows a black screen and hangs...

What should I do?
Please Help.

BTW my Laptop is IBM R51. Its about 7 years old.

Thanks...

---

### Post by runeh76 on 2011-03-01
Hello

Read next pls:
[http://ohioloco.ubuntuforums.org/showthread.php?p=9137450]("http://ohioloco.ubuntuforums.org/showthread.php?p=9137450")

---

### Post by arjunbajaj on 2011-03-01
hey runeh76... thanks for the input...

but i tried it and it didn't work.

what i did:
booted into the live cd
mounted my drive
opened nautilus in root mode
went the etc/default/grub
opened the file

updated the line where it was written: GRUB_CMDLINE_LINUX_DEFAULT="quite splash"

to GRUB_CMDLINE_LINUX_DEFAULT="quite splash nomodeset"

Saved it
and rebooted

It didn't work. Again it hung at "Checking battery state"

What should I do?
Please help...
Thanks...

---

### Post by arjunbajaj on 2011-03-01
and when the computer starts... it directly starts in the virtual terminal. and then when i press Ctrl+Alt+F7 to go to the GUI it gets stuck on the checking battery state...

---

### Post by theozzlives on 2011-03-01
If you can get to the login screen, click on your name and select "Ubuntu Desktop" on the bottom. You may have to re-install Unity for it to work.

---

### Post by arjunbajaj on 2011-03-01
i cant get to the visual login screen. only the virtual terminal login. what should i do?

---

### Post by runeh76 on 2011-03-01
This is copyed from another site:
"The above fix also gave me high res ctl+alt+F1-F6 console modes but i can not change to GUI pressing ctrl+alt+F7.  It will be stuck at 'checking battery state [ok]'. To get back to GUI i log in to root from first console and restrted gdm. Then Gnome will start from login screen and all your work at GUI is lost  . Its ridiculous and very annoying. There are many ugly multicolored flashes in my screen when i change from one console to another and some times it gets all stuck."

Okey..u could try from root-terminal:

```
sudo apt-get install gnome-desktop
```
```
startx
```

If that doesnt work, add new user

```
adduser test
```
```
passwd test
```

---

### Post by inkrypted on 2011-03-01
Try to disable ACPI in your BIOS and then reboot. You can usually get to the BIOS during boot by using the DEL,F1,F2 keys there is usually a message at boot that says press (one of the keys I mentioned) to enter setup.

---

### Post by arjunbajaj on 2011-03-01
hey it cant find the gnome-desktop package and the test user is not helping...

i'm really stuck with nothing here....
what should i do?
isn't there any way i can restore back my system... something like a restore point?

thanks,,,

---

### Post by arjunbajaj on 2011-03-01
inkrypted i'm not getting from where to disable ACPI. I think its not there on my BIOS... I had also tried that earlier for something else but it wan not there...

---

### Post by runeh76 on 2011-03-01
Yes there is old kernels what u can try..hit SHIFT or ESC when reboot.

Internet doesnt work in ROOT-terminal?
Did u create "test" user?

U should configure GDM also to auto boot that account:
```
gksudo gedit /etc/gdm/custom.conf

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=**test**
TimedLoginEnable=false
TimedLogin=**test**
TimedLoginDelay=5
DefaultSession=xsession

---

### Post by runeh76 on 2011-03-01
Another idea...video-driver?

post next code output:

```
sudo lspci -v
```

---

### Post by Krytarik on 2011-03-01
Since I believe the installation of the mentioned video driver created or modified "/etc/X11/xorg.conf", you should try to rename that file, if it indeed exists.

---

### Post by arjunbajaj on 2011-03-09
hey everyone, thanks for ur inputs and spending ur precious time to write them...

but nothing quite worked...

so i just reinstalled ubuntu on my laptop...

thanks...

---

