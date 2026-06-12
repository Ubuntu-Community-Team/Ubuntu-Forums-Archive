---
title: "HowTo - Updating the BIOS on Dell systems without using Windows"
date: 2007-09-12
forum: Dell  Ubuntu Support
---

### Post by magicfab on 2007-09-12
Hi,

I have started writing a guide to updating your Dell system BIOS without using Windows. It's mostly based on existing documention from one particular project (biosdisk), except I tested and documented information specific to Ubuntu.

This was tested on Ubuntu 7.04. 

The guide is available at:
[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

If anyone want to contribute to the document or would like to comment on its readbility, I'll be subscribing to this thread and taking all suggestions or corrections.

Thank you,

---

### Post by mandz on 2007-10-25
Hi, 

This is very useful but when I enter:

sudo biosdisk mkimage [-o option] [-i destination] [-k baseimage] D600_A16.EXE

I get:

Error: /usr/sbin/biosdisk does not take "[-o option]" as an option.

Are you able to tell me what I'm doing wrong?

Thanks

---

### Post by raggari on 2007-10-26
> **magicfab said:**
> Hi,

I have started writing a guide to updating your Dell system BIOS without using Windows. It's mostly based on existing documention from one particular project (biosdisk), except I tested and documented information specific to Ubuntu.

This was tested on Ubuntu 7.04. 

The guide is available at:
[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

If anyone want to contribute to the document or would like to comment on its readbility, I'll be subscribing to this thread and taking all suggestions or corrections.

Thank you,

Why not just follow steps defined in Dell Linux Wiki? It takes max two minutes to upgrade BIOS with these instructions.
[http://linux.dell.com/wiki/index.php/Tech/libsmbios]("http://linux.dell.com/wiki/index.php/Tech/libsmbios")

---

### Post by mandz on 2007-10-26
I've tried that method, but after installing the necessary packages, when I type:

%getSystemId

I get:

Libsmbios:    0.13.6
Error getting the System ID   : Could not instantiate SMBIOS table.
Error getting the Service Tag : Could not instantiate SMBIOS table.
Error getting the Product Name: Could not instantiate SMBIOS table.
Error getting the BIOS Version: Could not instantiate SMBIOS table.
Error getting the Vendor      : Could not instantiate SMBIOS table.
Is Dell:      0


Any ideas why? I can get the service tag off the bottom of the laptop,  but all I need is the system ID to download the correct file. Surely there's another way of finding it out.

I can give details if you need. Thanks!

---

### Post by Linicks on 2007-10-26
> **mandz said:**
> I've tried that method, but after installing the necessary packages, when I type:

%getSystemId

I get:

Libsmbios:    0.13.6
Error getting the System ID   : Could not instantiate SMBIOS table.
Error getting the Service Tag : Could not instantiate SMBIOS table.
Error getting the Product Name: Could not instantiate SMBIOS table.
Error getting the BIOS Version: Could not instantiate SMBIOS table.
Error getting the Vendor      : Could not instantiate SMBIOS table.
Is Dell:      0


Any ideas why? I can get the service tag off the bottom of the laptop,  but all I need is the system ID to download the correct file. Surely there's another way of finding it out.

I can give details if you need. Thanks!

You need to be root.  Try:

```
% sudo getSystemId
```

Nick

---

### Post by mandz on 2007-10-26
Amazing! Why on earth didn't I think of that? Well thank you greatly Nick, lets see if I can follow it through now...

---

### Post by Linicks on 2007-10-26
The Dell wiki is somewhat a bit lacking - they have a few instructions on there that need to executed as root/sudo, but forget to tell you.

And they will not allow updating to it either.

Nick

---

### Post by raggari on 2007-10-26
> **Linicks said:**
> The Dell wiki is somewhat a bit lacking - they have a few instructions on there that need to executed as root/sudo, but forget to tell you.

And they will not allow updating to it either.

Nick

Actually notes are there but not very visible:
Libsmbios is used for both flash. You will need to install it before you start. It is assumed throughout this page that all commands will be run as the 'root' user. Use either 'sudo' or 'su' to become root before attempting any of these commands or they will fail.

---

### Post by Twintop on 2007-10-26
Sweet deal. Thanks for putting this together!

---

### Post by faust99 on 2007-10-27
This is a great how to, but I can't find the BIOS i need (A07) on the repo linked in the Dell Wiki. I can't find my system ID in there (0x018D) anywhere....

---

### Post by prinknash on 2007-10-27
> **faust99 said:**
> This is a great how to, but I can't find the BIOS i need (A07) on the repo linked in the Dell Wiki. I can't find my system ID in there (0x018D) anywhere....
My System ID (0x020D, for an Inspiron 530N) isn't in the list either. I assumed that simply means that there's no BIOS update available yet.

p

---

### Post by faust99 on 2007-10-30
Perhpas it has not made it to the repo yet. Mine is available for windoze though.

---

### Post by MarilenCorciovei on 2007-12-08
I was able to upgrade my BIOS from A06 to A07 on a D820 using [these steps]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/bios-upgrade-with-no-windows-or-floppy/view")

---

### Post by de_valentin on 2007-12-10
Hi I have Packard Bell Easynote and I wonder if it is possible to use the same method to upgrade the BIOS. I have a .EXE

---

### Post by mozetti on 2007-12-10
Another method is to create a Bart's Pre-installation Environment (Bart's PE) boot CD. It gives you a minimalist gui based on Windows that allows you to run Windows-only programs (which most BIOS update programs are).

---

### Post by jobsonandrew on 2008-03-15
So has anyone established what to do if your System ID isn't listed on:
[http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)
????

I have an Inspiron 1501 with BIOS 2.1.0 and want to downgrade the BIOS to version 1.7.0 so that the LCD brightness will work

======Update======
I looked further into it:
[https://fedorahosted.org/libsmbios/wiki/broken](https://fedorahosted.org/libsmbios/wiki/broken)
Seems my System ID (0x01F5) doesnt work with libsmbios :( anyone know a way around this?

---

### Post by 787b on 2008-07-20
> **jobsonandrew said:**
> 
I looked further into it:
[https://fedorahosted.org/libsmbios/wiki/broken](https://fedorahosted.org/libsmbios/wiki/broken)
Seems my System ID (0x01F5) doesnt work with libsmbios :( anyone know a way around this?

Yes, I just upgraded my BIOS to 2.6.3. I don't have a single Windows box, so I couldn't use BartPE or similar to make a disk. 

I found a way however, and put the steps here:  [http://787b.net/inspiron1501bios.html]("http://787b.net/inspiron1501bios.html")

---

