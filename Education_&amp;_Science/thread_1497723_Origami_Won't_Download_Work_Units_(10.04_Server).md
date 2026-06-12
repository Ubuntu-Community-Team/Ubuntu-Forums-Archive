---
title: "Origami Won't Download Work Units (10.04 Server)"
date: 2010-05-30
forum: Education &amp; Science
---

### Post by palsyboy on 2010-05-30
I recently resurrected an Athlon X2 box to make it into a Folding@Home machine.  I decided the simplest approach would be to run 10.04 Server 64-bit.  The system installed quickly and easily, and now I have it pleasantly running headless via OpenSSH.

The only problem is that Folding@Home can be a pain to install.  I just want it to run nicely at startup in case I update the kernel or something, and Origami looked like the only simple solution.  It installed easily, and the configuration was no problem - until it showed that it won't download work units.  The service is started, and if I run "origami status," it says, "No work units have been assigned yet. Please check status again later."  /var/lib/origami/work/ contains nothing, and /var/lib/origami/CPU1/FAHLog.txt has the following:

```

--- Opening Log file [May 31 01:43:35] 


# SMP Client ##################################################################
###############################################################################

                       Folding@Home Client Version 6.02

                          http://folding.stanford.edu

###############################################################################
###############################################################################

Launch directory: /var/lib/origami/foldingathome/CPU1
Executable: /var/lib/origami/foldingathome/CPU1/fah6
Arguments: -smp 

[01:43:35] - Ask before connecting: No
[01:43:35] - User name: palsyboy (Team 14)
[01:43:35] - User ID: 36910B877B82967A
[01:43:35] - Machine ID: 1
[01:43:35] 
[01:43:35] Loaded queue successfully.
[01:43:35] - Preparing to get new work unit...
[01:43:35] + Attempting to get work packet
[01:43:35] - Connecting to assignment server
[01:43:35] + No appropriate work server was available; will try again in a bit.
[01:43:35] + Couldn't get work instructions.
[01:43:35] - Attempt #1  to get work failed, and no other work to do.
             Waiting before retry.
[01:43:45] + Attempting to get work packet
[01:43:45] - Connecting to assignment server
[01:43:46] + No appropriate work server was available; will try again in a bit.
[01:43:46] + Couldn't get work instructions.
[01:43:46] - Attempt #2  to get work failed, and no other work to do.
             Waiting before retry.
[01:44:06] + Attempting to get work packet
[01:44:06] - Connecting to assignment server
[01:44:07] + No appropriate work server was available; will try again in a bit.
[01:44:07] + Couldn't get work instructions.
[01:44:07] - Attempt #3  to get work failed, and no other work to do.
             Waiting before retry.
[01:44:36] + Attempting to get work packet
[01:44:36] - Connecting to assignment server
[01:44:36] + No appropriate work server was available; will try again in a bit.
[01:44:36] + Couldn't get work instructions.
[01:44:36] - Attempt #4  to get work failed, and no other work to do.
             Waiting before retry.
[01:45:18] + Attempting to get work packet
[01:45:18] - Connecting to assignment server
[01:45:18] + No appropriate work server was available; will try again in a bit.
[01:45:18] + Couldn't get work instructions.
[01:45:18] - Attempt #5  to get work failed, and no other work to do.
             Waiting before retry.
[01:46:47] + Attempting to get work packet
[01:46:47] - Connecting to assignment server
[01:46:47] + No appropriate work server was available; will try again in a bit.
[01:46:47] + Couldn't get work instructions.
[01:46:47] - Attempt #6  to get work failed, and no other work to do.
             Waiting before retry.
[01:49:36] + Attempting to get work packet
[01:49:36] - Connecting to assignment server
[01:49:37] + No appropriate work server was available; will try again in a bit.
[01:49:37] + Couldn't get work instructions.
[01:49:37] - Attempt #7  to get work failed, and no other work to do.
             Waiting before retry.
[01:55:10] + Attempting to get work packet
[01:55:10] - Connecting to assignment server
[01:55:11] + No appropriate work server was available; will try again in a bit.
[01:55:11] + Couldn't get work instructions.
[01:55:11] - Attempt #8  to get work failed, and no other work to do.
             Waiting before retry.
[02:06:00] + Attempting to get work packet
[02:06:00] - Connecting to assignment server
[02:06:01] + No appropriate work server was available; will try again in a bit.
[02:06:01] + Couldn't get work instructions.
[02:06:01] - Attempt #9  to get work failed, and no other work to do.
             Waiting before retry.
[02:27:28] + Attempting to get work packet
[02:27:28] - Connecting to assignment server
[02:27:28] + No appropriate work server was available; will try again in a bit.
[02:27:28] + Couldn't get work instructions.
[02:27:28] - Attempt #10  to get work failed, and no other work to do.
             Waiting before retry.
[03:10:10] + Attempting to get work packet
[03:10:10] - Connecting to assignment server
[03:10:10] - Successful: assigned to (171.64.65.64).
[03:10:10] + News From Folding@Home: Welcome to Folding@Home
[03:10:10] Loaded queue successfully.
[03:10:13] + Closed connections
[03:10:13] 
[03:10:13] + Processing work unit
[03:10:13] Core required: FahCore_a1.exe
[03:10:13] Core found.
[03:10:13] Working on Unit 08 [May 31 03:10:13]
[03:10:13] + Working ...
[03:10:13] 
[03:10:13] *------------------------------*
[03:10:13] Folding@Home Gromacs SMP Core
[03:10:13] Version 1.74 (November 27, 2006)
[03:10:13] 
[03:10:13] Preparing to commence simulation
[03:10:13] - Ensuring status. Please wait.
[03:10:30] - Looking at optimizations...
[03:10:30] - Working with standard loops on this execution.
[03:10:30] - Previous termination of core was improper.
[03:10:30] - Going to use standard loops.
[03:10:30] - Files status OK
[03:10:31] arting from initial work packet
[03:10:31] 
[03:10:31] Project: 5101 (Run 0, Clone 17
[03:10:31] Project: 510Entering M.D.
[03:10:31] e 173, Gen 168)
[03:10:31] 
[03:10:31] Entering M.D.
[03:10:31] e 173, Gen 168)
[03:10:31] 
[03:10:31] Entering M.D.
[03:10:37] Finalizing output
[03:10:41] CoreStatus = 7F (127)
[03:10:41] Client-core communications error: ERROR 0x7f
[03:10:41] Deleting current work unit & continuing...
[03:15:12] - Preparing to get new work unit...
[03:15:12] + Attempting to get work packet
[03:15:12] - Connecting to assignment server
[03:15:13] + No appropriate work server was available; will try again in a bit.
[03:15:13] + Couldn't get work instructions.
[03:15:13] - Attempt #1  to get work failed, and no other work to do.
             Waiting before retry.
[03:15:32] + Attempting to get work packet
[03:15:32] - Connecting to assignment server
[03:15:32] + No appropriate work server was available; will try again in a bit.
[03:15:32] + Couldn't get work instructions.
[03:15:32] - Attempt #2  to get work failed, and no other work to do.
             Waiting before retry.
[03:15:50] + Attempting to get work packet
[03:15:50] - Connecting to assignment server
[03:15:50] + No appropriate work server was available; will try again in a bit.
[03:15:50] + Couldn't get work instructions.
[03:15:50] - Attempt #3  to get work failed, and no other work to do.
             Waiting before retry.
[03:16:14] + Attempting to get work packet
[03:16:14] - Connecting to assignment server
[03:16:15] + No appropriate work server was available; will try again in a bit.
[03:16:15] + Couldn't get work instructions.
[03:16:15] - Attempt #4  to get work failed, and no other work to do.
             Waiting before retry.
[03:16:55] + Attempting to get work packet
[03:16:55] - Connecting to assignment server
[03:16:56] + No appropriate work server was available; will try again in a bit.
[03:16:56] + Couldn't get work instructions.
[03:16:56] - Attempt #5  to get work failed, and no other work to do.
             Waiting before retry.
[03:18:19] + Attempting to get work packet
[03:18:19] - Connecting to assignment server
[03:18:20] + No appropriate work server was available; will try again in a bit.
[03:18:20] + Couldn't get work instructions.
[03:18:20] - Attempt #6  to get work failed, and no other work to do.
             Waiting before retry.

Folding@Home Client Shutdown.


--- Opening Log file [May 31 03:21:50] 


# SMP Client ##################################################################
###############################################################################

                       Folding@Home Client Version 6.02

                          http://folding.stanford.edu

###############################################################################
###############################################################################

Launch directory: /var/lib/origami/foldingathome/CPU1
Executable: /var/lib/origami/foldingathome/CPU1/fah6
Arguments: -smp 

[03:21:50] - Ask before connecting: No
[03:21:50] - User name: palsyboy (Team 14)
[03:21:50] - User ID: 36910B877B82967A
[03:21:50] - Machine ID: 1
[03:21:50] 
[03:21:50] Loaded queue successfully.
[03:21:50] - Preparing to get new work unit...
[03:21:50] + Attempting to get work packet
[03:21:50] - Connecting to assignment server
[03:21:50] + No appropriate work server was available; will try again in a bit.
[03:21:50] + Couldn't get work instructions.
[03:21:50] - Attempt #1  to get work failed, and no other work to do.
             Waiting before retry.
[03:22:01] + Attempting to get work packet
[03:22:01] - Connecting to assignment server
[03:22:02] + No appropriate work server was available; will try again in a bit.
[03:22:02] + Couldn't get work instructions.
[03:22:02] - Attempt #2  to get work failed, and no other work to do.
             Waiting before retry.
[03:22:26] + Attempting to get work packet
[03:22:26] - Connecting to assignment server
[03:22:27] + No appropriate work server was available; will try again in a bit.
[03:22:27] + Couldn't get work instructions.
[03:22:27] - Attempt #3  to get work failed, and no other work to do.
             Waiting before retry.
[03:22:58] + Attempting to get work packet
[03:22:58] - Connecting to assignment server
[03:22:59] + No appropriate work server was available; will try again in a bit.
[03:22:59] + Couldn't get work instructions.
[03:22:59] - Attempt #4  to get work failed, and no other work to do.
             Waiting before retry.
[03:23:46] + Attempting to get work packet
[03:23:46] - Connecting to assignment server
[03:23:47] + No appropriate work server was available; will try again in a bit.
[03:23:47] + Couldn't get work instructions.
[03:23:47] - Attempt #5  to get work failed, and no other work to do.
             Waiting before retry.
[03:25:15] + Attempting to get work packet
[03:25:15] - Connecting to assignment server
[03:25:15] + No appropriate work server was available; will try again in a bit.
[03:25:15] + Couldn't get work instructions.
[03:25:15] - Attempt #6  to get work failed, and no other work to do.
             Waiting before retry.
[03:27:59] + Attempting to get work packet
[03:27:59] - Connecting to assignment server
[03:27:59] + No appropriate work server was available; will try again in a bit.
[03:27:59] + Couldn't get work instructions.
[03:27:59] - Attempt #7  to get work failed, and no other work to do.
             Waiting before retry.
[03:33:23] + Attempting to get work packet
[03:33:23] - Connecting to assignment server
[03:33:24] + No appropriate work server was available; will try again in a bit.
[03:33:24] + Couldn't get work instructions.
[03:33:24] - Attempt #8  to get work failed, and no other work to do.
             Waiting before retry.
[03:44:14] + Attempting to get work packet
[03:44:14] - Connecting to assignment server
[03:44:14] + No appropriate work server was available; will try again in a bit.
[03:44:14] + Couldn't get work instructions.
[03:44:14] - Attempt #9  to get work failed, and no other work to do.
             Waiting before retry.

```

---

### Post by robinl on 2010-06-17
Here's the relevant bug
[https://bugs.launchpad.net/ubuntu/+source/origami/+bug/567075](https://bugs.launchpad.net/ubuntu/+source/origami/+bug/567075)

The solution worked (kinda, at least I actually got a WU), but YMMV

---

