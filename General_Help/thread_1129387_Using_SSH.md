---
title: "Using SSH"
date: 2009-04-18
forum: General Help
---

### Post by sr243 on 2009-04-18
Noob question:

From my laptop, I ssh'd into my university cluster to run a batch job that takes a day or so. As the job is running, do I have to leave the ssh connection open, or would the job continue even if I disconnect the laptop?

If so, if I disconnect, is there any way for me to know that the job is complete?

---

### Post by sr243 on 2009-04-18
?

---

### Post by prshah on 2009-04-18
> **sr243 said:**
> 
From my laptop, I ssh'd into my university cluster to run a batch job that takes a day or so. As the job is running, do I have to leave the ssh connection open, or would the job continue even if I disconnect the laptop?


If you disconnect the ssh connection, any batch jobs started in that session will be interrupted and closed.

To prevent this, use the excellent "screen" command; you need to install it first; it's available in the repos. To install, ssh into your server, and use```
sudo apt-get install screen
``` then just prepend the word "screen" to your command. Your command will open in a new virtual screen. To disconnect this screen and return to your ssh terminal, press Ctrl+A, Ctrl+D. Now, the job will continue to run even if you disconnect the ssh terminal.

You can log back in anytime and check if the screen is still running using the ```
screen -list
``` command. To re-open the virtual screen, use the command```
screen -r
```.

As long as the job is running, it will be listed in the screen -list command output. When the job terminates, the virtual screen will terminate as well.

---

