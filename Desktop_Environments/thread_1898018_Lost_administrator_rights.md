---
title: "Lost administrator rights"
date: 2011-12-20
forum: Desktop Environments
---

### Post by prashant.saraf on 2011-12-20
Today some how I lost my admin right. now I can't mount any of the usb/attached drive. I can't unlock the user details.



I have tried following thing

i rebooted to recovery mode and login as root to reset the default user password but i got following error.
```

Authentication token manipulation error
```

Please help, I am using ubuntu 11.10

---

### Post by prashant.saraf on 2011-12-20
with this I also getting new Problem.. my system is not shutting down after clicking shutdown. it gets log off and on login screen nothing happens

---

### Post by prashant.saraf on 2011-12-21
can someone please help me on this???

---

### Post by grahammechanical on 2011-12-21
Do you have more than one user on your system? Perhaps you have a user who does not have administration rights and you are logged in as that user.

I have two users like this. If I log in as myself with Admin rights I can shut down. But If I log out and then log in as the user with Standard rights then shut down will only get me to the log in screen where I have to log in as the user with Admin rights in order to shut down the system.

It is a way of preventing one user (a second user) from shutting down the machine and thus loosing data that the first user was working on when he logged off.

Regards.

---

### Post by prashant.saraf on 2011-12-22
Ok.. I have only one user till I install openbravo and Oracle, openbravo created one user and Oracle created one.
So is there any way to create additional  admin user ??  or how to grant admin user right to current user?

---

### Post by ubix on 2011-12-22
> **prashant.saraf said:**
> ...

i rebooted to recovery mode and login as root to reset the default user password but i got ...
So you have **root** account set up?

How exactly did you attempt to change the problematic user password, in GUI or from the terminal?

How did the root account get set up? Did you do it or someone else? You must have set the password for root at the time of creation. Use the same technique to change that user's password now.

You should have been doing something along these lines:

```

1.   Open a terminal and login as root
2.   su
2.1. Enter root's password
3.   passwd problematic_user_id
3.1. change-it
3.2. retype-(verify)-it
```

or alternatively something a bit different but logically the same with **sudo**.

If **sudo** got corrupted than the first method I showed you (in the code window above) is your only bet. Short of fixing the error you are getting, nothing else except reinstalling OS will work!!!

Please, tell us what I asked on top of this reply.

---

### Post by ubix on 2011-12-22
There is one other thing you may try, _if you know the password for your Oracle user_.

1) open non-graphic terminal by pressing **<Ctrl+Alt+F1>**
2) log in as oracle user
3) sudo passwd problematic_user_id

You usually get back to graphic display by clicking  **<Ctrl+Alt+F7>**. If F7 doesn't work for you try in sequence all other function keys.

---

### Post by prashant.saraf on 2011-12-23
I tried to change the password of user. it was successfully done but issue is not resolved.

also I tried to  **<Ctrl+Alt+F1> **but it is giving just red bar in title nothing is happening.

Also below is output of my group
```

userabc@localhost:~$ groups
userabc root adm dialout cdrom plugdev lpadmin admin sambashare dba
```please suggest me what to do next. I can create a new user with admin rights as I am single user accessing this system. Can you suggest how to create admin user using command prompt.

---

### Post by ubix on 2011-12-23
> **prashant.saraf said:**
> I tried to change the password of user. it was successfully done but issue is not resolved...1) Why is the issue not resolved?
2) What is the problem now?
3) How did you change the password? 

I want to know what works and what does not!

---

### Post by prashant.saraf on 2011-12-28
> **ubix said:**
> 1) Why is the issue not resolved?

I tried all my best but still I am not able to solve this.
> **ubix said:**
> 2) What is the problem now?
1. I do not have any of rights like mount drive(not even pen drive), 
2. Even can't shutdown the system 
> **ubix said:**
> 
3) How did you change the password? 

i use following command with actual user name
```
sudo passwd username
```> **ubix said:**
>  I want to know what works and what does not!
Every thing is working as normal just I can't do the above mention things.

---

### Post by ubix on 2011-12-28
> **prashant.saraf said:**
> I tried to change the password of user. it was successfully done ...
...
Every thing is working as normal just I can't do the above mention things.
How did you change the password for the user? If it was successfully done from a different user account I need to know how did you do it? I thought you were not able to use that user. Do you, or do not you have a root password and account?

I still do not know what exactly is not working, is it your **sudo** that gives you headaches?. Can you use **su**?

Everything is not ***»working as normal«***. Your function keys are not doing what they should. Without them  we have to improvise, if at all possible due to your other sudo problems, to get you logged in as another user. As far as I know you have at least two more regular users installed on your system. These are your words: ***»_... openbravo and Oracle, openbravo created one user and Oracle created one_«***. We need to login as one of these and use their sudo facility, because you have screwed up the one for the user for which you had changed the password. We need function keys to work - for that, to bypass your current sudo screw-up.

Are you sure your function keys are NOT working?
How and where (on what hw) are you running your Ubuntu 11.10?
What exactly do you mean by: ***»is giving just red bar«***
Did you try **<Ctrl+Alt+F1>**, **<Ctrl+Alt+F2>**, **<Ctrl+Alt+F3>** ... **<Ctrl+Alt+F7>**

---

