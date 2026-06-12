---
title: "Disk space management"
date: 2009-02-18
forum: General Help
---

### Post by farfromapro on 2009-02-18
I have ubuntu 8.1 installed on a 4 GB HD; the machine also has a 9 GB HD.

I'm wondering how to manageme my small amount of space with respect to packages / software installs / misc files...

Can I modify my apt-get, aptitude, dpdg,...etc. type commands to use a location on my larger drives as default?  Such as "moving" the /var/cache/apt/archives to the 9 GB HD?  Also the default location for package installs?

I think I want the system on the small drive and everything other than the base install on the larger one? (which is pretty small and I am sure I'll be upgrading in a few months)

What is the best way I can do this?  Maybe some type of RAID setup that would make data locations transparent to the user?

Is the true solution to just be very carefull with where each install goes?  In all honesty I've only installed a few packages and didn't see any way to install them where I wanted...

Any opinions or advice is always appreciated!

thanks!

---

### Post by yoyoned on 2009-02-18
mount /usr and/or /var  on the 9 gig disk

---

### Post by crokett on 2009-02-18
> **yoyoned said:**
> mount /usr and/or /var  on the 9 gig disk

What he said.  I have a box with a 20GB where Ubuntu lives and a 70GB where /home is.  I added the 70GB after the install and here is what I did.  You can adjust accordingly. 

I created a partition on the 70GB disk.  I mounted it temporarily under a directory I called /stuff

I copied everything from /home to /stuff.  Then I edited fstab to mount the partition on the new drive to /home.  Worked great.

---

### Post by farfromapro on 2009-02-19
Thank you for the info!

This is a brand new install and I have only installed a few packages (which I could just redo in the end); so I may omit the copying stuff and work with that fstab command.

For a noob is it really as simple as fstab?  I'll do some research to understand that command a little more.  the 9 gig drive is mounted and accsssible so does that mean the fstab will basically mofiy the system to point to the new drive?  i.e. no new install?

Thanks for the direction!

---

### Post by dcstar on 2009-02-19
> **farfromapro said:**
> I have ubuntu 8.1 installed on a 4 GB HD; the machine also has a 9 GB HD.

I'm wondering how to manageme my small amount of space with respect to packages / software installs / misc files...

Can I modify my apt-get, aptitude, dpdg,...etc. type commands to use a location on my larger drives as default?  Such as "moving" the /var/cache/apt/archives to the 9 GB HD?  Also the default location for package installs?

I think I want the system on the small drive and everything other than the base install on the larger one? (which is pretty small and I am sure I'll be upgrading in a few months)

What is the best way I can do this?  Maybe some type of RAID setup that would make data locations transparent to the user?

Is the true solution to just be very carefull with where each install goes?  In all honesty I've only installed a few packages and didn't see any way to install them where I wanted...

Any opinions or advice is always appreciated!

thanks!

You can simply replace the folders with soft links to locations on the large drive (assuming you have a Linux filesystem on it). Also setting Synaptic to delete packages after install can save you a lot of space.

Personally I would have the base O/S on the 9G drive and use the smaller one for /home, that would allow you to install another version on the 9G without losing your user data.

---

### Post by farfromapro on 2009-02-19
Using softlinks is a pretty interesting solution dc star.  

> Personally I would have the base O/S on the 9G drive and use the smaller one for /home, that would allow you to install another version on the 9G without losing your user data. 

So I copy current contents of /home from 9GB to 4GB, install base on 9... will the /home ever use all of 4GB drive though?  I want to utilize as much of the limited space that I have.

thanks... haven't had a chance to look into fstab; this weekend I will...

Thank you!

---

### Post by HermanAB on 2009-02-19
You can move a single directory too:
Copy the whole directory somewhere else using 'cp -a', delete the orignal directory and replace it with a soft link to the new one using 'ln -s'.

Cheers,

Herman

---

