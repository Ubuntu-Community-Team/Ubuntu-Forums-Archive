---
title: "samba still doesnt work"
date: 2006-11-08
forum: Desktop Environments
---

### Post by ilkerka on 2006-11-08
hi 
i followed the howtos on samba and couldn't get it work. I can see my ubuntu desktop from my laptop(via Wireless router) but cannot access it. I ve allowed connection to the desktop from firestarter. Here is my smb.conf file:
```
[global]
    ; General server settings
    netbios name = ilkz
    server string =ilkz
    workgroup = BIZIM
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment ;the
 ;lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    writable = yes
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/ilkz
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ilkz
    force group = BIZIM
available = yes
public = yes
writable = yes

```

any help would be appreciated.

---

### Post by boban on 2006-11-08
Hmm... Your smb.comf looks ok... I don't know if it will help, but this is how I set up my samba. 

1. Install samba (apt-get)
2. Setup shares in smb.conf
3. Add me to samba users (sudo smbpasswd -a boban)
4. Resstart samba (sudo /etc/init.d/samba restart)

And everything is working just fine...

---

### Post by ilkerka on 2006-11-08
thnx somehow i fixed the problem. I had to install something to nautilus to get access to my microsoft folders. I like ubuntu i think linux distros make great competition to windows and mac os. But the problem is that the things that we get granted in windows arent so easily done with linux distros. I am a fairly knowledgable computer user but still i can get stuck with lot of issues in linux. Hopefully distros can mature more and make things easier to setup for all levels of users.

---

