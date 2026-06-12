---
title: "HEEEEELP!!! Operating system not found!"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Isoss on 2006-06-18
believe be all I did was installing 3 softawres with wine: UltraEdit, RealPlayer10, and WINSCP ... UltraEdit worked but the other's did not then i rebooted and I can't login the system! instead of giving me the GRUB menu it says: Operating system not found

I can't reinstall cuz I have been installing my packages and organizing my world for ages ... Please help!!!

---

### Post by bohboh on 2006-06-18
Some things to try:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+missing]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+missing")

---

### Post by Isoss on 2006-06-19
I reinstalled grub and the "operating system not found" remained!!!
AND I HAD TO REINSTALL ](*,) 
I used the ubuntu-server CD which has the rescue broken system property, I opned a shell and tried to backup some files and /var/cache so I won't be spending time downloading all the packages that I had again if I had reinstall the system ... everything I've backed up "including my /var/www and /var/lib/mysql/" was actually backed up!!! although I was pretty sure cuz I could mkdir and I used "cp -r" to copy the backup!!!:( 

This is ONE HELL OF BUG!!! I hate this it's been bugging me since I have switched to linux ... I had to reinstall the system 7 times in 4 months:mad: 

I tried once backing up my partition using partimage in case I had to format and the partimage it self broke the system!!!

PLEASE GUYS, I LOVE LINUX ... BUT THIS IS NOT COOL AT ALL, SO SOMEBODY HELP so somebody suggest something before I kick the buket. In what way can i securily backup my systems without using much space as partimage does? ... I need to know what system files to compress in-order to avoid re-downloading and re-installing my applications with synaptic again!

Thanks!

---

### Post by Luke771 on 2006-06-19
Did you try booting from Ubuntu install CD in rescue mode and running ```
grub-install hda0,0
``` ?

I did that a couple of times on Breezy,  never on Dapper so far.  But it should work. I guess.

EDIT
Ah, OK. You *did* reinstall Grub then, and it didn't work.
I should read more carefully before posting. Sorry.

---

