---
title: "HELP!? Broken xorg, now I can't do anything"
date: 2009-04-09
forum: General Help
---

### Post by Psychopump on 2009-04-09
Hi all,

I was trying to make a nice config for conky, rebooted and was suddenly confronted with a broken xorg!

I now have no GUI, can only startup in recovery mode and also have no wifi connectivity. Trying to fix the xorg does nothing and I am starting to panic...

PLEASE can anyone help?

I will be ahppy to answer any questions needed to resolve this issue!

---

### Post by Nano_ext3 on 2009-04-09
Conky should have nothing to do with your xorg, conky's file should be "~/.conkyrc" not anything in xorg.  Do NOT modify xorg for conky in the future if you did, follow guides on the internet.

Run "sudo dpkg-reconfigure xserver-xorg" in Terminal to reconfigure Xorg

Another way is to load up the Ubuntu LIVE CD and copy that xorg to a USB or file on your Linux partition.  Boot into recovery partition or another kernel version on bootup and copy it over to you actual xorg from you Ubuntu Partition.  When you start up your computer insert the USB right when grub's menu shows up so it doesnt try to boot from it before hand, then when you are in recovery mode the usb should be under /media or maybe in /mnt.  Use "sudo fdisk -l" to find the /dev location of your drive then use "mount /dev/sbd1 /mnt" if you need to, where sbd1 is the /dev location of the USB drive.

Cheers,

_Nano

---

### Post by Psychopump on 2009-04-09
Hi Nano,

Thanks for your reply!
Unfortunately, my laptop has no cd-rom drive and my USB ubuntu stick is missing...
Is there any way to connect to internet with ethernet from the comand line so I can get the file?

BTW: "sudo dpkg-reconfigure xserver-xorg" did not work.

---

### Post by Nano_ext3 on 2009-04-09
On arch linux when I set it up, I always perform these steps in the CLI or terminal to get an ethernet address:

[LIST=1]
[*]ifconfig
[*]note what interface is ethernet and which is wireless
[*]you can confirm what interface is wiress with "iwconfig"
[*]use the command "dhcpcd eth0" to grab a dhcp address for a brief time, where eth0 is your ethernet interface
[*] you can also use the command "ifconfig eth0 192.168.1.xx" to set a static address to your interface.  You many need to specify the netmask like so, "ifconfig eth0 192.168.1.100 netmask 255.255.255.0"
[/LIST]

