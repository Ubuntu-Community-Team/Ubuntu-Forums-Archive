---
title: "how much space for root and for the user"
date: 2006-08-14
forum: Desktop Environments
---

### Post by joy83 on 2006-08-14
i am pretty much advanced in linux but totally new to ubuntu, one of my friends told me about this distribution so i installed it and he was right this is a very good distribution, now my question is how much space should i allocate for root and the user, because in ubuntu the first user is basically the root so should i keep the space for the user a lot more than the root so that i can install different softwares or does everthing install in root in which case i have to give more space to root, my linux partition is 43GB so how should i divide it between root and the user if i want to download and install lots of softwares,

---

### Post by kriding on 2006-08-14
if your talking about splitting your drive, then root has nothing to do with users. The root is where the  critical OS files are stored, and as such, it is where the OS boots from, so you need to flag this partition as bootable.

The home folder is where all the user files are kept, and the user settings.

The root user is an admin account that allows you to make system wide changes, so you don't actually log in as root, or saveanything as the root user, you just borrow the privaleges from the account, therefore you don't need to allot any space for the root user account.

---

### Post by wjp.reg on 2006-08-14
> **joy83 said:**
> i am pretty much advanced in linux but totally new to ubuntu, one of my friends told me about this distribution so i installed it and he was right this is a very good distribution, now my question is how much space should i allocate for root and the user, because in ubuntu the first user is basically the root so should i keep the space for the user a lot more than the root so that i can install different softwares or does everthing install in root in which case i have to give more space to root, my linux partition is 43GB so how should i divide it between root and the user if i want to download and install lots of softwares,

Typically the software you install will NOT be placed in your /home folder.  The /home folder is normally treated like "My Documents" folder in windows.

---

### Post by joy83 on 2006-08-14
thanks for the info, so thats how i installed it, of my 43GB partition for linux i gave 40 GB to home and 3Gb to root, and after that i started downloading some softwares using automatix but suddenly this popup popped up saying that i have very less space on root and i have used 96% of it, after 5 minutes it says that i have used 98% of it, so i was wondering if the software files are getting installed in the root directory which is only 3gb

---

### Post by wjp.reg on 2006-08-14
> **joy83 said:**
> thanks for the info, so thats how i installed it, of my 43GB partition for linux i gave 40 GB to home and 3Gb to root, and after that i started downloading some softwares using automatix but suddenly this popup popped up saying that i have very less space on root and i have used 96% of it, after 5 minutes it says that i have used 98% of it, so i was wondering if the software files are getting installed in the root directory which is only 3gb

You got it.  Small  correction: the apps are not getting installed in root folder, but rather on the /root partition folders like /usr /etc/ /opt, so it is a good idea to keep /root partition a little bigger than 3gigs, perhaps 10-12 (also has /tmp folder which is used for 'scratch' files).

---

### Post by joy83 on 2006-08-14
thanks for all these infos, i am learning a lot about ubuntu, but still i would like to know then what is the use of giving lots of space to the user, i mean i want to have lots of space in the account where my software and other files will be downloaded whether that be root or the user, so for that what should be the optimum space settings in a 43gb linux partition,

---

### Post by az on 2006-08-14
Just put everything on one partition.

It avoids problems like this.  You do not need more than one partition and a swap.  Itis easier and simpler to backup your data the regular way anyway.

---

### Post by [h2o] on 2006-08-14
> **azz said:**
> Just put everything on one partition.

It avoids problems like this.  You do not need more than one partition and a swap.  Itis easier and simpler to backup your data the regular way anyway.

But it is very nice to have /home on a different partition. I went from Suse to Ubuntu without cleaning my /home partition, and when I had Ubuntu installed I had all my documents, music and settings ok from the beginning. Really sweet :)

---

### Post by joy83 on 2006-08-14
so u guys are saying that i should have a swap and only one partition which is the root partition, so is this ok
760mb for swap
40 gb for root 
2 gb for user

now if i want to install a software i have got enough space (40 gb), but if i want to download any movies then where do i download it ? can i download it in root or do i have to download it in user (in which case i have to increase the size)

---

### Post by ozorba on 2006-08-14
My experienece:

I have a /boot partition of 128MB. Generally this is suffcient.
I also habe 760MB for the swap. Actually the swap should be at least as big as your RAM.

The / partition where everthing else goes should not be less than 6GB. 

If you have a large HDD then would it not be better to allocate 10GB for / partition (sufficient for large number of applications) and the rest for the /home?

---

### Post by joy83 on 2006-08-14
thanks for the reply ozorba, i was just wondering what is the use of this \boot partition

---

### Post by anindya_m on 2006-08-14
Hi,

Typically it's a good idea to keep /home on a different partition. In your case, as was already suggested before, a 10 GB / partition should be fine. So maybe you can try

/     - 10GB
/home - 32GB
swap  - 1GB

(assuming a total of 43 GB). Note that for linux you do not have to set the bootable flag on the / partition. GRUB will handle the booting. If in this situation you find that you have run out of space on /, you can make a /home/software directory and install stuff such as acroread, etc. there. Then you can just make symlinks to /usr/local/bin and they'll work fine.

regards,
Anindya

---

### Post by joy83 on 2006-08-14
can i download stuff in the root directory from the user so that in that case i can give a lot of space to root

---

### Post by kriding on 2006-08-14
I have read many threads on partitioning a drive for linux, and thi is what I've found.

the easiest method is to let ubuntu format the entire partition as one. This will create the swap partition and the root partition where everything is stored.

To manually partition the dirve i have read the best nethod is to have the following setup:-

/. - (root) at least 10gb
/swap - 1.5 x the amount of RAM you have
/home - remainder of the drive

there are arguments for and against both methods, but I prefer the second option as 'when' I break my installation, I still have all my saved files and apps.

---

### Post by hexion on 2006-08-14
My configuration is:

15 GB for /
25 GB for /home
2 GB for swap (1 GB of RAM x 2)

I don't know if it's the most correct but for me it's ok :P

---

### Post by anindya_m on 2006-08-14
> **joy83 said:**
> can i download stuff in the root directory from the user so that in that case i can give a lot of space to root

By default no. You can download the installer files to /home, then just run the installer as root - then it will install by default in the / partition. The installer files themselves do not have to be on the / partition. Does this answer your question (I might have misunderstood)?

---

### Post by joy83 on 2006-08-14
> **anindya_m said:**
> By default no. You can download the installer files to /home, then just run the installer as root - then it will install by default in the / partition. The installer files themselves do not have to be on the / partition. Does this answer your question (I might have misunderstood)?

thanks for the reply but i was wondering this, because in ubuntu the user is more or less the root so what if i make keep lot of space for the root and but i use the user account to download stuff  into the root account ( which has a lot of space)

---

### Post by az on 2006-08-14
> **'[h2o] said:**
> But it is very nice to have /home on a different partition. I went from Suse to Ubuntu without cleaning my /home partition, and when I had Ubuntu installed I had all my documents, music and settings ok from the beginning. Really sweet :)

Usually, when your applications act quirky, you want to delete the old configurations anyway.  It would have been trivial to backup your data and music an other way than using a seperate partition.

---

### Post by az on 2006-08-14
> **joy83 said:**
> thanks for the reply but i was wondering this, because in ubuntu the user is more or less the root so what if i make keep lot of space for the root and but i use the user account to download stuff  into the root account ( which has a lot of space)

You clearly would benefit from keeping your things simple.  Just put everything on one partition.  Don't worry about what goes where.  The package manager decides where applications and their files go and you put all your files in your home directory.

---

