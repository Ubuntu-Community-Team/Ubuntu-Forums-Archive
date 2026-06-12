---
title: "Gdebi hung - no synaptic no add/remove"
date: 2006-08-03
forum: Desktop Environments
---

### Post by alexlloyd on 2006-08-03
I tried to install the Brother HL1030 LPR driver. I downloaded the package as per the instructions and double-clicked. Gdebi launched and the process returned a pile of errors.(I have a screenshot) Now I can no longer add or remove software, run Synaptic or force a remove of the package. I get the same error

[I]E: The package hl1030lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/I]

I went to Add/remove applications to to install IRC chat to find out how to fix this and all I get is the same message and the software will not install. 

in terminal i tried to remove the package

[I]alex@alex-main:~$ sudo dpkg -r hl1030lpr
dpkg: error processing hl1030lpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 hl1030lpr[/I]
 


Short of blowing off this installation, and my confidence in 6.06, what do I do now.
](*,)

Alex

---

### Post by pbbear on 2007-05-10
I cannot help you with your problem (I am only a novice myself).

All I can report is that I have had exactly the same error message, but with trying to install a program called VirtualBox.

I'm not yet ready to shoot myself, but I have considered reinstalling Ubuntu Feisty to cure the problem.  However, this is the first time I have seriously come to grips with Linux, and I have already invested a lot of time and effort into the present installation.

Best Wishes

---