Hope this gets you an IP, as for the USB stick, go to the library, or someplace run the LIVE cd and make a Bootable usb(see my blog: [http://thelinuxcauldron.wordpress.com/category/usb/](http://thelinuxcauldron.wordpress.com/category/usb/)).

If you cant, Copy the file via some else's USB drive, I'm sure you can find a way :)

Cheers,

_Nano

---

### Post by stalkingwolf on 2009-04-09
what version are you running?  try sudo displayconfig-gtk

---

### Post by Psychopump on 2009-04-09
Apparently I do not have dhcpcd installed...
I live MILES from a library and have no USB stick at hand.

I do however have a USB pocket drive and a netbook running an earlier version of ubuntu....could this help?

Please remember when replying that I am a n00b and really need step-by step instructions!

Thanks, Nano

---

### Post by Nano_ext3 on 2009-04-09
Use your other laptop to make a new USB drive.  See my blog:

[http://thelinuxcauldron.wordpress.com/category/usb/](http://thelinuxcauldron.wordpress.com/category/usb/)

You can download the "usb startup disc creator" if you have 8.04 on that other machine.  This is already installed in 8.10 and above.  This will make a live CD onto your USB.

If you have 8.10 or later, it is in "System > Preferences (maybe Administration) > Usb Startup disc creator>"  Its fairly simple from there.  

Picture:  [http://farm4.static.flickr.com/3214/2946247371_ee0f82be7e_o.png](http://farm4.static.flickr.com/3214/2946247371_ee0f82be7e_o.png)

Make sure to hit "format" and the second box on that screen should show the only "sbd" which is your USB, available.  Hit Make USB Then.  If running from your install on your netbook , you may have to download the .iso image from Ubuntu's Website, then in the first box on the USB cretor, point it to the .iso file you saved to your desktop or wherever.

---

### Post by Psychopump on 2009-04-09
Thanks again,Nano.
As I ststed before I have no USB stick at hand.
Is there ANY way to get my ethernet running from the kernel please?

---

### Post by Gaweph on 2009-04-09
Im sure the ethernet should simply start running on its own.

Wireless is a different story.

You could check if there is a backup copy or default copy of xorg.

cd /etc/X11/
then you wan to do: ls -l

if there is another copy of xorg.conf in there do:
CP backup/copyxorg.conf xorg.conf

Worth a shot

---

### Post by Psychopump on 2009-04-09
Imanaged to get eth0 running with these commands:

sudo ifconfig eth0 up
sudo dhclient eth0

and ran the command:

sudo apt-get install --reinstall xserver-xorg

when it had run, I tried startx but still get the message:

Saw signall 11. Server aborting.
giving up.
xinit: Connection refused (ewrrno 111): unable to cennect to X server
xinit: NO such process (errno 3): Server error

Any ideas?

---

### Post by Psychopump on 2009-04-09
@Gaweph

Thanks!
There IS a backup copy of xorg in the X11 folder called xorg.conf.backup

I tried:
cp xorg.conf.backup xorg.conf

But no joy...

---

### Post by Gaweph on 2009-04-09
What happened? did you restart X and still no GUI?

or were you not able to copy the file?

perhaps sudo cp is in order.

---

### Post by Psychopump on 2009-04-09
Could you explain sudo cp please?
I entered it and it says:

cp: missing fileoperand

EDIT:

Scratch that last comment.
I prefixed sudo to the command yet still no GUI.

---

### Post by Psychopump on 2009-04-09
ok..in 30 minutes I can reclaim my USB installer from my friend.
Can I fix my install with this without losing my data?
If so, please  explain how?

---

### Post by Gaweph on 2009-04-09
I think that the backup was probably created when you did the reinstall command:
sudo apt-get install --reinstall xserver-xorg
(So it is probably still notgoing to work)

I think you should try:

sudo dpkg-reconfigure xserver-xorg

Which should reconfigure and create a working xorgfile for you.

---

### Post by Psychopump on 2009-04-09
Tried that, same problem.&#296;t does not seem to be repairing the xorg file.

---

### Post by Psychopump on 2009-04-09
Here is what I have decided to do:

I am installing another intrepid on my HD by creating a new partition and installing onto it with the live USB.

First I will try to copy the xorg.conf from the new install into the old one on the other partition and reboot into it to see if it works.

If it does work I can reformat the new partition to be used for whatever.

If it doesn't work, I can boot into the new install, mkount the old partition and copy over all my files to the new one. Then I can reformat the old drive to be used for whatever.

Can anyone see why this would not work?

---

### Post by Psychopump on 2009-04-09
> **Psychopump said:**
> Here is what I have decided to do:

I am installing another intrepid on my HD by creating a new partition and installing onto it with the live USB.

First I will try to copy the xorg.conf from the new install into the old one on the other partition and reboot into it to see if it works.

If it does work I can reformat the new partition to be used for whatever.

If it doesn't work, I can boot into the new install, mkount the old partition and copy over all my files to the new one. Then I can reformat the old drive to be used for whatever.

Can anyone see why this would not work?

This is what I did.
Kept the new install and deleted the old.

---

### Post by Nano_ext3 on 2009-04-10
As I said before type "sudo dpkg-reconfigure xserver-xorg" when you boot into the recovery enviroment to reconfigure xorg.

---

### Post by Psychopump on 2009-04-10
> **Nano_ext3 said:**
> As I said before type "sudo dpkg-reconfigure xserver-xorg" when you boot into the recovery enviroment to reconfigure xorg.

I tried that multiple times before even posting this thread...
It didn't work.

Thanks though.
I have fixed it with a reinstallation.

---

