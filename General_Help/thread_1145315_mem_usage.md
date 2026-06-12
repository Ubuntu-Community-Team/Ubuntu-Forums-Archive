---
title: "mem usage"
date: 2009-05-01
forum: General Help
---

### Post by sam_delta on 2009-05-01
im currently with 2 open office documents (about 2 pages each), firefox thunderbird and pidgin open.
gnome system monitor reports a memory usage of 800~ mb, which sounds reasonable, but the system starts to slow a bit, the swap starts to be used alot, and the most strange thing, top reports a mem usage of 2 gig (almost 100%), so, who should i trust? gnome system monitor or top?? 

attached picture shows sys monitor and htop

Thanks, Sam

---

### Post by Legace on 2009-05-01
Type **free -m** into Terminal.
Type** ps aux** into Terminal.

Post output here..

---

### Post by sam_delta on 2009-05-01
EDIT, i attached txt files for better readability

thanks, sam

---

### Post by sam_delta on 2009-05-01
i think its a bit unformatted,let me knokw if you prefer it on a txt file, so it can be more readable

sam

---

### Post by Legace on 2009-05-01
This is odd. The MEM% total is clearly less the 50%, even though free reports that you are using 1961MB of your 1977MB..

Could you post a TXT file? Pretty hard to read that :P

---

### Post by mali2297 on 2009-05-01
> **sam_delta said:**
> 
```

     total        used free shared buffers cached
Mem: 1977         1961   15      0       7   1154
-/+ buffers/cache: 799 1178
Swap:3623          174 3449

```

This tells you that your applications are occupying 799 M of RAM. The cached memory is used but is made available when needed, so we can regard it as free.

---

### Post by sam_delta on 2009-05-01
yeah, something looks wrong , lets see if someone have any idea on whats goin on

thanks
Sam

---

### Post by sam_delta on 2009-05-01
> **mali2297 said:**
> This tells you that your applications are occupying 799 M of RAM. The cached memory is used but is made available when needed, so we can regard it as free.
ohh alright, that clears things out  a bit,, another question,, is it normal the extensive use of swap??, its using over 150 mb of swap, even tho im using a swappiness of 10.

thanks
sam

---

### Post by mali2297 on 2009-05-01
> **sam_delta said:**
> ohh alright, that clears things out  a bit,, another question,, is it normal the extensive use of swap??, its using over 150 mb of swap, even tho im using a swappiness of 10.

thanks
sam

Some application might at one point have used the swap. Even though it is no longer used, it still shows until you reboot.

---

### Post by sam_delta on 2009-05-01
> **mali2297 said:**
> Some application might at one point have used the swap. Even though it is no longer used, it still shows until you reboot.
aaalright, getting it straigh now,, thanks for the info
ill mark this post as solved,, thanks all

Sam

---

