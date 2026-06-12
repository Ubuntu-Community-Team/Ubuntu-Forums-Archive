---
title: "Desktop dont open, returns to login screen"
date: 2013-03-12
forum: Desktop Environments
---

### Post by mandza on 2013-03-12
Hi,
i am using ubuntu 12.04LTS
i used it without any problem, but 1 week ago i just couldnt open my desktop.
when i select my user name i write password, i just return to same place dont open my desktop.
But when i select guest user i login with out any problem.
What problem can be and how can i fix this without re-installation?
Thanks a lot.

---

### Post by Toz on 2013-03-12
You might be suffering from the .Xauthority issue where your user doesn't have ownership of that file. Try going to the first tty (Ctrl+Alt+F1), logging into the text console and deleting that file like this:
```
rm .Xauthority
```
...then returning the graphical log-in screen (Ctrl+Alt+F7) and trying to log in again.

---

### Post by ibjsb4 on 2013-03-12
Check to be sure your on the right desktop at login.  When I upgraded to 12.04.01, it bumped be back to ubuntu-desktop which I do not have installed and did the same thing.

---

### Post by mandza on 2013-03-12
i am now on windows, but i will try it as soonest as possible. Thank you a lot.

---

### Post by mandza on 2013-03-13
i had go to the first tty and i successfully loged in.
but i couldnt open my home folder. i recive error message as on the photo attached.[IMG]http://img.1zh.us/rb.php?p=489[/IMG]

---

### Post by schragge on 2013-03-13
Try this
```
sudo touch /forcefsck
```
and reboot. This should force full filesystem check on the next boot. If it doesn't help then probably your hard disk is dying.

---

### Post by mandza on 2013-03-14
[COLOR=#000000]schragge thank you for your replay, i will try it, but i use SSD.
if [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo touch /forcefsck dont repair it, does it mean that i need new disk?[/FONT][/COLOR]

---

### Post by schragge on 2013-03-14
Not necessarily. I guess a physical failure of an SSD is less likely. BTW, does your */home* resides in its own partition? If your system still seems to work on the command line otherwise than the problems with /home then you can try troubleshooting it further by installing smartmontools
```
sudo apt-get install smartmontools
``` and running ```
sudo smartctl -a /dev/sda
``` Replace *sda* with the name of the disk where your */home* resides.

---

### Post by mandza on 2013-03-14
after i run [COLOR=#000000][FONT=Ubuntu Mono]sudo touch /forcefsck[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] and reboot my pc i am opened my home directory but i couldnt find any daa in it. just lost+found folder and empty desktop folder in it.
i think i had lose all my daha in home folder. if i had to i will reinstall my system again.
Thank you all for your help[/FONT][/COLOR]

---

### Post by mandza on 2013-03-14
i opened tty with Ctrl+Alt+F1 and go to home folder,
after that i create new folder with my username, after that my problem with login was solved.
But non of my programs of files was there, all data is lost.
i think that somehow my home folder was deleted, but i dont know how.
Now i can use my Ubuntu but without programs and files :(
thank you all again.

---

### Post by schragge on 2013-03-14
Perhaps you will be able to recover some of your data from [/lost+found]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html").

---

### Post by mandza on 2013-03-14
is there any specific method for recovering data from /lost+found ???
becouse when i open it, i see just two folder, and in booth of them is empty Desktop folder, nothing else.
And i want to add one note for my frevious post.
my programs are still installed on my pc they just dont show up on my side bar. i had to put them my self again.

---

