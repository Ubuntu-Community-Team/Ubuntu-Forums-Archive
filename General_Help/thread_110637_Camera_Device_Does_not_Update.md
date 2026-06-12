---
title: "Camera Device Does not Update"
date: 2005-12-31
forum: General Help
---

### Post by noeluylee on 2005-12-31
Hi, I plugged in my Digital Camera "Canon Powershot SD300/ IXUS 40" and my Kubuntu can detect the digicam and was able to view the pictures, however when I take out the camera and took another picture/ shot, and put it back to retrieve the pictures from camera, it does not show up the new photo taken and the old picture as well. I have to do restart the computer before i can retieve the new picture taken. more or less I think it does not auto refresh.

Also, my Kubuntu does not detect my sd card reader. I am using Dell Inspiron 700m computer.....


Can you guys help me how to solve this problem...

---

### Post by coolclassic on 2005-12-31
Did you unmount before disconnecting the camera and close the window you were viewing the pictures.

---

### Post by noeluylee on 2005-12-31
how to unmount the camera? when I right click, I dont see any unmount options.

Thanks,

---

### Post by coolclassic on 2006-01-01
When right clicking on the camera icon the option is "remove safely"

---

### Post by noeluylee on 2006-01-02
"When right clicking on the camera icon the option is "remove safely""

- when I click the Camera Icon on my desktop I dont see "remove safely" option. I can only see Open | Copy | Properties. When I lcikc the icon, it showed me my camera model Canon Digital IXUS 40, when I right click, i can only see, Open New Windows, Open New Tab, Cut, Copy, Delete, Priview In, Compress, Copy to, properties.

Any suggestions?

Ty.

---

### Post by noeluylee on 2006-01-03
any workaround here? :)

---

### Post by xmastree on 2006-01-03
Try running ```
sudo /etc/init.d/hotplug reatart
``` When it's misbehaving. That might fix it faster than rebooting.

---

### Post by noeluylee on 2006-01-03
the command restarts the hotplug subsystems, but still it didnt update the content of my camera. 

Where can I find the unmount option on my camera? I couldnt find it.

Also my sdcard reader is not detecting my sccard when inserted. I am using Dell Inspiron 700m. I tried inserting the sdcard of my camera, but no avail. 

Hope you could help. ty

---

### Post by coolclassic on 2006-01-03
There might be an answer to your problems in this thread:

[http://ubuntuforums.org/showthread.php?t=77141&highlight=mounting](http://ubuntuforums.org/showthread.php?t=77141&highlight=mounting)

Some people have been having issues with auto mount ans installing the software sudjested in above thread has solved the problem.

---

### Post by noeluylee on 2006-01-08
The thread does not help my problem :( the problem become worts..

I tried to plug in my digicam in ubuntu/ gnome, (same computer) and it worked. the program for the cemera open. but in my kubuntu/ KDE 3.5, when i plug my camera, nothings happen. i check my /media, it was not there!! but i can see icon of the camera in KControl > Peripheral > Camera. any help will be highly appreciated. :)

---

### Post by coolclassic on 2006-01-09
Are you using the same kernel to boot ubuntu and kubuntu?

---

### Post by noeluylee on 2006-01-09
Yes... I am using 2.6.12-10-386. I just logout and login to ubutun / gnome. 

i tried fdisk -l   i got nothing :(

Any workaround?

---

### Post by fsanders on 2006-01-11
Have you tried installing digikam?  I had similar problems with my Canon Powershot A620, but everything worked perfectly using digikam.

---

