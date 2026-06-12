---
title: "Another dual boot query"
date: 2006-07-13
forum: Desktop Environments
---

### Post by CheeseAndToast on 2006-07-13
Hi, 

I have a 200gb hard drive and 2.5gb ram....running 100% dapper.
Unfortunately I need to go back to windows.....I need about 40gb for windows the rest dapper - it sounds really easy - but i can't figure out how to get windows to install...i tried [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm") - but I don't get half the option he did - plus i don't get "install in text mode".  

What I did was rund live CD > start or install > went thru the setup, until I came to the parition part.  I resized the dapper partition and added a new NTFS parition.  But i don't let me mount windows??

I seen somewhere that I need, dapper, fat32, ntfs and swap.....if so how much of dapper, fat32, ntfs do I need? and how do I mount windows?

Thanks

---

### Post by Maggot on 2006-07-13
Are you starting this from scratch or are you trying to save dapper?

At minimum you need NTFS, ext3 (or whatever your preference is for linux) and swap.  You can have FAT32 if you want the ability to write with both windows and linux.

The rule for SWAP is 1.5 to 2 times the size of your RAM.

If you have a 200 GB hard drive I wouldn't sell yourself short and only give windows 40GB....never know what the future holds.  I would just split it in half. Again, it all depends on what you store on it.

You cannot mount the windows drive if windows is not installed.

I'm guessing the reason you don't get the "text install" option is because you have the "Desktop" version of ubuntu? If memory serves me correct, you only get the text install with alternate version and probably server as well.

---

