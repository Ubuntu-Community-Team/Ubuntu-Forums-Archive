---
title: "is there a way to run windows..."
date: 2007-03-24
forum: Desktop Environments
---

### Post by k0mpresd on 2007-03-24
if its already installed on a seperate hdd?

i saw a link to a free software app on here the other day that would allow you to install windows and run windows while under linux

but i dont want to reinstall windows..i want to run the copy i already have set up

---

### Post by mac.ryan on 2007-03-24
If you want to run windows as an operating system while also running linux, then you are probably looking for a virtual machine like "VMware".

if you want to run windows applications from withing linux, you will probably need an interface layer like "wine".

I have no experience in either of the two, but I understood from other threads and posts, that you have to install the software (or the system) after you installed either of them.

---

### Post by FXWGBill on 2007-03-24
If Windoze was already on your puter when you installed Ubuntu, what you should have done was let it install the Grub bootloader.  I am pretty sure you can go back and do it now, from the repo's.  It will set it up so that  a menu comes up, at boot time, and you can select what you want to boot up in, Linux or Windoze.  And like the other post said, if you want to run a couple of Windoze apps, Wine does a pretty good job, depending on what you want to do....

Need more info...

---

### Post by tagra123 on 2007-03-24
You can have VMWare using your existing windows partition. 

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

I have a similar setup on a Dell 3800 Laptop.  Works nicely.

---

### Post by FXWGBill on 2007-03-24
Not to hijack the thread, but do you have grub on that laptop, tagra123?  And if so, how did you get Vmware to load and run Grub? (I'm thinking a link to the menu list might solve it)

And I am in the process of checking out the Vmware setup... But all I have used thus far is Wine, as I said.  I guess I'll see shortly what the better way for me to do it is....  You'll have to make the same determination k0mpresd.

---

### Post by k0mpresd on 2007-03-24
thanks for the replies :)

ok..i installed wine

where did it install to? i cant seem to find it and/or get it running

---

### Post by FXWGBill on 2007-03-24
tagra AND k0mpres, better slow down on the Vmware setup, not sure if you are aware, Tagra, but when I read the post I am gonna link you to, it all made sense...  The Vmware method is NOT  a good way to go, if you need to dual boot sometimes... read this WHOLE thread before going any further!!!  Wine is DEFINATELY the better way to go if you only need a couple windoze proggys here and there.....

