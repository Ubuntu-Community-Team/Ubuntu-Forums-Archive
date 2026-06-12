---
title: "Password unrecognized at login"
date: 2011-02-16
forum: Desktop Environments
---

### Post by benny7440 on 2011-02-16
After a couple of months of not using the dektop it warned me to check/correct some issue with the HDD, which I did. After the steps taken by the system to check the disk it went to the sign-in screen for ubuntu but it no longer recognize my password, so can't use it.

I remember that at the time when I was installing the OS it gave me a long list of alphanumeric characters which I would need in case of login problems in the future but I can't find where I wrote that string of chrs..

Can I deal with this issue by using the livecd from where I installed the OS or I do indeed need that string?

Thanks in advanced for any help on this!

**_Important notes_**
1) Ubuntu 10.04 LTS
2) Plenty of free hard disk space
3) Properly partitioned disk
4) Recognized partitions at startup
5) Never before any issue/error of this sort

---

### Post by ajgreeny on 2011-02-16
Is this an encrypted system disk, ie did you choose encryption when you installed?  If so, you may be out of luck if you can't remember your passphrase.

---

### Post by benny7440 on 2011-02-17
Thanks ajgreeny for responding!

As far as I can remember I didn't choose to encrypt anything. I do insist, though, that this issue might have something to do with that message shown at startup that states that *a checkdisk action is necessary*...

---

### Post by Krytarik on 2011-02-17
Then try changing your password from within the "root shell prompt" after choosing "recovery mode" at the boot menu:
```
passwd YOURUSERNAME
```
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by benny7440 on 2011-02-19
Thanks, Krytarik for the link; very useful! In the next hour or so I'm going to perform the procedure. Hope it works! I'll post here afterward with the results.

---

### Post by benny7440 on 2011-02-20
As I said above, I'm sending now my results.

I managed to change my password & were able to sign in, but there's a problem in the harddisk structure of some kind. All that I had after signing in was a blank (empty of icons & functionality) desktop. I think that my only alternative is to use the live cd to either try to fix with it the problem or reinstalling. If reinstallation is going to be my alternative, that's to be found, but in that case I'll probably be posting for some advise before committing.

PS. There were 2 'Messages' that appeared at startup but I was too tired to annotate them (one of them had a numerical code). Think I can get those again if signing in once more.

---

### Post by Krytarik on 2011-02-20
When you boot into recovery mode/root prompt, can you access the files/dirs in your home directory?

---

### Post by benny7440 on 2011-02-20
Thanks for responding, Krytarik!

I know it & I nosed a little yesterday. But, what I don't get is what I'm supposed to look for there; if I find it, what to do next?

---

### Post by Krytarik on 2011-02-20
Check what ownership the file ".ICEauthority" in your home directory has, if it's not you change it back.
```
krytarik@krytarik-desktop:~$ ls -al .ICE*
-rw------- 1 krytarik krytarik 88494 2011-02-19 18:21 .ICEauthority
krytarik@krytarik-desktop:~$ 

``````
chown YOURUSER.YOURUSER .ICEauthority
```(No need for sudo since you are at the root prompt.)

This can happen if you use "sudo" instead of "gksudo" for graphical apps:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by benny7440 on 2011-02-20
I issued the command as it appears in your post but the result is as follows:
<ls: cannot access .ICE*: No such file or directory>

PS. If I issue the command **ls -a** the result is:
".   [COLOR="Olive"].bash_history[/COLOR]   [COLOR="Purple"].dbus   .gconfd   .gnome2_private   .pulse   .synaptic   ..[/COLOR]   [COLOR="Olive"].bashrc[/COLOR]   [COLOR="Purple"].gconf   .gnome2[/COLOR]   [COLOR="Olive"].profile   .pulse-cookie[/COLOR]   [COLOR="Purple"].wapi[/COLOR]"

Note: In my screen, all that appears here in greentea color appears in white, the violet is as is.

PSS. What the different colors mean?

---

### Post by Krytarik on 2011-02-20
The colors are not really important, they indicate the type or state of the files/dirs.

Did you issue the command in your home directory?

Meaning, in my case, after I got to the root prompt:
```
cd /home/krytarik
ls -al .ICE*
```Notice that it is an upper "I", not lower "L"!

---

### Post by benny7440 on 2011-02-20
Apparently, the file's missing. Even tried with sudo. Same exact result as before.

I saw something that is giving some kind of problems:
"161 packages can be updated.
 61 updates are security updates.

 [B]keyctl_search: required key not available
 Perhaps try the interactive 'ecryptfs-mount-private'[/B]"

Think we're running out of alternatives...

---

### Post by Krytarik on 2011-02-20
Where did you see those?

---

### Post by benny7440 on 2011-02-20
After issuing the command cd /home/myusrname login & entering my usrname & pwd. It gives some other info but that's not relevant to this issue.

---

### Post by Krytarik on 2011-02-20
Then your home directory is indeed encrypted, as supposed before.
I hope you have nothing in there, what you can't recover!

I have to say, that I'm not familiar with encryption, so I cannot help.

---

