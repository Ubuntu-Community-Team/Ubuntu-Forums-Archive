---
title: "OMG I friggin typed sudo rm * ~"
date: 2009-04-24
forum: General Help
---

### Post by dogdaynoon on 2009-04-24
Ok so I am using 8.10 on a playstation 3.... very similar to ubuntu

I was trying to clear my backup files, you know the ones that end in "~".

So I typed in this little diddy. "sudo rm * ~"   
Notice the space in between the * and the ~ ! DangIT!!!!
Is there any way back? I have not done anything except :dir  

Lost like 2 hrs of work on website!!! crap!!!

Thanks,
dogdaynoon

---

### Post by jowilkin on 2009-04-24
There are tools to try to recover deleted files, but it is not easy.  You should immediately stop using the machine.  Probably shutting down X is a good idea too.  I will try to find a link for you.

Edit: I'm assuming you are using EXT3 for your filesystem: [http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by jimv on 2009-04-24
First, turn off the machine and boot from the live CD.

Then read this:

[http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html](http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html)

---

### Post by dogdaynoon on 2009-04-24
I am checking out jimv's link now... will let you know.
in the mean time if you think of any thing, pleeeease let me know.
Thanks,
dogdaynoon

Edit: jowilkin, That is  a huge tutorial. I am gonna get some sleep. I will look at it again in the morning.
Thanks guys...

---

### Post by dogdaynoon on 2009-04-26
So I got foremost to work. It is an amazing tool to anyone who accidentally deletes important files.

SCARY but amazing...

---

### Post by Peasantoid on 2009-04-26
Question: Were you trying to type "sudo rm *~" in order to remove backup files?

Also, be glad it didn't delete your home directory &#8212; you'd have had to use -r.

---

### Post by dogdaynoon on 2009-04-26
> **Peasantoid said:**
> Question: Were you trying to type "sudo rm *~" in order to remove backup files?


LOL That is exactly what i was trying to do. When you accidentally put a space tween the * and the ~ you get very undesirable results.
I happened to be inside the directory where the backup files and the main files were. It only rm'd the files and none of the directories. Thank Tux for that little can't rm directories without the -fr option.

---

