---
title: "First attempt at getting Ubuntu..haveing problems.."
date: 2005-11-01
forum: Desktop Environments
---

### Post by gamer345 on 2005-11-01
Hi, 
Im not sure if this is the right place to post, this is my first post for this forum.  I am trying to install a free OS onto a laptop for someone.  Intel Celeron, 120mb memory, and @12 gb on the harddrive.  I tried several times to download Ubuntu and other Linux OS on Sonic burner and than tried to boot these burned cdrw's on the laptop, the boot sequence is set to boot from cdrom first however I am still haveing problems of it booting up and getting the OS onto the laptop.. I think that the explanations of installing these various OS's are very complex and at times incomplete, there is yet a simple step program of showing someone how to get this running.  Can someone lay it out for me from the begining so that I can get the OS running... Thanks for any attempt to handle this request..

---

### Post by felix_stegerman on 2005-11-01
Hi,

[QUOTE=gamer345]I think that the explanations of installing these various OS's are very complex and at times incomplete, there is yet a simple step program of showing someone how to get this running.  Can someone lay it out for me from the begining so that I can get the OS running...[/QUOTE]

You could take a look at the Ubuntu Installation Guide:
[http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/](http://archive.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/)

Just remember that you have to be willing to learn how to do certain things
"the GNU/Linux way". Linux is, after all, not Windows.
([http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm))


Felix

---

### Post by mips on 2005-11-01
Does the CD actualy boot ?
Does the Installer start ?

---

### Post by gamer345 on 2005-11-01
Thanks for the response, but I thought this was a Linux forum... There has got to be someone who can make this simple instead of giveing me a 500 page lay out.  There also has to be someone on here who has actually downloaded, burned to a cdrw and installed onto another computer here.. That is all I would like to know direction for a official downlaod of the OS, and burning metod as I described Im useing Sonic(cant get the bootable disk thing down;becuase the download of Linux isnt shown:dont know if that is really a problem), and last to boot from cd rom and presto.. thanks


I burned one cd already,, but would rather do the whole process over with the assistance of this forum..I am willing to start from point A.  To answer the second response to this thread,, I put in the cd hear it spin but nothing comes up as far as the installer is concerned..

---

### Post by Teroedni on 2005-11-01
Point a would be to go tu Ubuntu.com
Download brezzy 5.10 and save it on the desktop or an other folder of your choice.
Then use an good burner software
For example Nero
Chosse burn from image and browse to where you put the ubuntufile
Then make sure to burn at low speed .That will make the chances higher of a succesfull burning.

---

### Post by MacV on 2005-11-01
I was just going to suggest to make sure your not just burning the isos as data disks. Like Teroedni said, use a good burning program, although yours should be good enough(one would think), and make sure your tell it to burn the disk as an iso, NOT as data or a straight up copy. Also, don't use CDRW disks when making isos, they work, but it;s better to use regular CDRs.

---

### Post by Teroedni on 2005-11-01
and here you got the wiki for installing

It is maximum 2 pages long so you should be able to read it without being tired or getting headaches

[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

---

### Post by Teroedni on 2005-11-01
And if you cant get the bios to boot your cd make an floppy which load the cd :)


here is the link:)
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by felix_stegerman on 2005-11-01
Hi,

Sorry about the "headache manual reference" ;-)
I'm still not familiar with all the "simple docs".
I learned everything the hard way. And I did read most of the "big manuals".
I guess there's something here for me to learn as well ;-)

You may want to look at [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
(if you're not sure how to properly burn the Install CD)


Felix

---

### Post by gamer345 on 2005-11-01
Thanks for all the good and quick responses.  Ok this is what ive managed to do.  I downloaded Deepburner and that did the trick, I was burning a data file with sonic and with *Deepburner* I was able to do the ISO thing with it.  Now I booted up the cd, but everything was going cool until this popped up: "Network autoconfiguration failed"  Your network is probably not useing the DHCP protocol.  Alternatively, the DHCP server may be slow or some network hardware is not working properly.  hmmm

---

### Post by gamer345 on 2005-11-01
Never mind,, im on a home network I bypassed that part... made the auto partition.. and now it is installing the base system.. thanks so far..

---

### Post by mips on 2005-11-01
Does the PC you are installing to have an Ethernet LAN card ?
Is the LAN card plugged into anything ?

---

### Post by ajgreeny on 2005-11-01
I've installed ubuntu 5.04 twice on my current machine, built to my spec (asus board, sempron 2400+, 512Mb ram), and also on other machines attached to my wired LAN.  Each time I have done the install I have had the exact same message as gamer345 about the DHCP not being detected.  I have continued and made a second try at detection when given this option and the LAN is always found very quickly at this second try.

gamer345 should try this if the LAN detection is still a problem.  You never know, it might be the same slow pick up of DHCP.

Stick with it gamer345, Ubuntu (even the now older hoary version) is a total blast and better than any other of the several distro's I've looked at, like Mandriva, Suse, Fedora, RedHat, and even some of the small ones like Feather, DSL, and Puppy.  Long live Ubuntu!

---

### Post by sarah_b on 2005-11-01
[QUOTE=gamer345]"Network autoconfiguration failed"[/QUOTE]

Ok, go to Systems > Administration > Networking and choose your connection, then activate.

This worked for me, hope it does for you also so you don't have to do it manually

sarah

---

### Post by gamer345 on 2005-11-02
Whats up now you guys are makeing me excited about Ubuntu.. I was going to install this for someone and than probably get windows 95 for it... Im installing an OS for someone on their laptop.. So no its not going to be on a LAN..I bypassed that option.. however I ran into something else, I think all the information wasnt transferred over from the CD I made so Im makeing another one right now but letting it burn over at a slower rate 16X....One more thing if I get this to work will it be easy for someone to have Access to their AOL account through Ubuntu with minimum maintanence.. take care

---

### Post by gamer345 on 2005-11-02
Getting This:
1st.
base system installation error
The debootstrap program exited with an error(return value1)
check/target/var/log/bootstrap.log for the details.
pressed continue
Than tried to reinstall the base system...

2nd.
Cpying packages failed.
Copying packages to the hard disk failed.  You may have run out of disk space in the target /var filesystem, or your cd drive may be having problems reading packages from the cd.  Cleaning the cd drive or burning the cd at a lower speed may help..
check/var/log/syslog or see vitrtual console 4 for details..

When I set the install I chose 
Erase entire disk: ide1 master hda 20gb 

I want the whole harddrive to be clean and place Ubuntu on it..

---

### Post by mips on 2005-11-02
Sound like the CD or drive is dodgy.

---

### Post by ajgreeny on 2005-11-03
[QUOTE=mips]Sound like the CD or drive is dodgy.[/QUOTE]
Or you are still burning the iso image to CD at too high a speed.  I always do it at 4X and never have a problem (This assumes the iso you are trying to burn is OK in the first place.  Did you check the md5sum?

---

