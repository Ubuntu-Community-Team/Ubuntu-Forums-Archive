---
title: "Mounting iPod Touch to Ubuntu 10.10 (dell n5010)"
date: 2010-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nightlock on 2010-12-27
Hello, whenever I plug the ipod sync chord into my computer (with my itouch 2g with software 4.2.1 on the other end), I get an error message about not being able to mount. A screenshot of the error message is attached.

---

### Post by rodrigoart on 2010-12-29
i got the same error, 

in 10.04 i used the ipod whit out problems.

now i got the error

"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"

i hope someone has solved this.

I will still serch a solution.

Regards.

---

### Post by michaert on 2010-12-29
Close the error message and open a terminal and type (without quotes):


"idevicepair unpair" hit enter then type:

"idevicepair pair" hit enter then type:

"idevicepair validate" and hit enter.

If your device doesn't automatically open, open the "System" menu and select your device.

Please note you must have libimobiledevice 1.0.4

Hope this helped :p

---

### Post by rodrigoart on 2010-12-29
i have not installed libimobiledevice

so, i think new gnome has native support for ipods and iphones. I really need to install this soft????

---

### Post by rodrigoart on 2010-12-29
sorry i think i have not installed this library because 

the comands you gave me, don t work.

coman line says me "idevicepair: orden no encontrada" in english command not found....

Thanks for your help, i will serch more abot this library.

---

### Post by michaert on 2010-12-29
@rodrigoart: libimobiledevice is the library/framework that Gnome uses to mount/connect with iPhones and iPod touches, along with ifuse and gvfs.

You already have these libraries, it's just Ubuntu hasn't updated the repo. To update the required libraries, do this:


Open a terminal and type (without the quotes):

"sudo add-apt-repository ppa:pmcenery/ppa" Hit enter and then type:

"sudo apt-get update"


If it asks you to update any packages, type "y" and hit enter. If it doesn't, try opening "Package Manager" and hitting "check". After all of that, restart your computer and plug in your device. You might still get an error message but thats OK. Try my previous post again. 

Hope it works for you.

---

### Post by Iislsdum on 2010-12-31
Actually, 'apt-get update' only updates the information about the packages, and to update the packages themselves, as the update manager GUI would do, you must run 'apt-get upgrade'.  Other than that, thank you for the help!

---

### Post by Iislsdum on 2010-12-31
Actually, 'apt-get update' only updates the information about the packages, and to update the packages themselves as the update manager GUI would do you must run 'apt-get upgrade'.  Other than that, thank you for the help!

---

### Post by rodrigoart on 2010-12-31
it works!!!

Thanks!!!

---

### Post by InvisibleEye on 2011-01-12
Thanks for the tip, it worked flawlessly (IPod touch 2G, 4.2.1).

---

### Post by JD32 on 2011-02-11
I still get the error??? :confused:

---

### Post by brclancy111 on 2011-04-11
Yes, in the newest version, you can get the utility, but there is no point.

It works for me just to upgrade. OF course, this is after I added the utils... so... idk lol

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=188794&stc=1&d=1302576193[/IMG]

---

