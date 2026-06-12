---
title: "Failsafe MOde"
date: 2009-04-14
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-14
******i accidently use the rm -r cd /home/suresh.. after i restart my system go to the Fail safe mode..it is logout the 10seconds.. how to recover this problem**

---

### Post by maheshasolkar on 2009-04-14
If you used 'rm -r cd /home/suresh' you probably removed your entire home directory. If so, you have deleted all your settings and data.

Can you login as yourself in fail safe mode?

---

### Post by suresh_vandiyur on 2009-04-14
> **maheshasolkar said:**
> If you used 'rm -r cd /home/suresh' you probably removed your entire home directory. If so, you have deleted all your settings and data.

Can you login as yourself in fail safe mode?
NO.. i can't login.. after i create a new user.. that also the go to fail safe mode.. is it possible recover this problem?.. any options.. reply me..

---

### Post by maheshasolkar on 2009-04-14
After creating the new user did you delete the old user, or kept it? If the old user was set for auto-login, it might still be a problem.

Can you login as the new user?

---

### Post by suresh_vandiyur on 2009-04-14
> **maheshasolkar said:**
> After creating the new user did you delete the old user, or kept it? If the old user was set for auto-login, it might still be a problem.

Can you login as the new user?
i did not delete the old user..am using ubuntu 7.10.. can u explain how to recover this problem. in /home the old user home directory was gone.. but old user login in recovery mode..
how to recover this problem.. plz explain me...

---

### Post by maheshasolkar on 2009-04-14
If the old user directory in /home is gone, it is hard to get the data back. Unless you use some low level hard disk data recovery tools (which I am clue less on).

If you have a back up of your old user data, I'd suggest you create a new user and then restore the old user data from back up via *sudo*.

---

### Post by suresh_vandiyur on 2009-04-14
> **maheshasolkar said:**
> If the old user directory in /home is gone, it is hard to get the data back. Unless you use some low level hard disk data recovery tools (which I am clue less on).

If you have a back up of your old user data, I'd suggest you create a new user and then restore the old user data from back up via *sudo*.
i no need the old user backup.. i need login via new user... that all.can u tell me..

i go to recovery mode.  i add the new user but not create in home directoy for the new user in /home...how to recover this problem

---

