---
title: "Intel 82852 resolution"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by guruvenk on 2007-05-25
hi all
this is how I resolved my screen resolution problem from 800x600 to 1024x768 in Intel 82852/82855 GDM card laptop.
1.after installation i went to synaptic package manager, search type i915 and it will show two files,then remove i810 resolution
2.installed i915 resolution through console by *sudo apt-get install 915resolution*
3.restart the computer in rescue mode and enter *sudo dpkg-reconfigure xserver-xorg*
4.choose vesa as grahic card and restart the computer.
5.then go back to synaptic and type xorg,it will give list of available installation possible,then choose xorg video files and one with xorg-intel files and install them.
6.restart the comp in normal mode,enter console and type *sudo dpkg-reconfigure xserver-xorg*
7.there choose intal as graphics card and choose only 1024x768 as the available resolution,choose vertical and horizantal frequency upto 75
8.restart the comp and it will give that screen resolution

cheers
venkat

---

