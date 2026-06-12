---
title: "NEW HELP.. installing nvidia drivers.."
date: 2005-07-13
forum: Desktop Environments
---

### Post by Boggles3 on 2005-07-13
First of all im new to Ubuntu and for that matter linux..
but i needed to make the switch sometime and this summer is that time.
Im a graphics student living in washington state  US.
i got the nvidia-gfx stuff working but i need to be able to use the card to its fullest..
ive got a quadro 1300 .
i went and downloaded the driver for it but i am running in to probles seems how im learning..
id:3:initdefault and that apperently takes away xserver wich from what i have gathered so far is the gui or has some strong connection to the gui...
anyways..
point being im looking in this directory but i cant find

in the read me it wants me to  shut down xserver before i install.. but i dont know how.. i went hunting for how to do this and i came across something about changing the file inittab. opening it and changing the line to id:3:initdefault and that apperently takes away xserver wich from what i have gathered so far is the gui or has some strong connection to the gui...
anyways..
point being im looking in this directory but i cant find this inittab file to change.

they also mentiond that many distributions have shortcuts to edit the runlevel.
are there shortcuts for this in ubuntu. and if not where do i find this file or what is its name in ubuntu...

or am i going about this horrably and making it to confusing.. 

please forgive the ignorance but u gatta start somewhere..
thanx ](*,)

---

### Post by yage on 2005-07-13
To shut down graphics press Ctrl+Alt+F1 to go to console. Login and 
**sudo /etc/init.d/gdm stop**
This stops the graphics....
**sudo updatedb**
This updates the internall database.
**sudo locate "filename or directory"**
This locates the dir you are looking for.

To start the graphics again
**sudo /etc/init.d/gdm start**

Hope this helps  :grin:

---

### Post by Boggles3 on 2005-07-13
ok this helped a bit but im still having problems..
i go into console and stop gnome..
i did the update thing.. i enter the file i want.. but when i run the driver command i get a little blinking curser in the middle of the black console screen..
it ses right befor that that its inpacking the driver file stuff.. but then i get no text.. no anything..
when i press enter it routs me back to console with my user name and the extention i was in like nothing .. happend.

any body have any suggestions this is what im doing..

in console-
sudo /etc/init.d/gdm stop
sudo updateb
cd /home/boggles3(my username)/Desktop/driver(yes i created a folder and put the driver file in it)
sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run(the driver install file)

but then it goes to this black screen with marker i spoke about above..

thanx

---

### Post by Boggles3 on 2005-07-13
ok i tried running it in the root console to see if i get anything different out of that.
i know it wont work because gnome is still running.. i also would like to know if gnome is xserver or an xserver so that i know that when i shut down gnome that i am in fact shutting xserver down..

anyways i tried on root and got this msg

 An NVIDIA kernel module 'nvidia' appears to already be loaded in your
         kernel.  This may be because it is in use (for example, by the X
         server), but may also happen if your kernel was configured without
         support for module unloading.  Please be sure you have exited X
         before attempting to upgrade your driver.  If you have exited X, know
         that your kernel supports module unloading, and still receive this
         message, then an error may have occured that has corrupted the NVIDIA
         kernel module's usage count; the simplest remedy is to reboot your
         computer.
at first i thought that this is the message that i was sapposed to be getting when i was running in consol and i had a marker blinging..
but i dont think it can be the same error can it .. cuz im shutting down xsrever.. or am i only shutting gnome and nvidia xserver is still running or something??

im going to try rebooting and logging in under the console so that nvidia xserver doesnt get a chance to run and hopefully that will work for me..

i will be back shortly if it doesnt lol ](*,)

---

### Post by Boggles3 on 2005-07-13
ok i started in console this time and i atleast got an error instead of a black screen with a marker..

i tried to run the  driver from console and i got the an error saying it must be run as root...?

does this mean run it from root console... 
but i thought you couldnt run from root without gnome running..

any help is appritated thanx :-)

---

