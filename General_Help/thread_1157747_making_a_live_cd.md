---
title: "making a live cd"
date: 2009-05-13
forum: General Help
---

### Post by frente69 on 2009-05-13
Hi,

I am helping at a charity where we get a lot of donated computers. 
When we are entering the systems into the inventory system we currently:
[LIST]
[*]Test the ram using memtest+
[*]Use DBAN to erase the hard drive
[*]Enter the details of the computer into the web based inventory system.
[/LIST]

I was hoping to make this process a little more automated.
At the moment we use 2 different cd's for memtest and dban and then go to another computer to start entering the details of the computer by hand.

I was thinking of making a live cd which would:
[LIST]
[*]test the memory
[*]if that passes then securely erase the hard drive
[*]once done, load up minimal X(don't really need gnome or kde etc)
[*]load some form of inventory software which would gather the specs of the pc(cpu, fsb, video, ram, hdd etc) and display it
[*]finally fire up a copy of firefox pointing to the inventory sys.
[/LIST]

It would be nice to automatically upload the specs to the system but this would be something for the future - at the moment i am aiming for baby steps.

I would want it to be very lean as it would be running on low end Pentium 3's and up. 

I have a little experience with ubuntu but know nothing about modifying the boot time config (run certain applications before loading a GUI etc).

I would i also need to know how to add many different network card drivers as this will be running on many different hardware configs?
Also if you could suggest some good applications i could use for disk erasure and memory testing would be good as well as any tutorials that might be relevant on achieving the goals i have stated above.

Thanks,
Frente

---

### Post by sir_nasty on 2009-05-13
I'd do two things... for the newer systems I'd have a usb bootable drive with utilities on it then a cd that has them as well....

check this link and look at the system info lines, you could put together a simple script to do it then run sudo rm -rf and erase the whole drive.... maybe try a debian xfce distro or linuxmint.... idk... just some thoughts/ideas

---

### Post by Junkieman on 2009-05-23
Hi frente! I'd suggest an Ubuntu base just for the wide variety of hardware support, if the PC's will be connected to a wired network and get assigned an IP via DHCP then great!

[Remastersys]("http://www.dedoimedo.com/computers/remastersys.html") allows you to create a live CD from your local install, the **backup** option is the one you want, as it preserves your user settings and files on the live CD. The tut is for Hardy, but I successfully used the same method to make an Intrepid 8.10 live CD, and from a [virtual machine]("http://www.vmware.com/player") install too, worked great! And you don't mess up your real install. Just make sure you give the VM plenty of drive space!

You could setup the system to boot to runlevel 2, text mode only. Most console apps give a return code, 0 usually being success or 'no errors', which is how you could check the memtest result for example. There should be info in the mahelp/n pages for the application you're using.

You could then pull the PC's hardware info [ using commands]("http://linux.byexamples.com/archives/185/get-to-know-your-hardware-information/"), and append each command output to a text file like so: 

```
lspci >> /tmp/pc_info
lshw -short >> /tmp/pc_info
lshw -class memory >> /tmp/pc_info
```

*This will dump all the info into the /tmp/pc_info file*

Once you have your info, you could ftp the file up to another networked pc running a ftp server, afterwards you wipe the system. 

Just a few ideas ;)

Edit: As nasty said, a bootable usb drive is a good idea! RemasterSys creates a ISO of your live CD, from there you can make a usb disk bootable with your custom live CD. I've done it with knoppix and pretty sure we can find a way for this too ;)

---

