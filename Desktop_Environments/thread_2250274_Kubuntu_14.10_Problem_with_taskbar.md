---
title: "Kubuntu 14.10 Problem with taskbar"
date: 2014-10-27
forum: Desktop Environments
---

### Post by jaygee2 on 2014-10-27
I have just updated to Kub 14.10 and it went great. The problem is that I have managed to wipe out the Plasma DE and screw up the taskbar. All items seem to be working but there is no settings. If I log in as guest the Plasma screen is there so is there any way to get the admin log on to revert to the original.
Baby steps please and thank you in advance.


Jaygee

---

### Post by deadflowr on 2014-10-28
The simplest way would be to try this
[http://askubuntu.com/questions/31378/how-to-reset-kubuntu-to-initial-state](http://askubuntu.com/questions/31378/how-to-reset-kubuntu-to-initial-state)
Basically boot into recovery mode
Enter the root shell
(You'll need to reload the root shell as read/write[it opens read-only, so])
run this to reload as read/write
```
mount -o rw,remount /
```
Then move the old config folder
```
mv -r /home/yourusername/.kde /home/yourusername/.kde-bak
```
Changing yourusername to your user's name.

Then exit and try resuming a normal boot.
If that doesn't work, you can revert the changes by reversing the command.

More on booting recovery mode 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
(Not about booting recovery mode per se, but it's got easy to understand pictures, which is a lot better than I can write, by miles.)

---

### Post by jaygee2 on 2014-10-28
Thank you, Igot through the recovery boot and the part about reloading the shell but when it came to mv -r it would not accept the command. At this point panic set in and I scampered.
I will continue to use Kub as is with the task bar and no notification icon although I do get a popup about upgrades which shows for about 5secs and then goes. I am not that clever with command line and specially as root.

---

### Post by jaygee2 on 2014-10-28
OK, thanks for your help although I could not make it work so I have replaced Kubuntu with ubuntu Mate and it seems good. Truthfully Kubuntu was a littlee too fussy and I could not fix it so I will settle for Mate for the time being. This post is now closed.

Jaygee

---

### Post by jaygee2 on 2014-10-29
How do I finish this thread. Solved

---

### Post by deadflowr on 2014-10-29
Well click on the option Thread Tools above the first post and then mark as solved.

But to play monday morning quarterback, since this won't help anymore, the command I gave was wrong.
You did not need the -r option. I'm sooo used to copying, which does use the recursive option, that I added it without a thought.
It is not needed in move. My bad.
Also, it would have been possible to make a new user, who would not have had the screen problems.
But again this is all 20/20 hindsight, and moot.
Anyway, hope you enjoy mate.

---

### Post by slickymaster on 2014-10-29
> **jaygee2 said:**
> How do I finish this thread. Solved

[How to mark your thread as SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

