---
title: "How to measure cpu consumption for two processes?"
date: 2009-03-13
forum: General Help
---

### Post by abcuser on 2009-03-13
Hi,
I have written two bash scripts and I would like to message which one uses less CPU consumption. For example first script runs 10 minutes, second 11 minutes. But I don't care about time, I just care about CPU. I have a computer where less CPU consumption is better to have minimum impact on system. So I would like to measure which of this two scripts consumes less memory.

There is time command I can use to measure elapsed time, is there something like this for cpu consumption?
Regards

---

### Post by lloyd_b on 2009-03-13
> **abcuser said:**
> Hi,
I have written two bash scripts and I would like to message which one uses less CPU consumption. For example first script runs 10 minutes, second 11 minutes. But I don't care about time, I just care about CPU. I have a computer where less CPU consumption is better to have minimum impact on system. So I would like to measure which of this two scripts consumes less memory.

There is time command I can use to measure elapsed time, is there something like this for cpu consumption?
Regards
First off, there are *two* "time" commands on Ubuntu.  Yeah, it's confusing.  When you type "time" at a command prompt, you're getting the time command that's built into the bash shell, which is quite limited.

If you type "/usr/bin/time" instead, you get the "real" time command, which can give you a lot more information.  "man time" in a terminal window for more information (look at the options available using the "-f FORMAT" option.

Lloyd B.

---

### Post by abcuser on 2009-03-14
> **lloyd_b said:**
> When you type "time" at a ...

If you type "/usr/bin/time"
Hi,
I have tested both commands and it is really not the same using time or /usr/bin/time. Strange.

I have tried "which time" command to get which command is executed and it shows /usr/bin. I think executing "time" or /usr/bin/time is the same command, but it looks like it gets different default options depending how it is executed. Any idea why?
Regards

---

### Post by lloyd_b on 2009-03-14
> **abcuser said:**
> Hi,
I have tested both commands and it is really not the same using time or /usr/bin/time. Strange.

I have tried "which time" command to get which command is executed and it shows /usr/bin. I think executing "time" or /usr/bin/time is the same command, but it looks like it gets different default options depending how it is executed. Any idea why?
Regards

The command that executes when you type "time" while in a bash shell is internal to bash.  Try "sh", and then "time" - when using an alternate shell, it executes "/usr/bin/time", since that shell ("dash") has no internal equivalent to "time".

The "which" command isn't aware of what's available in the shell - it just searches the PATH to see where it will find a given command.

Lloyd B.

---

