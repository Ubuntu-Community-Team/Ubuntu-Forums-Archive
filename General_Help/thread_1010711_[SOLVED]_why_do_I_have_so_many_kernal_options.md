---
title: "[SOLVED] why do I have so many kernal options?"
date: 2008-12-14
forum: General Help
---

### Post by Kain000 on 2008-12-14
Hey everyone, I was just nodicing that with each kernal update, I get another two choices when grub starts.   

I currently have the option of 3 linux kernals and their respective safe modes and windows xp.

Is it nessary to have 3 options for ubuntu?   if not how do I remove them?

thanks

---

### Post by frankleeee on 2008-12-14
For ubuntu you can install startup manager from add remove and change the amount shown and the time it dwells on that screen setup and a few other things. I don't know about this program in regards to a windows set up being there so if anybody has any comments on this post away.

---

### Post by 2hot6ft2 on 2008-12-14
One reason for having more than 1 kernel is that if something stops working with the new kernel you can go back to the one that worked.

For me kernel 2.6.27-9-generic made my wifi keep dropping signal but when I boot with kernel 2.6.27-7-generic it stays connected. Go figure.

There is another way of doing it for those who feel uncomfortable editing the menu.lst and that is StartUp-Manager ("sum" in synaptic) where you can choose how many kernels to show and whether or not to show the (recovery mode) options or the memtest86+ option

Yes I know that can all be done by editing the menu.lst file. Just thought I would give an alternative method.

---

### Post by SPr on 2008-12-14
Edit /boot/grub/menu.lst and comment out the kernel options you don't want. Read the rest of the config to see how else it can be changed.

On the off-chance that you make a complete mess of menu.lst make a copy of it before editing it.

---

### Post by Bachstelze on 2008-12-14
> **Kain000 said:**
> 
Is it nessary to have 3 options for ubuntu?   if not how do I remove them?

Some people like to have more than one kernel so that if there is some kind of issue with one, they  can get back to another. Personally, when I see a kernel is working fine, I just uninstall the others (which will remove them from the GRUB menu). You can do so by removing the corresponding linux-image packages.

---

### Post by Kain000 on 2008-12-14
> **HymnToLife said:**
> Some people like to have more than one kernel so that if there is some kind of issue with one, they  can get back to another. Personally, when I see a kernel is working fine, I just uninstall the others (which will remove them from the GRUB menu). You can do so by removing the corresponding linux-image packages.


thanks everyone for your speedy responces, 


and to the above, does this mean that I have the entire ubuntu os installed three  times?   editing my menu file wont reclaim my disk space I assume.

---

### Post by eBoxNet on 2008-12-14
you can remove any unwanted kernerls..
 read this : [http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

---

### Post by 2hot6ft2 on 2008-12-14
No, just 3 kernels, NOT 3 OS's

---

### Post by hikaricore on 2008-12-14
You can easily remove the old kernels via Synaptic, located under System/Administration/Synaptic.
There will be a section which I believe is called "Obsolete" or "Auto Removeable" (i don't have it in front of me atm) where you will be able to see unused packages such as previous kernels.  You can select the ones you wish to be removed and apply the changes.

This can also be done from commands line:

> sudo apt-get autoremove

But be sure to read the packages names so that you don't remove something you installed at some point and are still using.  :)

Best of luck,

--Aaron

---

### Post by hikaricore on 2008-12-14
Wow there was a reply bumrush..

---

### Post by Kain000 on 2008-12-14
> **hikaricore said:**
> Wow there was a reply bumrush..

haha yes, but again thank you all for your help.

---

