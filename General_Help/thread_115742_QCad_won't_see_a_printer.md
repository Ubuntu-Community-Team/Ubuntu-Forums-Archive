---
title: "QCad won't see a printer"
date: 2006-01-11
forum: General Help
---

### Post by Beanbag on 2006-01-11
I know this problem's been discussed before. I searched the forum and found this topic:

[http://ubuntuforums.org/showthread.php?t=88589&highlight=QCad](http://ubuntuforums.org/showthread.php?t=88589&highlight=QCad)

which referred me to this solution from jlinkels:

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=363383&highlight=no+printer+qcad](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=363383&highlight=no+printer+qcad)

which said to use the follwing comands to fix the problem:

       mv /etc/printcap /etc/printcap_old
       ln -s /var/run/cups/printcap /etc/printcap

I noted that jlinkels  said this had to be run from root. I tried running them from sudo, but I get the following message:

      cannot stat '/etc/printcap':   no such file or directory

So, I enabled the root password and tried logging in as root from the graphical login screen, thinking this might solve the problem. Instead, I get a message on that says the system administrator is not allowed to log in from that screen.

Okay, what stupidly obvious item am I overlooking? Every other application (OpenOffice, AbiWord, etc.) can find the printer, just not QCad. Assuming I have to log in as root, how  and from what screen do I do it?

Pretend I'm REAL stupid when you give me an answer. Don't assume I know anything else about Linux except how to log in under my account name and launch a terminal session, and you won't go too wrong.

Regards;
Beanbag

---

### Post by kcr on 2006-01-28
Answer Dumbed down at your request

first up log in under your normal account name and launch a term.

then you just need to do a 

```
sudo ln -s /var/run/cups/printcap /etc/printcap
```

it will ask for a password - you enter your normal user password.

fixed the problem for me.

'sudo' means super user do - I never log in as root I always use sudo 

The "cannot stat '/etc/printcap': no such file or directory" message is because you tried to move (mv) the file /etc/printcap which didn't exist in the /etc/ directory

The no printer thing was pissing me off as well

Regards

KCR

---

