---
title: "New User Need Help..."
date: 2007-06-02
forum: Desktop Environments
---

### Post by jduped on 2007-06-02
Mr. Newbie here...

Here's the Dilemma, I'm trying to make the switch, and the more I dig/research/play, I truly enjoy what Linux has to offer, but I'm not able to do what I'd like to.

My network consists of the following from the outside in.

Modem
Linux Router
switched 10/100/1000
Media Gate > [http://www.airlinktek.com/english/prod_mg35.htm](http://www.airlinktek.com/english/prod_mg35.htm)
NAS
switched 10/100/1000
SOHO STATION 1
SOHO STATION 2

thats the layout...no comes the issues.

Modem > no issue
Linux Router > no issue
switched 10/100/1000 > no issue
Media Gate > no issue
NAS >>> ISSUE #1 
switched 10/100/1000
SOHO STATION 1 ISSUE #3, #4, #5
SOHO STATION 2


**ISSUE #1 - NAS O/S HELP**

no issue with windows server 2003 or XP...
I want to make the NAS box more functional then just data storage.
its a relatively high end machine running a SATA II hardware RAID 5 (4 drives)
for stability sake I have a dedicated PATA 133 drive running the o/s I'm using an ASUS M2N-MX board using the on-board raid controller. currently one large 1 TB drive is functional and viewable in windows and linux IE: see ISSUE #2

What I would like to do, in a perfect world

Is have the NAS setup up for fax, ftp, folder sync, data store, to run out of the way along side my custom router, and run the os off USB Thumb drive. I can do this with windows short of the Thumb drive...well its do-able but I'm not a fan of BartPE outside of live cd's.

so far I have loaded kubuntu / ubuntu / ubuntu server 64-bit (all 7.04) as live cd's they can see the NTFS formated raid partition as a drive but can not mount it, I've tried several solutions I read in the forums and the internet to no avail, as a side note, the PATA drive formatted as NTFS that I use to run the o/s can be mounted.  

**ISSUE #2 - Mounting Network Shares / Viewing Network Shares**

Now part of the reason I didn't do the switch to Linux sooner was short of routers, and the associated parts and programing for a net appliance's I wasn't to familiar with the desktop/workstation functions and win32 alternative programs.  Through the last week of me using the Ubuntu family I have solved countless issues and have been biting off piece by piece of the elephant I call Ubuntu.  I have read up on samba, fstab, openssh...and still I'm stuck.  I have shared music files on my data server at location 172.20.20.150 for example and the shared folder is music.

I can view it, I can temp mount it and save a net link

*Note in the example names and places have been changed to protect the innocent.
view it by 
>>smb://172.20.20.150/music

temp mount it
>>
mkdir /home/test_dummy/music
chmod 0777 /home/test_dummy/music
mount -t cifs //172.20.20.150/music /home/test_dummy/music -o user=linux,password=(super)star!88#

Net link (not sure of the name...just a globe icon that opens the smb refrence.)
>>
just enter the info in the wizard as a smb share and a icon is created that links to the share.

Those work...what I want does not.

I have been playing in /etc/fstab

the command that comes up here and abroad is 

in my application I have used this one and a few variants including gid/uid username and passwords.
//172.20.20.150/music /home/test_dummy/music smb defaults 0 0

I'm a little lost on this, as the mount comes up, and shows up like it would in windows if you mounted a drive, but inside is nothing...nothing I tell you!  I've removed passwords, tried guest accounts, no firewalls, that I can think of as to why they won't talk in that manner.  A side issue that may be related, when I try to talk to my NAS box, through the samba share folder it can see my network but it always times out when I try to browse it.  Another thing I find a little strange is my netbios name doesn't come up, I have to browse by IP, I don't know if this is linux or if I need to enable something stupid and small to solve all my woes... Any help on this front, would be, Just great! :D

**ISSUE #3 - Music Software**

If your reading this book and have made it here...good for you. It shows dedication. ;)
I use Media Monkey in windows for all my music needs, its a great fully functional software, for windows use.

