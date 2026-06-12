---
title: "Install on a Dell Poweredge 2400"
date: 2007-06-08
forum: Dell  Ubuntu Support
---

### Post by Danny159 on 2007-06-08
Hay!

I have downloaded 'ubuntu-7.04-server-i386' and when I put it into my server it doesn’t boot from the DC to install... even if I set it it... help please!
Also I have no current operation system to boot it for me...
So what im asking is how can I boot from CD..
Help please as I am new to servers lol :D
Thanks
Danny :popcorn:

---

### Post by ScottLij on 2007-06-08
You need to enter the BIOS and change the boot order so that it checks the CD-ROM first.

---

### Post by Danny159 on 2007-06-08
I have done but still not working

---

### Post by carlosfocker on 2007-06-08
Possibly a bad burn.  You might re burn the CD or download the image again.

---

### Post by Danny159 on 2007-06-09
What do i download as theres loads of options...

---

### Post by carlosfocker on 2007-06-09
When you say download are you talking about the area of the install where you choose what packages to install? If so, what type of server are you trying to stand up?

---

### Post by Danny159 on 2007-06-10
Yeah it is, and im looking to set-up a web server :D

---

### Post by steglasi on 2007-06-10
Hi,

I too have a PowerEdge 2400 and have managed to get it to boot off the CDROM itself.  I did this by putting in the bootable CD, then going into the SCSISelect utility for the SCSI Adapter that the CDROM is connected to (press CTRL-A when you see the 2nd SCSI BIOS message - AIC-7880 I think).  Then you have to set the boot SCSI ID to the ID of your CDROM.  The option is under "Configure/View Host Adapter Settings" and the name of the option is "Boot Device Options".  The ID of my CDROM was SCSI ID 3.

Hope that helps!

Anyway, I have another problem related to the PowerEdge 2400.  I've gotten the CD to boot, but it tries to look for the initrd image (I think) on /dev/fd0.  Since this is a floppy, it doesn't work, and dumps me to a BusyBox command prompt.  Any ideas on how to get it working past this point?  Should I try manually setting the location of the image?

Scotty

---

### Post by carlosfocker on 2007-06-11
If your setting up a web server you really only need to install apache (plus the other packages selected by default).  If you want to go the easy route, choose the Install LAMP server option at the boot menu.  This will set you up with a working Linux(Server OS), Apache(Web Server) , MYSQL(Database), PHP(HTML Scripting Language ) server that you can install most open source Web application software.

---

### Post by Danny159 on 2007-06-14
[COLOR="Red"]**_SEE NEXT PAGE_**[/COLOR]

---

### Post by Danny159 on 2007-06-16
Okey i have installed it..
now im having trubble with loggin in...
Ok when the server starts it dose its stuff then in gose too login username (in text mode)
so i put my username in then i put in my password and press enter!

then i get the screen "last  loggedin: ......"
....
....
....

And now i have 
daniel@ubuntu:&#732;$ 

but i dont know what to put there...

when i put in 'ROOT it says 
-bash: root: command not founed

Help please
Daniel:D

---

### Post by Danny159 on 2007-06-17
anyone know?

---

### Post by Jose Catre-Vandis on 2007-06-17
Ok, your machine has booted up to the command prompt. if you chose the LAMP server install then all your server requirements should be in place, but will need configuring for your needs.

You can test your server (apache) install from another machine if you are networked, just type 
```
 http://IPOFYOURSERVER
```
and you should get the standard apache starter page

If you need to check your network connectivity on the server, type
```
ifconfig
```
to see what your settings are like

There is no GUI installed in server mode.

What do you want to do next?

---

### Post by Danny159 on 2007-06-17
I dont have the server networked yet as this is my first server and i want to get it set-up first..

i just want to be able to login to then image version and see how too use it first...

so can you help?

---

### Post by NeoGreen on 2007-06-17
You should have setu a username and password when you first installed.  If you are going to configure you can look here to configure your Ubuntu LAMP install  [http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html]("http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html")  I have just installed it on my server and have it running on my network.

---

### Post by Danny159 on 2007-06-20
Ok, i will try this and then report back too you :KS

---

### Post by pete123456 on 2007-10-15
> **steglasi said:**
> Hi,

I too have a PowerEdge 2400 and have managed to get it to boot off the CDROM itself.  I did this by putting in the bootable CD, then going into the SCSISelect utility for the SCSI Adapter that the CDROM is connected to (press CTRL-A when you see the 2nd SCSI BIOS message - AIC-7880 I think).  Then you have to set the boot SCSI ID to the ID of your CDROM.  The option is under "Configure/View Host Adapter Settings" and the name of the option is "Boot Device Options".  The ID of my CDROM was SCSI ID 3.

Hope that helps!

>>>Anyway, I have another problem related to the PowerEdge >>>2400.  I've gotten the CD to boot, but it tries to look for the >>>initrd image (I think) on /dev/fd0.  Since this is a floppy, it >>>doesn't work, and dumps me to a BusyBox command prompt.  >>>Any ideas on how to get it working past this point?  Should I try >>>manually setting the location of the image?

Scotty

I have exactley the same problem installing ubantu 7 desktop on my poweredge 2400, once booted from intall cd i select the install option, then i get the ubantu loading progess bar/screen, whilst this is happening my floppy drive trys to read making noises then after about 12 read attempts the installer exits out into a busy box screen.

---

### Post by survient on 2007-12-22
I keep getting SCSI hang errors after I've installed it, and now I can't get it to boot from the CD, it doesn't even try. It says it finds a bootable CD, but it doesn't try to boot from the CD.

---

