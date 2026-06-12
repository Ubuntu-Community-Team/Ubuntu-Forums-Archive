---
title: "Account password does not elevate privileges"
date: 2006-04-11
forum: Desktop Environments
---

### Post by eutopion on 2006-04-11
I have a problem with root privileges in Ubuntu. Note that this is not the same issue as the usual "root problem" so please stay with me for a moment.

The problem is that my user account's password -- that which was set during installation and which works flawlessly for logging in to my desktop -- is not accepted by applications that require root privileges (such as most applications in the System > Administration menu).

Some kind souls on the #ubuntu channel on Freenode suspected a keyboard layout problem. After some experimentation, I managed to successfully launch applications that require root privileges after having installed a US keyboard layout and switched back and forth between that and my Swedish layout. However, I have not been able to replicate this success in any consistent way -- sometimes eventually it works, but usually it does not help. It may have been some completely different actions on my part that caused the problem to be resolved a few times, but I have not been able to think of what those may have been.

I have, however, found something that does appear to consistently work: hitting CTRL-ALT-F1 to get the text mode shell, and typing "sudo ls". At that point I am asked to enter my password, and it's accepted. After that, if I hit CTRL-ALT-F7 to bring back X and the desktop, desktop applications that require root privileges work fine as well. I am assuming that there is some sort of timeout at work;  since the console accepted me, the system as a whole accepts me for a period as well. Note that "sudo ls" does not work in the GNOME terminal -- my password is not accepted there. This may further strengthen the theory about a keyboard layout problem.

Having searched the forums and newsgroups, I have not yet come across my particular variation of the root problem. Most people seem to inquire about the lack of a dedicated root account -- of course this is not the issue at stake here. I use only lowercase a-z in my password, but I install using a Swedish keyboard layout. I select English as the general language. I have formatted my Ubuntu partition and re-installed it from scratch (release 5.10, to be precise), and the problem persists in exactly the same way following a fresh installation with no modifications whatsoever.

Although I am technically savvy in general (working with software development professionally and as a hobby), I have fairly limited Linux skills and virtually no prior experience with Ubuntu. I would appreciate it if someone could present some theories about this obscure problem, and perhaps suggest possible further avenues of trouble-shooting.

Thanks in advance,
Robert

---

### Post by eutopion on 2006-04-11
I believe that I have resolved this problem already.

What I did was elevate my privileges using a simple "sudo ls" in the text-mode shell, and then launched System > Administration > Users and Groups to change my password to something different. The new password appears to be accepted for launching applications that require root privileges.

To me, this further suggests a keyboard layout problem of some sort. Could it be a bug in Ubuntu 5.10...? About a year ago I briefly used an older version of Ubuntu with similar settings but did not come across this problem.

---

### Post by Mustard on 2006-04-11
Changing the password to something else was was going to be my first suggestion.  

I'm really not quite sure why the problem is occuring, so I couldn't speculate on whether its a bug or not.

---

