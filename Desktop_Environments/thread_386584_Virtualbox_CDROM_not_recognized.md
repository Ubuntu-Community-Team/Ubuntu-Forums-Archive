---
title: "Virtualbox CDROM not recognized"
date: 2007-03-17
forum: Desktop Environments
---

### Post by gjtoth on 2007-03-17
Trying out the latest version of Virtualbox since Parallels seems to have left it's users high and dry.  It installed just fine.  However, when I go to create a virtual box, I can't access the CDROM because my system has it designated at /media/cdrom0 and VBox only give me /dev/cdrom or /dev/hdc.

Anyone else come across this?  If so, how did you get around it or fix it?

Pardon me if this is in the wrong section....

---

### Post by penguinchrissy on 2007-03-17
I don't see why you can't edit you fstab so its mounted where it needs to be.

---

### Post by gjtoth on 2007-03-17
Weeeellllllllll... if I had just read the dialog box a bit closer, I would have seen that it said to make sure that I was in the group VBoxusers (or something like that).  I went to check and, sure enough, my name was there but the box was unchecked!

It works. :oops:

---

### Post by MemoryDump on 2007-10-25
I'm having the exact same problem right now with my setup. I've verified that I'm in the proper groups, however I still can't access the proper CDROM devices :(

---

### Post by MemoryDump on 2007-10-26
> **MemoryDump said:**
> I'm having the exact same problem right now with my setup. I've verified that I'm in the proper groups, however I still can't access the proper CDROM devices :(

anybody?

---

### Post by zaphod777 on 2007-10-26
> **gjtoth said:**
> Weeeellllllllll... if I had just read the dialog box a bit closer, I would have seen that it said to make sure that I was in the group VBoxusers (or something like that).  I went to check and, sure enough, my name was there but the box was unchecked!

It works. :oops:

I hate it when that happens :grin:

---

### Post by zaphod777 on 2007-10-26
> **MemoryDump said:**
> anybody?

try:

sudo gedit /etc/fstab 

and see if you can change the mount location of the cdrom to 

/dev/cdrom 

probably need to reboot

---

### Post by MemoryDump on 2007-10-26
> **zaphod777 said:**
> try:

sudo gedit /etc/fstab 

and see if you can change the mount location of the cdrom to 

/dev/cdrom 

probably need to reboot

still no go.. I changed it from /media/cdrom0 to /dev/cdrom and now my CDROM isn't even viewable/accessible via Linux itself. :(
makes no sense to me!

---

### Post by fdimmling on 2007-10-26
I just tested it on my Gutsy system and VirtualBox 1.5.2 running XP as a guest. It works out of the box, CDROM is /cdrom0 as to the Nautilus pop-up window.

Friedrich

---

### Post by zaphod777 on 2007-10-26
> **MemoryDump said:**
> still no go.. I changed it from /media/cdrom0 to /dev/cdrom and now my CDROM isn't even viewable/accessible via Linux itself. :(
makes no sense to me!

Strange lets see if anyone else has a sugestion.

---

### Post by ruisantos78 on 2007-10-28
the easy way is just edit the xml config file of your virtual machine....

- Configure your virtual machine to use /dev/cdrom as CD-ROM unit.
- Exit VirtualBox
- Open the VM config file (~/.VirtualBox/Machines/<Your VM Name>/<Your VM Name>.xml
- Change this line:

      <DVDDrive passthrough="true">
        <HostDrive src="**/dev/cdrom**"/>
      </DVDDrive>

to

      <DVDDrive passthrough="true">
        <HostDrive src="**/dev/hda**"/>
      </DVDDrive>

Save the file and open the VirtualBox

and is done....

cya

---

### Post by MemoryDump on 2007-10-29
> **ruisantos78 said:**
> the easy way is just edit the xml config file of your virtual machine....

- Configure your virtual machine to use /dev/cdrom as CD-ROM unit.
- Exit VirtualBox
- Open the VM config file (~/.VirtualBox/Machines/<Your VM Name>/<Your VM Name>.xml
- Change this line:

      <DVDDrive passthrough="true">
        <HostDrive src="**/dev/cdrom**"/>
      </DVDDrive>

to

      <DVDDrive passthrough="true">
        <HostDrive src="**/dev/hda**"/>
      </DVDDrive>

Save the file and open the VirtualBox

and is done....

cya

OMG! this worked!
I simply changed it to /dev/scd1 and it did the trick!
thanks a million!! :guitar:

---

### Post by bouncingmolar on 2007-10-31
> **MemoryDump said:**
> OMG! this worked!
I simply changed it to /dev/scd1 and it did the trick!
thanks a million!! :guitar:

In my case I looked in the /dev directory and saw cdrom cdrom1cdrw dvd. So i tried a few and replacing with /dev/cdrom1 worked!

---

### Post by coolcalt on 2007-11-03
> **gjtoth said:**
> Weeeellllllllll... if I had just read the dialog box a bit closer, I would have seen that it said to make sure that I was in the group VBoxusers (or something like that).  I went to check and, sure enough, my name was there but the box was unchecked!

It works. :oops:


I had the same problem, thanks for posting the solution.

---

### Post by jon80 on 2008-04-04
> **MemoryDump said:**
> still no go.. I changed it from /media/cdrom0 to /dev/cdrom and now my CDROM isn't even viewable/accessible via Linux itself. :(
makes no sense to me!

I've had a similar problem when trying to install 'startx' using:

*sudo apt-get install-xinit*

Ubuntu was prompting me to insert the cdrom, which I did, but it kept prompting me.

I checked /etc/fstab and cdrom points to /dev/scd0.  

It doesn't make sense because I installed Ubuntu from the same .iso image, hence I would have expected it to recognize the same image.

(see attachment)


Any ideas please?

---

