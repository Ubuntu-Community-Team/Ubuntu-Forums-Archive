---
title: "Folders not opening"
date: 2008-12-28
forum: General Help
---

### Post by Herstjori on 2008-12-28
Hi Guys,

I am having some issues with all of my folders not opening. I click on it and the loading symbol comes up but that is as far as it gets even after waiting 5 minutes. When I go to close the window via the x in the top right corner it states that the the folder is not responding and whether I would like to wait or force quit.

Any help please?

---

### Post by albinootje on 2008-12-28
> **Herstjori said:**
>  I am having some issues with all of my folders not opening. I click on it and the loading symbol comes up but that is as far as it gets even after waiting 5 minutes. When I go to close the window via the x in the top right corner it states that the the folder is not responding and whether I would like to wait or force quit.


Can you try these other file-managers and check whether they have the same problem, and also see whether you have enough free disk space ?

```

df -h
sudo apt-get install thunar pcmanfm

```

---

### Post by Herstjori on 2008-12-28
Thanks Albinootje

I have 13g of a 144g drive free

The pcman file manager works straight away!!

Can you advise please how I go about either fixing the filemanager that Ubuntu 8.10 comes with or failing that how I would go about making Pcman the default filemanager? - I have added the Pcman to a panel - should I simply use it from there and leave everything as is?

Thanks again!!!

---

### Post by albinootje on 2008-12-28
> **Herstjori said:**
>  Can you advise please how I go about either fixing the filemanager that Ubuntu 8.10 comes with or failing that how I would go about making Pcman the default filemanager? - I have added the Pcman to a panel - should I simply use it from there and leave everything as is? 

Can you try the following :

1) install some other windowmanager, e.g. icewm
```

sudo apt-get install icewm

```
2) Log out of your desktop.
3) Click on "sessions" at the bottom left.
4) Choose icewm.
5) Log in with your username, and choose "Just for this session".
6) Start a terminal.
7) Type in :
```

rm -r .gconf/apps/nautilus/
rm -r .gconfd/saved_state
rm -r .nautilus/

```
8) Logout of icewm, and try Gnome desktop again.


Here's option to change from Nautilus to Thunar :
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by Herstjori on 2009-03-11
Thanks AlbinootjeI tried doing this but it wouldn't work. I also followed your link to replace Nautilus with Thunar but the instructtions did not work. I followed them to the letter but it couldn't find the "defaultthunar.sh" file on my desktop kept saying no such file when it is DEF there?? 

I am also having new issues of pics not opening and new internet windows not starting up. I tried using the ICEWM thing but I don't see any of my files visable or if they are I cannot find them.

Can someone advise if the pics and internet not opening are related to Nautilus and if so how do I go about making thunar the default?

Thanks

---

### Post by albinootje on 2009-03-11
Hi Herstjori, you have so many different problems that I am wondering whether it makes more sense to find help at a Linux Users Group.
See here :
[http://www.linux.org/groups/australia.html](http://www.linux.org/groups/australia.html)
[http://en.wikipedia.org/wiki/Linux_User_Group](http://en.wikipedia.org/wiki/Linux_User_Group)

---

### Post by vanadium on 2009-03-11
> you have so many different problems that I am wondering whether it makes more sense to find help at a Linux Users Group.
We are not yet at the end of our latin here, I guess...

* You have 11 Gig free. On what partition? You might have 11 G in your /home, but none in your root. If that is the case, we have likely found the cause of the issue. You can tell from the output of "df -h".

* I would force a disk check on next reboot to be sure that a file system issue is not at fault. In the terminal, issue the command "sudo touch /forcefsck". Restart the computer: it will take some time as a thorough file system check is being performed. If you have multiple partitions, have them also force-checked.

* Then check whether it is a user configuration issue. Create a new user (and give him root permissions while you are at it). then log out, log in on the new user's account and see whether the problem persists. If not, then it is a user config issue and you might need to reset the config data on your other account. If yes, there is a system wide problem.

* In the later case (systemwide issue), I would try to purge-remove nautilus (and firefox while you are at it) then install it again.

---

### Post by Herstjori on 2009-03-13
Hi Vanadium thanks for your help I really appreciate it.

I had a look under the df -h there is nothing mentioning a root however everything else such as "tmpfs" "varrun" "varlock" "udev" and "lrm" have at least 1005m of 1007m available so used is 1% except for tmpfs which has 100% available - I hope this makes sense.
I have tried the touch/forcefsck with a result "command not found"

Not sure about paritions I believe I do not have any.

I have created a new user and yes the problem persists. so can you please help - how do I purge remove nautilus and also I use epiphany browser not firefox as it crashes every 2 minutes?

Thank you again

---

### Post by albinootje on 2009-03-13
> **Herstjori said:**
> 
I have tried the touch/forcefsck with a result "command not found"

It is (in a terminal) :
```

sudo touch /forcefsck

```
Please try this, and then reboot.
After finishing all the filesystem checking make sure to remove the /forcefsck directory.

---

### Post by Herstjori on 2009-03-14
hjatt Albinootje thanks that worked that time.

Scan went through with no results and at 100% jumped straight to login screen - I assume that this is a pass?!?

Also I notived that thsi scan is done every once i a while anyway.

Can you please advise how I turn it off now?

Thanks dude I appreciate it!!

---

### Post by albinootje on 2009-03-14
> **Herstjori said:**
>  Scan went through with no results and at 100% jumped straight to login screen - I assume that this is a pass?!?

Yes.
You can actually look in the directory lost+found in all of your Linux-partitions to see whether some bits of files ended up there, to give you an idea how much damage there possibly was.
> 
Also I notived that thsi scan is done every once i a while anyway.
Can you please advise how I turn it off now?

```

sudo rm -rf /forcefsck

```

---

### Post by vanadium on 2009-03-15
* We know it is not a user issue.

* It appears that it is not a problem of a file system inconsistency.

* Please post both command and output of "df -h" here so we can confirm there is no issue there

* My last suggestion involved removing nautilus completely, then reinstalling it hoping that would remove possible problems. I once had a situation where this worked.

I do not recommend disabling the periodic check of your file system!

---

### Post by Herstjori on 2009-03-18
Hi Vanadium,

CaN you please advise how to post the log as I can't cut and paste do I simply copy it letter for letter?

Thanks buddy

---

### Post by t0p on 2009-03-18
> **Herstjori said:**
> Hi Vanadium,

CaN you please advise how to post the log as I can't cut and paste do I simply copy it letter for letter?


Vanadium wants you to post the entire output of the command **df -h**.  If you really can't cut and paste, I guess you will have to type it out copying it letter by letter.  BTW, why can't you cut and paste?  Is this another problem you haven't included in this thread?

---

