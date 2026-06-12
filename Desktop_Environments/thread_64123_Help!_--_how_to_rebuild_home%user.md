---
title: "Help! -- how to rebuild /home/%user"
date: 2005-09-09
forum: Desktop Environments
---

### Post by pear-i on 2005-09-09
Help!!

i was renaming my username and accidentally deleted the wrong files in my /home/%user folder... 

so right now when i login as my primary user it just says gnome has quit in 10 seconds and stuffs...

I managed to make a temporary account... but as of right now it can't seem to sudo at all

even tho it has
<strong> %user  ALL=(ALL) ALL </strong> (not commented  its variable) </strong>

and the 
<strong>system_username	ALL=(ALL) NOPASSWD: ALL </strong>

yet despite that sudo functions don't work... and since this is ubuntu thats vital -- before i delete my only working sudo account any ideas?

thanks!

---

### Post by pear-i on 2005-09-10
ok now i feel kinda stupid... i tried getting into root su sudo and deleted teh accounts... so right now i have a working ubuntu installation with no accounts...

any ideas how i might create one that works w/ all the sudo stuff?
+i used useradd -g admin %name but stil nothing

---

### Post by amohanty on 2005-09-10
Try:

useradd -G<username>,admin -d/home/<username> <username>
passwd <username>

and setup the password, and log back in.

HTH
AM

---

### Post by pear-i on 2005-09-10
hms i can get into the accounts right now

but for some reason my accounts get get into sudo
even tho the one i messed up can get into su.... 

so i can get into the root's startX

problem is -- i want to get get a secondary sudo account working so i can delete my primary account and remake it... (since its corrupt and won't let me login)

---

### Post by amohanty on 2005-09-10
I think it will be easier for you to find out whats wrong and fix it, or you will lose all your settings and all. so what exactly is the problem with your primary account:
you cannot sudo?

AM

---

### Post by pear-i on 2005-09-10
basically whats wrong with my primary accoutn is that when i login to gnome it quits within 10 seconds and gives me some text about how the settings for my account are kidna screwed over.

what i'm trying to do is to give my secondary account sudo perms
so that i can delete the primary one and recreate it and then reconfigure it so that it works again.

(long story short i tried renaming my primary account, and after doing that it apparently wrote over the original home folder and thus impaired my gnome login settings)

so um.. yeah any ideas?

---

### Post by amohanty on 2005-09-10
In your primary account delete every file except the following:
.bash_profile
.bashrc
,Xauthority

Try logging in then.

AM

---

