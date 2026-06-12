---
title: "Unlocking old threads"
date: 2024-04-15
forum: Forum Feedback &amp; Help
---

### Post by timschumi on 2024-04-15
Hello!

The following (up to ~12 year old) threads describe a problem that has [recently been worked around]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1471380"):

[https://ubuntuforums.org/showthread.php?t=2257720](https://ubuntuforums.org/showthread.php?t=2257720)
[https://ubuntuforums.org/showthread.php?t=2086602](https://ubuntuforums.org/showthread.php?t=2086602)
[https://ubuntuforums.org/showthread.php?t=2407207](https://ubuntuforums.org/showthread.php?t=2407207)
[https://ubuntuforums.org/showthread.php?t=2276636](https://ubuntuforums.org/showthread.php?t=2276636)
[https://ubuntuforums.org/showthread.php?t=2079168](https://ubuntuforums.org/showthread.php?t=2079168)
[https://ubuntuforums.org/showthread.php?t=2271076](https://ubuntuforums.org/showthread.php?t=2271076)

I'd love to post laptop unbrick instructions (and a general PSA of "this is fixed on Ubuntu 24.04 beta") there to make sure that everyone who participated/subscribed in these old threads has a chance to get notified about this and to make sure that people searching via their preferred search engine can also find the solution in the same place.
However, all the threads have been locked from further discussion, presumably on an automatic timer.

Is there any chance to get these unlocked (temporarily) so that I may post a follow-up?

Thanks!

PS: And, to everyone reading along who is also on IRC: Hi! Yeah, I know. It took me a bit of time to get back to this.

---

### Post by ajgreeny on 2024-04-15
Just add a precis of the problem in a reply to this thread with you new update/workaround.

The links already shown here may be sufficient for anyone who still has this problem and will certainly be as useful as reopening those old threads.

---

### Post by coffeecat on 2024-04-15
Hi

Yes, I can help you with this, but in a slightly simpler way. Rather than open all the threads, wait for you to post in them and then close them again (see below for closure reasons), here's what I suggest:

[list=1][*]Please compose a standardised update post suitable for all the threads with your unbrick instructions, and post to this thread.
[*]I'll then use the vbulletin copy post facility (available to forum staff) to simply copy your post to all six threads and ensure that they remain closed.[/list]

You are right that threads are automatically closed after a certain period of inactivity, mainly to prevent spammers and unthinking necromancers. I don't know why, but old, open threads seem to be a magnet for spammers, and you would not believe the amount of pointless cruft that accumulated on old open threads before we introduced autoclosure. 

It may be a while after you post your instructions before I have the chance to copy them to the six threads. I'm not in my usual timezone and have some other demands upon my time, but I'll try to finish the job within 24-48 hours of you posting.

Kind regards

---

### Post by timschumi on 2024-04-16
> **ajgreeny said:**
> Just add a precis of the problem in a reply to this thread with you new update/workaround.

The links already shown here may be sufficient for anyone who still has  this problem and will certainly be as useful as reopening those old  threads.

This was something I considered (and that was suggested to me on IRC as well), but there are at least six threads that will pretty much always be higher-ranked in search results due to the sheer amount of keywords and incoming links that I have no hope of overtaking when posting separately.

> **coffeecat said:**
> Hi

Yes, I can help you with this, but in a slightly simpler way. Rather than open all the threads, wait for you to post in them and then close them again (see below for closure reasons), here's what I suggest:

[LIST=1]
[*]Please compose a standardised update post suitable for all the threads with your unbrick instructions, and post to this thread. 
[*]I'll then use the vbulletin copy post facility (available to forum staff) to simply copy your post to all six threads and ensure that they remain closed. 
[/LIST]

You are right that threads are automatically closed after a certain period of inactivity, mainly to prevent spammers and unthinking necromancers. I don't know why, but old, open threads seem to be a magnet for spammers, and you would not believe the amount of pointless cruft that accumulated on old open threads before we introduced autoclosure. 

It may be a while after you post your instructions before I have the chance to copy them to the six threads. I'm not in my usual timezone and have some other demands upon my time, but I'll try to finish the job within 24-48 hours of you posting.

Kind regards

Thank you for the help, that would indeed be a much better solution than what I had in mind. I'll compose a message and post it here in a separate reply.

No worries about taking some time to copy over the message. People have waited twelve years for this, they can wait a bit longer if necessary.

---

### Post by timschumi on 2024-04-19
I've recently looked into fixing this issue, and came up with a consistent way of restoring the laptop to full operation.

The boot menu entries can be partially restored by bridging the "CL1_CL2" test point  that is located under or next to the RAM slots.
It may be required to have the laptop powered (or even powered on) while bridging the contacts for the test points to have any effect.
This brings back the  device-based boot menu entries, but does not yet restore access to the  BIOS Setup menu.
For that, a USB stick with [Fujitsu's BIOS update tool]("https://support.ts.fujitsu.com/")  (search by serial number to make sure you find the correct hardware revision) needs to be prepared, booted from, and run.
This restores most BIOS  settings to their default, including the missing BIOS Setup menu.

Alternatively, if the currently installed Linux system is still  bootable, one can use [this tool]("https://github.com/timschumi/ah532-biostools") to restore all entries  without having to go through a BIOS update and reset.
This works by manually  rewriting all broken EFI variables with their expected content.
Please do make note of the list of supported configurations and of the  disclaimer (and let me know in case the tool does or doesn't work on  some previously untested configuration).
In case you want to know more about this works, there is a [post explaining the underlying details]("https://blog.timschumi.net/2024/01/20/ah532-bios-investigation.html").

Lastly, a [workaround for the issue]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f45812cc23fb74bef62d4eb8a69fe7218f4b9f2a") has been merged into the Linux  kernel, which should keep this from occurring on any new  installations.
This patch already ended up in the current installation  media for the Ubuntu 24.04 beta (which I have confirmed to be not affected), and it will presumably be included in  all installation media going forward.

---

### Post by coffeecat on 2024-04-23
Apologies for taking a little longer to do this than I intended, but your post immediately above this one has now been copied to all of the 6 old threads, and your post titles amended in each thread to match the thread title.

Thanks for your interest.

---

