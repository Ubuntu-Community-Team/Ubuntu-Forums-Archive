---
title: "How do I uninstall Windows 7?"
date: 2012-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Adeadlymermaid on 2012-06-23
Sorry if this is the wrong thread. Let me know and I will delete and change it. 

Ok so when I got my little netbook, I had Windows 7 Starter as the operating system, which is a very generic form of windows. So after I got really tired of Windows I searched for a new operating system and found the very lovely Ubuntu that I love! 

My question is how do I uninstall Windows? I imagine having 2 operating systems is hard on my little netbook, but I could be wrong.

---

### Post by JRV on 2012-06-23
It is not hurting anything being there, it just uses up disk space.

All you need to do is use gparted to delete the Windows 7 partition and create another EXT4 partition you can use with Ubuntu. 
Then run the command:```
sudo update-grub
```to remove Windows from the grub startup menu.

---

### Post by Adeadlymermaid on 2012-06-23
Although my confidence has gone up since I downloaded this and makes me feel more technologically more knowledgeable, however I don't really understand anything you just wrote.... sorry...:(

---

### Post by blackflame2996 on 2012-06-24
If you want to make Ubuntu your sole OS, just select the use entire disk option in the Ubuntu installer.

---

### Post by Shadius on 2012-06-24
> **blackflame2996 said:**
> If you want to make Ubuntu your sole OS, just select the use entire disk option in the Ubuntu installer.

But I'm guessing you already have Ubuntu installed and is dual-booting Windows & Ubuntu?

---

### Post by Adeadlymermaid on 2012-06-24
> **Shadius said:**
> But I'm guessing you already have Ubuntu installed and is dual-booting Windows & Ubuntu?
  
Yes haha I was so eager to install it I didn't select that option, nor did I even see that option....

---

### Post by Shadius on 2012-06-25
> **Adeadlymermaid said:**
> Yes haha I was so eager to install it I didn't select that option, nor did I even see that option....

You have a few options:

[LIST]Use [GParted]("http://gparted.sourceforge.net/") to delete the Windows partition. I think you'll be left with unallocated space after the deletion of Windows. Then, if you want to allocate the unallocated space to Ubuntu, format the now unallocated space to EXT4 filesystem and extend the existing Ubuntu partition into the unallocated space. All of this is done using GParted, I think (I'm a little rusty with GParted). Also, if Windows & Ubuntu are both on the same hard disk drive, you'll have to create a LiveCD and boot into it to use GParted because the hard disk drives can't be mounted. Hope that makes sense.[/LIST]
[LIST]Reinstall Ubuntu with the option to have the Ubuntu installer delete Windows and take over the entire disk. If I remember correctly, the option is "**Use Entire Disk**". [COLOR="Red"]Keep in mind that this will delete all your data from your current Ubuntu and Windows systems so if you have data you want to keep, do a backup.[/COLOR] [/LIST]

I think that covers everything. To get a better understanding of your setup, you can use the GParted that's already installed within Ubuntu and give us a screenshot of the hard disk drives. 
[LIST]If you're using the Unity interface, just open up *Dash* and type in *GParted*. Hit the Print Screen button to take a screenshot and attach it here.[/LIST]
[LIST]If you're using GNOME Classic, you'll find GParted from the *Applications* menu, then *System Tools*, then *Administration*, then *GParted Partition Editor*. Hit the Print Screen button to take the screenshot.[/LIST]
[LIST]Another way, is to do the following code in Terminal:[/LIST]
```
sudo fdisk -l
```

Hope I was clear!

---

### Post by Adeadlymermaid on 2012-06-25
> **Shadius said:**
> You have a few options:

[LIST]
[*]Use [GParted]("http://gparted.sourceforge.net/") to delete the Windows partition. I think you'll be left with unallocated space after the deletion of Windows. Then, if you want to allocate the unallocated space to Ubuntu, format the now unallocated space to EXT4 filesystem and extend the existing Ubuntu partition into the unallocated space. All of this is done using GParted, I think (I'm a little rusty with GParted). Also, if Windows & Ubuntu are both on the same hard disk drive, you'll have to create a LiveCD and boot into it to use GParted because the hard disk drives can't be mounted. Hope that makes sense.
[/LIST]

[LIST]
[*]Reinstall Ubuntu with the option to have the Ubuntu installer delete Windows and take over the entire disk. If I remember correctly, the option is "**Use Entire Disk**". [COLOR=Red]Keep in mind that this will delete all your data from your current Ubuntu and Windows systems so if you have data you want to keep, do a backup.[/COLOR]
[/LIST]

I think that covers everything. To get a better understanding of your setup, you can use the GParted that's already installed within Ubuntu and give us a screenshot of the hard disk drives. 
[LIST]
[*]If you're using the Unity interface, just open up *Dash* and type in *GParted*. Hit the Print Screen button to take a screenshot and attach it here.
[/LIST]

