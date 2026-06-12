---
title: "Cant get a samba configuration right"
date: 2009-01-16
forum: General Help
---

### Post by orlox on 2009-01-16
Hi!

I´m trying to configure a server with samba. The server works as an ftp server to see files over the web, and as a samba server so people can modify files in a local network. Every user has access to certain shared folders, linked to they're home folders.

The idea, is to create samba shares where each user can access his home folder with administrative privileges (so it can modify any file in the shared folders without problems over file privileges) using a password.

I tried this using this smb.conf:

```

[global]
    ; General server settings
    netbios name = SERVIDOR
    server string =
    workgroup = ROESSAN
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
    ;browseable = no
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

[GUILLERMO]
    path = /home/guillermo
    writeable = yes
    admin users = guillermo
    guest ok = no

[RES]
    path = /home/res
    writeable = yes
    admin users = res
    guest ok = no

```
Here I have two samba shares, guillermo and res. I enable passwords for each user ussing the command:
```

sudo smbpasswd -L -e <USERNAME>

```
After issuing this command, in windows I can create the network folder, and when accessing it, it prompts me for my username and password. If I use the share [GUILLERMO], I enter that username and password, and I can access the files as I want. The problem is, if in the same computer, I create an access to the share [RES], if I access the share guillermo (using my password) and then I acces the share [RES], I can access without using a password!

Anyone has a clue in how to fix this??

---

### Post by nquinnathome1 on 2009-01-16
Let me see if I have this correct; your problem is that if you access one of the shares (each share requiring a different login/pass), you can automatically then access the other share even though you didn't enter the other share's password?

---

### Post by fiatguy85 on 2009-01-16
It sounds possible that the logins are being cached and since you have logged in and created a share with each user, you are able to access both shares.

---

### Post by orlox on 2009-01-16
> [Let me see if I have this correct; your problem is that if you access one of the shares (each share requiring a different login/pass), you can automatically then access the other share even though you didn't enter the other share's password?

Yup, that's exactly the behavior...

> 
It sounds possible that the logins are being cached and since you have logged in and created a share with each user, you are able to access both shares.


If this is so, how can I avoid it?? It isnt a logical behavior that a login for one share is stored in cache and allows me to acces the other share. Unless I'm missing something important in the configuration file, This could be considered a security risk...

---

### Post by orlox on 2009-01-16
> 
It sounds possible that the logins are being cached and since you have logged in and created a share with each user, you are able to access both shares.


Another comment on this... I never had to enter both passwords, so its not possible that a cached login is the cause of this behavior. I only used the password of the user guillermo, and afterwards I could access the share RES with the user res WITHOUT never using the password! just leaving the password blank allowed me to enter the share :/

---

### Post by fiatguy85 on 2009-01-16
Ok, I thought you were typing in both passwords at one point.  Try adding in ```
browseable = no
``` to each share and then make sure to restart the samba daemon.  Note the example for home directories is actually implemented in the example file as:  ```
; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

```

The create mode and directory mode directives control file permissions and browseable should prevent other users from seeing the directory.

---

### Post by orlox on 2009-01-16
Thanx! Ill try it tomorrow (dont have access to the server right away) and tell you how it goes.

---

