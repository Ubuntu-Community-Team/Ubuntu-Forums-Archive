---
title: "Help Please!!!"
date: 2005-05-20
forum: Desktop Environments
---

### Post by rum beverage on 2005-05-20
I'm not sure where this should go and to tell you the truth I'm in no mood to care.  I _ up big time...and I mean BIG TIME.  I was trying to delete from hidden directories in my home drive and apparently i shouldn't be using the wild card while doing that.

My home directory is gone...completely.  I need to know if there is any hope in hell to get this back.  I've unmounted the drive and am using the root directory as my home in failsafe at the moment.  Please people, I'm sure some of you can imagine what I'd be feeling if any of you were stupid enough to do the same thing.  I'll admit I haven't checked the forums to see if anyone has had this stupid of an issue before but at the moment I just want to get on my way to finding some sort of solution...please help!

---

### Post by mtron on 2005-05-20
How could you delete your home directory? did you use a root terminal? 

if so, have you checked under /root/.Trash ?

and if it fails just create a new account from terminal 
sudo adduser *username*

---

### Post by rum beverage on 2005-05-20
I didn't actually delete the /home directory i just used the contents of my user directory

---

### Post by mtron on 2005-05-20
so you deleted the /home/username directory, right? and it is not in the root's trash i pointed you to?

---

### Post by rum beverage on 2005-05-20
[QUOTE=mtron]so you deleted the /home/username directory, right? and it is not in the root's trash i pointed you to?[/QUOTE]
 No it's not.  I've found what seemed to be my only solution.  i used reiserfsck and it pumped the lost+found directory full with what it could recover.  it seems to have recovered all the files i think is necessary, but it seems to put them in numbered directories and i can't really seem to find an easy way of sifting through them all.  i'm wondering can someone tell me where evolution stores email messages so i can try and recover them

---

