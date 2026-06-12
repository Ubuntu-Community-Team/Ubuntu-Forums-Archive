---
title: "How do I set my system name &amp; workgroup?"
date: 2013-01-07
forum: Desktop Environments
---

### Post by bamim2 on 2013-01-07
I've just installed Ubuntu 12.10 & I have a couple of things I need to set correctly:
1) I need to change my system name / hostname. 
2) I need to set my workgroup to match my Windows workgroup name. 

If somebody could please walk me through doing those things, I would really appreciate it. 

-THX-

---

### Post by haqking on 2013-01-07
> **bamim2 said:**
> I've just installed Ubuntu 12.10 & I have a couple of things I need to set correctly:
1) I need to change my system name / hostname. 
2) I need to set my workgroup to match my Windows workgroup name. 

If somebody could please walk me through doing those things, I would really appreciate it. 

-THX-

edit the```
 /etc/hostname
``` with gksudo gedit or nano if you do it in CLI

type ```
hostname <name>
``` for a temporary name

you may also want to edit the 
```
/etc/hosts 
```
this for workgroup [http://www.techrepublic.com/blog/opensource/how-to-join-ubuntu-to-a-windows-workgroup/1948](http://www.techrepublic.com/blog/opensource/how-to-join-ubuntu-to-a-windows-workgroup/1948)

---

### Post by slickymaster on 2013-01-07
In a terminal window run the following command:
```
sudo gedit /etc/hostname
```
Next, change whatever in this file to whatever you want it to be and save.

Afterwards run the command below to open the hosts file:
```
sudo gedit /etc/hosts
```
Then change the 2nd line of the file to reflect the new name and save.

Finally, to change your system workgroup name, run the command below to edit samba smb.conf file:
```
sudo gedit /etc/samba/smb.conf
```
Find the following line: **_workgroup = WORKGROUP_** and change the workgroup name to whatever you want it to be and save.

(Note that you have to replace gedit with the name of your textpad)

---

### Post by haqking on 2013-01-07
> **slickymaster said:**
> In a terminal window run the following command:
```
sudo gedit /etc/hostname
```Next, change whatever in this file to whatever you want it to be and save.

Afterwards run the command below to open the hosts file:
```
sudo gedit /etc/hosts
```Then change the 2nd line of the file to reflect the new name and save.

Finally, to change your system workgroup name, run the command below to edit samba smb.conf file:
```
sudo gedit /etc/samba/smb.conf
```Find the following line: **_workgroup = WORKGROUP_** and change the workgroup name to whatever you want it to be and save.

(Note that you have to replace gedit with the name of your textpad)

**gksudo** should be used for gedit and graphical apps and not sudo.

---

### Post by Morbius1 on 2013-01-07
If you are doing this only for Samba compatibility remember that technically samba / SMB knows nothin' about no hostname. Samba cares about netbios name - those are two different things.

Samba does force the netbios name to match the hostname but smb.conf can always be used to override this by adding a line right under the workgroup line:
```
netbios name = something
```[COLOR=Blue]*Just make sure that something is 15 characters or less in length.*[/COLOR]

Your hostname will be one thing and your netbios name ( and the name others will see on the network ) will be something else.

  Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by slickymaster on 2013-01-07
> **haqking said:**
> **gksudo** should be used for gedit and graphical apps and not sudo.

You're right. I stand corrected.

---

### Post by bamim2 on 2013-01-07
Thank you!!

---

