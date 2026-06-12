---
title: "Kiba dock question"
date: 2007-03-11
forum: Desktop Environments
---

### Post by philipho on 2007-03-11
Hi all,
i have the following problem regarding kiba dock, please help.

I got the latest version of kiba dock and installed it again using the following command:
sudo apt-get install kiba-dock

The following is what i see in the terminal:


philip@philip-laptop:~$ sudo apt-get install kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kiba-dock is already the newest version.
The following packages were automatically installed and are no longer required:
  libpopt-dev liborbit2-dev libatk1.0-dev libgtk1.2 libvorbisfile3
  libwxgtk2.4-1 libflac++5c2 x11proto-xinerama-dev libxi-dev libxcursor-dev
  libxml2-dev libidl-dev libart-2.0-dev libcroco3-dev libgtk1.2-common
  libgsf-1-dev orbit2 libxinerama-dev libbz2-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

However, i am unable to find the application anywhere. It is not in applications->accessories or applications->add/remove->instaled applications

Can someone please guide me on how to start this application? sorry i am very new to linux.

---

### Post by philipho on 2007-03-11
up....

---

### Post by zekopeko on 2007-03-11
alt+f2

kiba-dock

enter

---

### Post by philipho on 2007-03-11
Hi i did that, nothing happens...

i cant find kiba-dock in the list of known applications...

---

### Post by igknighted on 2007-03-11
Are you running beryl?  Kiba dock needs a composite window manager to run properly.  Also, it wont go to the menus as there would be nothing to launch from a menu.  Try running "kibadock" or "kiba-dock" from the terminal, and once you get the proper command add it to your System->Preferences->Sessions to start on boot.

---

### Post by philipho on 2007-03-11
Hi...

Yes i am running Beryl already.

when i run kibadock on alt+F2
it says could not open location file:///kibadock

when i run kiba-dock on alt+F2
the run terminal just disappears...

when i run it in terminal i get:

philip@philip-laptop:~$ kiba-dock
failed to load /usr/lib/kiba-dock/liblauncher.so
/usr/lib/kiba-dock/liblauncher.so: undefined symbol: kiba_object_exec
failed to load /usr/lib/kiba-dock/libclock.so
/usr/lib/kiba-dock/libclock.so: undefined symbol: kiba_object_exec
Segmentation fault (core dumped)
philip@philip-laptop:~$ kibadock
bash: kibadock: command not found

---

### Post by yigal.weinstein on 2007-03-11
What repository did you get kiba-dock from?  I built it from scratch.  I don't really like the thing to be honest and unfortunately threw out the .deb I made with checkinstall or I would have uploaded it for you.

---

### Post by PriceChild on 2007-03-11
Seems like whoever you got the deb from didn't compile it correctly... speak to them :)

---

### Post by philipho on 2007-03-11
hmmm.... 

i cant install another deb over this it will say this is the latest version.
How do i uninstall this? do u just delete the file?

---

### Post by yigal.weinstein on 2007-03-11
if it is a deb then

```
sudo dpkg -r "package"
```

repace package with kiba-dock ( or what ever the package was called )in this case

you could also use aptitude or apt-get but dpkg works fine.  You can even use Synaptic if that is what you use.  There are many options but just use the one above in a terminal its easy.

---

### Post by philipho on 2007-03-12
Hello yigal.weinstein,

thanks for helping...
I tried that command but it gives dependency errors as follows: 

philip@philip-laptop:~$ sudo dpkg -r "kiba-dock"
dpkg: dependency problems prevent removal of kiba-dock:
 kiba-plugins depends on kiba-dock.
 gset-kiba depends on kiba-dock.
dpkg: error processing kiba-dock (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 kiba-dock
philip@philip-laptop:~$

---

### Post by igknighted on 2007-03-12
add the dependencies to the list to remove as well... "sudo dpkg -r kiba-dock kiba-plugins gset-kiba"

---

### Post by philipho on 2007-03-12
Thank you.

I managed to uninstall it already...

---

