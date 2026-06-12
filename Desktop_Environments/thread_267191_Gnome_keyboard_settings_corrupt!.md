---
title: "Gnome keyboard settings corrupt!"
date: 2006-09-28
forum: Desktop Environments
---

### Post by VidarB on 2006-09-28
My Gnome keyboard settings are corrupt i think. If i press "i" - "5" is displayd on the screen, same for "u" and some other keys. 

The BIGGEST problem is that i cant login because both my username and password contains I an U ! ](*,) 

The keyboard works fine on my windows partition.

Can anyone help a noob?

---

### Post by whizbaby on 2006-09-28
Not knowing what crazed your keyboard I can help you to be able to login (would be long winded to check and change everything through live system).
Boot the liveCD, open a terminal and type (assuming *r0ckst4r* would work as a password on your keyboard, replace by what you want/is possible)
openssl passwd r0ckst4r
will give a result like this (though not the same when you do it)
**i60NXrYJEfH9Y**
then go (in terminal) to the ubuntu HD (with *cd* command, ask if unsure) and edit /etc/shadow of your hard drive (not of your live system, big difference):
sudo nano /etc/shadow
and do to your username what I did to my dummy
before:
dummy:**$1$9DHblwlm$l3bpZuE9mGpsl.pEgmNza1**:13419:0:99999:7:::
after:
dummy:**i60NXrYJEfH9Y**:13419:0:99999:7:::

(change the thing between the first two colons to the output of openssl)
and save.
Now dummy has the password r0ckst4r (and you whatever is typable with your keyboard).

---

### Post by VidarB on 2006-09-29
Changed my password, but how do i change my login? You see my login contains "i" also :-k

---

### Post by whizbaby on 2006-09-29
Change your username in (I changed to dummo)
/etc/passwd
and
/etc/shadow
(/etc/groups, too, if you want to delete the account later)
while in livesystem you should append to the /etc/sudoers of your HD
dummo    ALL=(ALL) ALL
(of course replace dummo by what you changed your username to)
to your liking, then you will be able to login. The first thing you should do is create a completely new user with new user name (your future account, because I don't know the number of problems heading at you because of changing the username) and copy your data (better not the configuration as something with the keyboard is wrong and the cause might be there) from your old account to the new. 
Add the new user to the group admin with
sudo adduser *replace_with_name_you_chose* admin
Then you may think about deleting the (old) account.
EDIT:
You can first try to rename the homedir
sudo mv /home/dummy /home/dummo     (replace the dummies)

and then change it in /etc/passwd (of HD),too. Also change the entry in /etc/groups mentioned above. See if you encounter problems (apart from wrong file permissions) then. (Anyway, it would be interesting to see if the new user has the same keyboard problem)

---

### Post by VidarB on 2006-09-29
Thank you for all your help, will try this later. :KS

---

