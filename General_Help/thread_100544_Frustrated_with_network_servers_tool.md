---
title: "Frustrated with network servers tool"
date: 2005-12-07
forum: General Help
---

### Post by bruce147 on 2005-12-07
Getting nowhere except frustrated with Places>Network Servers. How do I show my network neighborhood, my local windows shares? I installed linneighborhood and I can't find it anywhere on the menu system and issuing linneighborhood at the command prompt line does nothing. Where is it? It listed some samba requirements. How do I check if I have them all?

When I open network servers, it asks for some unknown password. I learned from the forum that by removing my user name I can get in after a while. It even showed all my windows shared folders on one occasion. Some I could click and open. Some appeared to locked, though I have set no passwords. 

FRUSTRATION

---

### Post by flopsy on 2005-12-07
You need to issue LinNeighborhood (yes, with that weird capitalisation). I think stock breezy meets at the requirements listed. Try setting a password on your Windows account; Windows XP, at least, won't let you in otherwise.

The Network Servers thing is rather flakey. Try this instead: open your Home Folder. Press Ctrl-L. Enter smb://192.168.1.3 (replace with the IP of your Windows computer) in the address bar that pops up.

Use the smbclient tool for testing. Replace with your Windows IP and your Windows username.
```

gee@daisy:~$ smbclient -L 192.168.1.3 -U molly
Password:
Domain=[DAISY] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        Shared          Disk
        Music2          Disk
        Video           Disk
        Downloads       Disk
        Documents       Disk
        IPC$            IPC       IPC Service (daisy server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (daisy server (Samba, Ubuntu))
        molly           Disk      Home Directories
Domain=[DAISY] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            DAISY

``` 

File sharing is a huge PITA if the Windows machine is doing the serving; I had difficulty getting it working between two XP machines (and it still wasn't quite right). It's spot on with Samba; persevere!

---

### Post by bruce147 on 2005-12-07
> **flopsy]You need to issue LinNeighborhood (yes, with that weird capitalisation). I think stock breezy meets at the requirements listed. Try setting a password on your Windows account said:**
> 
Thanks, that opened the program interface. It didn't really do anything helpful though. I will look into this more, maybe.

[QUOTE=flopsy]The Network Servers thing is rather flakey. Try this instead: open your Home Folder. Press Ctrl-L. Enter smb://192.168.1.3 (replace with the IP of your Windows computer) in the address bar that pops up.
Thanks! That opened up the windows folder and I could open files on the windows xp machine. I guess this will have to do for now. Best advice so far!!!

[QUOTE=flopsy]Use the smbclient tool for testing. Replace with your Windows IP and your Windows username.
```

gee@daisy:~$ smbclient -L 192.168.1.3 -U molly
Password:[/QUOTE]
Here is what I issued and got. Not so useful. I wonder if my problem is that I have no user name or password setup on the xp home machine, and samba expects something?
bruce@ubuntu:~$ smbclient -L 192.168.2.31
Password:
Domain=[SUKI] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
[CODE]
        Sharename       Type      Comment
        ---------       ----      -------
        My Documents    Disk
        CanonPIX        Printer   Canon PIXMA iP4000
        IPC$            IPC       Remote IPC
        SharedDocs      Disk
        Photos (G)      Disk
        print$          Disk      Printer Drivers
        Backups         Disk
        MYDOCS (I)      Disk
        Programs (Z)    Disk
        Music Suki      Disk
        H               Disk
        SpaceSuki       Disk
session request to 192.168.2.31 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[SUKI] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
bruce@ubuntu:~$
```

---

