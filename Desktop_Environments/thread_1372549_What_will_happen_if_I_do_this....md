---
title: "What will happen if I do this..."
date: 2010-01-04
forum: Desktop Environments
---

### Post by Moozillaaa on 2010-01-04
...or what *SHOULD* happen...

I did a cp task:
cp  /dev/sdc5  /dev/sdb6

So, if b6 (object disk) is a 300G partition, and c5 (object disk) is only 100G partition...

...then this will make b6 into a 100G partition, with 200G leftover as 'unallocated'???

Right? Wrong? Flip a coin?

---

### Post by alwayshere on 2010-01-04
install gparted partion editor and take a look 

put this in terminal to install it 

sudo apt-get install gparted


you will find the launcher under admin...

or just put   
sudo gparted 

in terminal

---

### Post by 3Miro on 2010-01-04
```
gksudo gparted
```

using sudo for a graphical app is a bad idea.

You should never physically write into a device, you can permanently damage it. Use gparted to format and partition the drive the way you want and then nautilus to copy the files that you want to.

---

### Post by alwayshere on 2010-01-05
i have had no problems with sudo

---

### Post by Moozillaaa on 2010-01-05
> **alwayshere said:**
> install gparted partion editor and take a look 

put this in terminal to install it 

sudo apt-get install gparted


you will find the launcher under admin...

or just put   
sudo gparted 

in terminal

I had GParted running before and after the task. I saw AFTERwards in GParted, something I did not expect, and still cannot explain. 

I'm hoping to get a few answers of what I SHOULD have afterwards gotten in GParted, given the task as I executed it...

---

### Post by lswb on 2010-01-05
> **Moozillaaa said:**
> ...or what *SHOULD* happen...

I did a cp task:
cp  /dev/sdc5  /dev/sdb6

So, if b6 (object disk) is a 300G partition, and c5 (object disk) is only 100G partition...

...then this will make b6 into a 100G partition, with 200G leftover as 'unallocated'???

Right? Wrong? Flip a coin?

The short answer is "Wrong" cp works with files, not devices. I would not expect, for instance, that disk blocks would necessarily be copied in the same physical order between source and target. The "dd" command can be used to copy devices in this way, since it does a byte for byte copy, but there are better tools for the job.

---