[LIST]
[*]If you're using GNOME Classic, you'll find GParted from the *Applications* menu, then *System Tools*, then *Administration*, then *GParted Partition Editor*. Hit the Print Screen button to take the screenshot.
[/LIST]

[LIST]
[*]Another way, is to do the following code in Terminal:
[/LIST]
```
sudo fdisk -l
```Hope I was clear!

Ok so I unistalled and reinstalled Ubuntu, and it never gave me the option of "Use Entire Disk" which is really inconveniant.

Then I tried to look for gparted and apparently I do not have it, and I searched for it through the dash. Help please!

---

### Post by Shadius on 2012-06-25
> **Adeadlymermaid said:**
> Ok so I unistalled and reinstalled Ubuntu, and it never gave me the option of "Use Entire Disk" which is really inconveniant.

Then I tried to look for gparted and apparently I do not have it, and I searched for it through the dash. Help please!

You said you've uninstalled Ubuntu? How did you do this? This suggests that you're Ubuntu installation was a WUBI installation, which is basically installing Ubuntu within Windows like it was a program. Please describe the steps you used.

---

### Post by nipunshakya on 2012-06-25
see the following link below:
[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml) to help you out with what u did with your installation...
gparted is a software available at the 'Software Center' , just search for 'gparted' in the search box and you are good to go... Goodluck

---

### Post by Adeadlymermaid on 2012-06-25
> **Shadius said:**
> You said you've uninstalled Ubuntu? How did you do this? This suggests that you're Ubuntu installation was a WUBI installation, which is basically installing Ubuntu within Windows like it was a program. Please describe the steps you used.
   
well i dont think it was because when i start up my netbook, it asks me if i want to use ubuntu or windows.  But when i went onto windows and searched Ubuntu i found t in my hard drive, but when i go onto ubuntu i cant find windows.....

---

### Post by Shadius on 2012-06-25
> **Adeadlymermaid said:**
> well i dont think it was because when i start up my netbook, it asks me if i want to use ubuntu or windows.  But when i went onto windows and searched Ubuntu i found t in my hard drive, but when i go onto ubuntu i cant find windows.....

If you go into Control Panel on Windows, do you see an entry for Ubuntu? Also, how did you reinstall Ubuntu? From a LiveCD or LiveUSB?

---

### Post by Adeadlymermaid on 2012-06-25
> **Shadius said:**
> If you go into Control Panel on Windows, do you see an entry for Ubuntu? Also, how did you reinstall Ubuntu? From a LiveCD or LiveUSB?

I just used the top download you see on this page [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by nipunshakya on 2012-06-25
Hello...if you are using wubi, please remember that wubi is not for total control of your machine as single boot.. in this case, if you remove windows, u remove ubuntu as well..

---

### Post by Adeadlymermaid on 2012-06-25
> **WinuxUser said:**
> Hello...if you are using wubi, please remember that wubi is not for total control of your machine as single boot.. in this case, if you remove windows, u remove ubuntu as well..

Great.... well how do I install it so it is in total control of my pc?

---

### Post by nipunshakya on 2012-06-25
If you want only ubuntu 12.04, or ubuntu and windows as dual boot,  then you must first have to download an iso for ubuntu from the following link:
[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)
Under the bit torrent section, select amd64-desktop(for 64 bit) and i386-desktop(32-bit) and download it... Burn it to a cd and run it in live mode first to check that your download is correct... after that you can try to remove windows and have only ubuntu....

**remember to boot to live mode, when u see the keyboard and human logos at bottom of the screen, press any key, select your language, and then select 'check drive for errors'** **to ensure your live cd has no errors. after that, you can run it once as a  livecd by selecting 'try ubuntu' to see if it is working on your machine. later, you can select to 'install ubuntu'(but thats the later part)**

Be sure to complete the task first and let us know.. we will be here..

---

### Post by Adeadlymermaid on 2012-06-25
Well I'm doing this on my little netbook, so it doesn't have a cd drive. Could I do this on a USB?

---

### Post by nipunshakya on 2012-06-25
surely it can be on a USB. After you download the iso file, see the following link:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) if you want to make a bootable USB using windows and [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu) if u wanna do it ubuntu's way.

---

### Post by Adeadlymermaid on 2012-06-25
> **WinuxUser said:**
> surely it can be on a USB. After you download the iso file, see the following link:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) if you want to make a bootable USB using windows and [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu) if u wanna do it ubuntu's way.


Ok great so where do I go after I put the file on my usb?

---

### Post by nipunshakya on 2012-06-25
did u make the usb bootable? did u follow any of the links given above or just copied the downloaded iso file to the USB...remember, that **just copying the iso file wont make it bootable one... **

---

### Post by Adeadlymermaid on 2012-06-25
> **WinuxUser said:**
> did u make the usb bootable? did u follow any of the links given above or just copied the downloaded iso file to the USB...remember, that **just copying the iso file wont make it bootable one... **