[http://www.ubuntuforums.org/showthread.php?t=380699&highlight=Grub+error+21+in+vmware](http://www.ubuntuforums.org/showthread.php?t=380699&highlight=Grub+error+21+in+vmware)

---

### Post by FXWGBill on 2007-03-24
where the binaries for ie6 and the basic 'things' that get installed are, will be in a directory right off of your home directory.  If you bring up a terminal, you will be in your home directory, just type cd /bin and you will be there.  then, to run ie6, you just type './ie6'  (that is 'dot forward slant and ie6) and it should come up.  If you do a 'ls' of that directory you will see IE6 abd wmplayer, etc. 

What I use to look around at the directories is:  Midnight Commander.  Don't know if you are familiar with Norton Commander of about 20 years ago, but it is a pretty exact clone.  Then you also have Gnome-Commander, both are in the repos or you can simpley type "sudo apt-get install mc"  and 'sudo apt-get install Gnome-Commander'  or to shorten it up a bit you CAN do 'sudo apt-get install mc gnome commander' I believe.  Or as I said you can bring up synaptic and get them that way.

Then with Midnight Commander, all you have to do is bring up a terminal and type 'mc' and up it will come.  Then just 'pg-dwn' through the directories till you find first /.wine  and further down  /bin and hit enter on them and in ./bin will be your binaries for IE6 and then in /.wine will be the 'drive_c'  and after that it looks just like a dos directory structure.  

This will help you get used to where the directories are and moving around them a bit; it's good to know where things go.  Oh... and Gnome-Commander will be in your Applications and Accesories  it's real handy for all kindssssssss of things.  You can bring it up in 'root' mode and change permissions and ownership of files and directories and all kinds of things....

that should get ya started....

---

### Post by tagra123 on 2007-03-25
> **FXWGBill said:**
> Not to hijack the thread, but do you have grub on that laptop, tagra123?  And if so, how did you get Vmware to load and run Grub? (I'm thinking a link to the menu list might solve it)

And I am in the process of checking out the Vmware setup... But all I have used thus far is Wine, as I said.  I guess I'll see shortly what the better way for me to do it is....  You'll have to make the same determination k0mpresd.

I copied the MBR or the first 64 bytes according the the instructions and set the VMDK file to use the copied image as the Boot Portion and the rest of the drive, according the instructions..  Then When I first booted the grub boot menu showed up in the VM.  Thats not what I wanted, so from within the VM I ran fixmbr. Fixmbr writes to the 64 byte image, not the real disk.  Now the only time I get the boot menus is when the computer is being rebooted, but I do not receive the boot menu when starting the VM.

Before messing with the fake mbr its a good idea to backup your real mbr and partition table using dd, just in case something wasn't set up correctly.

---

### Post by tagra123 on 2007-03-25
> **FXWGBill said:**
> tagra AND k0mpres, better slow down on the Vmware setup, not sure if you are aware, Tagra, but when I read the post I am gonna link you to, it all made sense...  The Vmware method is NOT  a good way to go, if you need to dual boot sometimes... read this WHOLE thread before going any further!!!  Wine is DEFINATELY the better way to go if you only need a couple windoze proggys here and there.....

[http://www.ubuntuforums.org/showthread.php?t=380699&highlight=Grub+error+21+in+vmware](http://www.ubuntuforums.org/showthread.php?t=380699&highlight=Grub+error+21+in+vmware)


I haven't experienced any problems with it and it's been this way for a couple of months.  I haven't tried it with an xp installation, my laptop has ME on it. Although if I were using XP I'd just write a simple boot batch script that copied the respective wpa depending on which machine I was using.

Wine doesn't run everything.  This setup is when  limited on disk space, The real bonus for me was that anything changed in the booted windows is also present the next time I boot windows using the virtual machine.  

I keep good backups -- before and after so no biggie there. If something does go wrong I can usually have my computer working the way it was before within an hour.

Biggest thing is to follow the directions when doing these sort of things and do not blindly copy commands from a how to.  If anyone doesn't know what the command is going to do then its a good Idea to read about the command before executing it on your system.

---

### Post by k0mpresd on 2007-03-25
i tried to install newsbin via wine

it installed but gave some errors along the way about some missing dll's and it wouldnt run :(

looks like wine is a no-go for me

---

### Post by FXWGBill on 2007-03-25
k0presd, I am not sure what that is, can you give some more details please....

and yes, some things just will not work in wine, but what you may find is that there are Linux equivalents that will work just fine.  Also...  there is a LOT of open source software that there are BOTH, XP versions and Linux versions.  I had started looking at all the open source software long before I started to run Linux, so I was 'prepared', more or less...

Can ya give some more info on what that exactly is and let me have a look.  Can't guarantee anything, but I might be able to help.  Also, you are running 'this' particular proggy in XP? or some other version of Windoze?  How old is the program, also; there are older versions of wine that more simulate Win98, etc...

---

### Post by FXWGBill on 2007-03-25
Tagra123...  You  lost me there... If the Vmware crashes there at the Grub menu, I don't see how you can run anything else, unless you mean don't let it get that far...  Could you explain a bit further please...

I understand what you are doing, just not all the particulars...

K0mpresd...  this may work for you too; vmware.  I am trying to make sure that what the post I gave earlier said where I quoted the thread where they were sayin you had to reregister XP and all that mess...  I think what he is/was saying is very misleading and I am working on figuring it out...

So ya ain't dead yet.... hang on...

---

### Post by tagra123 on 2007-03-25
1st -- The WPA -- XP

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/589309.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/589309.html)

If you can access (mount) windows partition find the WPA.DB and make a copy of it 

cp WPA.DB WPA-DB.RegularWindows

NOw I'm not sure but XP does allow for differing hardware profiles too so it might work. I'd tell windows that the laptop is dockable so it will ignore some of the settings it might otherwise look for. You can read about this by searching for google.

Now only if necessary you can register if it makes you the copy in the virtual machine. This would overwrite WPA.DB so I'd make another copy after activating the virtual machine from within the virtual machine  

copy WPA.DB WPA-DB.VIRTUAL

Now you have a copy for both and I think you could add a call in the autoexec to give you a choice -- 

REG 
Virtual

If virtual is picked do something like --  copy  WPA-DB.VIRTUAL WPA.DB

I think that should at least show the logic, although I'm not sure this is necessary with hardware profiles.

2nd

If you set up the VMDK file correctly then you are not actually using the harddrives boot partition. You will be using the file for the boot partition. Hence when you run fixmbr from the windows cd in the virtual machine, then you will be writing to the file not the actual harddrive  mbr.  That is, you boot  the vm from the CD and run fixmbr.  You could do this from the pc without  the VM but grub would disappear.

IF you cannot boot at all and you can tell grub to find the bootable partition. You can do this by reinstalling grub or using a utility like supergrub boot disk.

[http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html](http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html)

---

### Post by FXWGBill on 2007-03-25
I see what you are saying, but the thing is... that info to boot to XP is already 'around'...  somewhere...  Just gotta figure out where and I am thinking it might very well be in the grub directory... cause it has to go there to get the menu list and then by that it knows which/where to boot from.... hmmmmm

Lemme do some searching... I'll figure it out

---

### Post by tagra123 on 2007-03-25
If you know what partition number hdxX windows is on you should be able to make it start by editing 

sudo gedit /boot/grub/menu.lst

#
# title         Windows 95/98/NT/2000
# root          (hd0,0)      ** (Unless you messed with mapping This is grubs version of ubuntus hda1, and (hd1,1) = hdb2, etc....)**
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

---

### Post by FXWGBill on 2007-03-25
that's the whole problem... Grub won't fully load up... get 'Error 21'  and all I can find on the forums is that need to do that fixmbr thingy.  What I am thinking though, is that I need to get a better look at the partition info, the calculation might be off a bit...  I have that SystemRescueCD made up, here in a while I'll boot up to it, and see what I can see with it.   Something is 'off' just a bit... that's gotta be what it is...

---

