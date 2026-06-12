---
title: "Wired ethernet not detected"
date: 2010-09-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lalit_IIT on 2010-09-17
I am having a Dell Inspiron

Initially wired ethernet was not detected.

So I searched the forum and the solution suggested worked for me .

 This was the solution 
To download, compile and install the driver, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6)  and download the file named "compat-wireless-2.6.tar.bz2" (you can't  download it in the terminal because of anti-hotlinking).  Save it to  your desktop. Then run these commands:
     Code:
     sudo apt-get update sudo apt-get install build-essential cd ~/Desktop tar -xjvf compat-wireless-2.6.tar.bz2 cd compat-wireless* scripts/driver-select atl1c make sudo make install 
Then reboot.  Hopefully your ethernet will work automatically after reboot; if not, run:
     Code:

Yesterday I checked that no sound from headphone was coming so I installed the package

linux-backports-modules-alsa-2.6.32-23-generic

Now the headphone works fine but the ethernet is not being detected.

I tried the previous solution but its not working.

Any suggestions

---

