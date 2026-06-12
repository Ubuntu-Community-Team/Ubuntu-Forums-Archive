---
title: "I am off ubuntu"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Bjamin0325 on 2005-12-10
I loved Hoary, but Breezy is just not for me.  It is too temperamental.  I have not been able to get a solid install up yet, after 5 tries.

Mostly, it fails to recognize my internet connection, which for some reason on my machine ruins the install, as it will never let me adjust network settings after that.

Even if it does recognize it, it stops after about 5 minutes, and won't restart because it freezes up at synchronizing clock step.

This is too much.   I wish it was as solid as 5.04 for me.

---

### Post by invalid on 2005-12-10
Sorry to hear you are leaving.

You know, you can still use 5.04 instead. Security updates will still be provided when needed, and you can always use backports to install the lastest software.

Cb

---

### Post by magnusbb on 2005-12-10
[QUOTE=Bjamin0325]Mostly, it fails to recognize my internet connection, which for some reason on my machine ruins the install, as it will never let me adjust network settings after that.

Even if it does recognize it, it stops after about 5 minutes, and won't restart because it freezes up at synchronizing clock step.[/QUOTE]

Could it be the drivers? I had a wireless adapter stopping every 15 minutes or so, and had to reboot every now and then for that reason. Then I updated a kernel module (very simple) and it worked!

---

### Post by Bjamin0325 on 2005-12-10
I don't know, I've updated the kernel, and usually it just locks up on restart.  I might just go back to hoary, I do like it a lot.

---

### Post by linbetwin on 2005-12-10
[quote=Bjamin0325]I don't know, I've updated the kernel, and usually it just locks up on restart. I might just go back to hoary, I do like it a lot.[/quote]

If you updated to the 2.6.12.10 kernel, try booting into the 2.6.12.9.

---

### Post by valter on 2005-12-10
when synchronizing clock doesn't Crtl+c help?

---

### Post by nix4me on 2005-12-10
[QUOTE=Bjamin0325]I loved Hoary, but Breezy is just not for me.  It is too temperamental.  I have not been able to get a solid install up yet, after 5 tries.

Mostly, it fails to recognize my internet connection, which for some reason on my machine ruins the install, as it will never let me adjust network settings after that.

Even if it does recognize it, it stops after about 5 minutes, and won't restart because it freezes up at synchronizing clock step.

This is too much.   I wish it was as solid as 5.04 for me.[/QUOTE]

Please consider filing a bug report so that your problems can get remedied.  That would benefit you and others.  Im sure someone can help you figure out your problems quickly.

Post a very detailed message about your exact problems and see if you can get some help.

nix4me

---

### Post by Haegin on 2005-12-10
Or you could always try upgrading to dapper drake (the testing version) rather than downgrading to hoary (but thats probably even more broken). Just as a side question, how reliable is dapper drake? Im thinking of using it for another pc I'm hoping to make when I get around to it.

---

### Post by greenpenguin on 2005-12-10
Dapper is currently getting kernel upgrades - the latest two don't work on my computer (nvidia-glx problems), so you may want to wait a while.
 
On the other hand, if you can get a stable kernel, it is working very well (for me at least).
 
**Bjamin0325: **Can i suggest installing 5.04 and upgrading everything except the kernel?  And you might try dapper too, if you dont mind the odd crash :)

---

### Post by BLTicklemonster on 2005-12-10
Perhaps ubuntu could be made to catch when something that is not totally needed is taking way too long to load, it could prompt the user with 


press ctrl+c to skip


?

---

### Post by MetalMusicAddict on 2005-12-10
Bye

---

### Post by Bjamin0325 on 2005-12-10
Thanks for the replies, everybody.

I'm trying to install 5.10 again, maybe with your tips I can get it up and running.  If not, I'll bug report any problems.

Thanks, everybody.

---

### Post by BLTicklemonster on 2005-12-10
[QUOTE=MetalMusicAddict]Buy some coffee and sit down and give it your best shot. We want you to succeed.[/QUOTE]


...what he said.

---

### Post by Rackerz on 2005-12-10
[QUOTE=BLTicklemonster]...what he said.[/QUOTE]
Yep. I've reinstalled Ubuntu/Kubuntu 3 times, because i want to start again. This time around i've done everything rite. There is no reason to give up! Unless your using an Amiga :confused: :p

---

### Post by Bjamin0325 on 2005-12-10
Hi.

Thanks for the replies, everybody.  I think I've finally gotten 5.10 to work, even with FF1.5 installed somehow.

The only problem is it won't load with the new kernel.  Anyone know any way to make it default to the older one?

Thanks again.

---

### Post by BLTicklemonster on 2005-12-10
Sorry, m8, but I'm on my way out the door to buy stuff to build some christmas machines (for mortals, therefore they will probably get windows, not ubuntu), but you can start here:

```
sudo gedit /boot/grub/menu.lst
```

and someone will come in and help you with what you need to do. 

First off, though, you do have the ... bah.

Install grub, THEN do that up there.

Ah heck, I'm just making this worse. I wish I had time to help, but I probably just confused you.

Toodles, and good luck. Be patient, someone will be along to straighten up my mess, I'm sure.

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=Bjamin0325]Hi.

Thanks for the replies, everybody.  I think I've finally gotten 5.10 to work, even with FF1.5 installed somehow.

The only problem is it won't load with the new kernel.  Anyone know any way to make it default to the older one?

Thanks again.[/QUOTE]
In the file /boot/grub/menu.lst, there is probably a line that reads:
```

default 0

```
The zero is the index into the default option (top of the list).  Just change it to the number of the entry you want.  Note that seperators which are not real entries will count as an index.

---

### Post by dcstar on 2005-12-10
[QUOTE=Bjamin0325].......
The only problem is it won't load with the new kernel.  Anyone know any way to make it default to the older one?

Thanks again.[/QUOTE]
Apart from the Grub stuff, you can also use "Lock Version" to use a fixed version of the kernel in Synaptic, and then that version will be "Pinned" and you won't be prompted to upgrade all of the time (if it was an older version).

---

### Post by scruffy on 2005-12-10
Good to see your giving it more time :D , if I can do it you certainly can ;) 

All the best

Scruff

---

