---
title: "Samba makes documents read only"
date: 2009-01-12
forum: General Help
---

### Post by handyguy33 on 2009-01-12
Hi there. I've got a problem sharing files with samba. I can't get some of the windows machines to connect to my shared folders unless i # in front of force users and force groups. now everybody can see the shared folders, but all of the documents they open are read only. Here's my smb.conf Tell me what you think.

[global]
    ; General server settings
    netbios name = AEServer
    server string =
    workgroup = AE
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = yes
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
    ;browseable = yes

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

[SharedFiles]
    path = /home/administrator/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0775
   # force user = administrator
   # force group = AE

---

### Post by handyguy33 on 2009-01-19
Well, it's been over a week and nobody here seems to know anything about samba. In the interests of getting things done, I've re-installed windows and set up a shared folder there. i'm not giving up on Ubuntu, but the lack of responses here is a bit discouraging.

---

### Post by dcstar on 2009-01-20
> **handyguy33 said:**
> Well, it's been over a week and nobody here seems to know anything about samba. In the interests of getting things done, I've re-installed windows and set up a shared folder there. i'm not giving up on Ubuntu, but the lack of responses here is a bit discouraging.

There are numerous HOWTOs on Samba, as well as many posts on various sharing issues already in this forum.

Just because no one spoon-fed you an answer doesn't mean the answers are not out there.

---

### Post by handyguy33 on 2009-01-20
Oh I'm well aware of the resources available. But if any of that had panned out, I wouldn't be posting here. I knew that the only way to get a response after a week of nothing was to make a disparaging remark. And look, I was right. You jumped all over it. now if I could have only gotten a reaction that quickly to my original post. BTW, it looks like a hardware failure was the real issue. I'm going to try it with a new pc tomorrow. I'll be sure to let you know how I make out, but I don't predict any serious problems now.

---

### Post by handyguy33 on 2009-01-23
A new tower and a fresh install later. It took about 10 minutes to set up the shared folder, and nobody had to "spoon feed" it to me. Woo Hoo!

---

### Post by Iowan on 2009-01-23
Glad it worked for you - there are a few other "read-only Samba share" threads that might benefit from your experience.

---

