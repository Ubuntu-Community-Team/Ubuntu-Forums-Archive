---
title: "Problem with ieee80211...can't delete out of trash"
date: 2009-01-01
forum: General Help
---

### Post by Murrfk on 2009-01-01
I am an absolute beginner at Ubuntu and wish to learn.  I have just installed it on my MSI wind.  I installed the drivers to get wireless working, and they seem to be basically working...sometimes I lose my connection.  However, I installed the drivers, and then had a problem that I tried to fix by reopening the zip file and reinstalling.  I deleted the original folder, but I can't get it out of the trash.  I get a permission denied problem.  Seems to be related to the ieee80211 folder.

Also, when I tried to install a patch, I get this message:

insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

Something is wrong around the ieee80211 thingy.  I would like to delete everything and start again....but I can't even get the original folder to delete out of trash.  Can anyone assist me with respect to this?  TIA.

---

### Post by ibuclaw on 2009-01-01
This is probably because you used 'sudo make' to compile the modules. Just so you know, this is not needed. You only require the use of 'sudo' when you are installing the modules.
```
./configure
make
sudo make install

```

As for your trash problem, the following steps should be sufficient to remove everything from your trash folder.
```
cd ~/.local/share/Trash
```
```
sudo rm files info -rf
```
```
cd
```

Regards
Iain

---

### Post by Murrfk on 2009-01-02
THANKS!   That seems to have worked.  Things seem much more stable now.  I appreciate your assistance.  Thanks again.

---

