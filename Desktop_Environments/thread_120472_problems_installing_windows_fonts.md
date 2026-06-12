---
title: "problems installing windows fonts"
date: 2006-01-21
forum: Desktop Environments
---

### Post by blastradius on 2006-01-21
I've been trying to install the Windows fonts via a tutorial found here:-

[http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/](http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/)

My problem occurs when i try to run the cp line and i get the error that Linux can't find the file.  Turns out that i don't have a 'local.conf' file in the specified location but i do have a fonts.conf.

Should i just replace 'local' with 'fonts' or do i need to do something else.



Thanks for any help.


The tutorial says to do this:-


sudo apt-get install gsfonts-x11
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
sudo cp /etc/fonts/local.conf /etc/fonts/local.conf_backup
sudo gedit /etc/fonts/local.conf



Also, where in the fonts file do i actually paste this:-

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <include ignore_missing="yes">/var/lib/defoma/fontconfig.d/fonts.conf</include>
<!-- Uncomment below to enable bitmapped fonts -->
<!--
  <dir>/usr/X11R6/lib/X11/fonts</dir>
-->
  <match target="font">
    <test qual="all" name="rgba">
      <const>unknown</const>
    </test>
    <edit name="rgba" mode="assign"><const>rgb</const></edit>
  </match>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
P.S. I've just returned from the hospital where my brand new daughter has just been born.  Just thought i'd mention it!

---

