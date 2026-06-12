---
title: "Trying to change splash screen, what am I doing wrong?"
date: 2010-06-13
forum: Desktop Environments
---

### Post by morbid_bean on 2010-06-13
[http://gnome-look.org/content/show.php?content=73611&forumpage=2&PHPSESSID=6](http://gnome-look.org/content/show.php?content=73611&forumpage=2&PHPSESSID=6)


switched to the directory with the .so file and executed "sudo make install"

```
jimbo@monster:~/Desktop/usplash-macx-both/usplash-macx-ubuntu-morph$ sudo make install
[sudo] password for jimbo: 
cp macx-ubuntu-morph-splash.so /usr/lib/usplash
rm /etc/alternatives/usplash-artwork.so
rm: cannot remove `/etc/alternatives/usplash-artwork.so': No such file or directory
make: *** [install] Error 1

```

same error when i do
make
sudo make install

---

### Post by morbid_bean on 2010-06-13
bump :confused:

---

### Post by morbid_bean on 2010-06-14
So i got thinking... Mabey I should just make a usplash-artwork.so file... so i created a blank file in /etc/alternatives called usplash-artwork.so  and tried to run sudo make install again, this is the new output


```
cp macx-ubuntu-morph-splash.so /usr/lib/usplash
rm /etc/alternatives/usplash-artwork.so
ln -s /usr/lib/usplash/macx-ubuntu-morph-splash.so /etc/alternatives/usplash-artwork.so
dpkg-reconfigure usplash
Package `usplash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: usplash is not installed
make: *** [install] Error 1

```

---

### Post by cbrunhaver on 2010-06-14
Which version of Ubuntu are you using?

Ubuntu 9.10 used uplash but 10.04 uses Plymouth.

-Chris

---

### Post by morbid_bean on 2010-06-15
10.04.....   man that sucks...guess we wait it out, all them themes on gnome-look are useless untill something gets fixed

---

### Post by linux-hack on 2010-06-15
take a look at this : [http://www.tuxien.org/tutos/change-login-boot-screen-ubuntu-lucid/](http://www.tuxien.org/tutos/change-login-boot-screen-ubuntu-lucid/)

---

