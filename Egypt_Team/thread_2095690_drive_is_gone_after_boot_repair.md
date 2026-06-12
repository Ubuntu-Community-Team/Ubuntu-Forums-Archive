---
title: "drive is gone after boot repair"
date: 2012-12-17
forum: Egypt Team
---

### Post by mohab1989 on 2012-12-17
1st off i have a 1 terabyte hard disk devided into sda(500GB) sdb(500GB)  all is devided into 4 drives ( C & games on sda) & (media & sources on sdb)
ofcourse i have windows  installed on the C drive , installed ubuntu on the sdb hard disk and took 100 gb of tthe media drive to give to the ubuntu 

my problem is after i installed windows 8 of course i ruined the ubuntu boot so i put the dvd with ubuntu on it and started ubuntu and done the following

- open a new _terminal_, then type: 

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update- Press Enter. 
- Then type: 
sudo apt-get install -y boot-repair && boot-repair- Press Enter

it opened up boot repair and the only thing i changed in the advanced settings was 
-OS to be booted default... and i chose it to be windows (via sdb5 menu)
then i clicked apply

and heres it what happened afterwards
 if i left the count down all the way it will open windows recovery not windows 

if i choose to boot winodws it goes in normally the problem is i cant find the media drive and i can see the system reserved drive which am not suppose to see on windows 

i went to boot ubuntu and it booted fine and went to disk utility and found the drive there..

the strange thing i noticed is that there is no swap drive as it was before 

another thing .. if i open files on ubuntu i can see all the drives under devices except media i can see it under computer !!

the problem in short is after i repaired the boot i cant see drives on the same hard disk where the ubuntu is installed 

any help would be very much appreciated 
thanks

SOLVED!!
the issue of the missing drive  was fixed pretty easily , i went and opened Gparted and then right clicked on the media drive (the missing one) and the information and noticed in front of tags "hidden" so i went to flags and unchecked   hidden and voila its back..

the issue of the default booting , booting into windows recovery i went in advanced settings in  boot repair and  i choose to  install the grub  only on sda not sdb and checked the purge previous grubs followed the instructions and now my default boot is ubuntu

the issue of the system reserved drive appearing in windows where it shouldn't was solved by going to manage the disk managment on the left side panel then right clicked the system reserved, select change drive letter and  paths 
hilighted the letter and then clicked remove ... now its gone

---

### Post by oldfred on 2012-12-17
Welcome to the forums.

I do not know rules on loco forums, but I thought most were for those who did not read English as the main forums are English. I can move thread since you seem fluent in English to Absolute Beginner forum or you can stay in your loco.

Best to post link to BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by mohab1989 on 2012-12-17
thanks oldfred for telling me that, i didn't know. 
you can move the thread if you like of course

---

### Post by wafialmasry on 2013-10-27
Thanks . 4

---

