---
title: "damn install.."
date: 2009-04-13
forum: General Help
---

### Post by drakoumel on 2009-04-13
atm i am in the demo mode of ubuntu and i am installing em.. i am doing the partion part.. 
i have already made an ext3 partion of my main drive i click it but it says no root file system is defined what i gotta do?

---

### Post by brunogirin on 2009-04-13
Are you using the default option where Ubuntu uses your whole drive or are you trying to set up partitions manually? If the later, did you tell it to mount your ext3 parition as the / partition? / is the root partition on Linux so it needs to be mounted.

---

### Post by drakoumel on 2009-04-13
i do it manualy .
what i do first is change the use as for ext3 journaling file system ( it was do not use ) then set the megabytes and click to format it coz i got some things i wanna get rid off.. what do i have to do about the root thing?

---

### Post by brunogirin on 2009-04-13
When you enter the partition details, you should have a drop-down box to specify what file system will be allocated to that partition: it should be a list that includes things like "/", "/boot", "/home" and a raft of others. Select the "/" option: this will tell the partitioner to use the partition for the root file system.

Don't forget to create a swap partition too.

---

### Post by Yvan300 on 2009-04-13
It's been a while since i installed ubuntu, but when you are doing the manual stuff and after you have set the partition to ext3 journaling system you will see a little box that i think says what to use the partition for. When you click the box, you will get a whole list with mount points. / is root. You need to select / from the list to be used as your root partition.

---

### Post by drakoumel on 2009-04-13
i made a swap partition which i hadnt done named my other partition under the /svr ( on of the list ) but still no luck.. i will end up chossing another hard drive to install it.. 
if i choose another hard drive when i start up my pc will it ask for which OS to use? or it will load only one?

---

### Post by ajgreeny on 2009-04-13
Just choose /, not /svr on the dropdown box for the use of the partition.  Another disk will make absolutely no difference.

> if i choose another hard drive when i start up my pc will it ask for which OS to use? or it will load only one?           Sorry but I don't understand your question.  If you are installing ubuntu from the live CD it will only install that, not anything else, but you must choose  /  as the use for the main partition.

---

### Post by Yvan300 on 2009-04-13
Oh yeah and you might want to make a home partition for all your data. This is convenient when it comes to changing operation systems etc. So you create your root partition (/), your home partition (/home) and your swap partition and you're all set :)

---

### Post by drakoumel on 2009-04-15
i just put the ubuntu on my 2nd drive and its ok.. thnx for the help

---

