---
title: "cups pdf won't print any file"
date: 2008-12-04
forum: General Help
---

### Post by El-ahrairah on 2008-12-04
Hi everybody

I have got a little problem with the cups-pdf printer on my ubuntu 8.04.1: whenever I send a file to be printed, in the PDF folder there is nothing, like the file has not been printed, while all the printing seems to go fine without any error reported.

what can it be to cause this problem? do you need me to post any config file? (sorry, but I do not know which one you might need...)

thanks in advance

---

### Post by silkstone on 2008-12-05
After trying to print to PDF, if you look in /var/log/cups/cups-pdf_log you may find an error message similar to...

Fri Dec  5 12:15:15 2008  [ERROR] failed to set file mode for PDF file (non fatal) (/home/silkstone/PDF/242_Index_page.pdf)

As you can see, I get this too and so do many other people. I don't have an answer but I think it's due to something relating to CUPS and the apparmor package which is supposed to provide security. There are various posts about it on the web, but I haven't found anything which says definitely how to cure it.

I haven't altered any config files to change the default destination of PDF files, so that's not the answer.

It would be good if an Ubuntu guru could advise on this.

---

### Post by El-ahrairah on 2008-12-05
apparmor you say? uhm... is it installed by default? I ask because I actually use ubuntu eee, not the "plain" ubuntu install

anyway I'll give a look to that log, to see if there is a line like the one you say

---

### Post by silkstone on 2008-12-05
I also use Ubuntu-eee on an eee PC 901, and that's the only machine on which I've tried (unsuccessfully) to use CUPS-PDF.

Apparmor can be forced to let things through by...

sudo aa-complain cupsd

But that doesn't work for me, so I'm assuming it's not a problem with apparmor. (You can reset it with sudo aa-enforce cupsd.)

I'm still mystified. It appears as if the PDF file is being created, but there's nothing there. I've searched the whole filesystem and the missing PDF files are nowhere to be found.

The error message in the log file is caused by an attempt to chmod the permissions of a file that does not exist. But there's no error message to say why it wasn't created.

EDIT/ I'm wondering if this is specific to the Array kernel. I'll fire up another Ubuntu machine and check.

---

### Post by silkstone on 2008-12-05
OK, I've now tried CUPS-PDF on two other machines (laptop and desktop) running Ubuntu 8.04, and it works as expected. The file appears in ~/PDF as it should, and there are no errors.

As far as I can see, the cups-pdf.conf file is identical to the one on the eee PC.

I can't say for sure, but it looks as if this is related to the Array kernel or something else specific to Ubuntu-eee.

There is already a thread about this issue on the Ubuntu-eee forum, so I'll pursue it again there.

---

### Post by HumbleGod on 2008-12-05
This occurs for me on Ubuntu-EEE as well.

Through silkstone's efforts, this has been reported as a bug. I can confirm from other threads that this is not limited to just one or two people (see [https://answers.launchpad.net/ubuntu-eee/+question/45161](https://answers.launchpad.net/ubuntu-eee/+question/45161) as well).

---

### Post by stinger30au on 2008-12-05
go to your home directory and create a new directory and call it


PDF


restart the pc and try again. your pdf file should go into this directory. i had the same issue when i installed 8.04 as well as 8.10

---

### Post by silkstone on 2008-12-05
There is already a PDF directory in my home directory. CUPS-PDF managed to create this the first time I tried to print to .pdf.

Unfortunately nothing lands there, or anywhere else.

This isn't a general problem with Hardy - it seems to occur only with Ubuntu-eee 8.04.1 using the Array kernel - it looks as if .pdf files are being created, but they disappear into the ether and cannot be found anywhere in the filesystem. I don't have a problem with CUPS-PDF on other machines running 8.04.

---

### Post by El-ahrairah on 2008-12-05
I noticed that the folder created by cups-pdf has the permission set as rxw --- --- while the one I created has the permission rxw r-x r-x... can this change something? (i have not rebooted right now, but if I try to make a pdf, it still wont work)

---

### Post by silkstone on 2008-12-06
I don't think that's the problem, and you should be able to extend permissions to Group and Others from the Permissions tab in Nautilus. But the .pdf file is yours so permissions for others shouldn't prevent the file being saved there.

A bug report has been posted about this.

[https://bugs.launchpad.net/ubuntu-eee/+bug/294929](https://bugs.launchpad.net/ubuntu-eee/+bug/294929)

---

### Post by tiris on 2008-12-11
I found this from the homepage of cups-pdf
 
[http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml)

> # *** Starting with version 1.2.0 CUPS implements the "RunAsOption" no longer. In order to ensure CUPS-PDF is running with the required root privileges you have to make 'root' the owner of the cups-pdf backend and set the file permissions of the backend to 0700 (root only).

I don't know how "to make the 'root' the owner cups-pdf backend" but I think this is key to solving our problems.

I just installed ubuntu-eee on a 1000H.

---

### Post by silkstone on 2008-12-19
There is a fix for this - thanks to zeemor on the Ubuntu-eee forums for finding it.

The problem is with permissions in /var/tmp. If you set full permissions for everyone in /var/tmp, it all works.

---

### Post by El-ahrairah on 2008-12-20
will this work even if my /var/tmp is always located on RAM rather than hard drive?

---

