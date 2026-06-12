---
title: "Installing Samba"
date: 2006-07-14
forum: Desktop Environments
---

### Post by grmmr797 on 2006-07-14
I have been having trouble installing Samba for some time, but since Update Manager tried to update it, there is apparently a broken pakage, and Update Manager won't let me update any more software until this is fixed.  The exact terminal message is as follows:

(Reading database ... 137197 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3 (using .../samba_3.0.22-1ubuntu3.1_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any suggestions please?

---

### Post by JayCnrs on 2006-07-14
You could try cleaning your cache, go to a terminal or commandline and try typing : **sudo apt-get clean** this should clean your directory /var/cache/apt/archives, then go to that directory and ensure all files are removed. 

Once that is done try removing the samba file by using **sudo apt-get remove samba** this should remove samba, once it is removed we will need to refresh your cache so you will then use **sudo apt-get update** and then try re-installing samba by using synaptic or commandline, if you are going to use the command line you will use **sudo apt-get install samba** 

HTH

---

### Post by boxarocks on 2006-07-14
Tried to remove samba and got the following error:

~$ s[COLOR="Red"]udo apt-get remove samba[/COLOR]
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing samba (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
~$ Errors were encountered while processing:
 samba

Not sure where to go from here...

---

### Post by JayCnrs on 2006-07-15
Is Samba running when you are trying to remove Samba, try running:

**sudo /etc/init.d/samba stop**

Then try installing samba by using **sudo apt-get install samba** see if this works, you have cleaned out the old archive files?

---

### Post by John Jason Jordan on 2006-07-15
> **JayCnrs said:**
> Is Samba running when you are trying to remove Samba, try running:

**sudo /etc/init.d/samba stop**

Then try installing samba by using **sudo apt-get install samba** see if this works, you have cleaned out the old archive files?
I am having the same problems. I have used Ubuntu-64 on my laptop since Hoary and never had a problem connecting to my Windows 2000 desktop. The last time I connected was about a week ago. But now I get nothing. Neither computer can even ping the other via IP address.

I tried reinstalling samba via Synaptic, but I got:

"E: /var/cache/apt/archives/samba_3.0.221ubuntu3.1_amd64.deb:
subprocess new pre-removal script returned error exit status 102."

I tried sudo apt-get clean, followed by apt-get remove and apt-get install, but it made no difference. I still get the error message and samba still does not work. 

Any further suggestions?

---

### Post by JayCnrs on 2006-07-18
Well, I'm running out of ideas, I had this problem over a year ago with apt-get. I believe I have layed out all the steps I took, I'm not sure what is missing above, anybody else have any ideas?

---

### Post by blucht on 2006-07-21
I had the same problem. Fixed it by following the advice in [this]("http://ubuntuforums.org/showthread.php?t=214848&highlight=pre-removal+script+error+exit+status+102") thread. It was something about a dangling symlink (don't actually know what that means...) but the suggested fix was:
$ cd /etc/rc2.d
$ sudo rm K09samba
$ sudo ln -s ../init.d/samba K09samba
and then trying to update again. Worked like a charm.

---

