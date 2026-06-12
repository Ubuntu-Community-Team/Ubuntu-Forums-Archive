---
title: "Update mamager error"
date: 2009-06-22
forum: General Help
---

### Post by RazzyDaz on 2009-06-22
Ubuntu is trying to update, but it's giving me an error message of : The upgrade needs a total of 15.7M free space on disk '/boot'. Please free at least an additional 436k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean.

I typed sudo apt-get clean into the terminal, but nothing happened.  I'm not sure how else to fix this.  I'm still learning how to use the terminal, any suggestions?

Thanks...

---

### Post by lindsay7 on 2009-06-22
Sounds like you need to give your Ubuntu installation more disk space.  You can do this with Gparted. If you do not have it on your system you can get it from synapic under the system/administration menu. Post a screen shot of your drive if you need help with what to do.

---

### Post by blueridgedog on 2009-06-22
> **lindsay7 said:**
> Sounds like you need to give your Ubuntu installation more disk space. 

To confirm you can run and post the output of 
```

df
```

---

### Post by RazzyDaz on 2009-06-23
Ok..I have downloaded the program, I have attached a pci of what I have partitioned.  Sorry, I'm not sure how to post the picture in this box.  I'm new to linux, and still learning.

Thanks

---

### Post by drs305 on 2009-06-23
RazzyDaz,

From the LiveCD or a Gparted CD you will have to shrink your /home partition and expand your /boot partition. Shrink/drag the left edge of sda7 to the right, then drag the right edge of you /boot partition to the right, taking up the new free space. 500MB should be more than enough. It can be smaller if you really need the space elsewhere (200MB).

You have to do this from a LiveCd or gparted CD since /home and /boot cannot be mounted when you do this.

If you need instructions on exactly how to use gparted (selecting the partitions and moving them, just ask.

Backup up anything important you have in /home before you do this, as usual whenever performing partitioning actions.

---

