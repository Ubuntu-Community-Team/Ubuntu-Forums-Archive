---
title: "VMWare: how do I share files with Ubuntu host?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by temcat on 2006-06-10
Hi all,

I've installed WinXP as a guest system in VMWare Server, but I can't get it to share files with Ubuntu. I installed samba, set "security = share" in smb.conf, issued "sudo smbpasswd -a temcat" and gave it my password. I chose host-only networking in VMWare and VM setup, but I can't see anything from Windows Network Neighbouhood. Does anybody know a detailed working step-by-step guide on how to set up file sharing with VMWare, preferably in host-only mode (I don't want Windows to have Internet access, and my Ethernet interface is disabled in BIOS since I don't use it)?

Any help will be appreciated. Thanks in advance!

---

### Post by maybe on 2006-06-10
1. Open vmware;
2. Click menu "VM", then select "Settings";
3. Then click "Options" in the new window, and you will see an option "Shared folders Enabled" ;
4. Select it and add some folders;
5. OK, end.

VMWare set these shared folders as network drivers. And you must mapping them in your virtual OS
If you virtual OS is Windows, you can open "My Computer" and click menu "tools", then select "mapping network drivers", you will find those shared folders.

Sorry for my bad English.

---

### Post by Ramses de Norre on 2006-06-10
Is this possible in vmware player too? I don't see a settings menu, I've only got preferences where I can choose how to shutdown and two other things (don't remember) but nothing about file sharing.. I also have no clue on how to get the virtual machine to connect to the host, I don't think that's working now. Does anyone know a good guide on these things? I can't find one..

---

### Post by maybe on 2006-06-10
I am sorry, this is impossible in vmware player. To my knowledge  only  vmware can do this. So you can just try use vmware.

---

### Post by temcat on 2006-06-10
I have VMWare Server, and there's no such option there :-(

I switched to NAT networking, and got Internet connection working (I use ADSL on Ubuntu). Now I can connect to my machine if I enter its IP address directly, but I don't want Windows to connect to Internet.

---

### Post by Ramses de Norre on 2006-06-10
[QUOTE=maybe]I am sorry, this is impossible in vmware player. To my knowledge  only  vmware can do this. So you can just try use vmware.[/QUOTE]
Hmm I'm just experimenting with it, so I'm not going to buy it.

---

### Post by temcat on 2006-06-10
[QUOTE=Ramses de Norre]Hmm I'm just experimenting with it, so I'm not going to buy it.[/QUOTE]

So it's present in Player, but absent in Server?!

---

### Post by Ramses de Norre on 2006-06-10
No no, it's not present in player.

---

### Post by maybe on 2006-06-10
[quote=temcat]I have VMWare Server, and there's no such option there :-(

I switched to NAT networking, and got Internet connection working (I use ADSL on Ubuntu). Now I can connect to my machine if I enter its IP address directly, but I don't want Windows to connect to Internet.[/quote] 
We may have some missunderstandings I think. What I have installed in my system is  "vmware workstation-5.5.1". You may installed other version.
You see the picture:
[IMG]file:///home/jiabin/Desktop/Settings.png[/IMG]

Different versions have different features. But shareing folders in vmware workstation need not connect to Internet. I have chosed host-only network and it works well too.

---

### Post by maybe on 2006-06-10
How can I paste my picture?

---

### Post by temcat on 2006-06-10
OK, I've figured it out.

When using host-only networking, you should have this in smb.conf, among other settings:

interfaces = vmnet1
bind interfaces only = yes
workgroup = <the name of windows workgroup>
netbios name = <hostname of your ubuntu computer>
encrypt passwords = yes
security = share

Then if you set up sharing in Nautilus the usual way, it will show up in Network Neighborhood (select the task named "Show all computers in the workgroup" or smth. like this - I have Russian version of Windows so I don't know the exact name.)

---

### Post by dannymichel on 2007-06-26
> **temcat said:**
> OK, I've figured it out.

When using host-only networking, you should have this in smb.conf, among other settings:

interfaces = vmnet1
bind interfaces only = yes
workgroup = <the name of windows workgroup>
netbios name = <hostname of your ubuntu computer>
encrypt passwords = yes
security = share

Then if you set up sharing in Nautilus the usual way, it will show up in Network Neighborhood (select the task named "Show all computers in the workgroup" or smth. like this - I have Russian version of Windows so I don't know the exact name.)
Any way you can give me directions on creating the workgroups for both Vista and Ubuntu?
Please....
[[IMG]http://www.ny-dev.com/forums/gallery/data/529/medium/Screenshot-5.png[/IMG]]("http://www.ny-dev.com/forums/gallery/data/529/Screenshot-5.png")

---

### Post by dannymichel on 2007-06-26
> **temcat said:**
> OK, I've figured it out.

When using host-only networking, you should have this in smb.conf, among other settings:

interfaces = vmnet1
bind interfaces only = yes
workgroup = <the name of windows workgroup>
netbios name = <hostname of your ubuntu computer>
encrypt passwords = yes
security = share

Then if you set up sharing in Nautilus the usual way, it will show up in Network Neighborhood (select the task named "Show all computers in the workgroup" or smth. like this - I have Russian version of Windows so I don't know the exact name.)

Which one of these files?

---

### Post by fjf on 2007-06-26
AFAIK this only works on VMW workstation (that costs $180).  It works well however in virtualbox 1.4, which is free.

---

### Post by dannymichel on 2007-06-26
> **fjf said:**
> AFAIK this only works on VMW workstation (that costs $180).  It works well however in virtualbox 1.4, which is free.

Can we get a Seamless VirtualBox, RDesktop, Vista 
HOW TO
PLEASE.
I would be regretful

---

### Post by www.floranet.eu on 2007-09-19
Can anyone explain me how to resolve this problem with the remote folder on xp? I receive a message that the share is not acessible.... Help please......

I use this shell command:
 rdesktop -g 1280x1024 -a 16 -r 'disk:home=/home/$USER home' -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 172.16.214.128:3389 -u jmark -p XXXXXXX

There's the image......
[ATTACH]43873[/ATTACH]

---

