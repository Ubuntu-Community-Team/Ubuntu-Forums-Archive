---
title: "Trouble installing Moneydance"
date: 2006-01-08
forum: Desktop Environments
---

### Post by malacoda on 2006-01-08
Getting really flustered trying to install Moneydance...

 After the download is finished, double-click the moneydance_linux_x86.sh (moneydance_linux_x86wj.sh with java) file or run "./moneydance_linux_x86.sh" (again, "./moneydance_linux_x86wj.sh" for the version with java) from the command line, in the same directory as the downloaded file. 

Well, regardless of which version I download - w/ java, or w/o java - when I click on the icon (located on my desktop where I save to), rather than running the shell script is opened by Kate.

If I try through the terminal via the state execute command all I get is "command not found".

If I download the general unix version tarball from the Moneydance site, when I extract it no files are shown in the directory I extract to... yet if I try to extract again it states 'the following files will not be extracted because they already exist' and procedes to list a bunch of moneydance files that are not visible in the directory as viewed through Konqueror.  If I try to proceed even though I can't see them - under the pretense they're there but hidden - I follow the MD website instructions to link the script to java and then issue the run command only to get "command not found" again.

It's really driving me nuts since finding a good Quicken or Money like finance program is the only thing holding me back from dumping Windows (yes, I've tried Gnucash, KMymoney, and looked at Grisbi... no of them offer the same online account access flexibility or ease navigation I'm looking for...).

Any help would really be appreciated.

Regards,
Malac :confused:

---

### Post by angrykeyboarder on 2006-01-08
[QUOTE=malacoda]Getting really flustered trying to install Moneydance...

[....]

Regards,
Malac :confused:[/QUOTE]

[http://moneydance.com/forum/YaBB.pl?board=install](http://moneydance.com/forum/YaBB.pl?board=install) ?

---

### Post by trorion on 2006-03-05
I couldn't install with Moneydance's base package so I downloaded the "with java" version and it worked fine.

Still trying it out, wish it was free and wish it allowed QIF imports instead of just OFX.

---

### Post by hopstah on 2006-06-29
did you ```
chmod +x
``` it to make it executable?

i know that this thread is long dead, but maybe it can still help.

---

### Post by kperkins on 2006-07-05
[QUOTE=trorion]I couldn't install with Moneydance's base package so I downloaded the "with java" version and it worked fine.

Still trying it out, wish it was free and wish it allowed QIF imports instead of just OFX.[/QUOTE]
It does import QIF.

---

### Post by zafo on 2006-07-21
This thread has been going on for a while, but I haven't really seen an answer, so here it is:

1.  Download moneydance_linux_x86wj.sh from [http://moneydance.com/other](http://moneydance.com/other) 
2.  Open a terminal window and type:
    sudo sh moneydance_linux_x86wj.sh
3.  The Moneydance installer will start.  Just answer the questions.
4.  If you use the default directory locations for installing, the program
    will be located at:  /usr/local/moneydance/
5.  On first run, you will be asked if you want to delete the temporary  
    install file .install4j - Say y for yes.

I've used Moneydance for over five years and was initially attracted to it because of it's Linux/Mac/Windows availability.  I think it is great, worth the money and like supporting the "small guy" instead of Microsoft and Intuit.

zafo

---

### Post by abdabber on 2006-11-18
I've tried installing from the command line and keep getting:

"No such file or directory"

---

### Post by jwillar on 2007-06-18
I followed your instruction but all I get is: 

john@DELL03:~$ sudo sh moneydance_linux_x86wj.sh
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Error: no `server' JVM at `/home/john/moneydance_linux_x86wj.sh.13399.dir/jre/lib/i386/server/libjvm.so'.
john@DELL03:~$

Is there a problem installing this on Kubuntu 7.4?:

---

### Post by jwillar on 2007-06-18
I finally got Moneydance to install and run.  It turns out the latest Java file were already loaded so I needed to download the copy w/o java.  My next problem was failing to attempt to run the scripts provided in the same directory as the download.

Thanks for the help.

---

### Post by mcj0422 on 2007-08-27
I get the installer to start and blindly put in a directory to install. But the installer just does not seem to work. I can not see any options, the box comes up but no options for the installer. anyone have these same problems still and/or come up with a solution?

---

### Post by ericartman on 2007-10-13
I just downloaded the file from moneydance, couldn't find a java /nonjave  offering. I downloaded the file to my desktop then opened terminal and cd to desktop and pasted into terminal                             sh moneydance_linux_x86.sh, it informed me the proper java wasn't installed and it downloaded the java I needed and away we went. install went fine after I chose a directory I had write privileges on, it was the one it recommended. hope this helps.

Cart

---

