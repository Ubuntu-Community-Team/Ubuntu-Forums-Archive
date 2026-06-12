---
title: "[SOLVED] How to share files using Samba (the more secure way)"
date: 2005-10-15
forum: Desktop Environments
---

### Post by arnieboy on 2005-10-15
Written by **[vnbuddy2002]("http://ubuntuforums.org/member.php?u=13391")**

Required tools:

- samba
- samba-common

To install: ```
sudo apt-get install samba
```


Once the server is install, issue the following command:
```
sudo gedit /etc/samba/smb.conf
```
Make the following changes:
> workgroup = WORKGROUP
underneath it, add

netbios name = name_of_your_server (no spaces)

For example:
> netbios name = kenny_smb_server 
Make sure "security" is set to "user".

Scroll down until you see "[homes]", set:
> browseable = yes
writable = yes
Then save the changes.


Finally, create a SMB user, make sure this account exists on your Ubuntu Linux.
```
sudo smbpasswd -a `whoami`
```
and set your password

OKAY, you are finished configuring Samba on your Ubuntu Linux.

------------------------------------------------------------------------------------------------
Winblowz
------------------------------------------------------------------------------------------------

There are two ways to access it:

Method 1:
My network places > Entire Network > My Windows Network > Workgroup

Method 2:
in the address barm type in "\\[whatever you named the Samba server]". From my example above, I used "\\kenny_smb_server\".


You should see a folder call "homes", click on it, and it will ask you for your username and password, enter your Ubuntu Login Name and whatever you choose for the password when you used command "smbpasswd". You should be able to take it from here.

Keep in mind that you are sharing, /home/[login name]/*

------------------------------------------------------------------------------------------------
Linux
------------------------------------------------------------------------------------------------
Install smbfs:
sudo apt-get install smbfs
mkdir Network
```
sudo mount -t smbfs -o username=[network user],password=[network pass],uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //[whatever you named the Samba server]/[network user] /home/`whoami`/Network
```
Example:
```
sudo mount -t smbfs -o username=kenny,password=test,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //kenny_smb_server/kenny /home/`whoami`/Network
```

---- END

---

### Post by Stadsport on 2005-10-15
Thanks for the guide. I followed it, but have two questions
-When browsing the network (workgroup) from a Windows machine, my Linux machine (named Desktopsmb in Samba) doesn't appear. Typing \\Desktopsmb returns the error, "The network path was not found." Any ideas?

-Is there a way to share printers with SAMBA? Sorry if this is a different guide, but my mom uses my printer. ;D

Thanks!

---

### Post by arnieboy on 2005-10-15
[QUOTE=Stadsport]Thanks for the guide. I followed it, but have two questions
-When browsing the network (workgroup) from a Windows machine, my Linux machine (named Desktopsmb in Samba) doesn't appear. Typing \\Desktopsmb returns the error, "The network path was not found." Any ideas?

-Is there a way to share printers with SAMBA? Sorry if this is a different guide, but my mom uses my printer. ;D

Thanks![/QUOTE]
u will find the answer to this question as well as to others in the original thread which was written for hoary:
[http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)
use the "search this thread" tool

---

### Post by amorangi on 2005-10-16
apt-get install smbfs comes back with "package smbfs has no installation candidate". Can someone please help?

---

### Post by majikstreet on 2005-10-16
thanks so much....

why is this in gnome howtos?

---

### Post by arnieboy on 2005-10-16
[QUOTE=amorangi]apt-get install smbfs comes back with "package smbfs has no installation candidate". Can someone please help?[/QUOTE]
uncomment universe and multiverse in */etc/apt/sources.list* and do a ```
sudo apt-get update
``` after that

---

### Post by arnieboy on 2005-10-19
can a moderator kindly move this to the general HOWTO's forum? I wrote this here by mistake.

---

### Post by Binnikemasken on 2005-10-24
Thanks. Did every step there and it works fine. Not the way I wanted, but I'll be able to configure some things later on :)

