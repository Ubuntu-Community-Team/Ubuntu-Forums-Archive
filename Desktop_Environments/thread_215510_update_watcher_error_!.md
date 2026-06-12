---
title: "update watcher error !"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Pixie25 on 2006-07-14
this is completely redicule ! 
when I log into ubuntu it enounces me I have new software updates. 
I press it to update the computer and I get the folowing msg window:
"The following problems were found on your system:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
And so I did... but it still continues. 
The second thing is it tells me: 
Could not upgrade the system! Fix broken packages first.
The third thing after the upgrade manager opens is that it tell me I have another program trying to deal with packages and I should close it. ](*,) 

This is a clean install ! I just installed it yesterday. The only packages I added are: ndiswarpper-user-space and amarok.

after that I used ndiswrapper to install and run a driver for Edimax EW7108PCg PCMCIA wirelles card. 
After connecting to the internet I've downloaded all the updates and then this message appeared after reboot.

So I hope not to many details, but I hope you'd be able to help.
Thanks.

---

### Post by philippe_carlo on 2006-07-14
Try to run this once (but close the update manager first)

sudo apt-get install -f amarok

---

