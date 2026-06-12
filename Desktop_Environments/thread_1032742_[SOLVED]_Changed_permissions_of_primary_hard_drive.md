---
title: "[SOLVED] Changed permissions of primary hard drive by mistake now no sudo"
date: 2009-01-06
forum: Desktop Environments
---

### Post by taketimeout on 2009-01-06
Hello. 

Sorry if this is in the wrong category! Could a mod move it if it is! I have searched high and low for a solution but I think my situation is rather unique.

The problem is I was messing round with an external hard drive an permissions and I accidently changed the permissions of the hard drive where ubuntu is installed. Whooops.

Now I get the message about the home directory and .drmc file not having 644 permissions before i get to the desktop...AND I can't use sudo, get the error message 'sudo: must be setuid root'.

I can't re-install either because there is some data that I have had for the last however many decades that i need to keep. Pictures, accounts et

Could anyone give an idea how I could solve this dilema?

I've got the ubuntu LiveCD too if it's any conselation.

Chris

I also don't have sound or wireless connection anymore and when i start rhythumbox it crashes when play is pressed.

---

### Post by bunty on 2009-01-06
So let's recap . You have important accounts files and beloved photos that you have never even once backed up in "decades". Neither do you seem to have a backup of your *buntu installation.

Well I guess you will have to rot in hell. 

since you have not yet  mastered enough command line techniques to have completely destroyed your data there is still some hope of making a belated copy. Boot from any live linux CD and mount the partitions where you have your data. You should then be able to copy them off to some other medium like an external HD or USB flash device.

I don't think you can realistically expect to retore all the various permissions to get a correctly working system from what you have now, so it looks like a reinstallation. 

I also guess that you have not separated any of your user areas (/home) from the system partition so that may well get blown out too.

You can try to reinstall without reformating (expert mode during partitioning). If you are careful (and lucky) you may preserve /home which is presumably where your data is.

You could try installing with a different user name to leave the current user's home intact. Then copy across.

Good luck and need I say....b*** up.

If you have a lot of empty space on your drive use something like gparted live CD or partedMagic CD to shrink your partition and split things up.

I like to work with 7Gb partitions that I can quickly and regularly back up.

---

### Post by taketimeout on 2009-01-07
Ok! No need for the provocative language. :confused:

Thanks for your comments though! I have managed to chnge the permissions on the home folder using Nautilus and the LiveCD and now I am transferring it to an external HDD.

I will probably Partition my primary HDD so linux has it's own partition and the rest is for the home folder!

And I will take heed and back up!!! :lolflag:

Chris

---

### Post by scorp123 on 2009-01-07
> **bunty said:**
>  I don't think you can realistically expect to retore all the various permissions to get a correctly working system from what you have now, so it looks like a reinstallation. ...
 
You can try to reinstall without reformating (expert mode during partitioning). If you are careful (and lucky) you may preserve /home which is presumably where your data is.

You could try installing with a different user name to leave the current user's home intact. Then copy across. Yeap, looks like this is the only thing OP can do now.

---

