---
title: "Unable to save changes to Kmenu"
date: 2005-09-04
forum: Desktop Environments
---

### Post by MrSweet on 2005-09-04
I have seen this problem around the web but so far I have not seen a solution for it.  I have been reading these forums for a little while now so it seemed like the best place to post this problem.

   I have been using Kubuntu for a few months now, it is the second distro that I have tried.  I really do love it.  I learn something new everyday.  Also I love using KDE as well.  I find it to be a very useful tool with some great features.

   My problem is that anytime I bring up the Kmenu editor I am able to re-name items, move them around, and add new items to the menu.  I then save the changes by hitting the save button.  Everything looks fine until I close that window and bring up the Kmenu.  None of the changes that I mad show up, only the old settings.  I have been able to change things in the past, ( I am anal when it comes to menu items,) but now my old settings are the only thing that I have in my Kmenu.

   If I bring up a shell to launch kmenu and try to save changes I get the following error message:

msweet@Ubuntu-Xaser:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x80032d

   If I use "sudo kmenuedit" my menu items are different then the ones for my user account.  The menu shows other application that I have recently installed, like the edutianment package.  When I try to save any changes here I get the same error message as above.

   I do not know why I can not save changes now, or what I did to cause this error.  As I said I was able to make changes in the past.

   For some backgound, my system is as follows:
Hoary 5.04 Kubuntu - KDE 3.4.0
2.6.10-5-smp kerne
P4 2.8 w/hyperthreading
1 gig ram
ATI Radeon 9800pro

   If there is any other information that I need to post please let me know.  Thank you for any replies to this problem.

     Mr.  Sweet

---

### Post by MrSweet on 2005-09-05
I was just doing some exploring and I noticed something a bit strange.  I opened up my "/var/tmp/kdecache-<username>/ directory.  I had a file in there called ksycoca.  The owner of that file was Root.  I changed that file to my user name.  After I did that I opened up my Kmenu and now it looks just like the menu does when I try to edit it as Root.  All the recent apps show up.

I still can't get any changes to stick however.  Just wanted to let everyone know that I did make some progress, I think.   \\:D/ 

Mr. Sweet

---

### Post by Takis on 2005-09-05
I don't know what the problem is, but I can tell you that running KMenuEdit with root priviledges will only change what the KMenu looks like if you were to log in as root (i.e. it's not a system-wide change), so while it was a good try, that can't solve anything.

```
taki@mrflibble:~$ kmenuedit
[COLOR=Blue]<Taki makes some changes and hits save>[/COLOR]
taki@mrflibble:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x800428
taki@mrflibble:~$
```
That error message might not be all that useful, then.

---

### Post by Goochi on 2005-09-29
Hello all, I have the same problem with my kmenu, things don't get added and stuff. Now after reading this topic, I tried the following
```
sudo chown -R <username> /var/tmp/kdecache-<username>
```
I tried editing again, all is saved :D
Plus various (100's) entries were I added I never saw before, let's start sorting :)

Thanks for the ideas, and good luck solving!

---

### Post by kkass on 2005-11-29
I used the command below to also change the group.  Now all the changes I made previously show up, and new changes are saved properly.

```

sudo chown -R <username>:<username> /var/tmp/kdecache-<username>

```

---

### Post by pgroover on 2006-01-05
I entered the command, and verified that I have ownership of everything within /var/tmp/kdecache-<username>, but I'm still unable to make changes to the menu...

---

### Post by kkass on 2006-01-05
Sorry that fix worked for me!  Do you know what you did to cause this behavior?  (I ran adept as sudo over X11 forwarding.)

Try resetting your X session and see if it helps.  (<ALT>-<CRTL>-<BACKSPACE>)

Look in your home directory for any files that are owned by root and should not be.  This could be a daunting task!  Try using the command  'ls -lA' or 'ls -lAR |grep root'.

---

### Post by pgroover on 2006-01-05
Thanks for the suggestions, but I had already tried them all.  As a matter of fact ensuring everything in my home directory belonged to me was my initial option prior to coming to the forum.

As for what I  could have done to get it at this point,  that's difficult to answer as I just rebuilt it last night and I had just installed KDE when I noticed this problem that just wouldn't go away.

EDIT: Never mind, it turns out that I had missed the hidden files, all is good now.  Thanks!!

---

### Post by kkass on 2006-01-05
Glad to hear it!

---

### Post by EisenPM on 2006-01-15
hello, it doesnt work on my computer and i dont understand the solution completely.

is it just that the kdecache and the home directory have to be "mine"? and then the menu should remember the changes upon saving?

---

### Post by kkass on 2006-01-26
Well I do not know exactly what the kdecache files are used for, but if I had to guess KDE is using them to store temporary data.  I would guess is that the real problem is that the file for your user is now owned by root, and you do not have read or write permission to it.

---

### Post by scunc_dvl on 2006-02-04
I have this same problem with kmenuedit. Seems to be a somehwat older version too,maybe downloaded some debian package may include a fix to this behavior..  

Anyways this is such an obvious and relatively simple bug, it should darn well be fixed!! Bump!

---

### Post by ingo on 2007-02-05
I've got the same problem and none of the above has worked for me. Here are details of my setup:

ingo@dicker:~$ kmenuedit --version
Qt: 3.3.6
KDE: 3.5.5
KDE Menu Editor: 0.7
ingo@dicker:~$

How does it look with you lot? Could it be the wrong Qt version or whatever?

---

### Post by maestrobwh1 on 2007-04-06
It's a silly permissions thing.  Once you find the files that give you as the user permission to save, it all works out.  

Kubuntu Feisty seemed to have an issue from the install until now and I have been living with this minor annoyance for quite some time.

---

### Post by ingo on 2007-04-10
you know the files???

---

