---
title: "quick Q (cvscedgega) already installed...."
date: 2005-10-08
forum: Gaming &amp; Leisure
---

### Post by floyd27 on 2005-10-08
Hi. Just got through the install...
Wondering how to open the porg now ..hehe
I have games on my win patition can i play them from thee, or do i have to install a game in cedega?
thanx
anything else i should know is appreatiated

---

### Post by floyd27 on 2005-10-08
I found that i have alot of configing to do first...sorry..
I will reply if i come to a road block..
thanx

---

### Post by floyd27 on 2005-10-08
That was quick..
ok just installed, no problems there..
tried to run 
roderick@ubuntu:~$ cvscedega
bash: cvscedega: command not found
????????????????

im not sure about that..
there is a cvscedega in my /home/roderick/bin folder..
and in the /home folder there is 
"TransGaming_Drive"

I think thats the fake windows drive??

Am i on the right track here?
thanx

---

### Post by Perfect Storm on 2005-10-08
I have no experience with the CVS version, but I think you need to symlink it to /usr/bin if you want to start it via terminal


sudo ln -s /usr/bin /where/your/cvscedega/file/is/<name of the file>

See if it works.

---

### Post by floyd27 on 2005-10-09
that did something..
Im gona go through the process ill let you know how it goes..
thanx

---

### Post by floyd27 on 2005-10-09
Hi.
everything was going well until i was installing a game..
It is 2 disks..
I get through disk 1 but then it askes for disk 2..It would not let me tak eit out, so i forced the unmount. Now disk 2 doesnt get recognized?
no matter what i do disk 2 wont do anything.
When i press "ok" after inserting disk 2 it does nothing?????

any help?

---

### Post by floyd27 on 2005-10-09
I managed to install the full game.. Well it got to 100% then said insert disk 1 to complete install.
I did it and it just made the cpu go to 100% and did nothing form there?
How do i open the game?
I dont know where the fake c: drive is to go to that dir.. or what the run command for the game is?
help please..

---

### Post by seethru on 2005-10-09
I believe it is located at ~/.cvscedega

---

### Post by floyd27 on 2005-10-09
I found the folder with thew files in it..
I trued to open the exe by 
"open with"
cvscedega

but it says couldnt find a config file..
then says make sure the run file is in the right palce? or something..

How do you guys open games???
what do you do?
thanx

---

### Post by seethru on 2005-10-09
I personally forked over the $5/month for cedega

As for a config file...in the cvscedega folder do you see a .conf file? might be wine.conf or cvscedega.conf...sounds like you need to either edit that, or create it from scratch.

---

### Post by floyd27 on 2005-10-09
What would be in this folder?
All i have is this..

"/home/roderick/.WineCVS/installs/cvscedega/bin"

There is a "config" file here..
here is whats in it at the top of that config file.
Is this the one i need to config???

WINE REGISTRY Version 2
;; All keys relative to \\Machine\\Software\\Wine\\Wine\\Config

;; If you think it is nescessary to show others your complete config for a 
;; bug report, filter out empty lines and comments with
;; grep -v "^;" ~/.wine/config | grep '.' 
;;
;; MS-DOS drives configuration
;;
;; Each section has the following format:
;; [Drive X]
;; "Path"="xxx"       (Unix path for drive root)
;; "Type"="xxx"       (supported types are 'floppy', 'hd', 'cdrom' and 'network')
;; "Label"="xxx"      (drive label, at most 11 characters)
;; "Serial"="xxx"     (serial number, 8 characters hexadecimal number)
;; "Filesystem"="xxx" (supported types are 'msdos'/'dos'/'fat', 'win95'/'vfat', 'unix')

---

### Post by seethru on 2005-10-09
that looks like the right file, but it doesn't look like it's in the right place...

---

### Post by floyd27 on 2005-10-09
where is the right place?

---

### Post by seethru on 2005-10-09
well, you SHOULD have a ~/.cvscedega directory...

---

