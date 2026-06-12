---
title: "Help: Vmware workstation beta 6 in ubuntu feisty 7.04"
date: 2007-05-03
forum: Desktop Environments
---

### Post by galileux on 2007-05-03
Hi
I installed Vmware Workstation Beta 6 on Feisty (64-bit) as guest OS.
Installation and vmware-config.pl seem to have gone smooth.
Workstation starts OK.
I created a new VM for a WinXP guest.
When I try to power up the new guest machine for the first time, to install XP, I get the following error message:

"Unable to change virtual machine power state: Failed to connect to peer process."

I cannot get past that point.
I did some googling and tried a few hacks with no luck so far.
Everything I have tried seems to apply to different combinations of ubuntu/vmware than the one I have.

Can anyone help?
Thanks and regards
galileux

---

### Post by galileux on 2007-05-04
"Unable to change virtual machine power state: Failed to connect to peer process."

Still stuck there... any help would be much appreciated...
galileux

---

### Post by galileux on 2007-05-04
Hi
looks like I'm starting and ending this thread by myself, since THERE IS a solution to the issue above. I am posting it for the benefit of anyone who may get as desperate as I did with this annoying problem.

Looks like feisty-amd64 does not install some 32-bit libraries by default as you are expected to be running a 64-bit OS.

Nevertheless, if you try to power up a 32-bit virtual machine (not tried with a 64-bit VM) some libraries appear to be missing.

The solution is to install the 32-bit libraries required by Ubuntu to recognize the 32-bit operating system. Proceed as follows:

sudo apt-get install ia32-libs

No need to reboot nor to log out.

The 32-bit virtual machine should now power up.
Thanks a lot to Michael who provided this fix on the VMware Workstation forum!

Regards
Galileux

---

### Post by cmkoch on 2007-05-14
thank you, this saved me a lot of time :)

---

### Post by tormentum on 2007-05-16
Mate, it worked perfectly.  Many thanks!

---

### Post by galileux on 2007-05-17
you are welcome, my friends.

---

### Post by pjos on 2007-07-06
Once again, thanks, solved my problem.

---

### Post by nardo on 2007-07-09
Problem solved, thanks!!!!!

---

### Post by curtwillis on 2007-07-13
turns out this fix is needed with rtm and 64 bit versions when running on 64bit platforms.

curt

---

### Post by dhave-dhave on 2007-07-13
Thanks a ton. I have a new Kubuntu 64bit installation, and for the life of me I couldn't get VMware workstation 6.x to launch. This fix did the trick.

---

### Post by rasdol on 2007-07-16
Sorry but i don't understand what fix? I have ubuntu 64bit and couldn't run guest OS in vmware...
Heeeeeelp!

Added:
I didn't see the string "sudo apt-get install ia32-libs"... Is it relevant for 64 bit ubuntu (guest OS - XP)

---

### Post by Havoc911 on 2007-07-16
> **rasdol said:**
> Sorry but i don't understand what fix? I have ubuntu 64bit and couldn't run guest OS in vmware...
Heeeeeelp!

Added:
I didn't see the string "sudo apt-get install ia32-libs"... Is it relevant for 64 bit ubuntu (guest OS - XP)

Rasdol, this fix is entirely relevant for 64-bit Ubuntu systems. I myself have just tried this fix on 64-bit Kubuntu and it worked perfectly.

To the person who posted the fix: thank you so much for being kind enough to share your wisdom with us.

---

### Post by rasdol on 2007-07-16
Thanks... i will try it in the evening

...
All works great. thanks

---

### Post by galileux on 2007-08-18
> **Havoc911 said:**
>  To the person who posted the fix: thank you so much for being kind enough to share your wisdom with us.

Well, it looks like I made quite a few of you happy :-)

My "merit" however, is just that of having "ported" the solution into Ubuntuforums, since the solution was already available in the VMware Knowledge base:

[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=4483512&sliceId=1&docTypeID=DT_KB_1_1&dialogID=17554589&stateId=0%200%2017552174](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&docType=kc&externalId=4483512&sliceId=1&docTypeID=DT_KB_1_1&dialogID=17554589&stateId=0%200%2017552174)

and also in this VMware forum thread:
[http://www.vmware.com/community/thread.jspa?messageID=637170](http://www.vmware.com/community/thread.jspa?messageID=637170)

Definitely two resources worth checking out, if you get trouble with VMware under Linux.

All the best
Galileux

---

### Post by wdr1 on 2007-11-06
This also did the trick for me in Gutsy Gibbon.  Thanks much!

-Bill

---

### Post by mufflon on 2007-12-10
Oh, man! Thanks a ton!
I'm not a newbie in any way and still got seriously stuck on this. (contradiction in words?)
I've been nagging my co-worker that he should switch to 64-bit ubuntu. 
And he finally agreed. So when he was home sick I reinstalled his machine for him.

It's identical to the one I'm using at work (except that it has 1Gb more RAM which, in this
case, is totally irellevant). Now, I'm a linux-lover, so I use the host-OS whenever I can.
My co-worker on the other hand just uses linux as a host. He does all his work in one of his virtual machines. 
Because of that I already had the IA32-libs for other reasons. And VMware workstation works like a charm for me with a brand new tweaked kernel, and it would not work for him no matter what I did.

You just made my day. Seriously. I'm at home trying to fix it over VPN and your solution helped me out a lot!

---

### Post by NiceInVT on 2008-01-12
Problem FIXED.

System:  Dell Inspiron 1720
Linux Version: Ubuntu 7.10
Error Message: Failed to connect to peer process
Corrected by:    Install ia32-libs by running from command line:  "sudo apt-get install ia32-libs" 

Thank you all very very very very very very much.

-A

---

