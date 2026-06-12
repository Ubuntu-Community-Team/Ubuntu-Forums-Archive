---
title: "disable safe mode ?"
date: 2010-08-30
forum: Desktop Environments
---

### Post by vasilev on 2010-08-30
Hello  , 


i am using Ubuntu 9.10 installed on one server . 
I dont use keyboard - only power and net cable . When something is gone wrong with the power , the PC is restarting itself . 
Here is and the problem .. it is hanging on "choose wich system..safe mode..etc" , because i dont use keyboard , and i dont want :)
Is there any way to make some time interval in this options and after 10 second for example to boot normally , or is there any way to delete this option - safe mode .


thanks .

---

### Post by DMBert on 2011-10-13
I'm sure it's too late for the original poster but to disable the GRUB menu after a failed boot change the following line in the /etc/grub.d/00_header file:

From:
if["${recordfail}" = 1]; then
    set timeout = -1


To:
if["${recordfail}" = 1]; then
    set timeout = 5


where the 5 can be whatever wait value in seconds is desired (-1 is indefinite).

The timeout settings in the /etc/default/grub file (menu.lst in older versions of GRUB) do not apply after a failed boot or after a boot into Recovery Mode.

---

