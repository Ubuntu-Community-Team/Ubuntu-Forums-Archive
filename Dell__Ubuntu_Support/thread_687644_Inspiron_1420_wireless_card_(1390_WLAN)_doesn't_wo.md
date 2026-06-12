---
title: "Inspiron 1420 wireless card (1390 WLAN) doesn't work"
date: 2008-02-04
forum: Dell  Ubuntu Support
---

### Post by orchid10 on 2008-02-04
I have a Dell Inspiron 1420 with the 1390 wireless card. The computer came with Vista installed, it was a pig so I plunged into Linux-ubuntu.  I can't get the wireless to work but everything else seems to work OK.  Tried following the instructions noted on the ubuntu web-site using ndisWrapper that asks for the .inf driver file, that didn't work.  Putz’d around with all the configuration apps loaded with the original install, that didn't work.  It seems that the OS can't "see" the wireless adapter card (no driver present in guess).  I also noticed some forum members saying that the 1390 card is a pain in the butt to work with and recommend installing the 3945 card.  I really like the ubuntu UI and I don't want to go back to Vista.  Can anyone help?  Is the 1390 card worth all the trouble or should I just move to the 3945 card.

---

### Post by faulkes on 2008-02-04
The 1390 is the b/g card?

If so I have it working under ndiswrapper without much issue.  

IIRC the 3945 has a number of issues as well, not meant to disuade you, but to encourage you.

send the output of 

```

lcpsi 

and

ndiswrapper -l

and

lsmod

```

In addition, anything specific about the network you are trying to connect to (i.e. is it using a key for wep/wpa? etc)

Faulkes

---

### Post by faulkes on 2008-02-05
[QUOTE=orchid10]Faulkes,
Sorry for my delay in responding to your message.  I'm very new to ubuntu, Linux, and the forum and I really don't know my way around yet.  I'm a good Windows user but a rooky here.  
In Terminal, entering the code you noted gave the following replies: 

:~$ lcpsi
bash: lcpsi: command not found
richard@Laptop-Linux:~$ 1cpsi
bash: 1cpsi: command not found
[/QUOTE]

My mistake actually, it should be as below (I made a typo above) and nothing wrong with being new, the forums are here to help you.

```

/bin/lspci or /usr/bin/lspci

also the output of

/sbin/lsmod | grep ndis

```

Interesting, the above commands will give me a bit more information to go on.  Please reply on the forums though, that way it is public and other people can learn or offer additional help.

Faulkes

---

### Post by faulkes on 2008-02-06
> Originally Posted by orchid10
Faulkes,
richard@Laptop-Linux:~$ /bin/lspci

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

richard@Laptop-Linux:~$ /sbin/lsmod | grep ndis

richard@Laptop-Linux:~$

richard@Laptop-Linux:~$ /sbin/lsmod

Module Size Used by

bcm43xx 127336 0


Ok, broadcom 4311 wireless adapter, mini-pci.

It appears that you have the restricted driver being loaded - which means ndiswrapper will fail. First things first is to disable the bcm43xx module via the Restricted Drivers Manager.

you may also wish to read up [Here](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) and [here](http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/)

Faulkes

---

### Post by orchid10 on 2008-02-06
I looked at those very spots earlier this morning, I must have been reading your mind.  I'm in my day-job office right now with a highly restricted intranet so I can't get out to the Internet with my Linux lap-top to try these suggestions.  Traveling tomorrow and Friday so I'll continue to work the problem this weekend.  Thanks for your help, I'll get back to you with an update this weekend.

---

### Post by ÜbuntuMensch on 2008-02-07
I had the same card, tried a bundle of fixes, and eventually went with the 3945. It was like $35 2nd day delivery and I got to take the keypad off my laptop.

If you can get the 1390 working that's great, but don't be afraid to get a new card. Beats going back to Vista.

---

