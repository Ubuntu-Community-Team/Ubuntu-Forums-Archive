---
title: "Apt-get problems--&gt;locked file"
date: 2006-01-03
forum: General Help
---

### Post by orsula on 2006-01-03
Hello,

I am fresh to Ubuntu but had some experience with SuSe a while ago. 
I am trynig to install skype with apt-get. I attempted to follow some posted threads but always come to the following message. This one happened when I simply tried to do apt-get update

gidi@desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

what is that locked file and how can I unlock it?

Another newbie question: I thought that continuously pressing the arrow keys or backspace will continue to backspace or move the cursor. This is the first time I have a situation where I need to press multiple times on the key to get the same effect. It never happened to me on any OS before. Any ideas?

Thanks much and happy new year

Gidi

---

### Post by brynjarh on 2006-01-03
Do "sudo apt-get update" instead of just apt-get update.

---

### Post by orsula on 2006-01-03
Thanks...this seemed to work. Would you know the easiest way to put skype on?

much appreciated

---

### Post by orsula on 2006-01-03
I get the following when I try to install skype:

gidi@desktop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate

---

### Post by darth_vector on 2006-01-03
there is an article in the wiki on how to install skype:

[https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto)

worked fine for me.

---

### Post by dickohead on 2006-01-03
For the multiple key tap situation, you might have either:
A weird keyboard currently being used as a standard one
or
A standard keyboard being used a s a weird one

You will need to reconfigure your xorg.conf file in order to make sure that it is loading the required keyboard map and driver. (post your xorg.conf in another thread and ask for pointers or search the foum/google)

---

### Post by orsula on 2006-01-03
thanks
I fixed it in system>preferences>keyboard......newbie afterall ;)

---

### Post by orsula on 2006-01-03
Thanks. I tried to follow that and got to a point where I am asked to install the following:
sudo apt-get install libgcc1 libqt3-mt libstdc++5 

when I try to do so I get the following:gidi@desktop:~/src$ sudo apt-get install libgcc1 libqt3-mt libstdc++5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I really don't know what to do next to unlock whatever it is that is locked.
Any ideas?

---

### Post by darth_vector on 2006-01-03
are you presently getting any other updates with apt-get or synaptic? you cant do more than one at a time.

---

### Post by orsula on 2006-01-03
ok - thanks. I didn't think that simply having synaptic window open will cause problems, even without actually installing any packages.
All seems to work. If I could just ask one more thing - 
I have a buddy list that I know exists for my account when I log using Windows. Would you know why I get zero contacts when I log to the same account using Linux?

again - thanks for all the help.

---

### Post by darth_vector on 2006-01-04
your contacts are probably kept locally - i dont use skyp much so i dont know. i think the easiest thing would be to copy them over one by one, but there may be a way of sharing the data if you have fat32 partitions. twould be hairy, i think.

---

### Post by simon_is_learning on 2006-01-12
If you quit a downloading with ctrl-z. Then Apt-get wont start again becoude it has Orphaned proces going on..  

I managed to instead of reboot do a kill -9 PID
(find out the pid by running ps -fu root)

Maybee not relevent for the moment, but hey, I'm just so proud of being able to solve a problem.. ;)

cheers

---

