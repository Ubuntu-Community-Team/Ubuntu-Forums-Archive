---
title: "Things have realy c@#ked up"
date: 2005-08-14
forum: Desktop Environments
---

### Post by fig_jam_uk on 2005-08-14
Hi all i hope somebody out there can help  :roll: 

I had a problem with ripperx it got stuck encoding a CD so i had to xkill then reboot as still trying to read disk.... but upon first reboot i got an error with ripperx saying that no cd or must be root to run??? never had to before...

i then rebooted wich solved this  ;-) 

But now when i try anything sudo orientated like run synaptic or even use the sudo command in console i get errors  ](*,) 

See atachment for X based error and the console error is below

mark@hal9000:~$ sudo kuser
sudo: must be setuid root
mark@hal9000:~$

any ideas cause im stuck  ](*,)   ](*,)

---

### Post by cwaldbieser on 2005-08-14
> **fig_jam_uk]Hi all i hope somebody out there can help  :roll: 

I had a problem with ripperx it got stuck encoding a CD so i had to xkill then reboot as still trying to read disk.... but upon first reboot i got an error with ripperx saying that no cd or must be root to run??? never had to before...

i then rebooted wich solved this   said:**
> (*,) 

See atachment for X based error and the console error is below

mark@hal9000:~$ sudo kuser
sudo: must be setuid root
mark@hal9000:~$

any ideas cause im stuck  ](*,)   ](*,)

Can you boot into "Rescue Mode"?  Use this link [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and search down the page for the "Rescue Mode" section.

I am guessing that maybe your /etc/sudoes file got screwed up somehow, but you do need root powers to look at it or edit it.  You might see if you can add another user with the "adduser" command and see if that user can use sudo.

There is supposed to be a line in /etc/sudoers for your user that reads
```
your-user-name ALL=(ALL) ALL
```

---

### Post by fig_jam_uk on 2005-08-14
[QUOTE=cwaldbieser]Can you boot into "Rescue Mode"?  Use this link [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and search down the page for the "Rescue Mode" section.

I am guessing that maybe your /etc/sudoes file got screwed up somehow, but you do need root powers to look at it or edit it.  You might see if you can add another user with the "adduser" command and see if that user can use sudo.

There is supposed to be a line in /etc/sudoers for your user that reads
```
your-user-name ALL=(ALL) ALL
```[/QUOTE]

hi thanks for the reply. just wondering if the sdoers file should have some kind of file extention on there?

cheers

---

### Post by cwaldbieser on 2005-08-14
[QUOTE=fig_jam_uk]hi thanks for the reply. just wondering if the sdoers file should have some kind of file extention on there?

cheers[/QUOTE]
Nope, the file is just "/etc/sudoers".  In GNU/Linux, the extension doesn't associate an application with a file like it does in Windows.  Some conventions are still popular (like .txt for text files), but config files follow various conventions.

The "file" command will tell you the type of a file in many cases.  E.g.
```
$ file halloween.mid
halloween.mid: Standard MIDI data (format 1) using 19 tracks at 1/240
$ file IMG_0186.JPG
IMG_0186.JPG: JPEG image data, EXIF standard 2.2
```

---

### Post by fig_jam_uk on 2005-08-15
Hi cwaldbieser thanks for your responces, i booted into rescue mode ran nano /etc/sudoers and my name wasnt there s i added the line mark  ALL=(ALL) ALL
but im still having the same problem...  ](*,)   ](*,)   ](*,) 

thanks in advance

---

### Post by fig_jam_uk on 2005-08-15
I think it may bee i need to change the permissions of my user, does any body know how i can try this from recovery console because this has root prvieledges?


cheers

---

### Post by cwaldbieser on 2005-08-15
[QUOTE=fig_jam_uk]I think it may bee i need to change the permissions of my user, does any body know how i can try this from recovery console because this has root prvieledges?
cheers[/QUOTE]

Try
```
$ ls -l /usr/bin/sudo
``` 
If it doesn't come back with
```
-rwsr-xr-x  2 root root 95288 Jun 21 08:46 /usr/bin/sudo
``` 
(date can be different, but those funny characters at the beginning should be the same)

Then try (as root):
```
# chmod u+xs /usr/bin/sudo
```

---

### Post by fig_jam_uk on 2005-08-15
[QUOTE=cwaldbieser]Try
```
$ ls -l /usr/bin/sudo
``` 
If it doesn't come back with
```
-rwsr-xr-x  2 root root 95288 Jun 21 08:46 /usr/bin/sudo
``` 
(date can be different, but those funny characters at the beginning should be the same)

Then try (as root):
```
# chmod u+xs /usr/bin/sudo
```[/QUOTE]

Hi cwaldbieser all sorted had a word with one of the guys i work with and he helpmed me half the way and i stumbled the rest :)

booted into recovery then
vi /etc/passwd
i
changed my userid from 1000 to 0
etc
:wq
reboot
switch to console login
loged in as my user witch was then root
re-installed sudo using synaptic
rebooted now all is good again

i would just like to say thank you for the help you did provide i probably would have given up sooner and re-installed Kubuntu..

---

### Post by PeP on 2005-08-15
[QUOTE=cwaldbieser]Can you boot into "Rescue Mode"?  Use this link [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) and search down the page for the "Rescue Mode" section.

I am guessing that maybe your /etc/sudoes file got screwed up somehow, but you do need root powers to look at it or edit it.  You might see if you can add another user with the "adduser" command and see if that user can use sudo.

There is supposed to be a line in /etc/sudoers for your user that reads
```
your-user-name ALL=(ALL) ALL
```[/QUOTE]

I am quite surprised you can do that, I thought that /etc/sudoers must be edited from visudo.
from TFM:
> CAVEATS
       The sudoers file should always be edited by the visudo command which locks the file and does gram-
       matical checking. It is imperative that sudoers be free of syntax errors since sudo will not run
       with a syntactically incorrect sudoers file.

---

### Post by fig_jam_uk on 2005-08-15
[QUOTE=PeP]I am quite surprised you can do that, I thought that /etc/sudoers must be edited from visudo.
from TFM:[/QUOTE]

it seemd to work fine this time, anybody have the same problems as i had if you try this let us know how you get on :)

---

### Post by tisptn on 2005-09-07
hi this is exactly what happened to me i'm just gonna go home and try it out i'll let you know how it goes  :)

---

### Post by Gezzer on 2005-09-08
[QUOTE=][/QUOTE]
 have u tried 
kdesu
in the konsole instead of sudo ?..

---

### Post by tisptn on 2005-09-08
[QUOTE=Gezzer]have u tried 
kdesu
in the konsole instead of sudo ?..[/QUOTE]

um no i haven't is that using KDE? cos i'm using the default gnome. I did get it working again by the way but by then i'd messed up to many things so i re-installed anyway  ;-)  it was a little confusing to get the hang of the whole sudo thing, up till now i've been using mandrake linux 10.1 but i prefer ubuntu  :)  it's a bit more challenging to get going

:: just realised this was under kubuntu my bad ::

---

