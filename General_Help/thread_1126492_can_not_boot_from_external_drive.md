---
title: "can not boot from external drive"
date: 2009-04-15
forum: General Help
---

### Post by marcuskillion on 2009-04-15
Hi;
   I downloaded and installed ubuntu. I did not make a cd I just clicked on the install file. 
  I am running xp on c drive.
   I installed Ubuntu on my external usb hard drive.
   When I boot up I get a dos page that says :
   Rub4dos 0.4.4  Minimal BASH-like line editing supported.

   What do I do with this ?

   I also tried to install grub 4 dos but it had no install file in the package.

   Thanks for any help

---

### Post by prem1er on 2009-04-15
> **marcuskillion said:**
> Hi;
   I downloaded and installed ubuntu. I did not make a cd I just clicked on the install file. 
  I am running xp on c drive.
   I installed Ubuntu on my external usb hard drive.
   When I boot up I get a dos page that says :
   Rub4dos 0.4.4  Minimal BASH-like line editing supported.

   What do I do with this ?

   I also tried to install grub 4 dos but it had no install file in the package.

   Thanks for any help

What do you mean by "I installed Ubuntu on my external usb hard drive"?  Did you use a tool to do this or did you manually create the boot files on the usb drive?

---

### Post by bodhi.zazen on 2009-04-15
prem1er installed ubuntu using wubi.

Most likely this is a problem with your BIOS. Do you know if your BIOS supports booting to an external drive ?

If it is not the bios, what is the exact error  message ?

---

### Post by prem1er on 2009-04-15
> **bodhi.zazen said:**
> prem1er installed ubuntu using wubi.

Most likely this is a problem with your BIOS. Do you know if your BIOS supports booting to an external drive ?

If it is not the bios, what is the exact error  message ?

Oh, are you saying marcuskillion used Wubi to install Ubuntu?

---

### Post by bodhi.zazen on 2009-04-15
> **prem1er said:**
> Oh, are you saying marcuskillion used Wubi to install Ubuntu?

yes.

> I did not make a cd I just clicked on the install file.

---

### Post by marcuskillion on 2009-04-15
> **prem1er said:**
> Oh, are you saying marcuskillion used Wubi to install Ubuntu?

Yes I think that is what I did. When the install dialog box poped up I told it to install to my K drive ( external usb hdd )

I then changed my boot.ini . I get the the dos screen when I boot from Ubuntu . I do not know what to type in it. 

Do I need to install grub ? 

Do I need to make a cd and use that to install properly ?

I am wanting to keep my windows on C drive and Ubunto on external drive or on my D drive perhaps.

---

### Post by marcuskillion on 2009-04-15
> **bodhi.zazen said:**
> prem1er installed ubuntu using wubi.

Most likely this is a problem with your BIOS. Do you know if your BIOS supports booting to an external drive ?

If it is not the bios, what is the exact error  message ?

Not in the bios. I changed the boot.ini file to include ubuntu. 
It is not really an error message I do not think. It is a dos window that is RUB4DOS 0.4.4   Minimal BASH -like line editing supported > 
There is also a list of commands. I tried a few but nothing good happened.

Maybe I should have made the cd and installed from it.

---

### Post by prem1er on 2009-04-15
Does your bios support booting from an external source such as CD or USB?

---

### Post by marcuskillion on 2009-04-15
> **prem1er said:**
> What do you mean by "I installed Ubuntu on my external usb hard drive"?  Did you use a tool to do this or did you manually create the boot files on the usb drive?

No I did not use a tool or manually create them.

I downloaded the file from ubuntu. I then clicked on what I think was wubi to install it. A dialog box popped up and I clicked on install to K drive ( usb hdd ) and it installed. 
I thought the boot files were installing on my c drive from what I had read some where. I also read that I needed to install grub. But could not find an install file in the package that I downloaded.

---

### Post by marcuskillion on 2009-04-15
> **prem1er said:**
> Does your bios support booting from an external source such as CD or USB?

Yes

---

### Post by prem1er on 2009-04-15
IMO in order to save you a lot of time and headache if you can boot from an external drive I would use this [tool]("http://unetbootin.sourceforge.net/").  It makes sure to install the boot files correctly onto a usb drive.  Once you boot from the usb drive you can install ubuntu to a separate partition or continue to boot it from the flash.

---

### Post by marcuskillion on 2009-04-15
> **prem1er said:**
> IMO in order to save you a lot of time and headache if you can boot from an external drive I would use this [tool]("http://unetbootin.sourceforge.net/").  It makes sure to install the boot files correctly onto a usb drive.  Once you boot from the usb drive you can install ubuntu to a separate partition or continue to boot it from the flash.

another problem.
i made a new live cd. reinstalled to my external usb drive.

it does not boot but gets an error 21.

tried to boot into windows. can not.

boot from floppy . in win i can not access my usb drive. 

tried to uninstall. but since i can not see my drive i can not do it.

do you know why this would lock out mu usb drive ?

tried to restore to an earlier date. Windows said I could not. Any idea why that happened ?

thanks

---

### Post by prem1er on 2009-04-15
Can you log back into Windows.  If you can download that software that I sent you a link to.  It will put the live boot files on your usb drive.  Boot ubuntu from there and install on the partition of your choice.

---

