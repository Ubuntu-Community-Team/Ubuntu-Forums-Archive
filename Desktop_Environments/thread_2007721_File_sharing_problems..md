---
title: "File sharing problems."
date: 2012-06-21
forum: Desktop Environments
---

### Post by Darnthingy on 2012-06-21
I am not sure this is the right place but here goes.

I have been trying to get filesharing to work, but failed.
I have a machine running Lubuntu 11.10, and want to share files from it to other computers in the network, primarily win7, winxp and *buntu.
I have tried with samba, but failed. I also tried with nautilus, but failed.
I been reading some threads in this forum, followed them, but failed.

Funny thing is, I have a machine running Ubuntu 11.10, and there filesharing works without any kind of problem at all, and took just a minute or two to get it working.
Is Lubuntu really that different from Ubuntu?

Any help or pointers would be very appreciated.
Thanks in advance.

---

### Post by nothingspecial on 2012-06-21
Hi, see this thread

[http://ubuntuforums.org/showthread.php?t=1623346](http://ubuntuforums.org/showthread.php?t=1623346)

---

### Post by Darnthingy on 2012-06-21
Thanks.
I have already seen that, tried it and failed.
But I guess I should use that thread instead of starting a new one?

---

### Post by nothingspecial on 2012-06-21
Starting a thread for your own issue is fine. What do you mean by it failed?

---

### Post by Morbius1 on 2012-06-21
> I have tried with samba, but failed.Please post the output of the following commands:
```
testparm -s
``````
hostname
```> I also tried with nautilus, but failed.Please post the output of this command:
```
net usershare info --long
```And finally post the output of this command to see what kind of errors you get:
```
smbtree
```

---

### Post by Darnthingy on 2012-06-21
Well.. Windows can see the computer, and the shares, but can not reach it.
*buntu can see the computer, but not the shares.
That is how far I have come as of now.

---

### Post by Darnthingy on 2012-06-21
Long post..

testparm -s gives this:


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Publikt]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ARBETSGRUPP
	server string = %h server (Samba, Lubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[Publikt]
	path = /home/darn/Publikt
	read only = No
	guest ok = Yes

[share]
	path = /mnt/part/share
	read only = No
	guest ok = Yes


hostname:

bloaty


net usershare info --long:


[share]
path=/mnt/part/share
comment=
usershare_acl=Everyone:R,BLOATY\darn:F,
guest_ok=y

[publikt]
path=/home/darn/Publikt
comment=
usershare_acl=Everyone:R,BLOATY\darn:F,
guest_ok=y

And smbtree gives this:


ARBETSGRUPP
	\\SUNGMEE-PC     		
	\\MEDINATOR      		medinator server (Samba, Ubuntu)
		\\MEDINATOR\print$         	Printer Drivers
		\\MEDINATOR\files        	
		\\MEDINATOR\IPC$           	IPC Service (medinator server (Samba, Ubuntu))
	\\GAYMERION      		
		\\GAYMERION\C$             	Default share
		\\GAYMERION\ADMIN$         	Remote Admin
		\\GAYMERION\D$             	Default share
		\\GAYMERION\IPC$           	Remote IPC
	\\BLOATY         		bloaty server (Samba, Ubuntu)
		\\BLOATY\Deskjet-F300-series	HP Deskjet F300 series
		\\BLOATY\print$         	Printer Drivers
		\\BLOATY\Publikt        	
		\\BLOATY\share          	
		\\BLOATY\IPC$           	IPC Service (bloaty server (Samba, Lubuntu))

---

### Post by Morbius1 on 2012-06-21
** Your smb.conf appears to be textbook correct.
** smbtree lists the shares in Bloaty without problems or errors.
** You do have one issue though:

Shares created in smb.conf and shares created through Nautilus are both samba shares but created using 2 different methods and defined in 2 different places. You will note from your output that the specifications for those two types of samba shares don't match. I would get rid of one or the other. For example go back into Nautilus and just "unshare" /mnt/part/share and /home/darn/Publikt.

Aside from that it appears that nothing is wrong on the server end of this excepts maybe Linux permissions. Run the following commands and see if the entire path to the shared folders allow guest access:
```
ls -al /mnt/part/share
``````
ls -al /home/darn/Publikt
```If all of that checks out then run smbtree on another Lnux machine in your network and post those results.

---

### Post by Darnthingy on 2012-06-21
I removed the nautilus share. Still does not work.

smbtree on this machine gives this..


ARBETSGRUPP
	\\SUNGMEE-PC     		
	\\MEDINATOR      		medinator server (Samba, Ubuntu)
		\\MEDINATOR\print$         	Printer Drivers
		\\MEDINATOR\torrent        	
		\\MEDINATOR\IPC$           	IPC Service (medinator server (Samba, Ubuntu))
	\\GAYMERION      		
		\\GAYMERION\C$             	Default share
		\\GAYMERION\ADMIN$         	Remote Admin
		\\GAYMERION\D$             	Default share
		\\GAYMERION\IPC$           	Remote IPC
	\\BLOATY         		bloaty server (Samba, Ubuntu)
		\\BLOATY\Deskjet-F300-series	HP Deskjet F300 series
		\\BLOATY\print$         	Printer Drivers
		\\BLOATY\Publikt        	
		\\BLOATY\share          	
		\\BLOATY\IPC$           	IPC Service (bloaty server (Samba, Lubuntu))


I noticed one thing tho, this machine does not appear when i do smbtree.
Not sure if that is important or not.

---

### Post by Morbius1 on 2012-06-21
Didn't understand your last post:
>  smbtree on this machine gives this..
>  I noticed one thing tho, this machine does not appear when i do smbtree.

What machine are you running on?

---

### Post by Darnthingy on 2012-06-21
This machine is Slappy, a laptop running Lubuntu 11.10.

I ran smbtree on this machine, that is what i pasted in my last post.

---

### Post by Morbius1 on 2012-06-21
So you have 3 Linux machines:
MEDINATOR
BLOATY <--- The one with the shares you want to access.
SLAPPY

I guess it doesn’t matter I'm just trying to get everything straight.

In any event, this output from SLAPPY:
> \\BLOATY                 bloaty server (Samba, Ubuntu)
        \\BLOATY\Deskjet-F300-series    HP Deskjet F300 series
        \\BLOATY\print$             Printer Drivers
        \\BLOATY\Publikt            
        \\BLOATY\share              Also runs without errors and displays the shares on Bloaty. 

So what about Linux permissions. Take this share on Bloaty and post the output:
```
ls -al /mnt/part/share
```

---

### Post by Darnthingy on 2012-06-21
ls -al /mnt/part/share gives me this:

drwxrwxrwx   7 darn darn  4096 2012-06-20 20:05 .
drwxrwxrwx   4 darn darn  4096 2002-01-02 11:12 ..
drwxrwxrwx 107 darn darn 16384 2002-01-02 17:01 ebooks
drwxrwxrwx  73 darn darn  4096 2002-01-02 17:13 film
drwxrwxrwx  64 darn darn  4096 2002-01-02 13:57 games
drwxrwxrwx 430 darn darn 20480 2002-01-02 17:02 music
drwxrwxrwx 107 darn darn  4096 2002-01-02 15:42 prog

---

### Post by Morbius1 on 2012-06-21
Just so you know, your setup and every command I've asked you to run is returning perfect results and exactly the way it should look for this to be successful.

Let's try something different. From Lappy run the following command:
```
gvfs-mount smb://bloaty/share
```If there are errors post them.
If there are no errors then go to your home folder on lappy and look at the contents of the /home/your-user-name/.gvfs folder. Do you see a subfolder labeled:
> share on bloaty

---

### Post by zSeries on 2012-06-21
Hi,

I am no expert but I have samba working across serveral Ubuntu boxes, WinXP and Win7 and am happy with it. It is a fast learning curve when you begin.

You mentioned several times that it does not work with "but failed".

What exactly failed? What messages did you get? Did you go to Places>Network>Windows Network? Can you see any workgroups?

Can you ping between machines using the hostname (not the x.x.x.x ip address)?

If you want to see shares on a Windows 7 machine (I know you didn't mention that but you may want to in the future) you must take Win 7 out of homegroup and put it in a workgroup (google how to do that). You can use WORKGROUP as the name of the workgroup but I made one up and put it in the samba config on all my machines.

I use Samba Server Configuration GUI, cant recall if it gets installed with Samba or not but it a good starting point.

Tony.

---

### Post by Darnthingy on 2012-06-21
gvfs-mount smb://bloaty/share  gives no errors, but there are no subfolders at all in the gvfs folder. Should there be any?

To answer zSeries questions: 
Several things failed: first there was no response at all from samba. I fixed that by installing the missing bits. 
When I got samba running, I configured it according to a forum post, but it is not working as it should. 
On windows I can see the machine and when I try to reach it, I get a login prompt, and that is where it stops..I enter the needed user/password at the login prompt, but it just reloads the prompt, it does not let me in. 
On the buntu machine, I can see the sharing machine, but not the shares. 
No messages, atleast none I know of, have not tried to network via command prompt, only via GUI. 
All machines are in the same workgroup. 
If i try to ping the machine with the hostname, I get: ping: unknown host bloaty

---

### Post by zSeries on 2012-06-21
Try this

Install winbind if it isnt there.

Then update nsswitch.conf
sudo gedit /etc/nsswitch.conf
And put "wins" before "dns" on the hosts line

Can you now ping by hostname? 

If now works.. did you set up the samba users? If not 

sudo gedit /etc/samba/smbusers

Then for each user you must match the Linux id to the Windows id (I think this is required even if they are the same)

Mine contains one line

tony = tony

I hope it works cos I am out of ideas!

---

### Post by Morbius1 on 2012-06-21
>          gvfs-mount smb://bloaty/share  gives no errors, but there are no subfolders at all in the gvfs folder. Should there be any?On whatever machine you ran that command ( Lappy , right ) install the following packages:
```
sudo apt-get install gvfs-backends
``````
sudo apt-get install gvfs-fuse
```Then add yourself to the fuse group:
```
sudo gpasswd -a your-user-name fuse
```Logout and login again for the group membership to take affect.
> On windows I can see the machine and when I try to reach it, I get a  login prompt, and that is where it stops..I enter the needed  user/password at the login prompt, but it just reloads the prompt, it  does not let me in. 
All the shares you created allow guest access so they don't require a user name and password to access. Do you by any chance have the same user name on both the Windows machine and the Bloaty? If for some reason you created a samba password for that user on bloaty and it doesn't match precisely the windows user's password then you will get an error. The best thing to do is remove the samba password for that common user:
```
sudo smbpasswd -x user-name
```>  If i try to ping the machine with the hostname, I get: ping: unknown host bloaty     Don't be too concerned about not being able to ping by hostname. Samba uses a different protocol to discover hosts. Otherwise you would never have gotten this output from Lappy:
> \\BLOATY                 bloaty server (Samba, Ubuntu)
        \\BLOATY\Deskjet-F300-series    HP Deskjet F300 series
        \\BLOATY\print$             Printer Drivers
        \\BLOATY\Publikt            
        \\BLOATY\share                      



And whatever you do do not install winbind.

---

### Post by Darnthingy on 2012-06-21
Morbius1! I could kiss you right now! :D
Thank you ever so much for the help, it works as it should know (does a happy dance)

I can reach the shares from all the machines now.

Btw..I was not sure about the winbind thing, so I wanted to try your way first, and it worked so no need to bind windows. ;)

---

### Post by Morbius1 on 2012-06-21
Whew!

There is one more thing about the samba password thing. 

[COLOR=Blue]**NOTE**[/COLOR]: I'm a firm believer in if it now works don't mess with it but I post this just in case it becomes an issue after a reboot of bloaty:

There is a package that might have been installed on Bloaty that will mess up what you did with the "smbpasswd -x" command and that's libpam-smbpass. 

If you have it installed remove it:
```
sudo apt-get remove libpam-smbpass
```[COLOR=Blue]*Side Note: Winbind is a legitimate thing but applicable only in a network using a Windows Active Directory. Since most home users don't have that it serves no purpose and will eventually do harm.*[/COLOR]

---

### Post by Darnthingy on 2012-06-21
I will make a note of that, thanks. for everything.

Should I mark this a Solved? And how do I do so?

---

### Post by nothingspecial on 2012-06-21
You click thread tools at the top of the thread.

I've done it for you :)

---

### Post by Morbius1 on 2012-06-21
At the top of the page - right above your first post - is something labeled "Thread Tools" . Open that and you should have a mark as solved option.

---

