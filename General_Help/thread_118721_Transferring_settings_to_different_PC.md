---
title: "Transferring settings to different PC"
date: 2006-01-17
forum: General Help
---

### Post by zachariah on 2006-01-17
So, we have our perfectly configured Linux box ready to roll out to an unsuspecting user base. Trouble is, there's only one of it and lots of them.

There are a few identical PCs lying about, however. Is there a way to transfer the settings of the working box to the others? Like installing Kubuntu on them via CD then copying the /etc/ folder over?

The things that need to be replicated are non-default software (eg StarOffice, Scribus) and network settings, including custom PAM, SAMBA and Kerberos settings for Windows domain login. Ideally I'd just ghost the whole thing over and change the host name manually but that solution strikes me as lacking elegance - and requires me to be by the new PC, which may not be possible. Any ideas? Does this sound even remotely feasible?

---

### Post by otisraccoon on 2006-01-17
the way i would do it would be to install Kubuntu on the other machine

then get them on a network so they can talk to eachother

on the new install machine type ssh [ip number of other machine]

then after you enter the root password for that machine, that terminal  is now a terminal on the other machine.  open another terminal, and copy over what you want.  Make sure if you did any updates on the first kubuntu, that you make those updates on the 2nd machine and so on before you start transferring settings to be safe

another way could be doing a full backup on the other disk, but ive never done that with anything other than nortons ghost.

---

### Post by zachariah on 2006-01-18
Thanks, this is probably what I will do at first. However, there may come a time when we need to install Ubuntu on lots and lots of PCs in a short time. Is there an equivalent to MS RIS server (a TFTP server) that will run a remote install?

Or an equivalent to MS OEM Preinstallation kit that will 're-seal' a Linux install so that it will do a first boot, asking for root password, hostname again?

Thanks

---

### Post by feathers on 2006-01-18
I don't know if it works for Kubuntu, but it does for Debian: You can use fai (fully automatic install) to install Debian. I have never taken up the task to configure it. The other thing that may help is to get a list of all installed packages on your master machine with sudo dpkg --get-selections >> list. You get a text file, named "list" which contains all the packages. Then go to the other machine with a basic kubuntu or even just server install and type: sudo dpkg --set-selections < list. You must copy the file to this computer first of course. Then do: apt-get dselect-upgrade. All the packages will be installed. Then you can copy the required files from /etc/. You can even write a script that does that.

---

### Post by zachariah on 2006-01-19
Thanks, that sounds like what I'm after.

...Now I just need to work on my non-existent scripting skills...

---

### Post by linuxden on 2006-01-19
Zachariah,

There is a program called partimage which does exactly what you are after.... 

otherwise there is the trusted backup of the machine and restoring it on fresh ubuntu install on the other machines....( if the hardeware changes too much you might jhave to reconfigure xorg... but thats a piece of cake!!!

---

### Post by Derflection on 2006-03-08
[QUOTE=otisraccoon]the way i would do it would be to install Kubuntu on the other machine

then get them on a network so they can talk to eachother

on the new install machine type ssh [ip number of other machine]

then after you enter the root password for that machine, that terminal  is now a terminal on the other machine.  open another terminal, and copy over what you want.  Make sure if you did any updates on the first kubuntu, that you make those updates on the 2nd machine and so on before you start transferring settings to be safe

another way could be doing a full backup on the other disk, but ive never done that with anything other than nortons ghost.[/QUOTE]

Hi Everyone,
New to the forum and the world of linux so please be kind.  I am faced with a similar situation and am trying to troublshoot which is the best way to distribute a customized installation package containing some custom software (my companie's and a windows emulator), network settings and interface.  I have the exact build that I want running already.

I am faced with the task of upgrading about 25 computers all over the world with different hardware specs (nothing is exotic) with this distribution ( I need it to be exactly the same on all computers).  All of the computers are currently running windows 2000. 

The thing is I am dealing with users that have _very_ low level computer skills and I will be unable to visit any of these sites personally.  So i need something very simple that I can direct from the main office.   I orginially considered using a customized live cd because it simple enough for the users to install it ;) but there are some lag issues that I worry will affect our software.  

Am i searching for the impposible, or will the above soultion work for me as well? I am mainly worried about the different hardware configurations and user friendlyness.
thanks for helping a newbie.

---

### Post by hamsteri on 2006-03-09
I have been using [mondorescue]("http://mondorescue.org/") now for a while and it should fit your needs. 
You can also run it on a live filesystem which you can't do with partimage. 
Apt it down and test it ;)

<edit> In response to top post, haven't tested mondo with windowspartitions</edit>

---

### Post by jerrykenny on 2006-03-09
Zak, if the hardware is identical, can you take the new-clean-drive, plug it into a spare IDE socket, boot the old pc from the Ubuntu-install-CD, partiton the new drive and then use the option to "copy data from a different partition"  there is that option on every debian CD, but I've never tried it . . . . 

Alternately, boot into any live cd kubuntu kanotix, and make a mirror-backup of the configured hard drive, either to CDRW's or a plugged in HD, as above


Derflection, your best option might be to install Ubuntu Hoary, then Use the unofficial-addon-cd,  that was an excellent facility, and provided every bit of software anyone could ever want.

---

### Post by Derflection on 2006-03-14
Thanks for the information JerryKenny, I was unnaware that such a CD exists after checking it out it seems like a great idea for alot of the open source software out there, however I should have been more clear in my original post, my company runs a custom made software that can't really be duplicated.  Part of the reason I wanted to move to unbuntu is that everytime Microsoft updates we have to make costly alterations to the software that we are running. Plus I am still faced with the task of getting people who seem to have difficulty right clicking a mouse (the joys of tech support ;) ) to install an OS.

---

