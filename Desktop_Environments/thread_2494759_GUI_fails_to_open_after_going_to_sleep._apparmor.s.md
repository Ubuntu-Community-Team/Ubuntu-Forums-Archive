---
title: "GUI fails to open after going to sleep. apparmor.service failed."
date: 2024-01-25
forum: Desktop Environments
---

### Post by foxsquirrel on 2024-01-25
This has happened several times since the 6.5 update.

I can ssh into it and this is what is going on:

```
********:~$ sudo systemctl --failed
  UNIT             LOAD   ACTIVE SUB    DESCRIPTION           
&#9679; apparmor.service loaded failed failed Load AppArmor profiles

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
1 loaded units listed.
**********:~$ uname -a
Linux ********** 6.5.0-14-generic #14~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov 20 18:15:30 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
 

```

```
$ sudo systemctl start apparmor.service
Job for apparmor.service failed because the control process exited with error code.
See "systemctl status apparmor.service" and "journalctl -xeu apparmor.service" for details.
```

Here is the log:

```
journalctl -xeu apparmor.service
Jan 25 20:37:31 eng-dev2 apparmor.systemd[1231858]: Error: At least one profile failed to load
Jan 25 20:37:31 eng-dev2 systemd[1]: apparmor.service: Main process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit apparmor.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Jan 25 20:37:31 eng-dev2 systemd[1]: apparmor.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit apparmor.service has entered the 'failed' state with result 'exit-code'.
Jan 25 20:37:31 eng-dev2 systemd[1]: Failed to start Load AppArmor profiles.
&#9617;&#9617; Subject: A start job for unit apparmor.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apparmor.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 11962 and the job result is failed.
lines 499-521/521 (END)
Jan 25 20:37:31 eng-dev2 apparmor.systemd[1231858]: Error: At least one profile failed to load
Jan 25 20:37:31 eng-dev2 systemd[1]: apparmor.service: Main process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; An ExecStart= process belonging to unit apparmor.service has exited.
&#9617;&#9617; 
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Jan 25 20:37:31 eng-dev2 systemd[1]: apparmor.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; The unit apparmor.service has entered the 'failed' state with result 'exit-code'.
Jan 25 20:37:31 eng-dev2 systemd[1]: Failed to start Load AppArmor profiles.
&#9617;&#9617; Subject: A start job for unit apparmor.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617; 
&#9617;&#9617; A start job for unit apparmor.service has finished with a failure.
&#9617;&#9617; 
&#9617;&#9617; The job identifier is 11962 and the job result is failed.

```

---

### Post by #&amp;thj^% on 2024-01-25
Please show this first:
```
sudo systemctl reload apparmor.service
```
Paste that back  here so we can look at what's going on.

I suspect you have a bad profile in the mix. Have you added any new profiles since the install?

---

### Post by foxsquirrel on 2024-01-25
```
sudo systemctl reload apparmor.service
apparmor.service is not active, cannot reload.
```

```
~$ sudo systemctl --failed
  UNIT             LOAD   ACTIVE SUB    DESCRIPTION                                       
&#9679; apparmor.service loaded failed failed Load AppArmor profiles
&#9679; vmware.service   loaded failed failed LSB: This service starts and stops VMware services

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
2 loaded units listed.
```

Not sure how to read this, the gui is up, I am getting this via ssh.

I have not added any profiles, unless some package did. On that machine  VMware is up and the gui is up...

---

### Post by #&amp;thj^% on 2024-01-25
Good your here, I like a responsive poster...:)

Now lets disable apparmor, and then try to boot to your Desktop.
```
sudo systemctl stop apparmor.service
### AND
sudo systemctl disable apparmor.service
```
Now reboot.

---

### Post by foxsquirrel on 2024-01-25
```
********
    State: running
     Jobs: 0 queued
   Failed: 0 units
    Since: Thu 2024-01-25 23:10:00 EST; 51s ago

```

That cleared up the apparmor problem.

On the other machine I upgraded to the 6.5.15 from .14 ran the vmware removal script then reinstalled 17.5. It came up so I am assuming that is fine. What ever the issue was must have been in the .14 release?

Update: just tried the vmware on this machine and it will not start the vm. The player will open and allow a configuration however when it is ran it breaks. I will be back tomorrow, its getting late here.

---

### Post by #&amp;thj^% on 2024-01-25
Ah there it is>>>" vmware removal script"
If your now updated on vmware lets re enable apparmor ***but only if it is upgraded***
```
sudo systemctl start --now apparmor.service
#### And
sudo systemctl status apparmor
```
No Reboot yet...

Be aware apparmor won't load on next boot until it's enabled again, but for now we need to see if its happy now.

---

### Post by #&amp;thj^% on 2024-01-26
It's late here, I'll check back tomorrow.

---

### Post by #&amp;thj^% on 2024-01-26
Waiting for your reply now.

Solved via PM (This is the OP's request)

---

