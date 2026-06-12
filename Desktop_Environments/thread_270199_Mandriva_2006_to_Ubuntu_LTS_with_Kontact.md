---
title: "Mandriva 2006 to Ubuntu LTS with Kontact"
date: 2006-10-02
forum: Desktop Environments
---

### Post by suzao on 2006-10-02
I am switching from my Mandriva 2006 KDE setup to Ubuntu because I have always preferred the GNOME look and feel to KDE.  But this is my main work computer, so switching all my stuff from Kontact to Evolution is really not necessary since I like Kontact quite a lot and have a few years of business mail and contacts nicely organized.

I have Ubuntu booting and all hardware working correctly.  I have installed the KDE libs, KAddressbook, KMail, KOrganizer and Kontact installed and running.

My problem is that I can not figure out how to transfer all my mail and settings over from my Mandriva (on a separate partition) to Ubuntu.

1. I have copied mandriva_home/.kde/share/config/kmailrc to ubuntu_home/.kde/share/config/kmailrc updating only the version section of this config file.  I did not find any absolute path information, only relative path info from the KMail default folder ~/.Mail

2. Copied mandriva_home/.Mail (previous version default) to ubuntu_home/.kde/share/apps/Kmail replacing the original folder placed there by KMail.

3. Copied mandriva_home/.kde/share/apps/kabc/std.vcf ubuntu_home/.kde/share/apps/kabc/std.vcf 

Now when I start Kontact from the terminal command:
```
dfisher@dfisher-laptop:~$ kontact
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
QLayout::addChildLayout: layout already has a parent
dfisher@dfisher-laptop:~$ X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kabc: WARNING: address format database incomplete (no format for locale us found). Using default address formatting.
kabc: WARNING: address format database incomplete (no format for locale us found). Using default address formatting.

```

None of my mail is visible from within Kontact or Kmail, but my contacts are.  My POP and SMTP account information is correct and KMail could login to download mail, I just have not yet until I get it working correctly.

My old versions are:
Kontact 1.1.2
KMail 1.8.2
KAddressbook 3.4.2
KDE 3.4.2

New versions (standard Ubuntu) are:
Kontact 1.2
KMail 1.9.1
KAddressbook 3.5
KDE 3.5.2

Can anyone help me with the correct procedure to get this "upgrade" working correctly?

---

### Post by suzao on 2006-10-02
Nothing like hours of research to prevent any RTFM responses or worse wasting anybody's time, submitting a post, then 30 seconds later solving the problem.  

Contrary to my post's assertion:
> I did not find any absolute path information, only relative path info from the KMail default folder ~/.Mail

There was indeed path information in kmailrc.  I changed :
folders=$HOME/.Mail (old default location)
to
folders=$HOME/.kde/share/apps/kmail/mail (new default location and actual place I put the stuff.)

Now Kontact starts and I have access to all my previous mail.

---