Since diving in to the ocean of ubuntu, I've tried Amarok, Banshee, Exaile, BMP, Madman and all I really need is something that will host a library, read ID3v2 tags, read ratings, and pull in the music via the network share.  Now since I can't mount a network share permanently I've had little success, as described above, I can temp mount the drive, and I can connect via smb:// if I browse directly.

with Amarok since I played with that one the longest, I can pull in all my music via the add stream option and the smb:// link input, issue with this, no file info till you play the song, I have 20,000 tracks so its a little problematic to do it that way, though it does work, and I found that solution here.  Option 2 of temp mounting the drive I can scan the folder I mount and presto files come in, two smaller issues here, some of the files fail to import stating meta related issues, no album covers come in, no ratings.  Some of these things could be related to my network card on the mobo, from what I've read I've seen an issue stating under heavy loads the integrated nic drops packets...the problem is the process works in windows so I'm thinking its more software then hardware...though I do have another nic standing by.  

**ISSUE #3A**

I also really like the Madman software I was a little disappointed that its not being developed right now.  I have some issues with that software in that I can't get back to the main library screen after I start some tracks playing...

**ISSUE #4 - Desktop themes**

Tonight I was playing around with getting some cool skin's going on kubuntu and I seen this thing on youtube...
[http://www.youtube.com/watch?v=ovWU-N1o58k](http://www.youtube.com/watch?v=ovWU-N1o58k)
does any one know what theme this guy is using? and how to get it loaded.

From reading the post's I believe I need Beryl, and Emerald Themer...I'm pretty much suck there.

**ISSUE #5 - Norton Ghost like back up for linux?**

Ok I'm almost done dumping my brain here...I usually have Norton Ghost on the machines I run so I can deploy them, reload them, and really get them up and running faster then just reloading the os and all the softwares.  Is there anything like this for Linux where I can get something perfect and lock it, or set it up so that I could make my own kind of o/s disk, as I said new to linux I'm sure there something but I haven't been able to get much info on it.

To any and all that have read this, and taken the time to reply I thank you from the bottom of my cockles, or perhaps my sub-cockle area.

:p

---

### Post by llamakc on 2007-06-02
Don't include passwords when posting here. One of your samba mount lines has a password.

---

### Post by jduped on 2007-06-02
I put a disclaimer on it...none of them are legit, I did also include a note.
The only reason I have them there is so if some one provides me some help they can use them in there example...its easier to work things if they have names even if they happen to be fake, the ip ranges and shares are different as well.

> *Note in the example names and places have been changed to protect the innocent.

---

### Post by llamakc on 2007-06-02
Yeah I saw those. As a suggestion you could just mask the passwords with XXXXX, and I think most people would get the drift. I made the suggestion because many people new to Linux will often make that mistake.

---

### Post by llamakc on 2007-06-02
When you reboot and the share does not mount, who is the owner of the directory where you want the share to mount at?

---

### Post by llamakc on 2007-06-02
You could also specify in your fstab the 'noauto' option, and somewhere near the bottom of /etc/rc.local place:

mount /path/to/share/you/want/to/mount

as mentioned here:

[https://launchpad.net/ubuntu/+source/hal/+bug/44874/comments/48](https://launchpad.net/ubuntu/+source/hal/+bug/44874/comments/48)

---

### Post by jduped on 2007-06-02
I'm new to linux but not computers...I will in the future mark passwords with xxxx, as for the share its located currently on a windows 2003 box, I'll try the rc.local approach I didn't even think of that, for my router thats where I loaded all my iptables rules.  I'll try it out.

---

### Post by llamakc on 2007-06-02
What I meant by that, is the ownership of the target directory where you want to mount the Windows share TO. Who owns it?

---

### Post by jduped on 2007-06-02
soho station #2 running kubuntu 7.04 is where I want to mount the windows share...I aquired a used laptop today...running ubuntu 7.04 and I'll want simular mounts on this system as well.

---

### Post by llamakc on 2007-06-03
Okay, are you going to answer the question?

What is the ownership of the target directory on the box? I'm not asking about the Windows share, but the directory where you want to mount to, the same directory that works via the commandline but failed to mount after rebooting.

---

### Post by jduped on 2007-06-03
> **llamakc said:**
> Okay, are you going to answer the question?

What is the ownership of the target directory on the box? I'm not asking about the Windows share, but the directory where you want to mount to, the same directory that works via the commandline but failed to mount after rebooting.

its the prime account.  In both situations.

---

### Post by llamakc on 2007-06-03
That's not what I am asking you. What are the UID/GID for the directory? How about its parent directory?

---

### Post by hsweet on 2007-06-03
Partimage works rather like ghost.

---

### Post by llamakc on 2007-06-03
> **llamakc said:**
> That's not what I am asking you. What are the UID/GID for the directory? How about its parent directory?

Do this: Open a terminal. type:

ls -l /

if /WINDOWSSHAREDIRECTORY is directly under the / root directory (not root's home, but the root directory of the o/s); or ls -l /parentdirectory/

if its at /parentdirectory/WINDOWSSHAREDIRECTORY

---

### Post by jduped on 2007-06-04
First off I appreciate your help,

I typed in the command it didn't list anything of note, I did it as root and again it didn't list anything of interest.  I'm working on the laptop with a virgin o/s I was playing with beryl on the other pc and it wouldn't load to the desktop any more.

I can get to the share if I browse directly, and I'm assuming I can still mount, the uid / gid you are asking for is this the local station or on the server where the files are shared?  I have read only enabled on the music share I'm running and its available via the guest profile, when I get this working I'll be securing it with a password but for set-up I'm trying to figure out with out dealing with that side.

Now I have a question since I can mount via the terminal and it'll stick till I reboot, if I put it in the rc.local file does that file execute as root or as my active user?

Keep in mind the only thing I used Linux for before hand was a router appliance, and those are easy and solid, same with openbsd, but I've only ever dealt with windows networks for sharing and there mind numbingly easy to set-up.   I've got my win2k3 box up sharing and good to go with the only reaming windows client on my home network.  I also have as mention prior a little media gate that can also connect and read the drive.

In a perfect world from begging to end what would you do to mount a single ntfs formatted network share permanently in a ubuntu / kubuntu environment?

options I've been considering if fstab won't do the job...

a script either as a click option on the desktop or added to rc.local.

when I use fstab and use a variety of different attacks I always get a permission error if I try the right click and mount option, and when I remount the drive with mount -a command I get a windy error stating the drive are configured incorrectly.

As a side note...I'm running a terabyte RAID 5 server  I wanted to set it up with ubuntu instead of win2k3 but in ubuntu it wouldn't mount the drive or even recognize it, its hardware RAID using an onboard nforce sata configuration...I don't think it should be a factor but just something else to throw into the mix.

---

### Post by llamakc on 2007-06-04
I have been trying to address PRECISELY the problem you're having. I don't understand why you won't cut/paste the output of the commands I've requested. Until you share your files, I can't help. Hopefully somebody else may.

Good luck.

---

### Post by jduped on 2007-06-04
I think I get what your getting at, I'll try and mount the drive and give you a screen shot of it, I have other obligations atm so I'll do it tonight and paste what I believe your looking for.

---

### Post by llamakc on 2007-06-04
I AM NOT asking you to mount the drive. I am ASKING YOU what are the permissions and ownership for the directory WHERE you mount the share TO.

This is getting absurd.

---

### Post by jduped on 2007-06-05
well there's seems to be a communication issue, I'm not sure what your asking for and you seem to be getting impatient with me. if you could please leave this one to some one who wants to help.

Thanks.

---

