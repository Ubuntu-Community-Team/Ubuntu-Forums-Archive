---
title: "Ubuntu networking problems"
date: 2006-03-09
forum: Desktop Environments
---

### Post by kditty on 2006-03-09
ok, here is the deal... i downloaded ubuntu live cd, ran that to make sure that all my devices were supported, and so far they are. video, audio, keyboard, mouse, everything works just fine, even my wireless, but only on the live cd. well i like the ubuntu distro so much, especially since i can get online with wireless through ubuntu, so i decided to play around with it for a while, get familiar and then format my drive and instal ubuntu breezy 5.10.

well everything works great on my 5.10 install, except my wireless connection. i dont know if i messed some settings up during installation or what. but i am online right now as i post this VIA live cd. im just wondering what could have happened to mess the config up on my breezy full install. 

this is the only distro i have found that will even support my video card, much less my wireless card. FYI: i am using a d-link dwl520+ wireless card. i have to get this fixed because im pretty much a fiend now, and i want to start installing apps and learning, but its just a pain that i cant do this from a live cd.

this is my first post, so if i wasnt descriptive enough, or if there is anything i can ellaborate on to help you guys understand my situation a little better, please let me know, keep in mind that im a newb, i have only been toying with linux for about a month but i absolutely love what i see with ubuntu. 

please dont flame me for a repost, i did do a search before i decided to lower myself to asking for help, but my pride is getting me noplace fast and i hope you guys can help so that i can start running breezy and get rif of this live cd lag.

---

### Post by piglet_74 on 2006-03-09
I just started using ubuntu in the last week or so.  I downloaded breezy and just went after it.  I was amazed but once I gave the installer my ssid for my network it was connected and off to the horse races.  Only problems so far was a tried to set up a static ip using webmin and screwed that up.  I was able to fix it from the network manager System -> administration -> Networking.  I guess some questions would be can you see it there in networking, can you ping anything at all, what are the results of an ifconfig and iwconfig, does the TI 22mb chip show up in a lspci command.  That's what my 520 was listed as anyway.  BTW was it able to DHCP an address during the install?  It shouldn't be to hard to fix.  Good luck and let me know what you find.

---

### Post by kditty on 2006-03-09
from lspci on livecd:

ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:0b.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface


results from ipconfig livecd:

ubuntu@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5035225 (4.8 MiB)  TX bytes:5035225 (4.8 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:AC:42:75
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c8ff:feac:4275/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17916 errors:181 dropped:0 overruns:0 frame:0
          TX packets:14903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10575128 (10.0 MiB)  TX bytes:1708983 (1.6 MiB)
          Interrupt:11 Base address:0x3000

results from iwconfig livecd:

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"thenetwork"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:10:50:EC
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=93/100  Signal level=91/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


now this is all from the live cd, where everything works perfectly. i will try to somehow post the results from the installed version and see what i get. and as far as DHCP an address during install, i dont think that was successful, it said that some network devices may not be working properly or something similar. now i just have to find out a way to get my results from the other OS to here, since i dont have a net connection, possibly making a text file and mounting a drive to read from the live cd, is that possible?

thanks alot for the help, i hope to get this figured out so i can experiance the full benifits of linux.

---

### Post by kditty on 2006-03-09
well i tried to do the lspci, if config an iwconfig on my normal boot system, but i had no way to transfer the results to get them into the forum, short of writing them down which i have no time for right now. i copied and pasted them into the txt editor, then i tried to mount a floppy, then a cdrom drive to transfer the file to one of those to import here. but i had no write access to any of my folders. i don't even know how to log into root, or get admin commands, thats what was stopping me the whole time i believe, and the set up never gave me an admin or root user option :\

the results were totally different than the ones that come from the live cd, i saved it to my desktop on my main boot ubuntu then booted by live cd to come back here and ask if there is a way to mount that desktop from this live cd and gain read access to that file. any suggestions?

i was also thinking about printing out my settings that i get from this livecd, the ones in my second post, and then just manually entering them into my normal boot OS, and see if that makes a difference. 

any help or suggestions are badly needed because im crippled more on my normal boot OS than i am on my live cd, i cant write to any files or anything, i dont know what to do.

---

### Post by piglet_74 on 2006-03-10
The area of the disk that you would have free reign over as your user is your home folder and your desktop.  The paths are /home/"yourusername" and /home/"yourusername"/Desktop with a capital D.  Linux is case sensitive :-) You should be able to save things here and find them with the livecd.  I'll download a livecd and go through the motions of mounting and accessing the file incase you can't get that figured out by then.  One of the first things I did with my install was add the root terminal to my list of applications under applications.  

