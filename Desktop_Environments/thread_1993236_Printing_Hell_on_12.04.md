---
title: "Printing Hell on 12.04"
date: 2012-06-01
forum: Desktop Environments
---

### Post by TheTopcat on 2012-06-01
I have a printer problem with an epson inkjet and a hp LJ 2200n on 12.04
I have it setup as a network printer so my laptops can print I have 1 windows 7 laptop and 1 windows 7 / ubuntu 12.04 dual boot.
The problem is that I can print ok from my windows laptops over the lan but not from my ubuntu install here is a copy of the samba settings from the ubuntu desktop that is being used to serve the printer

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
    comment = All Printers
;    browseable = yes
    path = /var/spool/samba
    printable = yes
    guest ok = yes
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
    writeable = yes
    guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.

[cdrom]
    comment = Samba server's CD-ROM
;    read only = yes
    locking = no
    path = /cdrom
    guest ok = yes

[Work]
    path = /media/Work
    writeable = yes
;    browseable = yes
    guest ok = yes

Many thanks for any help on what is going wrong here ...

---

### Post by JohnH on 2012-06-02
To begin with, I'm no expert but I had problems installing my Samsung printer using the new dumbed down installer that comes with 12.04. 

To fix my problem I installed system-config-printer (the old printer installer) using Synaptic (although Ubuntu Software Center will do the same job). I then went to the "usr" directory where this package is installed and ran it . I also created a laucher in my Main Menu for future use. 

This GUI allowed me to install my printer over my wireless network. My laptops use the wireless network okay. 

Regards
John

---

