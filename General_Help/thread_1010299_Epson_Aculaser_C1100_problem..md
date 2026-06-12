---
title: "Epson Aculaser C1100 problem."
date: 2008-12-13
forum: General Help
---

### Post by Gunmanic on 2008-12-13
Hi people.

I have a problem with a printer that is connected to my dad's computer.
I got the ppd file for Epson AL-C1100 from the Avasys website and set it up through the printer setup GUI.

I didn't encounter any problems, the printer is detected and the driver went install went smoothly. But for some reason the printer doesn't appear to receive the data from my comp.  So I can't print.

Now here's what I've tried:

Instead of simply using the ppd file from the Epson-ALC1100-filter-1.2 pack, I installed it from source using a guide i found with google: [http://robert.cheramy.net/my.wiki/Divers/EpsonAcuLaserC1100](http://robert.cheramy.net/my.wiki/Divers/EpsonAcuLaserC1100) 

I restarted the computer.

I checked my firewall settings to see if it was blocking the connection, it appears that it doesn't.

I tried messing around with the settings in the printer setup thing.

I've tried almost everything I can think of.

My setup:

Running ubuntu 8.04 on an Acer Travelmate 290

1500mhz Centrino Processor
768mb DDR 333 Memory
Intel 855GM graphics card
connected to the internet with wireless Intel 2200BG card

My dad's comp:

Windows XP SP3
Intel Core 2 duo
1GB DDR2 Mem
Directly connected to the router.

I can print from my desktop which is running windows xp with no problems. 

Thanks in advance!

---

### Post by Marc Higgins on 2009-01-03
Firstly this might not work for everyone & there might be a better way (if you do know of one please share your knowledge & let me know).

It looks like something that ships with Ubuntu doesn't work with the Epson C1100r & the source file Epson-ALC1100-filter-1.2.tar.gz from epsons site [www.avasts.jp]("www.avasts.jp") doesn't work either (well I can't get it to work). However the rpm's available on the same site DO work if they are converted to deb's & installed.

#1 Install the dependencies (this is REALLY  important, if you don't do 
this it won't work)

```
sudo aptitude install gcc-3.3-base libstdc++5
```

or you could just use synaptic System > Administration > Synaptic & just search for & install gcc-3.3-base & libstdc++5

From here you can decide to;

[B]OPTION A
[B]
the simplest way to get your Epson C1100 printing on ubuntu is to just install the deb files direct from our site below[/B]
 
[http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb]("http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb")

[http://www.hunny.be/epson-alc1100-filter-cups_1.2-1_i386.deb]("http://www.hunny.be/epson-alc1100-filter-cups_1.2-1_i386.deb")


Just double click on EACH of these links, that will invoke the Gdebi package installer & install the files.

Then install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be printing happily in seconds :)

OR

OPTION B

you can make your own install files using Alien, the same way we did

Install Alien

```
sudo aptitude install alien

```
or just use synaptic System > Administration > Synaptic & search for & install alien

Then go to [URL="http://www.avasys.jp/english/linux_e/dl_laser.html"]http://www.avasys.jp/english/linux_e/dl_laser.html
[/URL]
download these 2 files

For Turbo/RedHat/Fedora (Epson-ALC1100-filter-1.2-0.i386.rpm)
For Turbo/RedHat/Fedora (Epson-ALC1100-filter-cups-1.2-0.i386.rpm)

then from a terminal run

```
sudo alien Epson-ALC1100-filter-1.2-0.i386.rpm

```

```
sudo alien Epson-ALC1100-filter-cups-1.2-0.i386.rpm

```
that will create 2 files

epson-alc1100-filter_1.2-1_i386.deb
epson-alc1100-filter-cups_1.2-1_i386.deb

you can then use dpkg -i

```
dpkg -i epson-alc1100-filter_1.2-1_i386.deb
```

```
dpkg -i epson-alc1100-filter-cups_1.2-1_i386.deb
```

or just double click the deb files with your mouse that will invoke the Gdebi package installer to install the files.

Then just install the printer normally using System > Administration > Printers (AKA system-config-printer) & hopefully you will be now be printing happily :)

---

### Post by Foottech on 2010-01-23
This worked a dream for me on a new 9.10 Koala install with my AcuLaser 1100 networked.


[LIST]
[*]Download and install  libstdc++5
[/LIST]
      [http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)

[LIST]
[*][COLOR=black]Install packages below[/COLOR]
 
[http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb](http://www.hunny.be/epson-alc1100-filter_1.2-1_i386.deb)

[http://www.hunny.be/epson-alc1100-fi...1.2-1_i386.deb]("http://www.hunny.be/epson-alc1100-filter-cups_1.2-1_i386.deb")
[/LIST]

[LIST]
[*]In ubuntu printers section search for network printer and drivers will appear.
[*]Select driver.
[*]Send test page to confirm you're up and running.!!!
[/LIST]
Thanks to all above especially Mark Higgins......top man!

---

### Post by lostinstarlight on 2010-02-28
I'm trying to get an ALC1100 installed on a 586 machine. Would you happen to know whether I should use the Debian libstdc++5 i386 package or is there a 586 package that I should be looking out for?

lis

It worked with the 386 package. Thanks guys.

lis

---

### Post by ceminino on 2011-03-21
I'm trying to install the C1600 model, any idea about this one? i can't find any driver for this one :(

---

### Post by nitocris on 2012-05-17
Installation on 32-bits systems : 
```

mkdir ~/temp 
cd ~/temp  

wget https://sites.google.com/a/hunny.be/www/epson-alc1100-filter-cups_1.2-1_i386.deb
wget https://sites.google.com/a/hunny.be/www/epson-alc1100-filter_1.2-1_i386.deb
wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-24ubuntu1_i386.deb

sudo dpkg -i libstdc++5_3.3.6-24ubuntu1_i386.deb
sudo dpkg -i epson-alc1100-filter-cups_1.2-1_i386.deb
sudo dpkg -i epson-alc1100-filter_1.2-1_i386.deb

cd -

```Installation on 64-bits system

```

sudo apt-get install build-essential
mkdir ~/temp 
cd ~/temp 
wget https://sites.google.com/a/hunny.be/www/epson-alc1100-filter-cups_1.2-1_i386.deb
wget https://sites.google.com/a/hunny.be/www/epson-alc1100-filter_1.2-1_i386.deb
wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-24ubuntu1_i386.deb
sudo dpkg -x libstdc++5_3.3.6-24ubuntu1_i386.deb . 
sudo cp -a usr/lib/i386-linux-gnu/libstdc++.so.5* /usr/lib32/
sudo dpkg --force-architecture --force-depends -i libstdc++5_3.3.6-24ubuntu1_i386.deb
sudo dpkg --force-architecture --force-depends -i epson-alc1100-filter-cups_1.2-1_i386.deb
sudo dpkg --force-architecture --force-depends -i epson-alc1100-filter_1.2-1_i386.deb
cd -

```

---

### Post by nitocris on 2012-05-17
installation on Precise 12.04 64-bits 
```

sudo apt-get install build-essential gcc-4.6-base libc6 libgcc1
mkdir ~/temp
cd ~/temp
wget https://sites.google.com/a/hunny.be/www/epson-alc1100-filter-cups_1.2-1_i386.deb
wget https://sites.google.com/a/hunny.be/www/epson-alc1100-filter_1.2-1_i386.deb
wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-24ubuntu1_i386.deb
sudo dpkg -x libstdc++5_3.3.6-24ubuntu1_i386.deb .
sudo cp -a usr/lib/i386-linux-gnu/libstdc++.so.5* /usr/lib32/
sudo dpkg --force-architecture --force-depends -i libstdc++5_3.3.6-24ubuntu1_i386.deb
sudo dpkg --force-architecture --force-depends -i epson-alc1100-filter-cups_1.2-1_i386.deb
sudo dpkg --force-architecture --force-depends -i epson-alc1100-filter_1.2-1_i386.deb
cd -

```

---

### Post by oldos2er on 2012-05-17
Old thread closed. Please don't bump old threads.

---

