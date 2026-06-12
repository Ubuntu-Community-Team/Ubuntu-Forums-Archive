---
title: "Samba Issues with 11.10"
date: 2011-10-20
forum: Desktop Environments
---

### Post by mshaffer on 2011-10-20
Let me preface by saying that I've been using Linux in some way for the last 15 years...yes, I began tinkering when I was 10. The reason that I need to switch to Linux is that the small business is growing, and we're reaching the connection limit placed by Windows 7 Professional.

I've run into a problem that I've never seen before. I installed 11.10 on my small business server, it's overkill for its purpose.

It consists of:
i5 2500k
Gigabyte Z68XP-UD3P
2x4GB Corsair 1600MHz RAM
Onboard Video
Running a Raid10 (0+1) 4x 1TB WD Enterprise Drives
OCZ SSD for Boot Drive

I can install and update 11.10 without any issue save for a small video driver concern. Considering it's a file server, I'm not concerned with this.

I install samba with:

sudo apt-get install samba samba-common system-config-samba
I try and edit the samba share in two different ways. First by:

Alt+F2 then typing gksu system-config-samba
I'm prompted to enter my password, and nothing ever opens/happens.

I've also tried editing the conf file manually with:

Quote:
sudo gedit /etc/samba/smb.conf

Adding the lines:

[MyShare]
path = /media/samba/
browseable = yes
read only = no
guest ok = yes
force user = samba
force group = samba

I then try and connect with ip or computer name from either Windows XP or 7. This works perfectly fine on a Q9550 and Gigabyte EP45-UD3P with a dedicated Graphics card, I did it yesterday. But it does not work on the machine above. Any and all help would be greatly appreciated.

---

### Post by weedwacker on 2011-10-20
I'm having similar problems with Samba. I got some part to work---sometimes. One of my computers (with 11.10 Ocelot installed) dual boots with Windows. This was a clean install of Ocelot. 

Using Samba from this computer to connect to my other computer (dual boot with 11.04 Natty and 11.10 Ocelot) worked somewhat yesterday. Today, not.

If I am on the computer that dual boots with Windows and I am using Ocelot and click on **Network** in Nautilus it may "see" my other Network locations, but then when I try to get to the other machine Share the throbber spins forever and a day and gives me a "fail" message.

When I am on the Natty/Ocelot dual boot and using Natty 11.04 and try to access the Windows/Ocelot machine share - bam! Like lightening I get it.

One thing I have discovered: Using the Ocelot "Network" and right clicking on the other machine share **Properties** and looking at "Open With" it tells me to "Select an application to open/and other files of type "(null) document" and then: No applications available to open "unknown"

Compare this with what I get when I use the Natty 11.04 Samba Network: The "Properties > Open With" of any network share I "see" says: Select an application to open/and other files of type "folder" and in the box below there is and icon of a folder and the words "Open Folder" and also a selection button.

For some reason Ocelot 11.10 is not setting up "Open Folder" in these Properties.

Hoping for a resolution soon as I do like the new Ocelot.

---

### Post by mshaffer on 2011-10-20
Let me ask you this, are you able to open the gui editor for samba shares in 11.10?  Everytime I try I enter my password and hang.

---

### Post by weedwacker on 2011-10-20
OK, this is what I just got a tip about:

in File System/etc/samba: I opened smb.conf with "gksudo nautilus" and I re-arranged the order of this:
     

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

to this:

 # What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = bcast lmhosts host wins

I saved the file and samba appears to be working on Ocelot just fine. Oh, be sure to remove that ";" just before the word "name".

Will keep you posted if I have any problems.

---

### Post by mshaffer on 2011-10-20
I've never heard of anything like that, but I'll try anything once.

---

### Post by jimerman on 2011-10-20
You have a lot more Linux experience than I, but I recently solved my Samba issues by installing the "Samba Server Configuration" admin utility.  It is a GUI that guided me on setting up my shared folders.  In my case, my shared folders were an NTFS drive used for backup from a time when the server used to be Windows, so I had to add automount info to the fstab to ensure it mounted after a reboot.  However, after configuring with the GUI it has worked great for over a month.

I should add, to get to the GUI, it is System / Administration / Samba (from the classic GUI, not Unity).

---

### Post by mshaffer on 2011-10-20
Thank you all for your help, I've also concluded that I can't stand Unity.  From a user standpoint I can see it being a pleasure to use, but from the Admin side, it's a nightmare.

Nothing is where I think it should be, and I'm missing some very simple things.  After I get 11.10 reinstalled, I'm going to install gnome-shell and setup auto login to it.

I'll be sure to post back here when everything is working it can't be this hard.  I ain't let a machine beat me yet.

---

### Post by mshaffer on 2011-10-28
So I have part of my share working.  From 11.10 I can browse to any and all of my Windows machines and see their shares.  if I do a smbtree in terminal, they all show up.  From the Windows side, I can see the initial shared folder, S4A-Users, but I can't see any subfolders, or files.  Below is my smb.conf as has been copied from gadmin.

Honestly, I'm sure there are a lot of useless lines, but I am skeptical of removing any, until I have a working share.  I believe it to be a permissions problem, but I'm not certain.  I've chown & chmod the mount, which is NTFS with the -R option.  I am implementing these shares in an environment where where all connected computers are seen to be safe, so guest sharing should be fine.  If you need any other information, please let me know.

> 
[global]
netbios name = S4A-Server
server string = S4A-Server
workgroup = S4A
security = share
hosts allow = 192.168.100.
interfaces = 192.168.100.100
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbgueste
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = lmhosts wins bcast host
wins support = yes
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no
client ntlmv2 auth = no
guest account = nobody

[S4A-Users]
path = /media/Solutions4Automation_/S4A-Users
comment = S4A-Users
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
guest only = yes
public = yes
printable = no
locking = no
strict locking = no
create mask = 0777


---

### Post by mshaffer on 2011-11-03
Does anyone have any ideas?  Right now I'm quite stuck.

---

