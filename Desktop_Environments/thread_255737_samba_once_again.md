---
title: "samba once again"
date: 2006-09-11
forum: Desktop Environments
---

### Post by sefs on 2006-09-11
I need help i have been trying to get this thing working for goodness knows how long.  I can't find the solution to my problem.

I've set up samba ... I can see windows shares and log in correctly from ubuntu to windows, but going from windows to ubuntu i get an error path //xxx.xxx.xxx.xxx does not found or is not a directory.

How can i browse shared folders on ubuntu from a windows machine.

Thanks.

---

### Post by MetalMusicAddict on 2006-09-11
Have you added your user on windows to your Ubuntu box? Also you have to add them as a network user. To do that, from a terminal type **sudo smbpasswd -a** (Put user name here) then it will ask you for a password you want to use. If you do those 2 things you should be golden.

---

### Post by sefs on 2006-09-11
> **MetalMusicAddict said:**
> Have you added your user on windows to your Ubuntu box? Also you have to add them as a network user. To do that, from a terminal type **sudo smbpasswd -a** (Put user name here) then it will ask you for a password you want to use. If you do those 2 things you should be golden.

No that didnt work.

---

### Post by MetalMusicAddict on 2006-09-12
Do you have Samba and smbfs installed on your ubuntu box? What are the permissions on the shares you have setup? Are you in the states?

---

### Post by sefs on 2006-09-12
> **MetalMusicAddict said:**
> Do you have Samba and smbfs installed on your ubuntu box? What are the permissions on the shares you have setup? Are you in the states?

Nope not in the US.

the folder I am sharing is called "myshare"

its located in my home folder of the main ubuntu user.

It has permissions of 777

the smb.conf file share part looks like this... where <username> is a place holder for my real username.

[myshare]
    comment = Network Share
    path = /home/<username>/fsh_share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = <username>
    force group = <username>
    ;available = yes
    ;public = yes
    writable = yes

