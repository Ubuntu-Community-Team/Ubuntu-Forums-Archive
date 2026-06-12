---
title: "how to install virtualbox closed version on ubunt? and unistall ose version"
date: 2009-02-15
forum: General Help
---

### Post by shateredsoul on 2009-02-15
Hi yes yes I'm a newb but I'm getting better and might be able to help soon.

So it turns out I installed an ose version of virtual box, i must have found a post that explained how to install it through terminal commands without realizing the ose version didn't allow the use of usb drives.

So my question is.. does anyone know how I install using the terminal?

How do I completely uninstall the ose version? should i delete the virtualbox folder (the virtual drive is there too)?

I went to the website and found the download link which is
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

Is this the closed version? How do I know if i need the i386 or amd64 version?

I tried looking, but i guess it's considered common knowledge.. I would appreciate any help.  Any.. I need xp to look over my student's papers in word (i used track changes). 

I don't mind doing the work to find my own answer, so links that might help me get a start would also be helpful.

---

### Post by uidb4056 on 2009-02-15
To uninstall ose version go to menu System-Administration-Synaptic Package Manager and search for 'virtualbox' you will see virtualbox-ose packages that are installed, right click on them an choose completely remove then click on the apply button.

Once are uninstalled to install the non opensource Virtualbox follow the instructions at bottom of page to download you have: (I've green marked the relevant ones)

> Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list:

[COLOR=SeaGreen]Open Terminal an copy the appropriate line according your distribution at the end of the file inserting first a new line.

sudo gedit /etc/sources.list
[/COLOR]
 deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) dapper non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) etch non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) sarge non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xandros4.0-xn non-free

The Sun public key for apt-secure can be downloaded [here]("http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc"). You can add this key with
 sudo apt-key add sun_vbox.asc

or combine downloading and registering: (copy next line and paste it to terminal)

 [COLOR=SeaGreen]wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -
[/COLOR]
The key fingerprint is  AF45 1228 01DA D613 29EF  9570 DCF9 F87B 6DFB CBAE
Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

To install VirtualBox, do

 [COLOR=SeaGreen]apt-get install virtualbox-2.1
[/COLOR]
Replace virtualbox-2.1 by virtualbox to install VirtualBox 1.6.6, or replace it by virtualbox-2.0 to install VirtualBox 2.0.6.

**Note:** Ubuntu users might want to install the **dkms** package (not available on Debian) to ensure that the VirtualBox host kernel modules (*vboxdrv* and *vboxnetflt*) are properly updated if the linux kernel version changes during the next apt-get upgrade. 

---

