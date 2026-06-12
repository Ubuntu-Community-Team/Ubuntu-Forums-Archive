---
title: "Latest Ubuntu 14.04 update, now no side bar or top bar, need help..."
date: 2014-07-09
forum: Desktop Environments
---

### Post by Christopher on 2014-07-09
I updated my desktop last night, i just booted it up and put in my password and after my desktop loads all seems fine, but i have no side bar or top bar with my clock on it. When i click my reset button on my computer tower and Im at my login screen I select "Guest Session" all is good, any help to fix this issue would be very much appreciated.

---

### Post by Christopher on 2014-07-09
How do i bring up terminal & launch Firefox in 14.04?  Thanks in advance.

---

### Post by Christopher on 2014-07-09
Ok i created another user account & launched the software updater, updated & even rebooted my PC, crossed my fingers and all is good with the new user account. Not sure what happened with my main account sidebar? I try ctrl-alt-t with my main account and no terminal pops up at all. When i update with the software updater do the updates affect both accounts or just the one im logged into? thanks in advance.

---

### Post by ibjsb4 on 2014-07-09
I only use only one account, but I would think an update would do both.  What are you smoking?

---

### Post by Christopher on 2014-07-09
> **ibjsb4 said:**
> I only use only one account, but I would think an update would do both.  What are you smoking?

Im not sure why you feel the need to personally attack me, im just trying to get this issue resolved. Thanks for your reply.

---

### Post by ibjsb4 on 2014-07-09
Wasn't personal. just asking. Sorry

---

### Post by ajgreeny on 2014-07-09
> **ibjsb4 said:**
> I only use only one account, but I would think an update would do both.  What are you smoking?

I think you totally misunderstood the reason behind the OP's question at the end of post #3.

You did, however, answer the question correctly; any updates to the system done with the updater application, or apt-get install, or synaptic, or software-centre will all update every user on the system.  There must be some configuration file or folder in your original user's home that caused that problem, but if you're using unity I have no idea what it might be as I don't use that DE.  You might try renaming the hidden** .config** folder in the home folder of that user to see if doing that rights the wrongs that you're seeing at the moment.

---

### Post by TCSnyder on 2014-07-09
I had this issue on an install one time. For some reason ubuntu found a monitor that did not exist and made it the primary display and the screen i saw was the secondary monitor. Can you right-click and "Change Background" and then go back to "All Settings" and check your display settings?

---

### Post by ibjsb4 on 2014-07-09
Thanks ajgreeny
 ..

Guess this would be a good time to step out of this one.

---

