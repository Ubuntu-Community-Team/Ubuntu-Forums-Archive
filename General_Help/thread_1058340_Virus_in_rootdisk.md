---
title: "Virus in rootdisk"
date: 2009-02-02
forum: General Help
---

### Post by marticc on 2009-02-02
Hello,

First I'd like to apologise for my poor English. I hope you understand  what I want to say.

Second: I am not sure whether this is the right phorum to post this thread. If this is not the right phorum to post this thread, please move it to the right phorum

Third: I would really apreciate any advice about the following problem:

 Two months ago I installed ubuntu 8.10 in my Windows partition using Wubi,and it has been working properly so far. In fact currently I hardly use Windows Vista. Howewer, as I still have to do some tasks in Windows, every now and again I scan my computer using  Avast antivirus.

Two weeks ago, Avast found a virus in the file swap disk (file located in the file C:\ ubuntu\disks. I quarantined the file, and before deleting it, I  checked that my Ubuntu worked properly without that file. As Ubuntu worked fine, I eventually deleted the file, and I haven't had any problems.

Yesterday, Avast detecteed the following virus win 32 Crypt-D D1 in te following files: root.disk and hidden_fuse 0000000600000001 (both files are located in the folder C:\Ubuntu\disks).

I have several questions I'd like to ask:

root.disk is too large to be sent to the chest, so I am not able to do the test (send the file to the chest, and see if Ubuntu works properly without this file) I did when I had the problem with the file swap.disk. So the question is: If i delete the file root.disk, will I be able to access to my Ubuntu?.

Does this virus compromise my security if I surf the web (and buy things online) using Ubuntu?. Can a win32 virus located in root.disk, "perform its task" when I work with UBUNTU?.

Has anyone had this problem?

Thanks for your answers.

---

### Post by Steelfan555 on 2009-02-02
> **marticc said:**
> 
root.disk is too large to be sent to the chest, so I am not able to do the test (send the file to the chest, and see if Ubuntu works properly without this file) I did when I had the problem with the file swap.disk. 
.
Did you try moving it to another folder instead of sending it to the recycle bin?

---

### Post by marticc on 2009-02-02
Hi, thanks for your answer. I have not done anything yet, so my infected root.disk is still in its original folder. Before doing anything I would like to find some information about my problem.

---

### Post by Dies on 2009-02-02
Definitely don't delete "root.disk".

Sounds like you're getting false positives. ;)

Get a second opinion if you're truly concerned about it, try AVG free edition. But in any case I wouldn't worry about those files. You might want to let the Wubi team and Avast know about it though if you have the time.

BTW even if those files did in fact contain Windows viruses, they wouldn't be able to run under Ubuntu.

---

### Post by khelben1979 on 2009-02-02
According to [this site]("http://www.econsultant.com/spyware-database/t/trojan-win32-crypt-d.html") (econsultant.com): you have the possibility on removing the virus with a special tool. Maybe it can be of interest to you?

Quoted from the site:

Malware Type : Trojan (A Trojan is a program that either contains a malware program or performs (subversive) actions not asked for by the installing user.)

Executable File(s) : smssa.exe

---

### Post by abn91c on 2009-02-02
check the wubi website, that might be a false positive

---

### Post by hansdown on 2009-02-02
Hi marticc.

This thread seems to have the same problem.

[http://ubuntuforums.org/showthread.php?t=911994](http://ubuntuforums.org/showthread.php?t=911994)

---

### Post by khelben1979 on 2009-02-02
> **Dies said:**
> BTW even if those files did in fact contain Windows viruses, they wouldn't be able to run under Ubuntu.

If he runs Wine then they will be able to create a mess within his Wine enviroment. Maybe it's worth mentioning?

---

### Post by marticc on 2009-02-02
Thanks again for your quick answers.

I m not using Wine nor similar software, so i hope that the virus won't run under my ubuntu.

I will scan the file with another AV to confirm the existence of the virus and i will let you know about the results.

Thanks again, and good night from Spain.

---

### Post by Dies on 2009-02-02
> **khelben1979 said:**
> If he runs Wine then they will be able to create a mess within his Wine enviroment. Maybe it's worth mentioning?

Not really. This requires way too many assumptions, at least IMHO.


You have to assume that his AV is not only accurate but amazing in it's scanning abilities. 

That he somehow caught a Windows virus/trojan while using Ubuntu.

That he's using Wine within a Wubi install.

And that this particular virus/trojan is able to run succesfully in wine.

---

### Post by marticc on 2009-02-24
Hi,

I just wanna tell you that eventually I fixed this problem.

As I told you in my latest post, I scanned the file with other antivirus tools (Bitdefender online, Panda online, AVG, Abvira, A squared and Norton), and none of them detected a virus in that file. So I guess that it was a false a positive.

Anyway, as I am  quite a paranoid person , I decided to use a Backup tool I have in my computer to restore the whole system to a date prior the problem started, so I put things back they were early this year. After that I have scanned those files several times, and I have not found any viruses so far.

Thanks for your help.

---

