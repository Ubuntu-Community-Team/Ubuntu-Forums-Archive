---
title: "wanna install the xubuntu desktop"
date: 2007-03-10
forum: Desktop Environments
---

### Post by tocilog on 2007-03-10
i keep getting this error message: 

The following have unresolvable dependencies. make sure all repositories are opened and enabled yada yada yada

xubuntu-desktop:
 Depends: dvd+rw-tools but it is not going to be installed
 Depends: gaim but it is not going to be installed

i dont even have a dvd+rw drive. gaim isnt installed, i use kopete. so how does one go about fixing this?

also, if i install the xubuntu desktop package, ubuntu basically becomes xubuntu right?

---

### Post by FyreBrand on 2007-03-10
1. First the easy one: Ubuntu becomes Xubuntu right?  No not really.  Whatever desktop environment you have will still be installed.  So you will have Ubuntu or Kubuntu desktop installed.  When you login you can choose what desktop environment you want to login as.  Just choose Xubuntu.  Your other DE will still be available.

2. Now the almost easy one:  Why won't Xubuntu install.  Gaim is a dependency of the xubuntu-desktop package so that's why it wants to install it.  If you have the appropriate repositories  enabled and still can't install you might have broken packages.  You might also have conflicting package versions depending on what you've installed and what and when you've last upgraded.

Before you tried to install xubuntu-desktop did you update your package list?  For example:
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

The following solutions can fix things, but they can also cause some packages to break so fix at your own risk:
If you're still getting error messages you can try and fix them with
```
sudo apt-get install -f
```This will try and fix broken package depencies.

Before installing xubuntu-desktop I would do the following
1. Backup all my important files

2. Have a live CD handy in case things go wrong.

3. Update my system:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
If you have broken packages use the -f switch after dist-upgrade

4. Install xubuntu-desktop
```
sudo apt-get install xubuntu-desktop
```

---

### Post by magnus07 on 2007-03-28
I have ubuntu 606 on a very slow PIII-667 with 392MB. 
Wished to speed-up and so using your instructions I have installed flawlessly xubuntu.
After an HW reboot it popped up a xubuntu login. Good
After login I get all the old things I had.
How can I veryfy it's XFCE and not Gnome? :confused: 
Thanks for your previous response that was right to the point.
magnus07

---

### Post by lawrens on 2007-03-28
There's a xfce option under the session menu on the login screen, so you'll have to choose that inorder to log into your new xfce desktop, else you'll remain gnome, hope that helps :)

---

