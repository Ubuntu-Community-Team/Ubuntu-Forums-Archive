---
title: "Programs not responding. Can I increase &quot;waiting time&quot;"
date: 2014-06-22
forum: Desktop Environments
---

### Post by rvdmeijden+launchpad on 2014-06-22
Since my update to 14.04 and gnome shell 3.12 some programs have the tendency to start slow according Ubuntu. 
After programs like the "package manager" and bijiben notes a dialogue screen pops-up saying that the program has stopped responding and I can close of wait. Waiting does the trick. 

So the question is can I specify for example Bijiben a longer waiting time so I don't get this message?

Thanks

---

### Post by grahammechanical on 2014-06-22
I have only seen that message when I am closing an application and it is busy doing something. I think that message is a response to an action that we have started. The system is saying that it cannot carry out the action and giving the reason why it cannot carry out the action. It is designed to prevent us getting impatient and doing something that will mess up the OS or cause us to lose data such as powering off the computer because we think it has stopped working.

Regards.

---

### Post by tgalati4 on 2014-06-22
There is something called the "watchdog" that monitors processes to detect any that have "hung".  There is some control over how sensitive it is.

> tgalati4@Mint14-Extensa ~ $ apropos watchdog
rtkitctl (8)         - Realtime Policy and Watchdog daemon control

You can install *htop* and monitor your processes in a window to see what the bottlenecks are.

There is also the *watchdog* package that you can install, but it uses the hooks within the kernel to reboot the machine if a process gets stuck for more than 10 seconds--not very useful for a desktop environment.  [http://askubuntu.com/questions/134899/watchdog-0-process-using-all-my-cpu-suddenly](http://askubuntu.com/questions/134899/watchdog-0-process-using-all-my-cpu-suddenly)

---

### Post by rvdmeijden+launchpad on 2014-06-22
I'll check what I can see on htop when starting bijiben and the package manager.

---

### Post by rvdmeijden+launchpad on 2014-06-23
The package manager problem resolved itself and a purge and re-install of bijiben solved that one.

---

