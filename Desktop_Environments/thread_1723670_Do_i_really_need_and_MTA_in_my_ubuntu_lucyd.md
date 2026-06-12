---
title: "Do i really need and MTA in my ubuntu lucyd"
date: 2011-04-07
forum: Desktop Environments
---

### Post by jao_madn on 2011-04-07
Hi  I would like to ask some information regarding the installed package name  Exim Mail Transport Agent installed in my ubuntu desktop. what caused this package installed in my ubuntu desktop system. i understand that this package is mail server package used to send and receive email and my ubuntu desktop is not a didicated or a mail server either. Im just curios about this package installed on my system.  Thanks for any info and reply.

---

### Post by Seq on 2011-04-07
> **jao_madn said:**
> Hi  I would like to ask some information regarding the installed package name  Exim Mail Transport Agent installed in my ubuntu desktop. what caused this package installed in my ubuntu desktop system. i understand that this package is mail server package used to send and receive email and my ubuntu desktop is not a didicated or a mail server either. Im just curios about this package installed on my system.  Thanks for any info and reply.

You can use the `aptitude` command to see why a particular package was installed.

```
aptitude why exim4
```

---

### Post by 3Miro on 2011-04-07
This is not installed by default, I don't have anything Exim installed on my 10.10 (or are you working on 10.04).

If it is not installed by default and you didn't install it yourself, then it was pulled as a dependence of another program. Removing Exim could break that program.

Go to System -> Admin -> Synaptic Package Manager, then find the Exim package and select it for uninstall DON'T UNINSTALL, JUST SELECT. This will give you a list of all programs/packages that depend on Exim and will have to be uninstalled as well. Then you will know which programs are using Exim. DO NOT APPLY CHANGES, unless you want to uninstall everything on that list.

Note that even if a program "depends" on Exim, this can be for extra functionality that you are not using. In such case Exim will only sit on your machine and do nothing.

---

### Post by jao_madn on 2011-04-07
Hi  This is what i found in the uninstalled dependencies report  EXIM dependencies  all package start name EXIM bsd-mailx rkhunter  Im curios: Does rkhunter using email to send and recieve.  Also i noticed in the cmd line i can use mail or mailx to see my root mail msg log. and will create an mbox files in my home dir.

---

### Post by Seq on 2011-04-07
> **3Miro said:**
> Note that even if a program "depends" on Exim, this can be for extra functionality that you are not using. In such case Exim will only sit on your machine and do nothing.

There are three kinds of dependancies relavant here:
[LIST]
[*]Hard depends (or just "depends"): Something **needs** exim4 to work
[*]Recommended: Something **can optionally use** exim4, and this is default. exim4 is installed automatically.
[*]Suggested: Something **can optionally use** exim4, and this is **not** default. exim4 is **not** installed automatically.
[/LIST]

If you select to uninstall exim4 in synaptic, it will only warn you of "Hard" depends that will also be removed. It won't tell you what "recommended" depends you are now losing (i.e. something still works, just can't send mail).

`aptitude why ____`, as I posted above, will actually tell you why exim4 is there, whether it is a depend or recommend, etc. From the documentation:


```
By default aptitude outputs only the “most installed, strongest,
           tightest, shortest” dependency chain. That is, it looks for a chain
           that only contains packages which are installed or will be
           installed; it looks for the strongest possible dependencies under
           that restriction; it looks for chains that avoid ORed dependencies
           and Provides; and it looks for the shortest dependency chain
           meeting those criteria. These rules are progressively weakened
           until a match is found.
```

---

### Post by 3Miro on 2011-04-07
@Seq: I cross posted with you and I didn't know the aptitude why command. It should indeed give us more verbose information.

---

### Post by jao_madn on 2011-04-07
@seq:  I try the aptitude suggestion   result:  

#aptitude why exim4
 i   rkhunter Depends exim4 | postfix | sendmail | mail-transport-agent 


I noticed rkhunter depends on MTA and try to investigate. I had the same ubuntu lucyd lynx in VBox for trial and error installion of package before i applied it in my local system. when i check my vbox ubuntu i noticed there no mail or mailx command and diffenitely no exim package installed. icheck further and found that rkhunter installed the MTA

LucydLynxVbox:~$ sudo apt-get install rkhunter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light unhide
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks tripwire
Recommended packages:
  mailx
The following NEW packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light rkhunter unhide
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,034kB of archives.
After this operation, 6,955kB of additional disk space will be used.
Do you want to continue [Y/n]?  



So my question would be: Does exim MTA package is ok to installed on my system. rkhunter is a valid package am i right. if i installed then it must be used to email send and receive right. so theres a package on my system that send and receive email.

---