Well I downloaded the Universal USB Installer, and it only allows me to install one of the iso files, and then I looked and it didn't give me the option to make it bootable.  I followed all of the instructions as well.

And since I have a little netbook should I download the Desktop or the alternate i386? I suppose there is a difference.

---

### Post by nipunshakya on 2012-06-25
the iso you selected is the option for letting you make it bootable... it does that for you by itself...
Now that your bootable pendrive is ready, follow my post #16 and follow the bolded texts carefully.... let us know what happens then....
Goodluck

---

### Post by Adeadlymermaid on 2012-06-25
> **WinuxUser said:**
> the iso you selected is the option for letting you make it bootable... it does that for you by itself...
Now that your bootable pendrive is ready, follow my post #16 and follow the bolded texts carefully.... let us know what happens then....
Goodluck

Thank you, I'm realizing now that this is going to be a lot more complicated then I thought it was going to be, but atleast I'm learning haha. Thank you for your patience! I'll be sure to post back if it doesn't work.

---

### Post by nipunshakya on 2012-06-25
now assuming that you have clearly followed post # 16, here is a link that will well instruct you on how to completely use ubuntu 12.04 as the only OS in your machine and install it:
[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)

Goodluck

---

### Post by Adeadlymermaid on 2012-06-25
> **WinuxUser said:**
> now assuming that you have clearly followed post # 16, here is a link that will well instruct you on how to completely use ubuntu 12.04 as the only OS in your machine and install it:
[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)

Goodluck

Well I tried following your instructions and it says that the file was corrupt and could not open. I'm trying to find something to make sure I downloaded the right file for this netbook. Anywhere I can find that and make sure?

---

### Post by Adeadlymermaid on 2012-06-25
Success! I officially ONLY have Ubuntu as my operating system. lol Thankyou everyone!:KS:guitar::KS

---

### Post by nipunshakya on 2012-06-25
Whoa!! you said wubi??? and now only ubuntu?? how?? if the file was corrupt, you could have tried to download another iso file too... but i'd like to know what worked ..... 

And its good to know that your machine is up and running now...

Btw,please mark the thread as [SOLVED] by selecting 'Mark thread as solved' from the drop down on the top right marked as 'Thread Tools' on this very page...

Goodluck

---

### Post by Shadius on 2012-06-25
> **WinuxUser said:**
> Whoa!! you said wubi??? and now only ubuntu?? how?? if the file was corrupt, you could have tried to download another iso file too... but i'd like to know what worked ..... 

And its good to know that your machine is up and running now...

Btw,please mark the thread as [SOLVED] by selecting 'Mark thread as solved' from the drop down on the top right marked as 'Thread Tools' on this very page...

Goodluck

I'm confused. You used the Windows installer (WUBI) again to install Ubuntu and now Ubuntu is your sole operating system? :confused:

---

### Post by nipunshakya on 2012-06-25
> **Shadius said:**
> I'm confused. You used the Windows installer (WUBI) again to install Ubuntu and now Ubuntu is your sole operating system? :confused:
Thats my sole question to the OP... i lost track of her last night as i went to sleep after i suggested her how to install only ubuntu..... she said her downloaded file got corrupt... then re downloaded... but i guess she got confused.. it wasn't wubi.. she might have misanalysed it ... im confused here too...
lets wait for her to answer..

---

### Post by Shadius on 2012-06-25
> **WinuxUser said:**
> Thats my sole question to the OP... i lost track of her last night as i went to sleep after i suggested her how to install only ubuntu..... she said her downloaded file got corrupt... then re downloaded... but i guess she got confused.. it wasn't wubi.. she might have misanalysed it ... im confused here too...
lets wait for her to answer..

Yeah, I was getting a bit confused from when she said the uninstalled Ubuntu. That's why it occured to me her initial install might've been a WUBI installation. Was it confirmed that the initial installation was in fact a WUBI installation? Thanks for helping her out also.

---

### Post by nipunshakya on 2012-06-25
Yeah the initial installation was a wubi one..
 its probable that she downloaded the iso from torrent i suggested... but she might have been confused with the wubi thing still... so maybe we can wait for her to respond on what she did because she reported that the downloaded iso was corrupt and had to download again... but i assume she downloaded from the same site as well...
lets wait for her to respond now.. a little bit of confusion still persists...

---

### Post by Shadius on 2012-06-25
> **WinuxUser said:**
> Yeah the initial installation was a wubi one..
 its probable that she downloaded the iso from torrent i suggested... but she might have been confused with the wubi thing still... so maybe we can wait for her to respond on what she did because she reported that the downloaded iso was corrupt and had to download again... but i assume she downloaded from the same site as well...
lets wait for her to respond now.. a little bit of confusion still persists...

:lolflag: Yeah, a little bit of confusion remains. Let's wait and see...

---

