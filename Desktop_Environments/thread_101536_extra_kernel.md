---
title: "extra kernel?"
date: 2005-12-10
forum: Desktop Environments
---

### Post by nrwilk on 2005-12-10
I recently had to reinstall because I accidentally performed a very big no-no.

If you must know what I did, it was my first big linux command-line screwup.
I was TRYING to do this:
```
sudo mv bin/* /data/scripts
```

but instead I did this:

```
sudo mv /bin/* /data/scripts
```

And, no more system...


Anyway, when I reinstalled, I used the same disk that I used the first time.  But, this time I have 2 kernels in my grub menu.  Is this because it downloaded a newer one from the repositories?  One kernel is labeled:
> 2.6.12-9-386
The other is labeled:
> 2.6.12-10-386

Can I get rid of one?  Why did the one labeled ...-10-... install this time and not last time?  Do they compile and offer a new kernel every month?  If so, why install both kernels?

More curious than anything else, really.

---

### Post by aysiu on 2005-12-10
The 10 kernel is a new update.
You can keep both around or uninstall 9.
I don't see any reason to get rid of either one. Just use 10.

---

### Post by wishyjr on 2005-12-31
well, i have had a few new kernels added to my grub menu over the last few months (after me playing around an all) and to be honest - my grub menu is getting really messy. I'm not really into the idea of ubuntu giving me 4 grub options anyway, i can see the advantages and why they're there but still..

anyway, is there a way of getting rid of those boot options in the grub menu? i'm not sure how large the average kernel is or how much space it takes up on my drive but i'm guessing not much so i dont really mind leaving older ones there but i would like a tidy looking grub menu. any ideas? is it a simple case of editing the grub config file?

---

### Post by pharcyde on 2005-12-31
You can remove grub menu items by editing **/boot/grub/menu.1st** and removing the entries you don't want.

To remove old kernel binaries u can do **sudo apt-get remove linux-image-2.6.12-9-386** for example.

---

### Post by wishyjr on 2005-12-31
thanks. just out of interest -how large is a kernel (generally?)

thanks again!

---

### Post by daniel49 on 2005-12-31
if you type the number of the kernel into synaptec on the search you will find it listed there and it will clean up everything including the grub entry if you mark for uninstall.

---

