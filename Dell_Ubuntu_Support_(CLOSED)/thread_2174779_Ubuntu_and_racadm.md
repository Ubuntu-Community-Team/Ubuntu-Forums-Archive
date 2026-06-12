---
title: "Ubuntu and racadm"
date: 2013-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nc64 on 2013-09-16
Hello.
I recently purchased a used poweredge 1850 server and it came with a DRAC card.  After wiping the HDD and installing ubuntu server 12.04.3 LTS amd64 on it, I am now trying to gain access to the DRAC which I believe is version 4.  I have properly configured the DRAC to use it's own IP on my LAN and when I point my browser to the IP address, I am greeted with the DRAC login page (it has the dell logo and everything).  However, after trying the credentials of root/calvin, I was denied access.  So I think that the previous owners had set their own password.  After doing some reading, it appears that I can reset the credentials to the default using 
```
racadm config -g cfgUserAdmin -o cfgUserAdminPassword -i 1 newpassword


```
but upon entering the command, I get this error:
```

bash: /usr/sbin/racadm: No such file or directory

```
This holds true even if I run
```

sudo su

```
prior to running the *racadm* command.

If, however, I run 
```

sudo racadm config -g cfgUserAdmin -o cfgUserAdminPassword -i 1 newpassword

```
there are no errors.  Yet, when I try to log into the DRAC via the web interface using the credentials of root/newpassword I am still not granted access.

I installed the dell utilities via the guide at [https://wiki.ubuntu.com/HardwareSupportMachinesServersDellNotes](https://wiki.ubuntu.com/HardwareSupportMachinesServersDellNotes).  I first tried to install the 64 bit version that is on the dell repositories, but after that was unsuccessful, I just followed the guide verbatim.  No errors were produced in either case.  I even followed the information at the bottom of the guide by executing 
```

sudo pppd /dev/ttyS1 1382400 crtscts noipdefault noauth lock persist connect 'chat -v "" CLIENT CLIENTSERVER "\\c"'

```
but obviously, replacing the */dev/ttyS1* with the correct information for my system.

```

ls -l /usr/sbin/ | grep racadm

```
yields 
```

-rwxr-xr-x 1 root    root        87930 Sep 16 04:03 racadm

```

I have tried these credentials after each attempt of changing the password:
root/calvin
root/newpassword
admin/calvin
admin/newpassword

All have been unsuccessful.  What is the next course of action that I should take?

---