---

### Post by dgermann on 2005-10-25
Hi--

Not sure what I need to do, but I have a suspicion it relates to smbfs:

Have a samba server named samba1 which has been serving up files to Win95 and WinXP machines for a couple years. I went to ubuntuguide.org and it says to enter this command to mount them on my new Ubuntu box:

```
sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777
```

However, what I get is 
> mount: wrong fs type, bad option, bad superblock on //192.168.0.1/linux,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


and dmesg | tail produces a bunch of setkeycode errors.

I am able to mount nfs shares, which is another way to do this, I suppose, but since I already have samba running on the server, it seems like I am opening another security hole to have nfs open, too.

BTW, there is a graphical controller for samba: it is called swat.

So what have I missed to be able to mount the samba shares from the server on my local Ubuntu box?

Do I need to install samba and smbfs on my local ubuntu box? Both or just one? Maybe they are already there. Do I need to start either one? How? Neither one shows up on ps -aux.

Thanks!

{Edit:}

I did install smbfs using Synaptic and that solved my issues here. Now I just need to figure out what the difference is between the options you used and the ones on ubuntuguide.

Thanks!

---

### Post by FLeiXiuS on 2005-10-25
You may also want to add 

```
*/etc/samba/smb.conf*
[global]
...
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
...

```

```
sudo cat /etc/passwd | sudo mksmbpasswd > /etc/samba/smbpasswd
sudo chmod 600 /etc/samba/smbpasswd
sudo smbpasswd username
```

This would provide SAMBA users with encrypted passwords over the network.  :-)

---

### Post by foxy123 on 2005-10-25
[QUOTE=FLeiXiuS]You may also want to add 

```
*/etc/samba/smb.conf*
[global]
...
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
...

```

```
sudo cat /etc/passwd | mksmbpasswd > /etc/samba/smbpasswd
sudo chmod 600 /etc/smbpasswd
sudo smbpasswd username
```

