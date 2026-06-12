---
title: "Alien iscan problem"
date: 2009-02-08
forum: General Help
---

### Post by Mike-97470 on 2009-02-08
Having just gone through probably my worst Ubuntu gyration ever that's resulted in a fresh install of 8.10 and a quite crappy "simple restore", this is hopefully the last of numerous problems that I've had to troubleshoot and fix, thanks to the info in this great forum.

Anyways, I'm trying to get my Epson Perfection 4490 scanner working again--

I'm trying to create an installable .deb version of the .rpm iscan and iscan plugin for the 4490 that Epson provides at--

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)

When I run Alien this happens:
```

mike@mike-desktop:~$ cd /home/mike/Desktop/Epson
mike@mike-desktop:~/Desktop/Epson$ sudo alien iscan-2.10.0-1.c2.i386.rpm[sudo] password for mike: 
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
make: dh_testdir: Command not found
make: *** [build] Error 127
find: `iscan-2.10.0': No such file or directory
mike@mike-desktop:~/Desktop/Epson$ sudo alien iscan-plugin-gt-x750-1.0.0-1.c2.i386.rpm
[sudo] password for mike: 
Warning: Skipping conversion of scripts in package iscan-plugin-gt-x750: postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
make: dh_testdir: Command not found
make: *** [build] Error 127
find: `iscan-plugin-gt-x750-1.0.0': No such file or directory
mike@mike-desktop:~/Desktop/Epson$ 
```Alien does generate root owned folders with debian/etc/usr subs, but it apparently hasn't shuffled stuff around quite right so that it can be apt-get installed as a .deb package.

As always thanks for help!
Mike

---

### Post by hansdown on 2009-02-08
Hi Mike-97470.

Hopefully this will help.

[http://joshualowry.vox.com/library/post/epson-scanner-setup-ubuntu-710.html](http://joshualowry.vox.com/library/post/epson-scanner-setup-ubuntu-710.html)

If not, google 

```
Epson Perfection 4490 scanner in ubuntu 7.10
```

---

### Post by rbmorse on 2009-02-08
The downloaded .rpm package from Avasys converts just fine here, so I'd recommend that you check your setup. Looks like make is missing something. 

There are a number of packages that 8.10 needs to make the Epson 4490 work as it should:  

build-essential
libstdc++5  (libstd++6 may work...both in repository)
sane-utils
libsane-extras

When you get the Avasys .rpm packages converted, the plugin will install with gdebi, but the iscan package will report a conflict with the libsane-extras package.  The conflict is real but not particularly important, install the iscan package with:

sudo dpkg --force-overwrite -i iscan-2,tab><enter>

You might also have to edit 

/etc/udev/rules.d/50-libsane-extras-rules

and change the permissions in the line that configured the 4490 (product id=119) from 0644 to 0666.

I don't know if it's necessary, but I also add my username to the "scanners" group.  You'll have to log out of the session and log back in to make that change effective.

---

### Post by Mike-97470 on 2009-02-08
Thanks guys for the quick response and info/advice...

What had me stuck was just the .rpm to .deb conversion.  Reinstalling Alien didn't fix anything. So I used a flash drive moved the .rpm's to a laptop where I did the conversion.  I noticed that when I installed Alien, multiple dependencies were also installed, reinstalling just installs Alien.

That fixed the conversion problem.  Curious, isn't it, that my desktop just a had a reformat and fresh install on 8.10 a few days ago.  Fresh, that is, except that I used Simple Backup/Restore:::next time I will only restore /home and not /etc /var or /usr, I think those were the other directories.........and I've been fixing numerous problems since.

So now getting this Epson 4490 working is the last problem, so far I think I've taught Xsane that my TV card, a Hauppauge PV-150 is not a scanner.  So now I can just follow the simple instructions.... :)

---

### Post by locutus42 on 2009-02-11
I just added the 4490 to my 8.10 system so for anyone else who ventures down this path and finds this thread, here's my script of things I did to get it working. It's commented so should be self explanatory and it was built from scraping my bash history.

```

echo "Add:"
echo "none /proc/bus/usb usbfs defaults  0  0  # needed for usb scanner"
echo "to /etc/fstab and reboot"
vi /etc/fstab
sudo shutdown -r now

echo "Install sane and xsane stuff"
sudo apt-get install sane sane-utils libsane
sudo apt-get install xsane-common libsane-extras

echo "Get your Epson Scanner drivers from Espon/AvaSys"
firefox http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do

echo "Get tools needed to convert RPM from Epson and install libsane-extras(?)"
sudo apt-get install alien

echo "Convert RPM to DEB, (these are for an Epson 4490 PHOTO scanner"
sudo alien ~/Desktop/iscan-2.10.0-1.c2.i386.rpm 
sudo alien ~/Desktop/iscan-plugin-gt-x750-1.0.0-1.c2.i386.rpm 

echo "Make sure we don't have old iscan stuff installed"
sudo dpkg --remove iscan-plugin-gt-x750 iscan

echo "Install the new drivers/app and force any issues"
sudo dpkg  --force-conflicts --force-overwrite -i iscan-plugin-gt-x750_1.0.0-2_i386.deb 
sudo dpkg  --force-conflicts --force-overwrite -i iscan_2.10.0-2_i386.deb 

echo "Look for your scanner and note the Vendor and Product IDs"
echo "also look for and note the libusb address(ex. usb:003:009 )"
sane-find-scanner 
scanimage -L

echo "Comment out everything but "usb 0x04b8 0x0119" in epkowa.conf file"
sudo vi /etc/sane.d/epkowa.conf

echo "Add 'epkowa' after 'epson' listed in dll.conf
sudo vi /etc/sane.d/epkowa.conf

echo "Use libusb address from sane-find-scanner, set privs to rwrwrw on device"
ll /proc/bus/usb/003/009 
sudo chmod 666 /proc/bus/usb/003/009 

echo "Run the scanner utilities and test the preview"
echo "Be sure to notice the light blinking on the front of the scanner as it"
echo "warms up the first time, then you should be scanning"
iscan 
xsane 

```

NOTE: make sure to get the 4490 and not the 4990. I spend well over an hour trying to get this working but had the wrong iscan package. Got the correct ones and it worked like it was supposed to.

---

