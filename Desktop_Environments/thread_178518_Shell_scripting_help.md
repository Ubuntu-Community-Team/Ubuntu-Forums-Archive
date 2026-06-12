---
title: "Shell scripting help"
date: 2006-05-17
forum: Desktop Environments
---

### Post by wetumka_ok on 2006-05-17
I used my command history to put together this script, I haven't executed it yet I thought I might use this if I ever had to reinstall my system, my question is will this execute everything at once or line by line completing the previous command first? if it executes everything i need some help. I need it to complete the previous command before the next

thanks

# setting DVD region
sudo apt-get install regionset
regionset
# enable DVD reading
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo apt-get install dpkg-dev fakeroot debhelper build-essential
# setting dma enable
sudo hdparm /dev/cdrom
# editing cd configuration
sudo gedit /etc/hdparm.conf
sudo hdparm -d1 /dev/cdrom
# enabling mp3 playing
sudo apt-get install gstreamer0.8-plugins-multiverse
sudo apt-get install gstreamer0.8-ffmpeg-plugins-multiverse
sudo apt-get install gstreamer0.8-ffmpeg
sudo aptitude install gstreamer0.8-mad
sudo aptitude install gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg  106  wget [http://beerorkid/automatix/automatix_5.8-4_i386.deb](http://beerorkid/automatix/automatix_5.8-4_i386.deb)
wget [http://beerorkid.com/automatix/automatix_5.8-4_i386.deb](http://beerorkid.com/automatix/automatix_5.8-4_i386.deb)
sudo dpkg -i automatix_5.8-4_i386.deb
# installing rar 
sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar
# updating system
sudo apt-get update



 sorry thanks

---

### Post by tribaal on 2006-05-18
Hum well bash executes lines one after the other, waiting for the first one to end before running the second.

If you want to get around this you can always append "&" at the end of the line, and it'll tell bash to run the line in background (as another process), and return the prompt.

You should probably just test this out yourself though, it's still the best way to learn :)

- trib'

---

