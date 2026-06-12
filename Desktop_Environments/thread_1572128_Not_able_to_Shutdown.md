---
title: "Not able to Shutdown"
date: 2010-09-10
forum: Desktop Environments
---

### Post by anieruddha on 2010-09-10
Hi,

I am using Ubuntu 10.04. From last 3-4 days, after updating, I am not able to shutdown the system. I try to use command, but behavior is same 
Whenever I try to shutdown the system, it exits from desktop environment and a white screen displays on screen. And nothing happened. One time I did wait for 1/2 hr, but system dont seems to power down.

---

### Post by fatman65535 on 2010-09-10
I have had the same problem with 10.04 since I installed it back in April. Googling for a solution has not too helpful.  What I found out by the process of trial and error is to determine where I can get the machine to shutdown.   Can I get it to shutdown from the (dreaded) command line? - YES. Can I get it to shutdown from the user login screen? - YES Can I get it to shutdown from the applet at the top of the screen when logged in? - NO!!  So, how did I get around this, simple, I log out, and return to the user login screen, and from there, shut the machine down.  A royal PITA - YOU BET!!!  Good luck.

---

### Post by anieruddha on 2010-09-11
While I google for solution, found this workaround work for me..
[http://forum.eeeuser.com/viewtopic.php?id=1859](http://forum.eeeuser.com/viewtopic.php?id=1859).

It suggest to edit /etc/init.d/halt file and add following entry (without quotes) at top of the file. I added after end of comments.
      "rmmod snd-hda-intel"

---

### Post by anieruddha on 2010-09-11
One more thing...
> 
Can I get it to shutdown from the (dreaded) command line? - YES. Can I get it to shutdown from the user login screen? - YES 
for me, it is No, from command line. And I set auto-login, so never check with user login screen. 

And also check this link, it might help you
[http://wiki.eeeuser.com/ubuntu#shutdown_poweroff_workaround](http://wiki.eeeuser.com/ubuntu#shutdown_poweroff_workaround)

---

### Post by fatman65535 on 2010-09-11
> **anieruddha said:**
> One more thing...
for me, it is No, from command line. And I set auto-login, so never check with user login screen. 

And also check this link, it might help you
[http://wiki.eeeuser.com/ubuntu#shutdown_poweroff_workaround](http://wiki.eeeuser.com/ubuntu#shutdown_poweroff_workaround)

 I read the linked article, and must note that it applies to an eeepc. The second thing I noted was the mention of adding &quot;rmmod snd-hda-intel&quot; to the `halt` script. After doing a lsmod on my system, the module `snd-hda-intel` is not loaded on my system, so removing it will not do anything for me. (This is not to say that it does not work for others - YMMV.) I wonder if there is not a semantic misunderstanding regarding the function of 'halt', 'shutdown' and `poweroff'. While I an fairly new to Ubuntu, I am familiar with *nix, as I was responsible for a CTIX multiuser (old green screen terminal) system. We had three distinct options: 'shutdown', 'halt' and 'crash'. The primary difference between them was what the system did. 'Shutdown' did exactly that, a nice graceful, orderly shutdown of the system, complete with locking out new logins, warning messages to log off, buffer syncs, etc, followed with a complete power off of the machine. 'Halt' locked out new logins, informed the users of the system shutdown; took the machine out of multiuser mode, and established a single user console. At that point you had a message that it was OK to stop or reset the processor. This was the mode you could use for system maintenance. 'Crash&quot; was the worst one; WITHOUT ANY WARNING, IT WOULD BRING THE SYSTEM COMPLETELY DOWN. It was NOT supposed to used unless there was some urgent reason to kill the system. One day, I left my terminal logged in as `root` and this wise guy thought that it would be &quot;fun&quot; to see what `crash` did. Needless to say, that was the last day he worked for us, and I could not sit for a week!  So, I think that the devs at Ubuntu need to clarify the actions taken by CLI versions of 'shutdown', 'powerdown', 'reboot' and 'halt'; and what the GUI applet actions are that correspond to the CLI commands. So, humbly, I suggest that 'powerdown' does EXACTLY THAT, takes the computer down, and kills the power. 'Shutdown' and 'halt' should take the computer to a state where the machine is left running, but the OS is stopped. And, then 'reboot' is the same as whacking the reset button, a forced reboot. Your thoughts?

---