I have samba and smbf installed yes.  I did it following this guide....  [http://ubuntuforums.org/showthread.php?t=202605&highlight=smb](http://ubuntuforums.org/showthread.php?t=202605&highlight=smb)

What i cant understand is why i can see windows but windows cant see me.

Does encrypted passwords have anything to do with it? I saw that in some reading I was doing this morning but wasnt sure.

One silly question.... I have also seen something about mounting shares.  Do i have to do anything special to mount a folder I have shared? to make it accessible on the LAN in ubuntu? or is this automatic?  For example.  I have shared the folder but do i have to do something else with it.



Thanks.

---

### Post by MetalMusicAddict on 2006-09-12
Really this should be easier than the guide says. Ubuntu runs my server and 2 windows boxes connect no sweat.

What flavor of Ubuntu are you running? Ubuntu, Kubuntu, Xubuntu? Dapper, Hoary, Breezy? Im just tryin to get a start point for you.

---

### Post by sefs on 2006-09-12
> **MetalMusicAddict said:**
> Really this should be easier than the guide says. Ubuntu runs my server and 2 windows boxes connect no sweat.

What flavor of Ubuntu are you running? Ubuntu, Kubuntu, Xubuntu? Dapper, Hoary, Breezy? Im just tryin to get a start point for you.

I'm on Ubuntu Dapper Drake 6.06.1 LTS

If the kernel ver. is important i'll put that up as well as soon as I get home.

But am glad to hear that it actually works. so something is worng somewhere with my setup.

---

### Post by Amorphous_Snake on 2006-09-12
> **MetalMusicAddict said:**
> Have you added your user on windows to your Ubuntu box? Also you have to add them as a network user. To do that, from a terminal type **sudo smbpasswd -a** (Put user name here) then it will ask you for a password you want to use. If you do those 2 things you should be golden.

Thank you. Thank you. Thank you.
You saved my day. I have been trying to overcome this "password" thing for months now. Now I can call myself officially an Ubuntu user!!!

Thanks again. And I hope the original poster finds the answer he/she is looking for.

---

### Post by sefs on 2006-09-12
> **Amorphous_Snake said:**
> Thank you. Thank you. Thank you.
You saved my day. I have been trying to overcome this "password" thing for months now. Now I can call myself officially an Ubuntu user!!!

Thanks again. And I hope the original poster finds the answer he/she is looking for.

This is off topic...but was the problem you were trying to solve one where when you double click on a share it dosnt pop up a password and username box?

---

### Post by Amorphous_Snake on 2006-09-12
Yes. In Windows, when I click on the Ubuntu box in My Network Places I am asked for a username and a password. I tried everything. Really everything! Until METALMUSICADDICT mentioned the smbpasswd -a command.

Do you have the same problem?

---

### Post by sefs on 2006-09-12
> **Amorphous_Snake said:**
> Yes. In Windows, when I click on the Ubuntu box in My Network Places I am asked for a username and a password. I tried everything. Really everything! Until METALMUSICADDICT mentioned the smbpasswd -a command.

Do you have the same problem?

Not really.  why i asked is because i thought it was unsafe to have shares that were not password protected. For example if a network aware trojan gets unto a machine with a file share thats not protected by a password then it seems that this way makes it easier for the trojan to propagate across a network.  If however to get into a share you need to supply a username and password then that makes it more difficult.   Note that I am no expert but thats how it appears to me.

---

### Post by sefs on 2006-09-12
Metal some more info...i've been messing around....

with wins enable i can doubl-click on the linux share i see in the windows neighbour hood and it can browse the share.  NB that I had to enable wins to do this in the smb and then go into the network properties on the windows machine and specify a wins server.

If i disable the wins support in smb on linux machine and remove the wins ip from the propertis on the windows box...then I have to use the ip address of the machine...the net bios name no longer works (anyway around that?)  So althought the share showes up when double clicking on it... it gives a not accessible or directory not found or a similar error.

I also realised that I think i have to have netbios over tcpip selected on the windows box for the share to even show up.


Linux box
----------
going the other way now...on the linux box the windows shares never show up if i open nautilus and go to the network menu item, however if i select the location menuitem a path bar appears and I can type smb://ip.of.windos.machine/sharename ... and it goes to the windows share folder.   Why o why dosnt it simply just show up in the nework neighbourhood thing as an avaialbe share?

Thanks.

---

### Post by sefs on 2006-09-14
I am down to the last hurdel.

What I did was remove wins support from samba, and remove the wins ip address from the windows machines.

Next I installed winbind and added wins to the end of the hosts line in /etc/nsswitch.conf

What that did was allow me to use the windows netbios names in ubuntu.  Got that tip from elsewhere on the forum. 

also resolved misconfiguration of policies in firestarter that was also the cause of some of the problems.  Windos shares now appare correctly in nautilus and are browsable.

The last problem that remains is this....

windows sees the unbuntu share and displays it in the neighbourhood.  However double clicking on it gives you the venerable "\\ubuntunetbiosname is inaccessible. Share name or computername cannot be found"

I can how ever access the ubuntu share if i use the ip address of the machine.

I know if i were to re-enable wins in samba to act as a wins server this will solve the problem.  But I do not want or need a wins server running.  I know they must be a diffrent simpler way to do this.

The problem here looks like the ubuntu netbios name is simply not being resolved on the windows machines ... yet the correct netbios name is appearing in the neighbourhood.  I can ping the ubuntu machine from windows via IP but not the netbios name.  I can ping the windows machines from ubuntu by either IP or nebios.

What could be the problem at the windows end that they would not recognise the netbios name of the ubuntu box.

Thanks.

---

### Post by sefs on 2006-09-15
Latest....

Every thing works fine from Samba Server end.  All computers show up or disappear as they come and go.  Can double click on associated icon in nautilus network browser and reach the share.  Can also ping all machines using their netbios names from samba server.


From windows all machines show up.  But can only reach other machines which run windows.  Although samba servers show up when I double click on the said samba server I get an error as seen in the attached pictur.

Any ideas how to get the windows machines to access the ubuntu machine via the icon in their network neighbourhood?

Computers in listed order are of type
1) Ubuntu /w samba
2) Windows 2000
3) Windows 98
4) Windows 98

See pics attached for examples.

Thanks.

---

### Post by S1NGH on 2006-09-15
> Yes. In Windows, when I click on the Ubuntu box in My Network Places I am asked for a username and a password. I tried everything. Really everything! Until METALMUSICADDICT mentioned the smbpasswd -a command.

Do you have the same problem?
smbpasswd -a <insert computer username here, not computer name, but log on name> just thought to add that, incase some people don't know.

---

