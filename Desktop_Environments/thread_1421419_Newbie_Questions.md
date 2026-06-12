---
title: "Newbie Questions"
date: 2010-03-04
forum: Desktop Environments
---

### Post by anon_private on 2010-03-04
Hi,
 
I have ordered a free UBUNTU CD for desktop.
 
I have some questions.
 
Can UBUNTU be run from the CD, or must it be installed?
 
Can the CD be updated on-line?
 
I realy want a copy that is portable. Have I ordered the right CD?
 
If it runs from the CD, I assume that I will need to boot from this CD.
 
Can it be run while Windows is running?
 
Thanks
 
PS. I like to run UBUBTU (and other securtiy software) in libraries to avoid loggers etc that can occur under Windows. Is this feasible (UK resident).

---

### Post by cherva on 2010-03-04
Yes you can boot ubuntu from the CD without any change to your system and you can update, BUT you will lose anything when you restart... If you want to save your changes make a bootlabe USB stick [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/")

You can't run it in windows like normal... you will have to make a virutual machine (you will need VirtualBox for that it is free or the proprietary vmware)

---

### Post by anon_private on 2010-03-04
Thanks for the very fast response.
 
What happens if I boot from the CD, assuming that I am currently running Vista?
 
Could this OS be used in a public library?
 
PS. Is this CD what is commonly referred to as a 'Live CD'. If not, what is the difference between this UBUNTU CD and a Live CD. 
 
Thanks
 
'You can't run it in windows like normal... you will have to make a virutual machine (you will need VirtualBox for that it is free or the proprietary vmware)'
 
What will happen to the Vista OS?

---

### Post by cherva on 2010-03-04
If you boot from the CD it will load ubuntu and you will be able to use it as normal you will be able to see you hard drive files and manipulate them and as soon as you remove the cd Vista will boot and nothing will be changed. I don't know if they will allow you to boot in a public library because after you boot you will be able to do anything on the computers hard drive.

There are two types of linux CDs:
- Live CD - you can boot from it and use the OS without installing and you can isntall it if you want.
- Alternate CD - you can only install the OS from this CD.

VirtualBox is a program that emulates a PC. You can give the virtual PC part of your RAM and make a file which acts as a hard drive or use an existing partition... It's nice to test different OSs and play with them without the need to wait for them to install ( you can minimize the window and do something else)

---

### Post by nothingspecial on 2010-03-04
Maybe you should take a look at [[COLOR="Magenta"]puppy linux[/COLOR]]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm") which is designed to be run from a cd or (even better in my opinion) a usb stick and transportable between different pcs

---

### Post by anon_private on 2010-03-04
The Live CD seems to be best for my purposes.
 
I asked for the free CD to be sent to me. Will I receive the Live CD version?
 
I will read the puppy version as well.
 
My interest in Linux is due to the fact that I may need to occasionally access an on-line bank using publically available pc's. I believe that Linux is more secure that Windows. Other security software will also be used. I don't much like the idea, but, needs must.
 
Thanks
 
PS. Bank does use https. I need to guard against loggers, etc., hence the security software.

---

### Post by medicalystoned on 2010-03-04
puppy linux rocks... it is my second favorite Linux os....you may want to give xubuntu a try to also... i think it is a little lighterweight  than ubuntu.... but then again, i am a perpetual noob...anyway, have fun with Linux...peace

---

### Post by ndefontenay on 2010-03-04
Hi.

Considering linux for security is very right :)

I have to warn you however that some banks use microsoft only technologies to access bank account online.

I live in Thailand and that for instance is a no no for me. All banks says it "works best wit IE" (read: we have been too lazy to make a portable version of our web site) and "IE is better for security" (now that one makes me laugh. read: lets give him a lot of ******** as a reason).

You will be able to run a session of firefox from a live CD. Be prepared for a longer boot time (CD are slower than HD) and usage of the PC generally. If speed is not an issue then it's going to be ok. As soon as firefox is open, then the speed you get is only from the internet connection. 

Public PCs if done properly will have a protected BIOS which means you might not be able to change the boot order to boot from your CD. So it's a high chance you can't do much with your CD.

Good luck anyway.

Nico

---

### Post by ssulaco on 2010-03-04
> **anon_private said:**
> Hi,
 
I have ordered a free UBUNTU CD for desktop.
 
I have some questions.
 
Can UBUNTU be run from the CD, or must it be installed? **[COLOR="MediumTurquoise"]Yes,can be run from the CD,Live[/COLOR]**
 
Can the CD be updated on-line?**[COLOR="MediumTurquoise"]The CD itself cannot be updated online[/COLOR]**
 
I realy want a copy that is portable. Have I ordered the right CD?**[COLOR="MediumTurquoise"]Yes[/COLOR]**
 
If it runs from the CD, I assume that I will need to boot from this CD.**[COLOR="MediumTurquoise"]Yes,I always keep my bios set to boot from the CD first[/COLOR]**
 
Can it be run while Windows is running?**[COLOR="MediumTurquoise"]No[/COLOR]**
 
Thanks
 
PS. I like to run UBUBTU (and other securtiy software) in libraries to avoid loggers etc that can occur under Windows. Is this feasible (UK resident).
Also you have the option to Wubi install,installing Ubuntu within Windows without partitioning.......
[https://help.ubuntu.com/community/LiveCD#How-To%20LiveCD%20Ubuntu](https://help.ubuntu.com/community/LiveCD#How-To%20LiveCD%20Ubuntu)
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
[http://www.desktoplinux.com/articles/AT8963693541.html](http://www.desktoplinux.com/articles/AT8963693541.html)

---

### Post by anon_private on 2010-03-05
Thanks to all for responsing.
 
A few points.
 
Will I receive the Live CD free version by post? It is ordered, but I am not sure of the version, ie, type.
 
ssulaco implies that the CD is the Live version, If I have understood correctly
 
If ndef... is right and I can't change the boot order on a public pc, then what can I do to enhance my security when I am forced by circumstances to use a public pc for some banking?
 
Thanks

---

### Post by ssulaco on 2010-03-05
> **anon_private said:**
> then what can I do to enhance my security when I am forced by circumstances to use a public pc for some banking?

See if this fits your needs...
[http://kyps.net/home/index?lang=en](http://kyps.net/home/index?lang=en)

---

### Post by anon_private on 2010-03-05
Since I would like to run UBUNTU on a public pc would it be best to run it under Windows?
 
If yes, would I be safer when using online banking, or would I be just as vulnerble because Windows is running? I may be using additional security software (if it runs under UBUNTU), eg, to hide passwords.
 
Thanks

---

