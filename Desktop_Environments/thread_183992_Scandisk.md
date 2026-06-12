---
title: "Scandisk"
date: 2006-05-29
forum: Desktop Environments
---

### Post by JohnN on 2006-05-29
Does anybody know of a program that is already built into Ubuntu or a program I can easily get off of Stnaptic Package that will scan my hard drive and check it for errors and try to recover them, something like scandisk for the Dos/Windows side?

---

### Post by brt on 2006-05-29
usually you do not need to run such a programm manually because it is done every now and then automatically at bootup.

if you want to do that manually you have to unmount the drive first.

the used program is already installed and its called **fsck**

use **tune2fs** if you want to change the fsck-intervall at mount-time.

read **man tunefs** for options

---

### Post by JohnN on 2006-05-29
IWell, I am looking for more indept program that will scan each cluster of my linux hard drive for errors and tries to fix them, not just the brief one that ones does.

---

### Post by brt on 2006-05-29
[QUOTE=JohnN]IWell, I am looking for more indept program that will scan each cluster of my linux hard drive for errors and tries to fix them, not just the brief one that ones does.[/QUOTE]

hmm, whats the problem with your harddrive? 
have you got any errors on running fsck?

usually fsck will do exactly what you want.

---

### Post by JohnN on 2006-05-29
Nothing major, just sometimes Ubunutu freezes up, and I would like to see if there is any errors on my hard drive, I know its gets extermely hot inside the computer case

---

### Post by JohnN on 2006-05-29
How do I unmount my hard drive, and then run that fsck program?

My computer is acting strange, "unable to acess folder" errors, and unable to move files from my /home/Desktop directory to another folder...

---

### Post by steve.horsley on 2006-05-29
Well, fsck is the program you need to use - it's the scandisk equivalent. Only problem is, it can only check unmounted disks. You can of course check your hard disk from a live CD, which is wha I would do. But I wonder what they used to do before they had live CDs?

---

### Post by Sukarn on 2006-05-30
Because of bad sectors preventing my server installation of Breezy to upgrade to Dapper Desktop, I had to force a fsck.ext3 check. It warned me that it might cause errors, but I ignored that and it worked.
I wonder why i didn't think of using ubuntu live cd for it. I tried Knoppix and it was checking at a very slow speed, so I forced a check with Ubuntu.

---

### Post by cseljatib on 2008-02-24
hi John,

i have the same problem/question: How can I check for physical errors in my hard-disk in ubuntu?, did you find the answer?, if so, how?

thanks

---

