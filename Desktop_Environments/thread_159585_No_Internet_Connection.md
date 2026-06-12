---
title: "No Internet Connection"
date: 2006-04-13
forum: Desktop Environments
---

### Post by ccoppenbarger on 2006-04-13
After several days of configuring my Windows XP Pro SP2 to have enought disk space and be defragged, I finally installed Ubuntu as the second OS in order to have dual-boot system. No problem. Got both OSes installed on same machine now.

Here's a problem,
I have no internet connection.
I can't find info in the help. I searched here, but couldn't find anything.
DHCP was not installed on installation, so I don't know if I should install it or not. I connect to the internet through my ethernet port through a high speed connection.
Also, I can't get the synaptic package manager to load, or the Network Configuration manager to load.

Any ideas?
Thanks,
Chris

---

### Post by Ramses de Norre on 2006-04-13
Insert ubuntu install cd
do ```
sudo apt-get install dhcp3-client dhcp3-common
```
If it can't find the packages try ```
sudo apt-get install dhcp dhcp-client dhcp-dns
```
You can also set up internet with static ip and fill in the needed values yourself.

---

### Post by prophet on 2006-04-13
not an expert but if it's a simple problem - make sure you use a sudoer account to launch synaptic. - if you don't know what a sudoer is, just use the account first automatically created when you installed ubuntu. When it asks for your password give it the password for the account just mentioned. I suspect for same problem it will work with network config manager too.

---

### Post by xenmax on 2006-04-13
ccoppenbarger: Did you do an expert install? Apparently in an expert install, the first user accout is not in sudoers list by default. 
EDIT: I myself did an expert install and initially could not access any app from System->Admin as normal user until this fix.
Try this thread: [http://www.ubuntuforums.org/showthread.php?t=146859]("http://www.ubuntuforums.org/showthread.php?t=146859")
check out codejunkie's post which shows how to add your user account to sudoer's list for expert install case and otherwise. 
Hope this helps.

---

### Post by ccoppenbarger on 2006-04-13
Thanks for all the help. The first time I installed Ubuntu, I did not have it connected to my ethernet cable and so installed it off-line. DHCP did not get installed that time. I did a reinstall this time and now have internet. I'll look at the forum about adding my user to the sudoer list. That seems to be the problem I'm having now. Thanks.

---

### Post by ccoppenbarger on 2006-04-13
The sudo thing worked for me now as well. Looks like I'm all set. Thanks. Off to play around.

---

