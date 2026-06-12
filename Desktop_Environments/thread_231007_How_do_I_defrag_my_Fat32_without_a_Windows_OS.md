---
title: "How do I defrag my Fat32 without a Windows OS?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by randell6564 on 2006-08-06
Hey all!

I dumped my Windoze a while back, so now I only use ubuntu.

I have a 20gig fat32 drive that I use to store my music and video on. It just occured to me that I will need to defrag this drive occasionally.  How would I go about doing this since I am not using Windoze any longer?

Thanks!

---

### Post by coffeecat on 2006-08-07
I found nothing on a google search, except this idea which I think would be quicker and more thorough than an ordinary Windows defrag.

Copy the data from your fat32 drive onto another drive and then reformat the fat32 drive. Copy the data back again!

Sounds good to me. :)

---

### Post by h00s on 2006-08-07
I don't recommend this. It's a waste of time because there is no guarantee the files will be copied sector by sector (non-fragmented).

---

### Post by swamytk on 2006-08-07
> **randell6564 said:**
>  I am not using Windoze any longer?

then why do u still need FAT32 file system? is there any specific reason not to switch over to ext2/3?

---

### Post by coffeecat on 2006-08-07
> **h00s said:**
> I don't recommend this. It's a waste of time because there is no guarantee the files will be copied sector by sector (non-fragmented).

Are you sure of this? If you copy with 'dd' you'll copy sector by sector - I agree. But if you copy with 'cp', you'll copy file by file. Try it; use the v and R flags. 

**Afterthought**: But, to be honest, I wouldn't know how a GUI drag and drop would handle it.

---

### Post by tribaal on 2006-08-07
> Are you sure of this? If you copy with 'dd' you'll copy sector by sector - I agree. But if you copy with 'cp', you'll copy file by file.

I agree. That's what I do with fragmented files (the ones I download with bittorrent seem particularly prone to fragmentation), and it works wonders.

cp copies file by file, and dd sector by sector, that's right. If in doubt, just read the man pages :)

- trib'

---

### Post by peabody on 2006-08-07
> **h00s said:**
> I don't recommend this. It's a waste of time because there is no guarantee the files will be copied sector by sector (non-fragmented).

I'm pretty sure provided the filesystem is blank (fresh) and the copy operation is performed by one process a file at a time (say with something like tar), the files will be copied in the most straight forward manner which would simply append right along each cluster.  You of course will still get internal fragmentation with unfilled portions of clusters but windows defrag doesn't really get rid of that either.

If you used dd to copy the file system raw you'd copy the file fragmentation along with it.  I wouldn't recommend that.

If I'm mistaken about this I'm willing to be set straight, but I have copied files over to drives this way before and it seemed to work and it makes sense logically.

We are talking about fat32 here, not unix file systems retrieved via dump.

---

### Post by h00s on 2006-08-07
> **coffeecat said:**
> Are you sure of this? If you copy with 'dd' you'll copy sector by sector - I agree. But if you copy with 'cp', you'll copy file by file. Try it; use the v and R flags. 

**Afterthought**: But, to be honest, I wouldn't know how a GUI drag and drop would handle it.
I agree with you on this. When you copy file by file it should be non-fragmanted. I said should because we're talking of fat32 here.

---

### Post by randell6564 on 2006-08-07
> **swamytk said:**
> then why do u still need FAT32 file system? is there any specific reason not to switch over to ext2/3?


Good Question! (not enough coffee :P) 

Thanks you guy's!

---

