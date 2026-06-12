---
title: "Hardy~ccsm isnt working!!!!"
date: 2008-12-06
forum: General Help
---

### Post by KEE on 2008-12-06
```
root@root-desktop:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found
root@root-desktop:~$ sudo apt-get install compizconfig-settings-manager
E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
root@root-desktop:~$ 
``` ok so do it do again?

---

### Post by Giant Speck on 2008-12-06
> **KEE said:**
> ```
root@root-desktop:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found
root@root-desktop:~$ sudo apt-get install compizconfig-settings-manager
E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
root@root-desktop:~$ 
``` ok so do it do again?

Could you give us a readout of what your /etc/apt/sources.list file says?

---

### Post by KEE on 2008-12-06
> **Giant Speck said:**
> Could you give us a readout of what your /etc/apt/sources.list file says?

```
root@root-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
```

---

### Post by Giant Speck on 2008-12-06
> **KEE said:**
> ```
root@root-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
```

Open it in gedit, as in:

```
gedit /etc/apt/sources.list
```

---

### Post by KEE on 2008-12-06
> **KEE said:**
> ```
root@root-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
```

how do i  show it? you mean like a pic? Ook 1 sec

---

### Post by KEE on 2008-12-06
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb http://repository.cairo- dock.org/ubuntu
```

---

### Post by Giant Speck on 2008-12-06
> **KEE said:**
> how do i  show it? you mean like a pic? Ook 1 sec

No, if you open it in gedit, as in the command I gave above, it should open a text file.

Copy and paste everything in that file into a post.

---

### Post by Giant Speck on 2008-12-06
Change this line:

```
deb http://repository.cairo- dock.org/ubuntu
```

to this:

```
deb http://repository.cairo-dock.org/ubuntu
```

For some reason, there was an extra space between the hyphen and the word dock.

Once you've done that, save the file and attempt to install ccsm again.

---

### Post by KEE on 2008-12-06
> **Giant Speck said:**
> Change this line:

```
deb http://repository.cairo- dock.org/ubuntu
```

to this:

```
deb http://repository.cairo-dock.org/ubuntu
```

For some reason, there was an extra space between the hyphen and the word dock.

Once you've done that, save the file and attempt to install ccsm again.

hmm its not allowing me too ```
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```

---

### Post by Giant Speck on 2008-12-06
> **KEE said:**
> hmm its not allowing me too ```
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```

Are you logged into root?  And if not, are you using the sudo command?

I'm sorry, but I have to get to bed now.  Hopefully, someone will pick this up while I'm gone.

---

### Post by KEE on 2008-12-06
Do I open with text editor?

---

### Post by Giant Speck on 2008-12-06
> **KEE said:**
> Do I open with text editor?

Yes.  Open it as root.

---

### Post by KEE on 2008-12-06
> **Giant Speck said:**
> Yes.  Open it as root.

not sure i can. it says in not enough permissions to save =/ i think you mean in terminal though =)

---

### Post by KEE on 2008-12-06
> **Giant Speck said:**
> Yes.  Open it as root.

well i tried to open in terminal as a text in text editor but i still cant save it =(

---

### Post by Giant Speck on 2008-12-06
> **KEE said:**
> not sure i can. it says in not enough permissions to save =/ i think you mean in terminal though =)

Yes.

Open a terminal, type the following code in:

```
sudo gedit /etc/apt/sources.list
```

That will open the file in text editor as root.  Once the file is open, scroll down to the line that says:

```
deb http://repository.cairo- dock.org/ubuntu
```

and delete the extra space between "cairo-" and "dock," so that it looks like this:

```
deb http://repository.cairo-dock.org/ubuntu
```

Save the file.  Then close it.  And then go back to the terminal and try to install the program again.

---

### Post by KEE on 2008-12-06
> **Giant Speck said:**
> Yes.

Open a terminal, type the following code in:

```
sudo gedit /etc/apt/sources.list
```

That will open the file in text editor as root.  Once the file is open, scroll down to the line that says:

```
deb http://repository.cairo- dock.org/ubuntu
```

and delete the extra space between "cairo-" and "dock," so that it looks like this:

```
deb http://repository.cairo-dock.org/ubuntu
```

Save the file.  Then close it.  And then go back to the terminal and try to install the program again.

Ook how do you save?

---

### Post by KEE on 2008-12-06
> **KEE said:**
> Ook how do you save?

nvm =P thanks

---

### Post by KEE on 2008-12-06
> **Giant Speck said:**
> Yes.

Open a terminal, type the following code in:

```
sudo gedit /etc/apt/sources.list
```

That will open the file in text editor as root.  Once the file is open, scroll down to the line that says:

```
deb http://repository.cairo- dock.org/ubuntu
```

and delete the extra space between "cairo-" and "dock," so that it looks like this:

```
deb http://repository.cairo-dock.org/ubuntu
```

Save the file.  Then close it.  And then go back to the terminal and try to install the program again.

Goto System &#8594; Administration &#8594; Software Sources, and goto the Third-Party
Software tab. Click Add  deb [http://repository.cairo-dock.org/ubuntu?](http://repository.cairo-dock.org/ubuntu?) but the add file is grayed out and i cant select it

---

