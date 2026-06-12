---
title: "Cannot access next directory in que"
date: 2009-05-11
forum: General Help
---

### Post by Seafarer999 on 2009-05-11
How do I open this folder to continue? "install_flash_player_7_linux.tar.gz"

 "cd install_flash_player_7_linux.tar.gz" does not work. 

(Actual install command is at: ~/Desktop/DesktopTemp/FP7_archive/r25/ install_flash_player_7_linux.tar.gz/install_flash_player_7_linux/flashplayer_installer).

---

### Post by taurus on 2009-05-11
If you have unpacked the install_flash_player_7_linux.tar.gz, then you would not have to include the .tar.gz when you want to change to that new directory.

```
cd install_flash_player_7_linux
```

---

### Post by geraldvillorente on 2009-05-11
extract it first 
```

sudo tar -xvpf install_flash_player_7_linux.tar.gz

```
then 
```

cd install_flash_player_7_linux

```
Open the Readme.txt and read the installation instruction

---

