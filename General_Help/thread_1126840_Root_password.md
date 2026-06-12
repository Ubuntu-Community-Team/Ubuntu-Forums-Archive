---
title: "Root password"
date: 2009-04-15
forum: General Help
---

### Post by Monotoko on 2009-04-15
I have realized i have a slight problem with security, you need my password to change the BIOS so it will boot from anything but the harddisk, Ubuntu is password protected, but one problem i have noticed, if i boot into recovery mood, it lets me straght in as root :|

How do i set a password so it doesnt do that?!

---

### Post by codeseer on 2009-04-15
> **Monotoko said:**
> I have realized i have a slight problem with security, you need my password to change the BIOS so it will boot from anything but the harddisk, Ubuntu is password protected, but one problem i have noticed, if i boot into recovery mood, it lets me straght in as root :|

How do i set a password so it doesnt do that?!

Kinda useless to set one really. Physical access is equal to root anyway. BIOS passwords aren't that helpful either when someone has physical access, because there are super-passwords that over-ride BIOS passwords and someone could just pull the battery from the motherboard.

---

### Post by Monotoko on 2009-04-15
Hmmm...fair enough, maybe i should look into encrypting the important files

Thanks anyways :)

---

### Post by sp0nge on 2009-04-15
Unfortunately, I believe you're talking about a weakness in local access to a machine. 

While one certainly can [enable a password for BIOS]("http://www.lockdown.co.uk/?pg=biospsw"), the OS still has this chink in its' armor.

The thing is that there really is no "root account" in Ubuntu (you simply grant specific users access to the superuser group) . So if an attacker gained local access, they would need to know how to enumerate user names in order to go much further. Frankly, if you allow someone such access who knows what they're doing, they're going to get what they want one way or another.

---

### Post by codeseer on 2009-04-15
> **Monotoko said:**
> Hmmm...fair enough, maybe i should look into encrypting the important files

Thanks anyways :)

TrueCrypt ftw :p

---

### Post by mb_webguy on 2009-04-15
You can password protect any GRUB menu entry, including recovery mode.

First, open a terminal and type the following commands, replacing "12345" with your password of choice.```
$ grub
grub> md5crypt
Password: 12345
Encrypted: $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1
grub> quit
```
Copy the md5 hash it gives you (the bit after "Encrypted").

Now open the GRUB menu.lst file with "gksu gedit /boot/grub/menu.lst", and make the following change (highlighted in blue) using the md5 hash for your password.```
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
[COLOR="Blue"]password --md5 $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1[/COLOR]
```
Now go to the Automagic Kernels section.  Look for the following lines, and change "false" to "true" as shown in blue.```
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=[COLOR="Blue"]true[/COLOR]
```
Now save and exit, and in the terminal enter the command "sudo update-grub" to update the GRUB menu.

Given physical access and enough time, no amount of passwords will keep people out of your computer, but if you have a BIOS password keeping people from booting off of a CD, and you have a good password for all of the boot options in GRUB, then you should be able to feel pretty safe.

---

### Post by Monotoko on 2009-04-15
That is perfect! Thank you :)

---

### Post by bodhi.zazen on 2009-04-15
Set password is you like , but encryption is, IMO, a much better option.

---

### Post by Monotoko on 2009-04-15
I'l do both ;)

---

### Post by mb_webguy on 2009-04-15
> **bodhi.zazen said:**
> Set password is you like , but encryption is, IMO, a much better option.

Agreed, but setting a password is much easier.  And as I said, given physical access and enough time, any system can be cracked.  *If* someone yanks the drives out of your machine to plug them into another in order to bypass the BIOS and GRUB passwords, then encryption will help considerably to keep your information safe.  But I'd personally be more concerned about preventing that from happening in the first place.

---

