---
title: "compiz dosent work"
date: 2009-01-03
forum: General Help
---

### Post by jj3502 on 2009-01-03
when trying to use compiz in system > preferences > appearance when i try to enable advanced desktop effects i get the error message <desktop effects could not be enabled>  

and in ccsm the terminal says: ```
jeremy@jeremy-desktop:~$ ccsm
GConf backend: There is an unsupported value at path 

/apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path 

won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path 

/apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path 

won't be read. Try to remove that value so that operation can continue properly.
```

have I done something wrong?

(ubuntu 8.04)

:confused::(

---

### Post by Therion on 2009-01-03
What graphics card/integrated graphics chip does your PC have installed?

---

### Post by jj3502 on 2009-01-03
nvidia 7300 512 mb (ubuntu is runing in vmware)

---

### Post by sofasurfer on 2009-01-03
I have the same problem. Heres my thread. Contribute to it and maybe we can find a solution. [http://ubuntuforums.org/showthread.php?t=1027016](http://ubuntuforums.org/showthread.php?t=1027016)

---

### Post by Therion on 2009-01-03
VMWare may, or may not, be able to support Compiz.  Your video card would do so without question if you were running Ubuntu "natively" and using the restricted driver FOR your video card.  

In a virtual machine though, I believe you are using a sort of psudeo-driver provided by the VM software.  I used VM Ware some time ago to run a WinXP client (Ubuntu host) and I know that Virtual Box handles things that way.  In any case, though, this sounds like a driver issue.  I'm not sure how to tell you how to get a restricted driver running in in VM Ware however.

Edit: One thing you might want to look at is how much video memory you set aside for your VM.  In Virtual Box I can set aside as much as 128MB for "video".  Compiz will require, I believe, a minimum of 64MB.  But don't quote me on that number.

---

### Post by Forlong on 2009-01-03
> **jj3502 said:**
> nvidia 7300 512 mb (ubuntu is runing in vmware)
That's not going to work. Sorry.

---

### Post by jj3502 on 2009-10-25
wrong one sorry

---

