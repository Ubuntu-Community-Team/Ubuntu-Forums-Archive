---
title: "Wubu work if Windows is borked?"
date: 2009-04-21
forum: General Help
---

### Post by mogadishu on 2009-04-21
Hi all...Mr Nooob here :)

First off, I'm impressed how more 'user-friendly' Ubuntu is since the last dabble I had a few years ago....though I realize I've still got a HUGE amount to learn to get to grips with it!!

I've downloaded and burnt the v8.10 iso and chose to install it as a windows application via Wubu....

I was wondering (with it being activated from a boot menu) if it would still run if windows got zapped by a virus or something or would it need to be installed as a stand alone OS?

I've got a 500gig HDD partitioned with (C:\) 60gb-Vista (D:\) 60gb - <empty> and the rest (E:\) Storage/Docs etc

I was going to put it on the 60gb D partition but got a bit panicky when it said it was going to resize the larger storage bit of the drive so opted for the safe route for now....though after having it on for a few hours - might go for it again before I start to start tweaking and getting things to run (I'm still having a problem getting my Creative Zen to be detected despite finding a few threads saying it CAN be done with Amarok or Gnomad2....wont have it for me yet :( )

Anyway...I digress....can someone enlighten me on my original query...?

Thanks and hi again ;)

---

### Post by Nano_ext3 on 2009-04-21
First is "Wubi" and second here is your answer:

If windows crashes that most likely just affected windows files under c: drive.  I believe as along as the Wubi folder is not corrupted, theoretically it should still work.  This is why I stress to users NOT to use Wubi at least until it matures, instead parition their hard drives with a LIVE CD of Gparted.

Nano

---

### Post by jsowoc on 2009-04-21
If I understand correctly, your question is whether or not your Wubi install would survive if a virus decided to eat up your Windows.

There are very many viruses for Windows, and each one does its own kind of damage. Some just give you pop-ups. Some steal your passwords. These would not affect Ubuntu regardless of how you installed it.

There are some nasty viruses, like ones that delete your files. Because your Wubi installation is just another file on the hard drive, nothing is stopping such a virus from deleting the file. These viruses are rarer than the above breed, but they exist.

Finally, there are super-nasty viruses that are aware of your partitions, and they don't care how you've installed Ubuntu - they are capable of trashing your entire hard drive. These, again, are rarer than the ads/password kind.

It is a bit more difficult to install Ubuntu on a separate partition, but if you already have a 60 GB empty partition, manual partitioning is not that difficult.
During the install, select "manual partitioning". Delete the 60 GB partition. Then make a 59 GB partition as "ext3" and set the mountpoint to "/". Make a 1GB partition as "swap".

---

### Post by mogadishu on 2009-04-21
"Doh" on the Wubu :rolleyes: (Iknew what I meant really...:tongue:)....and thanks for the replies so soon!

**jsowoc**...with regards to your instructions on what to do with my spare 60gb partition...are the quotation marks to be included (I suspect NOT...)

Thanks for your patience....I promise if I get it installed OK - I'll stop asking, what to you experts are fundamental/basic Q's, and do some in-depth reading on the 'Newbies' section...

I just want to get a good starting point to get my teeth into!

Thx

---

### Post by Gannon8 on 2009-04-21
> **mogadishu said:**
> "Doh" on the Wubu :rolleyes: (Iknew what I meant really...:tongue:)....and thanks for the replies so soon!

**jsowoc**...with regards to your instructions on what to do with my spare 60gb partition...are the quotation marks to be included (I suspect NOT...)No, its not even a command. Just run the Ubuntu installer.

I also don't really recommend 1GB swap. You can do it if you want, but 512MB I think is a better number.

---

### Post by Nano_ext3 on 2009-04-21
On older machines swap was a good idea, its a general rule to make it twice as big as your RAM size, i.e. 1 gig for 512 MB of RAM.  On new computers, a swap is really all that necessary, just like with good amount of RAM, increasing virtual memory is not needed on windows.

---

