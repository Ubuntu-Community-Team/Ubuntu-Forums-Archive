---
title: "Cant setup SMB on second HD"
date: 2010-03-07
forum: Desktop Environments
---

### Post by codeblue2k on 2010-03-07
So am building a file server to hold all of my movies. Im at the point where I just need to setup a shared folder. Well for some reason I am not able to create a share on my 2nd HD. I was able to create a test share that existed on my main hard drive by adding the following to smb.conf

```
[share]
   comment = Codeblues Pictures Share
   path = /home/codeblue/Pictures/Test_Share
   browsable = yes
   guest ok = yes 
   read only = no
   create mask = 0755


```

Well I figured that worked why not just change the setting for the movies share that is on my second hard drive. I changed it to:

```
[movies]
   comment = Movie Share
   path = /media/sda1/multimedia/movies
   browsable = yes
   guest ok = yes 
   read only = no
   create mask = 0755
```

But when I try to access the Movies share I get a "Windows cannot access \\192.168.1.100\movies\"

But at the same time im still able to access the first share that I created on my main hard drive. Any ideas as to what im missing??

Oh im running Ubuntu 9.10 and its a completely fresh install with just Samba installed

---

### Post by Morbius1 on 2010-03-07
Maybe it's not a samba issue, maybe it's a linux permissions issue.

What is the output of:

[B] ls -dl /media/sda1/multimedia/movies

[/B]And is /media/sda1 a linux ( ext3 / ext4 ) or Windows ( ntfs / FAT32 ) formatted partition ?

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> Maybe it's not a samba issue, maybe it's a linux permissions issue.

What is the output of:

[B] ls -dl /media/sda1/multimedia/movies

[/B]And is /media/sda1 a linux ( ext3 / ext4 ) or Windows ( ntfs / FAT32 ) formatted partition ?

The output is
```
drwxr-xr-x 3 codeblue codeblue 4096 2010-03-07 10:19 /media/sda1/multimedia/movies

```

The drive is a linus ext3 partition


This is what I get when I run that same command on the main hd share

```
drwxrwxrwx 2 nobody nogroup 4096 2010-03-07 09:33 /home/codeblue/Pictures/Test_Share

```

---

### Post by codeblue2k on 2010-03-07
> **codeblue2k said:**
> The output is
```
drwxr-xr-x 3 codeblue codeblue 4096 2010-03-07 10:19 /media/sda1/multimedia/movies

```

The drive is a linus ext3 partition


This is what I get when I run that same command on the main hd share

```
drwxrwxrwx 2 nobody nogroup 4096 2010-03-07 09:33 /home/codeblue/Pictures/Test_Share

```

Does the nobody/nogroup thing have to do anything with it?

I added and it didnt help 
```
force user = nobody and force group = nogroup
```

---

### Post by Morbius1 on 2010-03-07
Well, you'll never get guest write access to that share because the target directory is set to read only: 
> drwxr-x[COLOR=Blue]r-x[/COLOR]But you should still get read access.

The other thing that I wasn't smart enough to mention in my original response is that the entire path to movies has to be readable and executable or else guest will never get to the target. Does

/media/sda1
/media/sda1/multimedia

All have a "r-x" at the end of a ls -dl command?

As to your second post, if anything you want to go the other way. Right now the only person who is allowed to write to that folder is 
codeblue. So add **force user = codeblue** to the definition.

[COLOR=Blue]EDIT: Just make sure you restart samba again: **sudo service samba restart**[/COLOR]

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> Well, you'll never get guest write access to that share because the target directory is set to read only: 
But you should still get read access.

The other thing that I wasn't smart enough to mention in my original response is that the entire path to movies has to be readable and executable or else guest will never get to the target. Does

/media/sda1
/media/sda1/multimedia

All have a "r-x" at the end of a ls -dl command?

As to your second post, if anything you want to go the other way. Right now the only person who is allowed to write to that folder is 
codeblue. So add **force user = codeblue** to the definition.

[COLOR=Blue]EDIT: Just make sure you restart samba again: **sudo service samba restart**[/COLOR]

/media/sda1 gets ```
drwx------ 4 codeblue codeblue 4096 2010-03-07 08:48 /media/sda1/

```

and /media/sda1/multimedia gets ```
 drwxr-xr-x 4 codeblue codeblue 4096 2010-03-07 08:51 /media/sda1/multimedia
```

So im guessing that /media/sda1 has the wrong permissions, right? How do I change them? When I look at the drive properties It says permissions cant be loaded for some reason

---

### Post by Morbius1 on 2010-03-07
Yep. That's it I think. You know the **force user = codeblue** may be the easiest way to resolve this issue. Have you tried that?

If you don't want to do that you need to set the entire path to at least 755:

** sudo chmod -R 0755 /media/sda1**

I was somewhat hesitant to recommend that because I don't know what else you have in that partition.

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> Yep. That's it I think. You know the **force user = codeblue** may be the easiest way to resolve this issue. Have you tried that?

If you don't want to do that you need to set the entire path to at least 755:

** sudo chmod -R 0755 /media/sda1**

I was somewhat hesitant to recommend that because I don't know what else you have in that partition.

There is nothing on the HD at all. Its an older terabyte drive that I want to keep all my movies on. The only folder on it is Multimedia

---

### Post by Morbius1 on 2010-03-07
Well, to accomplish everything that you want as defined by your share definition - guest access with write ability then I would change permissions to 777 :

**sudo chmod -R 0777 /media/sda1**

---

### Post by codeblue2k on 2010-03-07
Hey I think that did it!!!!! FANTASTIC... thanks so much!!

Can you answer one more question for me..

