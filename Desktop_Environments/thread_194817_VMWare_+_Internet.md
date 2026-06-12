---
title: "VMWare + Internet"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Harold P on 2006-06-12
Okay, I'm trying to fully run VMware with Windows XP Pro under ubuntu, but I have encountered a problem: The Internet keeps "losing connection". If I had vmware open with windows & firefox browsing along with gaim on ubuntu, they would conflict and ultimately gaim just lost connection to both services (AIM & MSN). I've only been able to download **two** things on this virtual machine; firefox and flash for firefox--everything else has just stopped in the middle of the download. So, I thinking someone was conflicting, I stopped all applications using the Internet (that I knew of) in ubuntu, it helped somewhat, but it still kicks this VM off a lot. Does anyone know of a solution? Any help would be appreciated...

Thanks,
HP

---

### Post by mdurham on 2006-06-12
make sure that Ubuntu & Windows have different addresses

---

### Post by Harold P on 2006-06-12
[quote=mdurham]make sure that Ubuntu & Windows have different addresses[/quote]
No clue on how to go about this. How do I set different addresses?

Thanks,
HP

---

### Post by darkpark on 2006-06-12
[QUOTE=Harold P]No clue on how to go about this. How do I set different addresses?

Thanks,
HP[/QUOTE]

Did you configure vmware to use NAT or Bridged?  (this was done when you ran vmware-config.pl).   By the way, when  you say that the internet loses connection , do you mean that windows would report that it lost its network connection?  
I had this problem with vmware workstion 5.0x but after upgrading to 5.5 the problem went away.

---

### Post by Harold P on 2006-06-12
[quote=darkpark]Did you configure vmware to use NAT or Bridged?  (this was done when you ran vmware-config.pl).   By the way, when  you say that the internet loses connection , do you mean that windows would report that it lost its network connection?  
I had this problem with vmware workstion 5.0x but after upgrading to 5.5 the problem went away.[/quote]
I am using Bridged. I used [this]("http://ubuntuforums.org/showthread.php?t=183209") tutorial. It looks like I just have the server console, though. I'm quite new to this vmware stuff.

HP

---

### Post by bulldog on 2006-06-12
Hi,I'm using vmware server and installed XP-Pro with the settings op using NAT,
and it's running fine.:) 

When you install a virtual machine you can alter these settings,I'm not sure if it can be altered later,but it seems that my virtal machine got a different IP than Ubuntu.
Take a look what's  happening on your virtual machine.
I use DHCP on my router and let him do the job for me and there's no problem what so ever.
Used the same tutorial btw.

---

### Post by Harold P on 2006-06-12
Hmm, I just tweaked a few settings and it worked. No clue what I did, but it's fine now. :p

---

