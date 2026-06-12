---
title: "Ubuntu for Desktopn (Oracle ERP)"
date: 2011-06-27
forum: Desktop Environments
---

### Post by fasi83 on 2011-06-27
Hi All Experts,
I am newbie in Linux and trying my existing network (1000+ nodes)  from windows XP to ubuntu. I need some expert opinion u all experts on below queries

1) Is Ubuntu be the right choice for windows users ???
2) My company are using Oracle ERP, for this i am going to test Oracle application behaviour on linux. I need to install Java to run my application but the version we are trying to install is older (jre 1.4.02.04). When i try to install it on my ubuntu box, it throws me error mentioned below

[FONT=verdana][COLOR=#006600]Do you agree to the above license terms? [yes or no] [/COLOR]
[COLOR=#006600]yes [/COLOR]
[COLOR=#006600]Unpacking... [/COLOR]
[COLOR=#006600]tail: cannot open `+417' for reading: No such file or directory [/COLOR]
[COLOR=#006600]Checksumming... [/COLOR]
[COLOR=#006600]1 [/COLOR]
[COLOR=#006600]The download file appears to be corrupted.  Please refer [/COLOR]
[COLOR=#006600]to the Troubleshooting section of the Installation [/COLOR]
[COLOR=#006600]Instructions on the download page for more information. [/COLOR]
[COLOR=#006600]Please do not attempt to install this archive file. [/COLOR]
[COLOR=#006600]jlouwers@NL-jlouwers:~/Desktop$

Please guide me .... 

[COLOR=Black]3) There are some client/server based custom applications we have developed on VB.net platform, is there any utility to migrate it or to run in linux environment?

Please guide me, thanks in advance.


Regards,
Faisal Habib
[EMAIL="fasi83@hotmail.com"]fasi83@hotmail.com[/EMAIL][/COLOR]
[/COLOR][/FONT]

---

### Post by FormatSeize on 2011-06-27
> **fasi83 said:**
> 
1) Is Ubuntu be the right choice for windows users ???
Probably. It does depend on the user, though, as different people expect different things out of a computer. You will have those that will want specific things from Windows to be available, and then you will have others that won't even realize that they aren't using Windows unless someone tells them. 
 
 
[FONT=verdana][COLOR=#006600]> Do you agree to the above license terms? [yes or no] [/COLOR][/FONT]> 
[FONT=verdana][COLOR=#006600]yes [/COLOR][/FONT]
[FONT=verdana][COLOR=#006600]Unpacking... [/COLOR][/FONT]
[FONT=verdana][COLOR=#006600]tail: cannot open `+417' for reading: No such file or directory [/COLOR][/FONT]
[FONT=verdana][COLOR=#006600]Checksumming... [/COLOR][/FONT]
[FONT=verdana][COLOR=#006600]1 [/COLOR][/FONT]
There's a file missing. Is it possible that you can upgrade to the later version?
[FONT=verdana][COLOR=#006600][COLOR=black]> 3) There are some client/server based custom applications we have developed on VB.net platform, is there any utility to migrate it or to run in linux environment?[/COLOR][/COLOR][/FONT]
 
Linux, inherently, does not understand VB code. I doubt that a Linux environment will be able to execute VB code. Your applications would have to be developed using source code that is Linux-readable, like C or Python. Learning a new language may or may not be something that you want to do to create a new application that is important to your business. You have to make that decision.
 
There is an application called Wine, which will run Windows programs. But if you take the time to install Ubuntu, learn your way around it, then install Wine to run your Windows programs, why bother with it in the first place?

---

