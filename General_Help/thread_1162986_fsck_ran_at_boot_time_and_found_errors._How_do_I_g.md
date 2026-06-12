---
title: "fsck ran at boot time and found errors. How do I get more info"
date: 2009-05-18
forum: General Help
---

### Post by ant2ne on 2009-05-18
This computer was shut down last night using the green running man icon. This morning, on boot up, my system halted saying something about fsck needing to be run manually. Which I then did. But it prompted me with a bunch of questions asking me if it should fix. So I re-ran fsck with -y and quickly enough I was at a prompt. I then restarted the computer. It barked an error about not being able to start X which I thought was silly since I was trying to restart the computer. On restart I encountered no additional errors and was able to log in and post this message.

I would like to examine this fsck more closely. I would like to know how to troubleshoot this in case I'm looking at additional hard drive problems. dmesg doesn't report anything of interest. Where else can I find information regarding this error? Once I find this information I'll want to investigate further which would probably include further questions to this thread.

---

### Post by Lampi on 2009-05-18
/var/log/syslog could be of use. I guess it collects some information, but not what errors fsck corrected.

There is /var/log/fsck/checkroot - but having a look at it, this does not seem to show more than the current session status.

Well ... go sniff through your logs, older logs as well (as long as they cover the time period of this morning)

---

