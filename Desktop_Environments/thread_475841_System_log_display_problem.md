---
title: "System log display problem"
date: 2007-06-16
forum: Desktop Environments
---

### Post by AndyPopely on 2007-06-16
I'm on Feisty Fawn and whenever I try to display the system logs (System -> Administration -> System Log)
a window opens with Log Viewer in the title bar but the window is empty and a second or so later the window closes and there's no reason given as to why it closed.

Anyone any ideas ?

---

### Post by dustigroove on 2007-06-17
[FONT=Arial][SIZE=2][COLOR=Black]Do you get any errors when running gnome-system-log from a terminal?

[/COLOR][/SIZE][/FONT]

---

### Post by AndyPopely on 2007-06-17
Just tried it and it did the same thing .... additionally the terminal window stated :-

Segmentation fault (cored dumped)

---

### Post by dustigroove on 2007-06-17
[FONT=Arial][SIZE=2][COLOR=Black]Take a look at the recommendation [here]("http://ubuntuforums.org/showthread.php?t=414064&highlight=segmentation+fault+location"), perhaps there is a non-parsable log that is causing the viewer to segfault.

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by AndyPopely on 2007-06-19
I followed the recommendation and moved all the files from /var/log to a temp directory and then moved them back one at a time to see which one was causing the log viewer to fail.  In my case it was /var/log/debug .... so I deleted that file

I now have the log viewer working again but ..... it only shows the auth.log in the left hand panel of the log viewer under /var/log ..... 

I compared the contents of the temp folder and /var/log and all the files seem to be there apart from the debug file. 

How do I get the other logs to show in the log viewer ?

---

### Post by dustigroove on 2007-06-19
[COLOR=Black][SIZE=2][FONT=Arial]You should now be able to go into the File menu within the log viewer, select Open, and then choose each log that you wish to see. The log will be added to the list on the left-hand side after opening.

[/FONT][/SIZE][/COLOR]

---

### Post by AndyPopely on 2007-06-20
When I tried opening some of the logs in the log viewer the log viewer abruptly exited.  

I looked at those logs and what they had in common was that all of them were hugh and had details from April up to the present day.  It looks like the log rotate function isn't running.  

So I went into /etc/logrotate.conf and changed weekly to daily.  As this laptop is only used a couple of times a week maybe the log rotate function doesn't get to run.

I made the weekly->daily change yesterday and today the logs have "rotated" and so far no problems adding logs to the log viewer.  I'll keep an eye on it.

Thanks dustigroove for your help.

---

### Post by AndyPopely on 2007-08-03
Solved - not long after I fixed one log then another log caused the viewer to exit .... the problem was anacron wasn't being scheduled thus stopping the logs from being rotated  ... I installed and ran sysv-rc-conf and reinstated anacron being scheduled and all is well

---

