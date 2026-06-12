---
title: "installing rpm and tar packages"
date: 2005-12-26
forum: Desktop Environments
---

### Post by zulughana on 2005-12-26
HI ,
can some please point me in the right direction as to installing rpm and tar software ?

thanks

---

### Post by bikeboy on 2005-12-26
I found this link to be very useful. It was provided in another thread on ubuntuforums.

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by kingsidy on 2005-12-26
to install rpm packages you use the alien command. Open the terminal and cd into the directory of interest and type in "alien *packagename.rpm*", then type "dpkg *packagename.deb*". If you do  not have the alien thing install, just get it through synaptic. As far as the tar packages are concerned, you have to first untar i think the command is like tar xvzf *packagename*, then cd into the directory, usually there read me, i always read it to make how to install the package, otherwise when in the untared directory type at the terminal: "./configure", then "make" and "make install". sometimes all you have to type in is ./install or something like that. sometimes it depends on how the program is packaged. i would say read the readme.

---

### Post by f1dave on 2005-12-26
You may also find that when you run dpkg you have insufficient priveliges to install, so you may need to run sudo dpkg -i packagename

---

