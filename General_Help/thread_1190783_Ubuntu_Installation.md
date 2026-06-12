---
title: "Ubuntu Installation"
date: 2009-06-18
forum: General Help
---

### Post by ranjith.ts on 2009-06-18
Hi folks,,

I am very new to this ubuntu so i hope u people can help me..

I want to install ubuntu 9.04 in my HP laptop

i read about Wubi installer but i wanted to know whether once i install it,can i make a back up of it so that after i uninstall it i need not have to download the whole 2.5gb stuff again

i am also not sure whether burning the 9.04 amd desktop 64.iso file in a disc and if i install it to my system will i loose my vista os or is it going to install only in a specific folder and can i uninstall it later thru add/remove programs

also wanted to know whether the .iso image which i burn into a cd doesn that contain wubi utility or not

---

### Post by lisati on 2009-06-18
If you burn the iso file to disk (see [here]("https://help.ubuntu.com/community/BurningIsoHowto") for more information) you can insert the disk while Windows is running and use wubi straight from the disk. You can also boot (start) your computer from the CD and choose a "try Ubuntu without installing anything" option, which is useful for checking if Ubuntu will run on your computer.

Whether you use Wubi or install Ubuntu in its own partition, you don't have to overwrite Windows. It's still a good idea to make a backup of your important data - as much as we don't like to admit it, things can sometimes go wrong, and it would be a shame to lose your work.

---

### Post by ranjith.ts on 2009-06-18
Thanks for that quick reply and giving nice information..Thank u Lisati

i just had one doubt.. Does the iso which i will burn it into a disc,,,doesnt it contain wubi installer?


All i wan to know is i just want to install this OS like an application and would like to remove and re-install whenever  like
i don wan to run os thru disc i wan to install it along with vista wihtuout any requirement for partitions

and also when i try to download thru wubi stnad alone installer it downloads 9.04 desktop amd64.iso and when i go to ubuntu website it gives me 9.04 desktop i386.iso...are both the files are same.....My laptop is running on AMD processor

---

### Post by lisati on 2009-06-18
The "Live CD", also known as the "desktop" edition (available from [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)) comes with a copy of Wubi on it. If you put the CD in the drive while Windows is running, wubi will normally start automatically. 

The "wubi" method of installing, also known as "installing within Windows" doesn't normally need you to set up a separate partition - it uses a folder in the Windows C: drive. It has the added advantage that if you change your mind for some reason, you can uninstall a copy of Ubuntu installed this way using the normal Windows control panel->add/remove programs option.

When running wubi from CD it won't need to download lots and lots of stuff, it will look at what's on the CD first.

---

### Post by oldos2er on 2009-06-18
> **ranjith.ts said:**
>  when i try to download thru wubi stnad alone installer it downloads 9.04 desktop amd64.iso and when i go to ubuntu website it gives me 9.04 desktop i386.iso...are both the files are same.....My laptop is running on AMD processor

 Wubi checks your processor to see if it's 64-bit or 32-bit; if 64, it installs the 64-bit version of Ubuntu.

---

### Post by RJ12 on 2009-06-18
But when you get Wubi running stay away with hard resets otherwise ...

You will have to reinstall Windows

---

### Post by ranjith.ts on 2009-06-21
Hi guys,

thanks for all ur help
After downloading it,checked md5 and it wasnt the same and re-downloaded it
Burnt it on the disc now and did integrity check>>went fine
i download ubutnu 9.04 desktop amd64.iso
Hope i believe the installation thru disc shud be easy thru wubi.

Thank u people :)

---

### Post by ranjith.ts on 2009-06-21
Hi guys :D,,,

Installed ubuntu finally and also installed nvdia drivers and its working perfectly smooth..
thank u guys for all ur support,,,i am enjoying every thing in ubuntu....

---

