---
title: "Error: Only one software management tool is allowed to run at the same time..."
date: 2009-01-02
forum: General Help
---

### Post by Slugzzz on 2009-01-02
Hi all,
    I am trying to install the ipod convenience package and I keep getting this error when I am trying to install packages:

     Only one software management tool is allowed to run at the same time. Please close the other application e.g. 'Update manager','aptitude' or 'Synaptic first.

I have checked to make sure that none of those are running... but none of them are... I've been thread hopping for about an hour and have failed to find a solution. :-(

        Please help!

               Slugzzz

---

### Post by hyper_ch on 2009-01-02
did one of the managers not close properly? If so, there still a lock file.

run

```

lsof > output.txt

```

and then search the output.txt if a file with "apt" or "synaptic" is still open.

---

### Post by cdtech on 2009-01-02
Try this then run the update manager:
```
kill -9 `pgrep update`
```
**UPDATED::.**
If you still get the error, use this command to list running processes:
```
ps -ax
```
If you find some update process running in the background use this command
to kill the process:
```
sudo kill <process number>
```
Hope this helps ya.......

---

### Post by Slugzzz on 2009-01-02
"Code:

kill -9 `pgrep update` "

I get:
bash: kill: pgrep update: arguments must be process or job IDs

Tried to run update manager and got following error:
E:dpkg was interrupted, you must manually run 'dpkg --configure-a"
to correct the problem.
E:_cache>open() failed, please report.

So... I did that and got:
dpkg: unknown option --configure-a

---

### Post by BuudWeizErr on 2009-01-02
This might not be the best way to do it, but I do..

"ps ax | grep <processname>"
if it shows up, then run "killall <processname>"

so...

ps ax | grep synaptic
killall synaptic

you might need to do sudo killall though, depending on your rights.

---

### Post by Slugzzz on 2009-01-02
I am not sure what process to look for, though.

---

### Post by Slugzzz on 2009-01-03
bump

---

### Post by cdtech on 2009-01-06
> **Slugzzz said:**
> "Code:

kill -9 `pgrep update` "

I get:
bash: kill: pgrep update: arguments must be process or job IDs

Tried to run update manager and got following error:
E:dpkg was interrupted, you must manually run 'dpkg --configure-a"
to correct the problem.
E:_cache>open() failed, please report.

So... I did that and got:
dpkg: unknown option --configure-a
That should be a separate command:
```
--configure -a
```

---

### Post by jerome1232 on 2009-01-06
And you will need to run it as root
```
sudo dpkg --configure -a
```

---

### Post by Krantarin on 2010-06-09
I just downloaded Ubuntu last night, and I've had the same problem. I've been utterly confounded by the advice... I'm really new to the terminal and any of the code stuff, so I may just be following directions badly.

I tried lsof > output.txt, and nothing showed up except for the thing that was there before (you know, where you write stuff, "____@ubuntu:~$ "). I checked to see if package installer would run, and it wouldn't, so I tried "kill -9 `pgrep update`". Once again, it simply prompted me to type more in and package installer still wouldn't run. Then I typed in "ps -ax" and it told me
"Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html" but still listed all of the programs that were running... I looked for a program that might be construed as a software management tool, but as an utter noob to linux and code and everything else that seems to matter on ubuntu, I could not understand more than a few token programs and nothing that seemed linked to software management. 

Ah, and prior to this I tried quite a few standard windows fixes: check processes on system moniter, restart, restart, and restart again, and I even killed a few processes that looked "software management" oriented.

I'd appreciate some help with this. I like and hope to become adept with Ubuntu, but it's been a rough start.

Edit: Now I see that Ubuntu software center has been rendered unusable as well. Upon attempting to download, it gives me the error message "Previous installation hasn't been completed. The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software." There seems to have been an error with the installation of Grub. This error is cataloged as "Bug #576823" in Launchpad, and I'm exploring fixing it as well. My first step was to try to remove Grub, which Software Center says has been downloaded, but it gave me the same error message "Previous installation hasn't been completed, yadayadayada." I understand that this is a different error that has probably been addressed in a different thread (and I will search for that thread), but I thought it may be linked to the prior error in an important way...

---

### Post by amite on 2010-06-09
**@krantarin**

with command " ps -ax" u got warning because - is not required,try "ps ax" it will give the same output without warning message. But best way to solve such type of problem is to look at man pages of the command,man pages are best thing u can find to learn linux.for man pages type...
$man ur_commmand 
as here $man ps


> 
I tried lsof > output.txt, and nothing showed up except for the thing that was there before (you know, where you write stuff, "____@ubuntu:~$ ").

$lsof > output.txt
lsof command is used to listing  open files and since u use '>' which is a redirection operator so output of ur command is not come to terminal instead it is saved as output.txt in ur current directory(which is ur home directory if didn't use cd).So to look at the output of the above comand go to ur current directory in gui and click on output.txt or in terminal type
$cat output.txt

---

### Post by Krantarin on 2010-06-09
Thanks, amite. That set me straight in some sense, but I'm still not home free. The output txt showed things when I searched synaptic and apt, but when I used BuudWeizErr's method of "ps ax | grep synaptic" (or aptitude, it showed ```
2537 pts/0    S+     0:00 grep --color=auto synaptic
``` and when I told it to "killall synaptic" it said "no process found."

My final try before this post was ps ax | update manager, but it showed 
```
No command 'update' found, did you mean: 
 Command 'uupdate' from package 'devscripts' (main) 
 Command 'lupdate' from package 'libqt4-dev' (main)
 Command 'lupdate' from package 'qt3-dev-tools' (main)
update: command not found
```I guess the next step is finding out which one is the Update Manager.

---

### Post by jerome1232 on 2010-06-09
> **Krantarin said:**
> Thanks, amite. That set me straight in some sense, but I'm still not home free. The output txt showed things when I searched synaptic and apt, but when I used BuudWeizErr's method of "ps ax | grep synaptic" (or aptitude, it showed ```
2537 pts/0    S+     0:00 grep --color=auto synaptic
``` and when I told it to "killall synaptic" it said "no process found."

My final try before this post was [COLOR="Red"]ps ax | update manager[/COLOR], but it showed 
```
No command 'update' found, did you mean: 
 Command 'uupdate' from package 'devscripts' (main) 
 Command 'lupdate' from package 'libqt4-dev' (main)
 Command 'lupdate' from package 'qt3-dev-tools' (main)
update: command not found
```I guess the next step is finding out which one is the Update Manager.

That should have been

```
ps ax | grep update-manager
```

---

### Post by Krantarin on 2010-06-09
ah, thank you for correcting me. Nevertheless, it showed the same answers to my ps ax | grep update-manager and killall update-manager. 

```
davy@ubuntu:~$ ps ax | grep update-manager
 2450 pts/0    S+     0:00 grep --color=auto update-manager
davy@ubuntu:~$ killall update-manager
update-manager: no process found
```

---

### Post by usmanajmal on 2010-08-25
Try:
```
sudo apt-get check
```

OPTIONAL: Update using following command
```
sudo apt-get update
```

This should solve your problem.

---

