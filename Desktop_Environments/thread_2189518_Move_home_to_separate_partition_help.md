---
title: "Move /home to separate partition help"
date: 2013-11-22
forum: Desktop Environments
---

### Post by kingkratos on 2013-11-22
Hello,

I am following the instructions at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) to move my /home to a separate partition and have run into a possible issue. I am on step > [h=2]Check Copying Worked[/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]You should now have two duplicate copies of all the data within your home directory; the original being located in /home and the new duplicate located in /media/home. You should confirm all files and directories copied over successfully. One way to do this is by using the diff command:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo diff -r /home /media/home[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]The only difference that should exist is the excluded /.gvfs directory mentioned above. If you are doing this from a [/FONT][/COLOR][LiveCd]("https://help.ubuntu.com/community/LiveCd")[COLOR=#333333][FONT=Ubuntu] or to an exisitng partition that already has stuff on it then you may find other differences but hopefully it should be obvious which diffs you can ignore.[/FONT][/COLOR]

and am recceiving a lot of diff "errors". They are all referencing .ecryptfs/(my username)/.Private and stating that these are all different. Is this supposed to be this way? What do I need to do to make sure this works correctly and I mess this up?

Kratos

---

### Post by oldfred on 2013-11-22
Is /home encrypted?

 If encrypted:
[http://askubuntu.com/questions/17332/how-can-i-move-an-encrypted-home-directory-to-another-partition](http://askubuntu.com/questions/17332/how-can-i-move-an-encrypted-home-directory-to-another-partition)

---

### Post by kingkratos on 2013-11-22
Yes, it was/is encrypted. I ended up finishing the directions as is from the link I originally posted and rebooted my system. Everything is working just fine, but now I am not sure if my data is encrypted or not. Is there a way to check and see if it is still encrypted?

Kratos

---

### Post by oldfred on 2013-11-22
If you boot from a live installer and do not use your passphrase do you see data you should not?

---

### Post by kingkratos on 2013-11-23
I have not tried that. I will give it a try right now and post back my findings.

Kratos

---

### Post by kingkratos on 2013-11-23
Ok, booted with live cd and tried to get into /home and was told I didn't have permission to access that area. Looks like I did everything correctly. 

And even better I finally got my swap partition to auto mount without errors! 

To think just a couple days ago I thought I was screwed when my upgrade failed miserably! Now that I have my data on a separate partition, I feel much safer doing upgrades.

Thank you for your suggestions as I never even thought about simply trying to access /home while logged out.

Kratos

---

