---
title: "Evolution Will not Start up"
date: 2011-10-29
forum: Desktop Environments
---

### Post by Alpha99 on 2011-10-29
Hi there 
Can any one help here - Running Ubuntu 11.10 OS

My Evolution mail client will not start up:
I have done the following so far:
1. UN-Installed  and reinstalled the Application. No improvement
2.There are no sessions of Evolution currently running on the system  
3. I have tried to restore from backup but this also dos not help same problem.
4.When i try to run the Application it opens - But then closes.
5.The only way to get evolution to stay up is to run it from the terminal - sudo evolution
   Whilst implementing changes setting up accounts- I have this Terminal Response:-

 (evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed

(evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed

(evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed

(evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
Segmentation fault

However i have checked the Keyring and i can see the password and all the relevant detail are there, so why wont it work? 

Is there anything more that i need to do or haven i missed out something or do i need to do more like restart the system that dos not help.

Can anyone help her please or is it a case of reinstalling the OS?
Thanks

---

### Post by zakjapanner on 2011-11-04
Same here - anybody?


> **Alpha99 said:**
> Hi there 
Can any one help here - Running Ubuntu 11.10 OS

My Evolution mail client will not start up:
I have done the following so far:
1. UN-Installed  and reinstalled the Application. No improvement
2.There are no sessions of Evolution currently running on the system  
3. I have tried to restore from backup but this also dos not help same problem.
4.When i try to run the Application it opens - But then closes.
5.The only way to get evolution to stay up is to run it from the terminal - sudo evolution
   Whilst implementing changes setting up accounts- I have this Terminal Response:-

 (evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed

(evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed

(evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed

(evolution:4267): e-utils-CRITICAL **: ec_assistant_forward: assertion `link != NULL' failed
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
Segmentation fault

However i have checked the Keyring and i can see the password and all the relevant detail are there, so why wont it work? 

Is there anything more that i need to do or haven i missed out something or do i need to do more like restart the system that dos not help.

Can anyone help her please or is it a case of reinstalling the OS?
Thanks

---

### Post by Alpha99 on 2011-12-01
> **zakjapanner said:**
> Same here - anybody?

Hi  zakjapanner

I am not sure if you are still looking for a solution but after many attempts I found one after reporting on Bugzilla (66310) for a solution. ( [http://www.bugzilla.org/](http://www.bugzilla.org/)) Try here next.

You Might want to install gbd if not on your system or not installed, and run evolution in gdb at the command line after.

It might be an idea to set up an account with  Bugzilla and report your problem there if you still have an issue I found them very helpful.

Sorry I am new but hope this helps you out.

---