what does "2" stand for in ```
"drwxr-xr-x 2"
```
That number changes depending on what folder im looking at... ive seen a "3" and a "4"

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> Well, to accomplish everything that you want as defined by your share definition - guest access with write ability then I would change permissions to 777 :

**sudo chmod -R 0777 /media/sda1**


Im going to leave the guest account with read only permission, so 0755 right?

I also just tried mapping the share from another computer with my codeblue account and I cant seem to access it , but I can see the contents with a guest account. Any thoughts on that? I need 755 for guests and 777 for my codeblue

---

### Post by Morbius1 on 2010-03-07
You lost me on that last post. It's probably the way I've been answering your questions so far.

The force user in the share definition creates a mask that makes the remote guest appear to by codeblue to linux - as far as that specific share is concerned. Since codeblue has read / write access and since samba is allowing read / write authority, all guests will have read / write ability. This has nothing to do with what account you use on the remote machine to access the share.

If you have permissions set to 0755 then you will need force user = codeblue to write.

But If you have permissions set to 0777 then you do not need force user.

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> You lost me on that last post. It's probably the way I've been answering your questions so far.

The force user in the share definition creates a mask that makes the remote guest appear to by codeblue to linux - as far as that specific share is concerned. Since codeblue has read / write access and since samba is allowing read / write authority, all guests will have read / write ability. This has nothing to do with what account you use on the remote machine to access the share.

If you have permissions set to 0755 then you will need force user = codeblue to write.

But If you have permissions set to 0777 then you do not need force user.

hmmmm... well the permissions are set to 0755 and force user = nouser. With it setup like this I can access the share but not write to it. If I try to map the share from another computer using my codeblue account i prompts me for my UN and PW and then denies me.

When I change force user = codeblue i am no longer able to access the share with the guest account at all. Very weird

Ok I went back and changed the permission to 0777 for everyone. I dont care if there is write permission on the share. Its in my own personal LAN and I will be backing of the data to another drive.

---

### Post by Morbius1 on 2010-03-07
Could you post the output of the following command please:

**testparm -s**

And are you using Gnome?

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> Could you post the output of the following command please:

**testparm -s**

And are you using Gnome?

Yes I am using gnome.

So I can access the share if i "\\192.168.1.100\movies" with no issue. Dosnt even ask for a UN and PW which is fine. But if I want to map the drive from my windows computer using the same location "\\192.168.1.100\movies" it asks me for a UN and PW, but my codeblue account gets denied.

```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Processing section "[movies]"
Processing section "[music]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[share]
	comment = Codeblues Pictures Share
	path = /home/codeblue/Pictures/Test_Share
	read only = No
	create mask = 0755
	guest ok = Yes

[movies]
	comment = Movie Share
	path = /media/sda1/multimedia/movies
	force user = nobody
	force group = nogroup
	read only = No
	create mask = 0755
	guest ok = Yes

[music]
	comment = Music Share
	path = /media/sda1/multimedia/music
	force user = nobody
	force group = nogroup
	read only = No
	create mask = 0755
	guest ok = Yes

```

---

### Post by Morbius1 on 2010-03-07
What exactly does this mean:
> So I can access the share if i "\\192.168.1.100\movies" with no issue.From where? From Windows? From another Linux machine? 

> But if I want to map the drive from my windows computer using the same location "\\192.168.1.100\movies" it asks me for a UN and PW, but my codeblue account gets denied.Nobody should be asking you for a password - it set to allow guest access.

And I've lost track here. Is /media/sda1/multimedia/movies set to 777 or 755?

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> What exactly does this mean:
From where? From Windows? From another Linux machine? 

Nobody should be asking you for a password - it set to allow guest access.

And I've lost track here. Is /media/sda1/multimedia/movies set to 777 or 755?

HAHA sorry about that. I set the drive to 777 using ```
sudo chmod -R 0777 /media/sda1
```

and from my testparm -s output in my last posting you can see what my smb.conf has in it

All of my other computers are running Windows, so when i type "\\192.168.1.100\movies" from "Run" I have no issues. It does not ask for a UN or PW. But if I go into My Computer in Windows and map the drive using "\\192.168.1.100\movies" it asks for a UN and PW and denies me when I give it my codeblue credentials

---

### Post by Morbius1 on 2010-03-07
> All of my other computers are running Windows, so when i type "\\192.168.1.100\movies" from "Run" I have no issues. It does not ask for a UN or PW. But if I go into My Computer in Windows and map the drive using "\\192.168.1.100\movies" it asks for a UN and PW and denies me when I give it my codeblue credentials       I have no idea. Don't know why there would be a difference in methods used to access the share. If it's asking for a password then give it one.
>  it asks for a UN and PW and denies me when I give it my codeblue credentialsAre you talking about the username and password that codeblue uses to login to the box or codeblue's samba password. In other words did you do a:

**sudo smbpasswd -a codeblue**

---

### Post by codeblue2k on 2010-03-07
> **Morbius1 said:**
> I have no idea. Don't know why there would be a difference in methods used to access the share. If it's asking for a password then give it one.
Are you talking about the username and password that codeblue uses to login to the box or codeblue's samba password. In other words did you do a:

**sudo smbpasswd -a codeblue**

Um I didnt know there was two different passwords. Im talking about the password that I use to log into the OS, the same one that I game it when installing.

---

### Post by codeblue2k on 2010-03-07
That seemed to do the trick! I can not map the share on my windows pc's and add/remove data.

Now if I ever want to make it so the guest account is only read only, how difficult would that be? If it is then I wont worry about it since like I said before its all within my personal little network behind my firewall.

Thanks again so so so much for your help. I truly do appreciate it. One day I will get this linux thing :)

---

