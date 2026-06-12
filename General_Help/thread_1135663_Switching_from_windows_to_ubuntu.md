---
title: "Switching from windows to ubuntu"
date: 2009-04-24
forum: General Help
---

### Post by Zoyberk on 2009-04-24
Hello, 

today I just decided to switch from win xp to ubuntu 9.04, 
since I had only one partition in windows and I wanted to keep all my data I tried to do that:
i had like 90G free space on my partition and i wanted to make new partition from that so i could put all my important files on it, delete my windows partition and then put ubuntu on it. For that i used some program partition magic or something, it warned me that there is possibility of error or data loss but i didn't relay care XD
...but the problem is that there was error, new partition wasn't made, and boot into windows fail.
Now I'm runing from ubuntu live cd and i can see and access all my files on windows partition.

So I Wonder if i can do what i wanted to do in windows but it failed(make new partition, putt all thinks on it then install ubuntu on other) whit ubuntu runing from live cd, or if i can just install ubuntu and import all my files on it? =)

any help would be appreciated  XD

---

### Post by zvacet on 2009-04-24
It should be possible when you comes to the partitioning stage in Ubuntui installation.Then shrink existing NTFS and make new one aloso NTFS and rest dedicate to Ubuntu ext3.If that way doesn´t work download [Gparted live Cd]("http://gparted.sourceforge.net/") and do that with it.

---

### Post by Zoyberk on 2009-04-25
I tired it in ubuntu live cd, and in Gparted live cd, but both times i get lost XD
 
...i click on my NTFS windows partition and try resice it, but all i can change is add 8MB to my partition(i have 8MB unlocated space)


I attached screan shoot, so if anyone could dell me how can I and what i need click to take away 90GB free space from my NTFS windows partition, and that i wouldnt lose my data from winodws partition/or i would just import data which i want to ubuntu =)

and I'm tootal noob in that, so dont piss off if i will make any stupid questions XD

---

### Post by stwschool on 2009-04-25
Quick bit of advice, before you do anything, boot up on the ubuntu live cd, and back up anything from the windows drive that's desperately important onto a memory stick!

---

### Post by Ericyzfr1 on 2009-04-25
> **Zoyberk said:**
> Hello, 

today I just decided to switch from win xp to ubuntu 9.04, 
since I had only one partition in windows and I wanted to keep all my data I tried to do that:
i had like 90G free space on my partition and i wanted to make new partition from that so i could put all my important files on it, delete my windows partition and then put ubuntu on it. For that i used some program partition magic or something, it warned me that there is possibility of error or data loss but i didn't relay care XD
...but the problem is that there was error, new partition wasn't made, and boot into windows fail.
Now I'm runing from ubuntu live cd and i can see and access all my files on windows partition.

So I Wonder if i can do what i wanted to do in windows but it failed(make new partition, putt all thinks on it then install ubuntu on other) whit ubuntu runing from live cd, or if i can just install ubuntu and import all my files on it? =)

any help would be appreciated  XD

I used Partition Magic to resize a partition once and ended up with an error because I forgot to stop the Anti-Virus. Anyway, in your case you should definitely consider to move your files manually to an external device before you attempt to resize that partition.

---

### Post by Zoyberk on 2009-04-25
> **stwschool said:**
> Quick bit of advice, before you do anything, boot up on the ubuntu live cd, and back up anything from the windows drive that's desperately important onto a memory stick!



thanks for advice, but i alerady screwed up windows before my first post :)

...also if someone could tell me how to set up lan betwen computer whit ubuntu and computer whit ubuntu from live cd. I tried it and got this error
> 
'net usershare' returned error 255: net usershare add: cannot share path /media/disk/Documents and Settings as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.
so if someone could tell me atleast how to fix that :)

...then i would just put all my important files on other comp and format this... XD

---

### Post by albinootje on 2009-04-25
> **Zoyberk said:**
> 
...i click on my NTFS windows partition and try resice it, but all i can change is add 8MB to my partition(i have 8MB unlocated space)


Your screenshot shows an exclamation mark on the NTFS partition, can you double click on the icon with the exclamation mark ?
The partition was probably not properly shutdown, you will need to fix that first.
Do the following in your Ubuntu live cd session, assuming that you have internet access :
1) open a terminal
2) type in :
```

sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
sudo gparted

```

And make sure to make a proper backup before doing any resizing!
If you run into a power outage you might lose all data during the resizing process.

---

### Post by stwschool on 2009-04-25
Doesn't matter, you should still be able to get the files from within the liveCD environment. I've done it before when windows has died on me.

---

### Post by albinootje on 2009-04-25
> **Zoyberk said:**
> thanks for advice, but i alerady screwed up windows before my first post :)

...also if someone could tell me how to set up lan betwen computer whit ubuntu and computer whit ubuntu from live cd. I tried it and got this error
so if someone could tell me atleast how to fix that :)

...then i would just put all my important files on other comp and format this... XD

Install ssh on the computer with Ubuntu :
```

sudo apt-get install ssh

```
Then on the machine using the Ubuntu live cd open a terminal, and 
type :
```

nautilus sftp://ip_address

```
where ip_address is the ip address of your Ubuntu machine.

---

### Post by Zoyberk on 2009-04-25
> **albinootje said:**
> ... sure to make a proper backup before doing any resizing!
If you run into a power outage you might lose all data during the resizing process.

That about losing all data would be problematic since only place where i can backup is other comp but i cant share files beacuse that eror:

> 'net usershare' returned error 255: net usershare add: cannot share path /media/disk/Documents and Settings as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.
so how can i fix this first?:)

---

### Post by Zoyberk on 2009-04-25
> **albinootje said:**
> Install ssh on the computer with Ubuntu :
```

sudo apt-get install ssh

```Then on the machine using the Ubuntu live cd open a terminal, and 
type :
```

nautilus sftp://ip_address

```where ip_address is the ip address of your Ubuntu machine.

did that and now i can see files of ubuntu pc from my live cd pc, since i need it just reverse i tried to do that reverse as you said but it didnt work since it ask me for password but live cd dont realy have one.

...i dont know, but this is just my noob guess: shouldnt i just add 
 > "usershare owner only = false" 
   to the [global] section of the smb.conf to allow this
line.

---

### Post by albinootje on 2009-04-25
> **Zoyberk said:**
> did that and now i can see files of ubuntu pc from my live cd pc, since i need it just reverse i tried to do that reverse as you said but it didnt work since it ask me for password but live cd dont realy have one.

...i dont know, but this is just my noob guess: shouldnt i just add 
 
line.

That's in my opinion a more difficult approach.

With my suggestion you should be able to copy and paste (or drag files/directories) from one the Nautilus window to another. No need to reverse the setup for that.

---

### Post by albinootje on 2009-04-25
> **Zoyberk said:**
> it didnt work since it ask me for password but live cd dont realy have one.


If you really prefer this setup, then simply give the ubuntu user from the 
live session a password :
```

passwd ubuntu

```

---

### Post by Zoyberk on 2009-04-25
oh oh i get it! its working! :guitar:

Thanks to all for all the help! and have nice day:)

---

### Post by albinootje on 2009-04-25
> **Zoyberk said:**
> oh oh i get it! its working!

Cool! :)
> 
Thanks to all for all the help! and have nice day:)
Thanks, you too!

---

