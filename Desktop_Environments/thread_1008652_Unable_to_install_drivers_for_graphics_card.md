---
title: "Unable to install drivers for graphics card"
date: 2008-12-11
forum: Desktop Environments
---

### Post by petem37 on 2008-12-11
hi all!
im new to ubuntu and im looking to know how to install a nvidia geforce 5200 graphics card so i can change my visual effects. i have went to 'system' 'administration' 'hardware drivers' and tried to activate the driver but it tries to activate then stops and nothing happens! i really want to customize my desktop but without this graphics card working i cant change the visual effects. any ideas?? thanks!!

---

### Post by cfehunter on 2008-12-11
normally what you've described works. However you could try using envy to install your driver.

It's an application that allows you to install the nvidia driver using a wizard.

install it by running one of these commands in a terminal

For Ubuntu/Xubuntu
```
sudo apt-get install envyng-gtk
```

For Kubuntu
```
sudo apt-get install envyng-qt
```

---

### Post by petem37 on 2008-12-12
thanks,
that solved the problem. the grpahics card is installed now and i am able to change my visual settings. thanks for the help!! ;)

---

### Post by josedb on 2008-12-12
I dont know what have happened to hardware driver installer, but this last time i have to use envy for installing nvidia drivers.

---