This would provide SAMBA users with encrypted passwords over the network.  :-)[/QUOTE]
```
$ sudo cat /etc/passwd | mksmbpasswd > /etc/samba/passwd
bash: /etc/samba/passwd: Permission denied
```
:(

---

### Post by arnieboy on 2005-10-25
[QUOTE=foxy123]```
$ sudo cat /etc/passwd | mksmbpasswd > /etc/samba/passwd
bash: /etc/samba/passwd: Permission denied
```
:([/QUOTE]
try doing it as su
```
sudo passwd root
su
cat /etc/passwd | mksmbpasswd > /etc/samba/passwd
```

---

### Post by foxy123 on 2005-10-25
[QUOTE=arnieboy]try doing it as su
```
sudo passwd root
su
cat /etc/passwd | mksmbpasswd > /etc/samba/passwd
```[/QUOTE]
thanks a lot, I did though
```
sudo -s
```

which seems the same...

---

### Post by glug101 on 2005-10-26
[QUOTE=foxy123]```
$ sudo cat /etc/passwd | mksmbpasswd > /etc/samba/passwd
bash: /etc/samba/passwd: Permission denied
```
:([/QUOTE]
Errr... am I missing something here?  The original post says
> sudo cat /etc/passwd | mksmbpasswd > /etc/samba/smbpasswd
But foxy123 seems to be typing in
> sudo cat /etc/passwd | mksmbpasswd > /etc/samba/passwd

That little 'smb' at the begining of the file name might be the issue.  Granted though, this is not the error that I would expect...

Another possibility (not likely to help, but might) is to do
> sudo mv /etc/samba/smbpasswd /etc/samba/smbpasswd.backup
and then try recreating the file.  (though I must admit I'm a little stymied meself ;) )

Good Luck!  :D

---

### Post by foxy123 on 2005-10-26
[QUOTE=glug101]Errr... am I missing something here?  The original post says

But foxy123 seems to be typing in


That little 'smb' at the begining of the file name might be the issue.  Granted though, this is not the error that I would expect...

Another possibility (not likely to help, but might) is to do

and then try recreating the file.  (though I must admit I'm a little stymied meself ;) )

Good Luck!  :D[/QUOTE]

maybe the original post was edited, because as I remember I just copied and pasted the code.

---

### Post by foxy123 on 2005-10-27
I wonder why samba does not start automatically. I have to start it with ```
sudo /etc/init.d/samba start
``` every time I boot my laptop...

---

### Post by FLeiXiuS on 2005-10-27
It's smbpasswd.  I never edited that portion.   I just recently edited to add sudo's...

---

### Post by manicka on 2005-11-03
This How-To is also available at the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by davethewave on 2005-11-25
Ok, so what am I doing wrong? :P I click the "Places" menu, "Network servers" and it says "Authentication Required" with Username - Domain - Password, so I enter my Linux login name, the windows shares Domain name (the workgroup name) and the samba password I set as instructed.. it opens the Network File Browser but just sits there for a long time, eventually it comes up with Mshome *which I removed* and my workgroup name. I open my workgroup but it says "Error Displaying Folder" "The folder contents could not be displayed." "Sorry, couldn't display all the contents of "windows Network: workgroupname:. I click "ok" and that's that, no access to shares :( Thanks

---

### Post by deNoobius on 2005-11-26
Moved

---

### Post by polpak on 2005-12-02
The only problem I have with this method is that it requires the user to either have administrative privileges or the samba details (user & password) have to be in a world readable file (/etc/fstab) in order for it to be mounted.

I'm writing a script which will use a user only readable config to mount shares to a given users home directory. Then you can edit /etc/sudoers to specify which users you want to be able to use this script.

If more people are interested I'll post it when I'm done.

If anyone else knows of a way to remove the restrictions above I'd love to hear them.

Basically I feel that so long as the directory the smbfs is mounted to is owned by the user, the user should be able to use mount (without root privileges and without an entry in fstab) to mount it.

---

### Post by mikk0 on 2005-12-10
[QUOTE=foxy123]I wonder why samba does not start automatically. I have to start it with ```
sudo /etc/init.d/samba start
``` every time I boot my laptop...[/QUOTE]
I have the same issue, although I started the daemons manually:
```

sudo nmbd -D
sudo smbd -D
```
Why aren't these daemons added to my init scripts so that they would start automatically?

If I would add them manually, is The Right Thing To Do:
```

sudo ln -s /etc/init.d/samba /etc/rc5.d/S99samba
```
Or what would you suggest?

Mikko

P.S. I have already tried with [COLOR="Blue"]sudo apt-get remove --purge samba samba-client[/COLOR], and then re-installing those, but it didn't solve the issue.
I also used [COLOR="Blue"]sudo dpkg-reconfigure -plow samba samba-common[/COLOR] to set up smbd to run as a daemon instead of getting called by inetd.

There are also confusing things in my /etc/rc2.d and /etc/rc3.d as shows:
```

mikko@mini:/etc/rc2.d$ ls -l
yhteens&#228; 0
lrwxrwxrwx  1 root root  6 2005-12-07 20:30 K09samba -> /samba
```
I wonder why the link to samba is pointing to /samba instead of /etc/init.d/samba?

[COLOR="RoyalBlue"]Edit:

I did the following, and yes, it works =)
```

sudo ln -s /etc/init.d/samba /etc/rc5.d/S99samba
sudo rm /etc/rc2.d/K09samba
sudo rm /etc/rc2.d/K09samba
sudo ln -s /etc/init.d/samba /etc/rc2.d/K09samba
sudo ln -s /etc/init.d/samba /etc/rc3.d/K09samba
```[/COLOR]

---

### Post by mikk0 on 2005-12-10
Actually I was wrong to make the symlink to rc5.d
As I learned today, Ubuntu boots to runlevel 2 instead of 5 (you may confirm this by running the command 'runlevel'), so the correct way to do the link is
```
sudo ln -s /etc/init.d/samba /etc/rc2.d/S99samba
```

Mikko

---

### Post by Dev3684 on 2005-12-11
I am farely new at Linux and I am trying to transfer some files.  I installed Samba following your directions but when I tried to set the password by using 
sudo  smbpasswd -a `password` 
I got..

"Can't load /etc/samba/smb.conf - run testparm to debug it"

Any suggestions?

---

### Post by infoseeker on 2005-12-11
> sudo smbpasswd -a `password` 

Enter your username (not password) :)

#whoami
#sudo smbpasswd -a username

---

### Post by Dev3684 on 2005-12-11
Thanks for the quick reply but I am a noob and need my hand held...(still suffering now on Linux is much better than windows)   Anyway again I tried this.

root@Dev:/home/devin # smbpasswd -a Devin
Can't load /etc/samba/smb.conf - run testparm to debug it

and...

root@Dev:/home/devin # smbpasswd -a `Devin`
bash: Devin: command not found

Is there another way to add users or should I try reinstalling Samba?

---

### Post by Dev3684 on 2005-12-12
Please disregard all my previous stupidity...I reinstalled Samaba and this time actually read the install to find out there is an error when installing from the cd...

Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 64043 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.10-1ubuntu3_i386.deb) ...
Setting up samba (3.0.10-1ubuntu3) ...
Generating /etc/default/samba...
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Can't load /etc/samba/smb.conf - run testparm to debug it
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is there another source for Samba or should I just upgrade to Breezy and use that cd?

---

### Post by dakota34 on 2005-12-20
Arnieboy, not to be a syncophant, but THANK YOU  very much for - once again - documenting/providing the absolute, bar-none, easiest way to do something that would otherwise be daunting if not impossible.  

You have a gift for simplifying complex tasks and instructions, which I think is the essence of empowering not-very-knowledgable Linux users like myself, enabling us to move away from Windows.  

Took me 5 minutes to get rocking and rolling transferring files from a windows pc over to my linux unit bcs of your instructions.:p

---

### Post by DJiNN on 2005-12-22
[QUOTE=dakota34]Arnieboy, not to be a syncophant, but THANK YOU  very much for - once again - documenting/providing the absolute, bar-none, easiest way to do something that would otherwise be daunting if not impossible.  

You have a gift for simplifying complex tasks and instructions, which I think is the essence of empowering not-very-knowledgable Linux users like myself, enabling us to move away from Windows.  

Took me 5 minutes to get rocking and rolling transferring files from a windows pc over to my linux unit bcs of your instructions.:p[/QUOTE]

I must then be on of the thickest people that i know, because after much mucking about, i can't get it to work at all.... :)  I just want to set up a simple Network using a router, but it would seem that "Simple" doesn't enter this particular equation! :)

I shall persevere, but i don't hold out much hope at present. Feeling sorry & sulking....? Heehee.... You bet, but i'll get over it. 

DJiNN

---

### Post by peanut butter on 2005-12-30
just use the internal ip of the server in windows like

\\192.168.1.120

(192.168.1.120 being the ip of your server

---

### Post by eriqk on 2005-12-30
Hmmm.
In windows, entering the name of the server doesn't work. Entering the IP doesn't work, either. Windows doesn't find anything. My Network Places > Microsoft Windows Network > Workgroup doesn't work either.
Searching the other thread Arnieboy linked to offered no solution.
Ports are open in Firestarter. On my Windows box, Kerio would notify me if any traffic happened, but it stays quiet.
I must be missing something, but I have no idea what- I just followed the entire howto again, step by step.

Groet, Erik

---

### Post by dark_mage93 on 2005-12-31
windows can't access the server, just returns "The network path was not found."...tutorial is well written, thanks in advance for anyone who can help me

---

### Post by Pretzal on 2005-12-31
Yeah I cant get it to work either. Ive managed to install samba ok and am trying to get 2 computers to talk to each other.  The desktop is running Ubuntu and the Laptop is running XP. They are connected through a Dlink wireless ADSL Router (G604T) (10.1.1.1). They can happily share an internet connection but cant talk to each other. I can ping the laptop (10.1.1.3) from the desktop (10.1.1.2). The error I am getting at this stage is: 

glasson@Ubuntu:~$ sudo mount -t smbfs -o username=glasson,password=*****,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //ubuntu_samba_server/glasson /home/`whoami`/Network
9368: Connection to ubuntu_samba_server failed
SMB connection failed

Any ideas greatly appreciated.

PS GREAT work on Automatix...brilliant!

edit: have attached a testparm in case that helps:

glasson@Ubuntu:~$ sudo testparm
Password:
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[UbuntuHomeFolder]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = HOME
        netbios name = UBUNTU_SAMBA_SERVER
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        username map = /etc/samba/smbusers
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[UbuntuHomeFolder]
        path = /home
        read only = No
        guest ok = Yes
glasson@Ubuntu:~$

---

### Post by sabitha on 2006-01-01
admin@ubuntu:~$ sudo mount -t smbfs -o username=client,password=fawwaz,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //client_smb_server/client /home/`whoami`/Network
16689: Connection to client_smb_server failed
SMB connection failed

i don't know what's wrong, maybe because i don't know what is my smb_server_name.
than whoe to know what is my smb_server name

---

### Post by Jeeevs2001 on 2006-01-10
Hello, total newbie here! I have managed to get this working 90% but could use a bit of help on the last 10! 

I can see my Ubuntu PC through my Windows 98 Network places, when I click on it it asks for a user name and password. I have created a second Ubuntu user and assigned a smbr password to the second user. I can use this to get access to Ubuntu.

The problem is the folder I get to through network places is empty! Even though I have set up 2 shared folders through Ubuntu (using Administration > shared folders). 

So my question is how do i get the network link to point to the folder i want to share? (this is an issue itself, I have a second hard disk which I have to manually mount each time I log in. This is the disk I want to share and have set it up under Administration > shared folders). 

Hope this makes sense! Any help would be great as this is one of 3 remaining issues preventing me getting rid of Windows completely!

---

### Post by Pretzal on 2006-01-11
Managed to solve my problem...turns out firestarter was blocking the connection from the Laptop running XP. For an explanation of what I did to solve it go here:

[http://ubuntuforums.org/showthread.php?p=646808#post646808](http://ubuntuforums.org/showthread.php?p=646808#post646808)

---

### Post by gatorbrit on 2006-01-21
I configured samba ok in linux, but in windows it does not find the samba folder - this may be dumb, but will samba work on a dual boot machine?  In other words can I use it so that I can read my linux partition when I am running windows (and not running linux - obviously).

Thanks

---

### Post by byen on 2006-01-23
A quick question.
Is there anyway I can restrict the user accessing the samba network to access only one folder rather than the whole home-folder? When the user tries to access the home folder he sees a ton of hidden system files and I just want them to get access to one folder? Can someone please help me in showing the way?
thanks guys. Sorry if Im posting it in the wrong section.

---

### Post by GeirG on 2006-01-26
[QUOTE=gatorbrit]I configured samba ok in linux, but in windows it does not find the samba folder - this may be dumb, but will samba work on a dual boot machine?  In other words can I use it so that I can read my linux partition when I am running windows (and not running linux - obviously).

Thanks[/QUOTE]

Your Linux system must be running for the Samba server to be able to share your files.
To read your ext2 and ext3 partitions from Windows, use something like [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by eriqk on 2006-02-06
Victory!
I'm now listening to a bunch of .oggs from my UbuntuShuttle on my Windows box.
In [another thread]("http://ubuntuforums.org/showthread.php?t=108691"), I learned that Samba as it comes with Breezy is slightly problematic, and that a better way would be to get rid of Samba and Samba_common alltogether. Then download the latest stable Samba and Samba_common from [Samba.org](http://www.samba.org).
I did this:
I got **samba-common_3.0.21a-1_i386.deb** and **samba_3.0.21a-1_i386.deb** from the Samba site.
I installed them with 
```

sudo dpkg -i samba-common_3.0.21a-1_i386.deb
sudo dpkg -i samba_3.0.21a-1_i386.deb

```
Then: 
```

sudo smbpasswd -a [my user name]
[enter password]

```

Next, I went to my Windows machine, and opened My Network Places. In the adressbar I did \\[my IP adress], filled in user and password, and that was it.

Next, I'll make everything secure. Lots of stuff to be read in this thread.

Thanks to I_am_socket for the instructions.

Groet, Erik

---

### Post by dominohc on 2006-02-06
I have 2 network cards in my computer.  One connects to the Internet and one connects to a local switch that connects 3 Windows computers on a network not connected to the Internet.  I am trying to make Ubuntu a server that can get files online and share the files to the Windows computers so they don't have to be online.  All Windows computers are on a Workgroup and talking back and forth fine, but Ubuntu can't see the Windows comptuers or vice versa.  I've tried setting up Samba, but not much luck.  Is there something I need to change because I have 2 network cards installed?  Is Samba only talking to one of the ethernet cards and not the one connected to the local switch?

---

### Post by DDM on 2006-02-06
Has anyone found a solution to the inexplicable linux-to-linux super slow Samba problem? This guide worked perfectly for me except for one thing: I cannot seem to transfer more than 100KB/sec using this method. 

Granted, I am using a less than perfect wireless connection, but I can transfer at least 1.2MB/sec using an apache server instead of Samba. If anyone has a solution, please post it.

---

### Post by thetragedyofhumor on 2006-03-25
hey, sorry to dredge up an old thread, but i was going through this howto on the unoficial starter guide, and i ran into a roadblock: i cant seem to edit /ect/samba/smb.conf...

EDIT: i figured out how to allow myself to log in as root, and iv edited the .conf as per HOWTO instructions, but my windows machine (lets call it win1) isnt picking up the linux machine at all. i dont know if this matters or not, but im using an ethernet connection to physicaly bridge the machines, but even when i ethernet win1 to another windows machine, the network manager says the connection has 'limited or no connectivity' and it allways displays zero packets recived (wich i know to be BS, as iv played starcraft over a lan with win1)

could my windows machine just be messed up, or did i set up the .conf wrong? maybe it would help if i posted the .conf file? (of corse id edit out the notes in it)

---

### Post by solusrex on 2006-07-19
damn! the first arnieboy howto that didn't work for me!

i follow it to the letter and get 'ERRnosuchshare'.

I have used linux for almost 5 years and have never ever been able to get a folder share going, that's why I switched to macs at home (so I can enjoy my evening away from a console...). Alas, at work it isn't an option. Looks like I'll have to keep plugging and unplugging an external drive (thank god they seem to work perfectly in Linux these days)

---

### Post by bdmp on 2007-01-07
This worked perfectly for me. Thanks

---

### Post by sieg on 2007-02-28
I have a dual boot server machine with windows and ubuntu called FASOLT. When booted under ubuntu, this is the samba server.

I have another windows clent machine called KING which had mapped a drive K: to FASOLT when FASOLT was booted under windows. I had mapped it using a windows/cygwin bash prompt on KING.

The above procedure would not work until I killed the cygwin/windows bash process on KING.  After that KING could see the samba shares on FASOLT! 


Thanks,
Siegfried

---

### Post by richardhsu on 2007-11-17
Thank you. It was helpful.

---

### Post by Roasted on 2008-01-17
I'm slightly lost. I followed the how-to on the first page. On my XP Pro laptop, I typed in \\sambadesktop @ the run prompt and typed in my information. A window appeared, with "Printers and Faxes" listed. Nothing else. 

This doesn't route to my home directory. I can't see any of my information I have in my home directory on my desktop.

What do I need to edit? There's a few lines I wasn't positive about whether or not I should touch them.

---

