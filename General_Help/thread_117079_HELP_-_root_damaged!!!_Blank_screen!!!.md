---
title: "HELP - /root damaged!!! Blank screen!!!"
date: 2006-01-14
forum: General Help
---

### Post by MJSOnline on 2006-01-14
Hi all.

Right I have tried to install Ubuntu 5.10 on my system 4 times now!!

I insert the CD, type install and the install gets to line two of the screen, then my screen goes blank, system freezes.  The only way I can get my pc back is to unplug it!!  Is this normal?  What do i need to do?

I have taken outg the partion table so it makes one its self.  That worked twice.  So I got into my system.

However when I goto created two partions on my SECOND hard drive, one for Ubuntu, one for Windows using gparted, it finds it and does it.  But when I format them and then reboot I get the blank screen again!!!

What am I doing wrong?  What do I format my SECOND hard drive as?  It to going to be used for wp docs, mp3, spreedsheets etc.  The Windows partion is there incase I have to go back to  Windows.

If I cant install Ubuntu for it to work correctly then I will have to back to Windows, dont want to tho.

I have a Samsung 10.2GB hard drive as master.
Maxtor 82.0GB as slave.

Please help!!  Idiot proof is poss.

Thanks all.
Matthew

---

### Post by MJSOnline on 2006-01-14
Anyone?  I can even boot into Live CD version of the DVD!!  Please!!! M

---

### Post by BathroomNinja on 2006-01-14
If you can't even boot the live CD version, how are you using gparted?

First off, make sure you have good media.  Are you using copies of Ubuntu that you burned yourself or did you get them in the mail.  Do you have another computer you can try booting the live cd up with, to test the disk?

Second.  What are the specs on your computer?  Tell us as much as you know.  You should be able to get a lot of information from the screen when the computer first turns on.

Are you able to boot into Windows?

---

### Post by MJSOnline on 2006-01-14
Ok an update.

I have now installed Ubuntu 5.10 (Gnome).  I had to wait 10mins to reboot.

How do I format my SECOND hard drive?  Partion it?  I am very new to this, I bet it shows too.

How do I "auto mount" at start up?

All I want to use the 2nd drive as data, mp3, doc etc.

Thats all.

Ok spec is
AMD 2.2Ghz
Asrock 462 chipset - K7S41GX
512 MB mem
Master Hard drive Samsung 10.2GB
Salve hard drive Maxtor 82.0GB
DVDRW Liton SOHW 832S

Any help would be great. Thanks.

Matthew

---

### Post by NiceGuy on 2006-01-14
*deleted*

---

### Post by NiceGuy on 2006-01-14
To partition the HD I'd use gparted: [http://ubuntuguide.org/#gparted]("http://ubuntuguide.org/#gparted")

