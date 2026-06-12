---
title: "Cd/?"
date: 2006-09-09
forum: Gaming &amp; Leisure
---

### Post by haxer on 2006-09-09
Hello i have downloaded something a file to a game and the guide on the internet tels me to use it in "terminal" then i should type in CD/downloaded directory/ ... but i have saved it to the desktop which is my downloaded directory then? im in oem mode now have been for a while if thats any help :S

---

### Post by HAARP on 2006-09-09
/home/*user*/Desktop

---

### Post by haxer on 2006-09-09
home/*user*/desktop? deosnt work please help im a noob i edmit it :)

---

### Post by Omnios on 2006-09-09
> **haxer said:**
> home/*user*/desktop? deosnt work please help im a noob i edmit it :)

 I think he ment cd /home/ " your user name " /desktop

 You might also want to read this threaed and the links others have posted here on how to install software in Linux.
[http://ubuntuforums.org/showthread.php?t=171822](http://ubuntuforums.org/showthread.php?t=171822)

---

### Post by fatsheep on 2006-09-09
This command will bring you to your desktop regardless of username:

> 
cd ~/Desktop


Oh and here's possibly the best guide for installing software in Ubuntu:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by haxer on 2006-09-10
"terminal"

cd ~/dekstop 
bash-: cd: /home/oem/desktop: no such file or directory? 

why the f*ck?

---

### Post by haxer on 2006-09-10
And i think the current helping is in how to cd to a directory?

---

### Post by v6ikek6rbes on 2006-09-10
type in terminal

cd /home/yourusername/desktop

---

### Post by oedipuss on 2006-09-10
also keep in mind that "desktop" and "Desktop" are considered two different words in linux. Files and directories are case sensitive. 
Therefore, if your user name is "oem" , your desktop would be at /home/oem/**D**esktop
The tilde '~' is like an abbreviation for /home/username for the current user.

---

### Post by 3rdalbum on 2006-09-10
> **haxer said:**
> "terminal"

cd ~/dekstop 
bash-: cd: /home/oem/desktop: no such file or directory? 

why the f*ck?

I too am wondering why, when you asked to change to a directory called "dekstop", Bash knew you wanted "desktop" :-P

It's case-sensitive: cd ~/Desktop will do it.

---

### Post by haxer on 2006-09-10
Thanks guys and girls :) really helpful :P

---

