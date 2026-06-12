---
title: "lost all email in evolution after hibernating"
date: 2009-01-28
forum: General Help
---

### Post by shadowone on 2009-01-28
Realize it's a touch more complex then most question, and I've already posted it as a bug... but hoping to get some advice from here as well

Always running the most up to date version of intrepid (8.10)

Yesterday, I decide to clean up my Microsoft exchange folder... Created or updated about 10 filters, 8 new folder, and moving lots of data around. All in all, brought down original mailbox size from 400+ email to about 125. Open ppt file and start reading

A few hours later, put computer in hibernation for the night.

Today, turn on computer, new desktop in place (i.e. hibernation didn't work, no evolution, no openoffice)
run evolution, and it gives me the new user setup dialog....
puzzled, I browse around and see my exchange folders still exist on the computer. I seem to be unable to restore data from the setup dialog. About to restart until I realize there is an evolution update to 2.24.3 (along with the kernel), which I decide to do.

After reboot, still getting new user setup.... (here, I'm not sure if the exchange folders are still present). I have difficulty to reestablish my connection to exchange from the setup (it usually requires a few workarounds)
So I decide to create a dummy email fetch to localhost and reconfigure my exchange from the inside. I've done this before, and I don't recall anything going wrong.

Dummy gets setup, and then I seem to have lost all my emails. In fact, it's all gone!!! 5+ years of emails, my exchange account, and a pop account have all vanished. Both the .evolution folder and .gconf are fresh puppies

Read somewhere that massive email reorganization in evolution can screw with memory... (I got 1 GB)

Short of taking my hard drive to an expert for data retrieval, what am I supposed to do?

---

### Post by pytheas22 on 2009-01-28
I'm not sure how that would have happened, but hopefully you can get a better explanation in your bug report.

As for recovering your data, you could boot to the Ubuntu live CD, install photorec by typing:
```

sudo apt-get install testdisk
```

(photorec is part of the testdisk package) and then use it to try to recover your mail.  Photorec can find deleted text files, which I believe is the format in which Evolution stores local mail.  Unfortunately, photorec can't distinguish between different kinds of text files, but once you've recovered all of the the ones from your hard disk, you could grep out the email relatively easily--I'm happy to provide more guidance on that once you get to this point

---