Ubuntu is set up so that you have to use sudo for everything there are some other things like gksodu I think for gui based apps too.  I've been using sudo gedit a lot.  For example #sudo gedit /etc/apt/sources.list will pop open the sources.list in a gui window with root permissions.  

When you run the live cd, do you make any changes to networks settings at any point or does the card just work?  I'll do some digging around and see if there are any differences between the livecd network config and the install cd too.  As for the installed version do you get a device listed under wlan0 fir iwconfig and ifconfig or is it missing?

---

### Post by piglet_74 on 2006-03-10
[http://www.ubuntuforums.org/showthread.php?t=139688&highlight=livecd+wireless](http://www.ubuntuforums.org/showthread.php?t=139688&highlight=livecd+wireless)

This guy seems to be having a similar problem.  Is there an installer from the live cd?  I used an install cd iso for mine.

---

### Post by piglet_74 on 2006-03-10
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

Here's a step by step troublehsooting guide.  Seems like there are a few others with problems.

---

### Post by kditty on 2006-03-10
[QUOTE=piglet_74]
When you run the live cd, do you make any changes to networks settings at any point or does the card just work?  I'll do some digging around and see if there are any differences between the livecd network config and the install cd too.  As for the installed version do you get a device listed under wlan0 fir iwconfig and ifconfig or is it missing?[/QUOTE]


when i run the live cd, i have to go to system>administration>networking and then select my wireless configuration for wlan0, inside that, there is a field for networkname(EESID) and i click the dropdown button and my network 'thenetwork' is listed there, i select that and then configuration i set to DHCP and hit ok and the wireless card connects. of course i have to do this everytime because with the live cd it doesnt save settings, but thats all i have to do to set it up right. 

and for the installed version, im not sure about the device listed under iwconfig and ifconfig. i have the log saved on my desktop of the installed version i had no way to tranfer it to get the log posted here, unless i can mount my desktop because thats where i saved it. if need be, i can log out and boot the install version and check...

---

### Post by kditty on 2006-03-10
ok what im going to do is go to [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide) on my other computer, then boot the regular instalation after i print out the instructions from that page. it makes it impossible for me to troubleshoot from the install version since im a newb and know hardly any commands. and i dont have a printer on this machine. ill print those directions, test them out and then ill let you know how it works, and if i get it working for anyone else with this problem ill tell how i got it working. thanks piglet for the help!

---

### Post by piglet_74 on 2006-03-10
Without having a livecd right now I'll try to guess at what I would do to mount the drive.  I'll try it tonight but anyway:

open a terminal and use sudo if anything fails the first time

#cat /proc/partitions
!This should show you all the drive partitions on the system mounted or not.
BTW #cat /etc/fstab will show what's mounted already

#sudo mkdir /mnt/localdisk
!This will create a place to mount the disk to once you find it

#sudo mount /dev/hda1 /mnt/localdisk
!This will mount partition 1 of the primary ide 0 hard disk to the /mnt/localdisk directory. If your root partition is not the first then it may be hda2 or 3

#cd /mnt/localdisk/home/%yourusername%/Desktop
!This should change directory to the dekstop of the installed version

#ls will show what's there.  With nautilus you can just browse the filesystem/mnt/localdisk/home/%yourusername%/Desktop directory.

BTW %yourusername% means type your account name

Hope this helps.

---

### Post by piglet_74 on 2006-03-10
OK Gui way (still downloading livecd) Click System -> Administration -> Disks
Select the hard disk from the storage list.  On the right choose the partitions tab and select the partition from the partition list.  To the right of the access path click choose and browse to the mnt directory.  Click create folder and create your mount point.  Now to the right of status click enable and your good.  Now in PLaces -> COmputer You'll find your drive under /mnt/%whatever%

---

### Post by kditty on 2006-03-10
piglet, thanks alot for the help, the mount commands worked... i saved the results from iwconfig, ifconfig and lspci to my desktop, the mount commands worked thanks alot. here are the results if they help any, there are a few differences on this config than on the live cd, ill color them so you dont have to compare all that much, unless you notice something more important i missed.

kditty@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21726 (21.2 KiB)  TX bytes:21726 (21.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:C8:AC:42:75
          [COLOR="Red"]inet6 addr: fe80::280:c8ff:feac:4275/64 Scope:Link [/COLOR]
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x3000

kditty@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"thenetwork"  Nickname:"acx100 v0.2.0pre8"
          Mode:[COLOR="Red"]Auto[/COLOR]  Frequency:[COLOR="Red"]2.412[/COLOR] GHz  Access Point: [COLOR="Red"]00:00:00:00:00:00[/COLOR]
          Bit Rate=22 Mb/s   Tx-Power=18 dBm   Sensitivity=187/255
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kditty@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA AC'97 Audio (rev 02)
0000:01:0b.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

---

### Post by kditty on 2006-03-10
piglet, do you have AIM or MSN? if you do and you can contact me, my sn on AIM is indica buds and on msn its mcren at hotmail.com

---

### Post by kditty on 2006-03-10
sorry guys, seems like i posted this in the wrong forum, feel free to move it to networking, mods.

---

### Post by piglet_74 on 2006-03-10
My last reply got lost I guess so lets try again.  It seems like your wireless is on the wrong channel (the difference in frequency)  Here were some commands to help get things sorted from another post.  Scip the key if you're not using one.

sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 key 12f45a78cc98... (your hex encryption key if needed)
sudo iwconfig wlan0 channel 11 (or whatever channel used by your router or IP provider if your card is able to negociate a channel with the router or provider set this to auto instead of 11)
sudo iwconfig wlan0 essid yourwifilanname ("sevcik" in my home, write it WITHOUT quotes)

now do
sudo iwlist scanning

I would try this once with the live to preactice it.  See if you can change a setting to break it, then fix it again.  I'll look into getting an MSN account in the mean time.

---

### Post by kditty on 2006-03-10
thanks, im gonna try this right now.

---

### Post by kditty on 2006-03-10
piglet, this worked. i cant think you enough... its amazing how something this simple can cause such a problem, it made me rethink my decision on installing ubuntu, im glad there are forums like this and people like you that take time to help newbs out or i would be running from a live cd for the rest of my life :D thanks alot.

---

### Post by piglet_74 on 2006-03-10
No problem, I'm glad I could help.  The big thing now is will it stay after a reboot.  If you don't mind using a static address on the system you can put your settings in the /etc/network/interfaces file and it will come up on boot.  There are also a few wireless utilities you can download that have guis for finding wireless networks.  They may help too.

I like ubuntu too, I've been using it for about 2 weeks now and I love apt-get.  I have one machine running as a desktop and my other machine is a server.  I'm using apache2, mysql, php5, denyhosts, openssh, vncserver, qdig, mondorescue and no-ip.  It took all of about 2 hours to get it up and running.  Anyway, now you can listen to cds with your cd drive.  :-)

---

### Post by kditty on 2006-03-12
ok, i rebooted, and the network wasnt picked up automatically on boot. it wasnt any trouble at all to change it to get the network back but id like it to load on boot if possible. what settings would i put inside of my /network/interfaces file piglet?

---

### Post by piglet_74 on 2006-03-12
The following is my static settings.  Here's a webpage that had some wireless settings described on it like channel [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/DISTRIBUTIONS.txt](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/DISTRIBUTIONS.txt)

wireless-channel #
Should work.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

# The primary network interface
iface wlan0 inet static
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid homer
	address 192.168.1.99
	netmask 255.255.255.0
	gateway 192.168.1.1

auto wlan0

---

