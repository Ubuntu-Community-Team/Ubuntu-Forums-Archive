---
title: "Samba Domain Name"
date: 2009-01-04
forum: General Help
---

### Post by tj71587 on 2009-01-04
Hey all,

I am using this to setup a domain for my windows machines:

[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)

I believe I have it working, but I cant find where the name of the domain is.  I'm sure its something stupid and I'm missing it, but any help would be appreciated.

Thanks,

T.J.

---

### Post by dcstar on 2009-01-04
> **tj71587 said:**
> Hey all,

I am using this to setup a domain for my windows machines:

[https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html](https://help.ubuntu.com/8.10/serverguide/C/samba-dc.html)

I believe I have it working, but I cant find where the name of the domain is.  I'm sure its something stupid and I'm missing it, but any help would be appreciated.

Thanks,

T.J.

Workgroup.

---

### Post by tj71587 on 2009-01-04
ah, makes sense. thanks.  On that same note, I can't get profiles to work in the conf file.  The only thing that works is home.  Is there anything that this howto missed that would prevent the profiles section from working?

---

### Post by pyromanic123boom on 2009-01-04
I just did this for a windows laptop using samba. For me, I only needed access to my /home folder. I right-clicked my folder, clicked properties, and set the info for the 'Share' tab. (Create a user, pass, etc). 

Easiest way for me to do it...also, I have sometimes used vsFTPd for more remote access.

---

### Post by tj71587 on 2009-01-04
Thanks, but here is what I am looking for.  I would like the profiles to be located on /media/sambashared/profile/$username.  I cannot seem to get this to work by using the profiles and home inside the conf file will only let me use the home folder, any ideas?

Thanks,

T.J.

---

### Post by pyromanic123boom on 2009-01-04
Can you define shared directories within the configuration file itself, or does it limit itself to only home directories? Could I see the actual samba.conf file?

---

### Post by tj71587 on 2009-01-04
Here is my .conf

```

[global]
    ; General server settings
    netbios name = UBUNTU-SERVER
    server string =
    workgroup = WORKGROUP
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

   domain logons = yes
   logon path = \\%N\%U
   logon drive = H:
   ;logon home = \\%N\%U
   logon script = logon.cmd
   add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u
   ;add machine script = /usr/sbin/useradd -s /bin/false -d /home/nobody/ %u
    

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S


; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
[netlogon]
   comment = Network Logon Service
   path = /media/samba/netlogin
   guest ok = yes
   read only = yes
   share modes = no


; NOTE: Again - only needed if you're running a primary domain controller.
[profiles]

   path = /media/samba/profile
   writeable = yes
   browseable = no
   create mask = 0600
   directory mask = 0700
   root preexec = PROFILE=/media/samba/profile/%u; if [! -e $PROFILE ]; \ then mkdir -pm700 $PROFILE; chown %u:%g $PROFILE;fi 

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

[Media]
    path = /media/samba/shared
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = tj
    force group = users


```

I have looked around the internet and the profiles areas that I have found are all similar to that.  Any ideas?

Thanks,

T.J.

---