And to auto mount the drives follow these instructions [http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

For the 2nd hard drive Its probably best to format it as FAT32

---

### Post by MJSOnline on 2006-01-14
[QUOTE=NiceGuy]To partition the HD I'd use gparted: [http://ubuntuguide.org/#gparted]("http://ubuntuguide.org/#gparted")

And to auto mount the drives follow these instructions [http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

For the 2nd hard drive Its probably best to format it as FAT32[/QUOTE]

Ok. Can I add Gparted using Synapic Package Manager?
I have now taken Windows off the system, left with just Ubuntu.

What 2nd option do I use to format the 2nd hard drive (80GB)?
Thanks again. Matthew

---

### Post by BathroomNinja on 2006-01-14
For the second hard drive, I recomend using EXT3.  Windows can easily read from EXT3 using this free (as in beer) driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)

In addition, Windows XP hates letting you use FAT32 above 32GB.  Since his drive is 82GB, he may have issues.


You can find Gparted in the panel.  
go to SYSTEM > ADMINISTRATION > DISKS
enter your password if needed

---

### Post by NiceGuy on 2006-01-14
I'd agree with BathroomNinja 'except' that you won't be able to access it if you use windows 98 (or 95), but if you don't then go for it (its what I use). Just read the ubuntu guide for mounting it as fat but put 'ext3' as the 'type' and 'defaults' for 'options' in your fstab

---

### Post by MJSOnline on 2006-01-14
[QUOTE=BathroomNinja]For the second hard drive, I recomend using EXT3.  Windows can easily read from EXT3 using this free (as in beer) driver: [http://www.fs-driver.org/](http://www.fs-driver.org/)

In addition, Windows XP hates letting you use FAT32 above 32GB.  Since his drive is 82GB, he may have issues.


You can find Gparted in the panel.  
go to SYSTEM > ADMINISTRATION > DISKS
enter your password if needed[/QUOTE]

I get the EXT3 thing but under the drop down in Admin > Disks > Select HHD > I get a sub menu saying /boot > /var  /media and so on.  What do I choose then? I have decided to forma the whole drive in EXT 2 or ,3 by the way.

Do the 2nd hard drive mount up at startup or do i have to "brows" for it my self?

Does that help?
Matthew

---

### Post by BathroomNinja on 2006-01-14
You should see something like the picture below (click on it).

On the left, Disk Manager shows the drives you have.  If you click on your smaller drive, then click on the partitions tab on the right, you should see the partitions that Ubuntu setup for you during install.

Now, click on the larger drive on the left side.  Then click on partitions on the right.  It should be blank.  If not, take a screenshot by pressing the 'Print Screen' key on the upper right of your keyboard, near the lights.  It will save a picture of your screen to your desktop.  You can then attach it to your next message using the 'attachments' button at the bottom of the screen when you're writing a new post.

--
Edited because I wasn't thinking

---

### Post by NiceGuy on 2006-01-14
BathroomNinja: urm.. thats not gparted - is it?

---

### Post by kosmic on 2006-01-14
Nop it Is the Disk Manager, you can find it in ADMINISTRATION - SYSTEM - DISK MANAGER

---

### Post by BathroomNinja on 2006-01-14
[QUOTE=NiceGuy]BathroomNinja: urm.. thats not gparted - is it?[/QUOTE]


haha, I'm still waking up. I'm trying to give him something easy to use.  Yeah, for him, I recomend Disk Manager, not Gparted.  What am I thinking?

---

### Post by NiceGuy on 2006-01-14
[QUOTE=BathroomNinja]haha, I'm still waking up. I'm trying to give him something easy to use.  Yeah, for him, I recomend Disk Manager, not Gparted.  What am I thinking?[/QUOTE]

Fair enough (was getting a bit confused!), I've never used it myself, is it really easier to use than gparted?

---

### Post by BathroomNinja on 2006-01-14
[QUOTE=NiceGuy]Fair enough (was getting a bit confused!), I've never used it myself, is it really easier to use than gparted?[/QUOTE]


OK, I think I'm awake enough.  It's 'pretty'.  I normally use Gparted to create partitions and Disk Manager to edit when and where they mount.  But Disk Manager can create partitions as well.  It has a very 'noob' friendly interface to it.

---

### Post by MJSOnline on 2006-01-14
OK.  am back. Done that. I have attached a screenshot too.

Matt

---

### Post by MJSOnline on 2006-01-14
[QUOTE=MJSOnline]OK.  am back. Done that. I have attached a screenshot too.

Matt[/QUOTE]

Add this one too.

---

### Post by MJSOnline on 2006-01-14
Anyone?  What do I do next?

Matthew

---

### Post by MJSOnline on 2006-01-14
Come on guys & girls.  All I need to know is how to create a partion on a empty hard drive using Disks Manager as in System > Administration > Disks.

Anyone?

Thanks in advance.
Matthew

---

### Post by NiceGuy on 2006-01-14
[QUOTE=MJSOnline]Come on guys & girls.  All I need to know is how to create a partion on a empty hard drive using Disks Manager as in System > Administration > Disks.

Anyone?

Thanks in advance.
Matthew[/QUOTE]

Urm... I'm afraid that I don't know how to do it in Disks Manager, but if you install gparted [http://ubuntuguide.org/#gparted]("http://ubuntuguide.org/#gparted")

then go to Applications > System Tools > gParted

select your 2nd HD (top right), and click new etc, etc...

It should be easy from there (I hope - I haven't used it in a while). If you have any problems post back.

---

### Post by MJSOnline on 2006-01-14
Ok.
Then do I do a reboot before formating it?  Ext2 formated? What options? /var /boot etc?

Thanks.
Matthew

---

### Post by NiceGuy on 2006-01-14
> Then do I do a reboot before formating it? If it told you to then yes
> Ext2 formated? If you like, either that or Fat32 (but I'd go for Ext2 or Ext3 if I were you)
> What options? /var /boot Urm... well you don't need to boot from it... If there are default options use those.

---

### Post by BathroomNinja on 2006-01-14
Sorry to leave you hanging, I'm at work and not always near a computer.  

Follow NiceGuy's instructions.  For the mount point, decide where you want it.  Since you are going for a media server thing, I would recomend creating a folder under /media.

On my computer, I have my media drive setup on /media/ZShare
So in my example, you would open up a terminal, type:

mkdir /media/ZShare

You can name it anything you want, but I always keep mine in the /media folder because I'm weird like that.
After making the partition in Gparted, set it to mount to the directory you created.  If you get lost at that point, let us know and we will walk you through it manually.

EDIT-  I want to emphasis that you do NOT want to set it to mount to /var or /root or anything else that YOU did not personally create.  Doing so WILL cause serious problems.

---

### Post by MJSOnline on 2006-01-14
Thats ok mate. no problem.
Ok. I got as far as Gparted. As a Primary partion in ext3.  Is that right?

Mount point? Is that formating?

What do I format it to? 

Once all that is done can I make it show at bootup? Make folders etc?
How do I do that?

Also I have to turn my system off and leave it off for 15mins or so before restarting it again or I get the blank screen.  Is this normal?

Thanks again
Matthew.

---

### Post by BathroomNinja on 2006-01-14
[QUOTE=MJSOnline]Thats ok mate. no problem.
Ok. I got as far as Gparted. As a Primary partion in ext3.  Is that right?

Mount point? Is that formating?

What do I format it to? 

Once all that is done can I make it show at bootup? Make folders etc?
How do I do that?

Also I have to turn my system off and leave it off for 15mins or so before restarting it again or I get the blank screen.  Is this normal?

Thanks again
Matthew.[/QUOTE]



create a new, primary partition, as EXT3 on that drive.  Don't set it to mount as anything yet.  Just do this first part and let us know when you get that done.

---

### Post by MJSOnline on 2006-01-14
Ok.

Done that.

Sorry for the wait.
Matthew

---

### Post by BathroomNinja on 2006-01-14
OK good!  We are making progress here.  Go back to Disk Manager (I detailed how to find it above in a previous post).

Follow the steps I mentioned up there.  Find the drive on the left, click on the tab on the right.  Also, have you already created a directory to house this drive as I mentioned previously?

---

### Post by MJSOnline on 2006-01-14
[QUOTE=BathroomNinja]OK good!  We are making progress here.  Go back to Disk Manager (I detailed how to find it above in a previous post).

Follow the steps I mentioned up there.  Find the drive on the left, click on the tab on the right.  Also, have you already created a directory to house this drive as I mentioned previously?[/QUOTE]

No I have not created a dircretory yet.  How do I do that again?

I have the Disks Manager up now showing a ext3 partion on my 80GB drive.

Does that help?  (I sound so thick!!)

Matthew

---

### Post by MJSOnline on 2006-01-14
When you said "mkdir /media/ZShare" is that to be typed in the terminal window?

So it would read as "mkdir /media/Matthew" for example?

Does that make sense?

What next?

Matthew

---

### Post by NiceGuy on 2006-01-14
Yes you type it in the terminal window except you will need to type:```
sudo mkdir /media/Matthew
```With the 'sudo' bit in front, otherwise you will get a permission error. It will ask you for your password, enter it and this will make a directory in your media folder. 

Next you will need to 'mount' your partition in this location. But first we need to find out the 'physical' location of the partition. 

Type this in to the terminal: ```
sudo fdisk -l
```

From the list shown you *should* be able to spot your partition. It will probably be /dev/hdb1 (but don't hold me to that)

now type this in to the terminal replacing the '/dev/hdb1' bit if different:

> sudo mount /dev/hdb1 /media/Matthew/ -t ext3

now in theory this should have mounted your partition.

Go to Places > Computer > Filesystem > Media > Mathew

Did it work? (look at your free space at the bottom of the window to see)

... more to come

---

### Post by NiceGuy on 2006-01-14
Presuming this worked you'll want to mount the partion automatically at startup. You need to edit a file called the 'fstab' (don't worry this is easy).

Type in a terminal: ```
sudo cp /etc/fstab /etc/fstab_backup
```
This makes a back up of your fstab (just in case!)

now type ```
sudo gedit /etc/fstab
```
This will open the file in a text editor, append the following to the bottom of the file (changing the /dev/hdb1 bit if necessary)

```
/dev/hdb1       /media/Matthew	ext3		defaults			0	0
```

Save and exit.

Now restart your computer. Did it work?

---

### Post by MJSOnline on 2006-01-14
Great.  How do I format it?  Does it need formating? Do I just make dir on the drive as before?

Thanks again. Matthew

---

### Post by NiceGuy on 2006-01-14
[QUOTE=MJSOnline]Great.  How do I format it?  Does it need formating? Do I just make dir on the drive as before?

Thanks again. Matthew[/QUOTE]

*How do I format it?* Thats what you just did using gParted.

*Do I just make dir on the drive as before?* Do you mean can you use it as you did under windows (making directorys etc)? If so then yes you can.

<off topic>
By the way, if you are a bit confused about all this 'mounting business' and the linux filesystem in general then I recommend you read [http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")

It looks bad but its quite an easy read (helped me when I first started)
</off topic>

---

### Post by MJSOnline on 2006-01-15
Thanks NiceGuy for the info. I have got it working, with a icon on my desktop too.

Ok, how do I make a dir / folder on the hard drive now? Calling it "Docs" and on other called "Music", etc.  Does that put an "shortcut icion" on my desktop too?  How do I do that?

Thanks again to you all.
Matthew

---

### Post by MJSOnline on 2006-01-15
Anyone?

The 2nd hard drive called "SlaveDrive" is under.
Device Boot Start End Blocks Id System
/dev/hdb1 1 9964 80035798+ 83 Linux

Does that help?
Matthew

---

### Post by NiceGuy on 2006-01-15
[QUOTE=MJSOnline]Thanks NiceGuy for the info. I have got it working, with a icon on my desktop too.

Ok, how do I make a dir / folder on the hard drive now? Calling it "Docs" and on other called "Music", etc.  Does that put an "shortcut icion" on my desktop too?  How do I do that?

Thanks again to you all.
Matthew[/QUOTE]

Good, glad to hear you've got your drive mounted! Now you should be able to use it as you would in windows ie. to make a new folder on the drive, double click on the icon on your desktop, then right click somewhere in the drive window and click create folder and then name it 'My Docs' or whatever. If you want a shortcut on your desktop to this new folder, right click on the folder and click 'make link'. this will make a shortcut, now just move this shortcut to your desktop.

Hope that helps!

---

### Post by MJSOnline on 2006-01-15
Did that. 
It did not work, damm!

Click in to new drive icon > Right clicked in the folder of new drive > Got Arrange Items, Zoom in,out,normal and Properties.

The Create folder is greyed out.
Wha tam I doing wrong?

After I edited the boot file as above and rebooted, I did get a red failed duriing booting up.  It scrolled up the screen.  Does that mean anything?

Matthew

---

### Post by MJSOnline on 2006-01-15
Rite I deleated the line of my automounted drive that we did yesterday and replaced it with the one that NiceGuy made above, replacing the location where listed in fdisk - l.

Now I dont get the "failed" in red at boot up, but I still cant create a folder on my new drive.

I tried creating a folder on my desktop and draging it to the "SlaveDrive" but it says "I do not have the permissions" do do this.  What do I do?

Any ideas?  I am going very grey just thinking about it!!

Matthew

---

### Post by NiceGuy on 2006-01-15
hurm... now thats odd. the 'defaults' setting in your fstab should have allowed you permission to read/write to the drive.

Could you right click on drive icon on the desktop and go to properties and then click on the permissions tab. You should be the 'file owner' (ie. not root - if it is owned by root we need to change that). The Owner read, write and execute tick boxes should be ticked.


*Minor brain spasm post changed :p*

---

### Post by MJSOnline on 2006-01-15
[QUOTE=NiceGuy]hurm... now thats odd. the 'defaults' setting in your fstab should have allowed you permission to read/write to the drive.

Could you right click on drive icon on the desktop and go to properties and then click on the permissions tab. You should be the 'file owner' (ie. not root - if it is owned by root we need to change that). The Owner read, write and execute tick boxes should be ticked.


*Minor brain spasm post changed :p*[/QUOTE]

How do you mean odd?
Did I do it all right?

Ok. I have right clicked the SlaveDrive icon on my desktop and gone to properties.  It shows the File Owner as "root" along with File group.

Also the Owner part is greyed out but shows Read Write Exceute as ticked.
Group part is greyed out but shows Read and Exceute ticked.
Others part is greyed out but shows Read and Exceute ticked.
Text view is drwxr-xr-x
Number view is 755
At te bottom it says "You are not the owner, so you can't change these permisssions"

I have attached two screenshots too for your ref.  Any good?

This is a copy of my "fstab" file too

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hdb1 /media/SlaveDrive ext3 defaults 0 0

And my "sudo fdisk -l

Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1185     9518481   83  Linux
/dev/hda2            1186        1240      441787+   5  Extended
/dev/hda5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9964    80035798+  83  Linux


Does that help?
Matthew

---

### Post by MJSOnline on 2006-01-15
Anyone got a clue? Please. I dont have to reinstall Ubuntu all over again do I?
Matthew

---

### Post by MJSOnline on 2006-01-15
Anyone got any ideas? What am I missing?  IK need this to work as the 2nd hd is where I want to all my data.  Docs, mp3 etc.  
Matthew

---

### Post by npmeyer on 2006-01-15
Hi,

You might try this:

```
sudo chown username:username /media/SlaveDrive
``` 
but replace "username" with your user account name on Ubuntu. That should change the owner of the "SlaveDrive" directory you created to be you, instead of root. I'm not sure, but that might work.

---

### Post by MJSOnline on 2006-01-15
[QUOTE=npmeyer]Hi,

You might try this:

```
sudo chown username:username /media/SlaveDrive
``` 
but replace "username" with your user account name on Ubuntu. That should change the owner of the "SlaveDrive" directory you created to be you, instead of root. I'm not sure, but that might work.[/QUOTE]

Ok.  So I put " sudo chown matthew:matthew /media/SlaveDrive " is that right?

Is that auto mounting too?

Matthew

---

### Post by npmeyer on 2006-01-15
That's correct.  That should change the owner of the drive from root to your account.  You've already configured Ubuntu to automatically mount that drive when you start you computer.  Now see if you can create a folder on that drive.

---

### Post by MJSOnline on 2006-01-15
[QUOTE=npmeyer]That's correct.  That should change the owner of the drive from root to your account.  You've already configured Ubuntu to automatically mount that drive when you start you computer.  Now see if you can create a folder on that drive.[/QUOTE]
All my god!! 

You saint you!!

It works!!!  WOW!!!  That took me over a day to fix.  Many thanks!!!

FAB!!!
Matthew

Now do I add packages that I have in gz files?

---

### Post by npmeyer on 2006-01-15
Great!

I'm not sure if I know what you mean by "adding packages you had in .gz files."  Do you mean you have programs that you want to install that came in .tar.gz files, or do you mean you had documents, mp3s and the like zipped up that you want to extract to that second hard drive, now that it's working?

---

### Post by MJSOnline on 2006-01-15
[QUOTE=npmeyer]Great!

I'm not sure if I know what you mean by "adding packages you had in .gz files."  Do you mean you have programs that you want to install that came in .tar.gz files, or do you mean you had documents, mp3s and the like zipped up that you want to extract to that second hard drive, now that it's working?[/QUOTE]

I have download azures as a gz file before I installed Ubuntu.  So I have it on CDR.  I want to install it onto my system if poss.

I also have a few documents zipped up, I used 7-zip open source software, that I would like to unzip to a folder if poss.  Does 7-zip work under Ubuntu too?

Thanks again.  Great!  Matthew

---

### Post by npmeyer on 2006-01-15
Hey,

You probably won't want to install Azureus onto that second hard drive that we just got up and running; that makes more sense to put on your primary hard drive that houses the operating system.  Some instructions for installing Azureus on Ubuntu can be found at [http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/]("http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/"): it's pretty far down the page under the heading "Installing an Application."  You might have to either change a few lines of his instructions, since yours is on CD-R, or download Azureus again.

7-Zip, as far as I know, is only a Windows application, but you can extract *.7z files on Linux as well, though I've never done it, so I can't say exactly how to do that.  A good place to start would be searching these forums or Google for "7-Zip Ubuntu" or something similar.  Google is the next best place to go when you can't find what you need on this site.

Best of Luck,
Nick Meyer

---

### Post by MJSOnline on 2006-01-15
> **npmeyer]Hey,

You probably won't want to install Azureus onto that second hard drive that we just got up and running said:**
> http://www.paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/[/URL]: it's pretty far down the page under the heading "Installing an Application."  You might have to either change a few lines of his instructions, since yours is on CD-R, or download Azureus again.

7-Zip, as far as I know, is only a Windows application, but you can extract *.7z files on Linux as well, though I've never done it, so I can't say exactly how to do that.  A good place to start would be searching these forums or Google for "7-Zip Ubuntu" or something similar.  Google is the next best place to go when you can't find what you need on this site.

Best of Luck,
Nick Meyer

Cheers Nick.

I understand.

No problem, will do.

Thanks again.

Regards
Matthew Staffa (AKA MJSOnline)

---

