---
title: "Xerox Phaser 3116 Installation problem"
date: 2005-12-07
forum: General Help
---

### Post by the_orphaned on 2005-12-07
Hi,

I just got myself a laser printer, Xerox Phaser 3116, but the problem is the installation doesn't work.

I went to the wiki page and followed the steps. I copied the CD contents to "*/tmp/printer*". Then the instruction goes like type "sudo ./setup.sh", I do so but I get this message in the terminal: "*/home/orphaned/.setup9683: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory*". 

How do I go about this now? I need help... Please...

---

### Post by the_orphaned on 2005-12-07
Solved. Synaptic Package Manager did not include all dependencies needed to run the app. From terminal, just used *sudo apt-get install gtk-1.2.**.

After that, just followed the Wiki instructions again.

---

### Post by arnab.bhaumik on 2007-07-15
hi all,

    after lot of trying to install phaser 3116 on my ubuntu 7.04 i am able to install the printer and get it worked.

    in ubuntu 7.04 go to system => administration => printing. then right click on the new printer icon and then add printer.....................


   well i will not go in the details of the installation process. the main trick is that the driver needed for the printer is Samsung- ML-1520. its working perfectly via usb.


   this is very important for the people of india because now it is the low priced laser printer in the country.......................


arnab/vu2bpw

---

