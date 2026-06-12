---
title: "How do you install Ubuntu into VM Workstation?"
date: 2006-04-20
forum: Desktop Environments
---

### Post by jacatone on 2006-04-20
I need WinXP to be my primary OS but would like to install Ubuntu into VM Workstation rather than creating a dual boot. Installing virtual memory seems to be a snap. Anyone know how to do this install? Thanks.

---

### Post by crispy_420 on 2006-04-20
Where are you having problems?

I got VM running Dapper as a test before I do a full install and it seems to be working fine for me.

Let me try to walk you through it:

Start VM
Go to: File -> New -> Virtual Machine (will start a wizard)

Click next.

I picked "Typical" The click next.

For Guest OS pick Linux and from a drop down menu Ubuntu is an option. Click next.

Name you can name your virtual machine and where it will live. Click next.

Now you want Ubuntu to have internet access. I picked "Use network address translation (NAT)". You'll need it to have access to the internet to complete the install. Click next.

Now pick how big you want your install to be. Keep in mind the if you put it on FAT32 anything over 4GB will be a problem. Then you can set an option below that. To save space at first you can leave unchecked (both) and it will grow as needed. Then click finish.

Before I started my virtual machine I click VM -> Settings to adjust some settings. Here you can adjust RAM, CD-ROM, etc.

For my install I just used the ISO I downloaded, an option under CD-ROM.

Now you can just start it and wait for the install to proceed.

***Is this what you were looking for?***

---

### Post by jacatone on 2007-03-12
Thanks. How do you install the "VM Tools" into Ubuntu 6.06 once the OS is installed into VM Workstation?

---

