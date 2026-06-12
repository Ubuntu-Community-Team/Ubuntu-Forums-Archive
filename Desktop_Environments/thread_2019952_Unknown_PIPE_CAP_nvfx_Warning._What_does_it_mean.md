---
title: "Unknown PIPE_CAP nvfx Warning. What does it mean?"
date: 2012-07-07
forum: Desktop Environments
---

### Post by bogan on 2012-07-07
Hi!,** All,**

When I run the unity_support_test, before the normal output I get half-a-dozen error lines:```
$ /usr/lib/nux/unity_support_test -p
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
```I have had: > could not write bytes: Broken Pipemessages displayed just before the login screen and at shut down, ever since I installed 12.04 LTS, the first day of its release.

But this is the first time I have seen any other signs of trouble that might be connected.

I Posted a thread about that error and also Posted  in another thread about the same error message, but there was no informative response.

Is it something that needs a repair?, or is it another: "Don't worry about it"?

Chao!, **bogan**.

---

### Post by htbw on 2012-07-07
Sorry I cant help on this one I did a quick google search and came up with a reference to a bug I do not know if this is the same error message you received.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1008684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1008684)

but I am having a similar error, or series of errors that keep popping up until the whole OS crashes and my wife starts yelling at me

make sure you have ubuntu one set up for any critical docs, that saved my butt last time around.

My current error is a little different, it says something about a panic alarm
It also mentions something about processor 2:100f42
and it further goes on to say the processor context is corrupt
next line is kernal panic not syncing
then it mentions the software centre being tainted.

My head hurts. I feel your pain. Sorry for jumping on your thread, for some reason I could not find any way to post a new thread.

---

### Post by bogan on 2012-07-07
Hi!,** htbw,**

Thanks for the bug link, I will check it out.

Edit, later: [COLOR=Blue]That has the same error messages, but refers to a 'stipled screen' in ubiquity, which I do not get.[/COLOR]

You Posted:  > Sorry for jumping on your thread, for some reason I could not find any way to post a new thread.     No problem.

To open a new thread:
In the Forums Home page, select the Forum you wish to Post to, and at the top left will be a "New Thread" button. Click it.

Chao!, **bogan.**

---

### Post by bogan on 2012-07-07
Hi!, **All**,

The mystery deepens: Previously   the unity_support_test file had always run perfectly normally.

The: "nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30" messages occured when running the test file in a direct installation of 12.04 LTS,  using the default nouveau driver.

When I ran the 'unity_support_test' file in another updated version of 12.04, using the nvidia 295.59 driver, in another partition of the same Desktop, I got a quite different set of error messages:```
~$ /usr/lib/nux/unity_support_test -print
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x26f
  Serial number of failed request:  41
  Current serial number in output stream:  41
~$ 
```and the test file did not run.

However, still on the same Desktop and also using the nvidia 295.59 driver but booted to 11.10 on an USB, the test file ran normally with no error  messages, showing all 'yes's.

Any suggestions??

Chao!, **bogan**.

---

### Post by bogan on 2012-11-11
Hi!,** ALL**,

Update 11/11/12

Does anyone know what these error messages mean ??

They do not seem to appear with any other application or script.

Chao!,** bogan**.

---

### Post by fixerdave on 2013-02-03
> **bogan said:**
> Hi!,** ALL**,

Update 11/11/12

Does anyone know what these error messages mean ??

They do not seem to appear with any other application or script.

Chao!,** bogan**.

I'm getting the same error while trying out "Processing" (processing.org) scripts.  Basicaly, a shell around java and I'm just trying out a few of the example scripts/programs/sketches (whatever you want to call them).  It seems at least some of the 3D stuff is broken.  2D stuff, however, seems to work.

For what it's worth, I've always had issues with the nvidia card on this system.  I suspect this is another one.

Sorry, no solution yet, but, yes, it does happen somewhere else.  It's all beta and I'm just taking a first peek at it, so not exactly at the bug report stage.  But, my first search brought me here so I figured I'd add a little info for the next searcher.

---

### Post by bogan on 2013-02-03
Hi!, **fixerdav**e,

Thanks for your info, interesting; I had not seen any hint that the video driver, nvidia or other, is in any way involved, other than the "nv" in the Warning message, and the first instance came when running the Nouveau driver..

However, it may be significant that of 5 different 12.10 installations and 2 of 12.04, running various nvidia drivers, only one of the 12.04's and one of the 12.10's - one that was updated from 12.04, not a fresh installations - showed either  'broken pipe', or 'nvfx screen UnknownPIPE_CAP30'messages.

In my case, 'broken pipe' came before the video driver is activated, or on shut down, and that seems to be connected with the 'Unknown PIPE_CAP nvfx' warning.

The best explanation I have seen so far, is that the system or a process, is trying to write to a file, but requires access to, or the use of, something that is either not yet ready, or is already in use by another process. A long-winded way of saying it can be a timing issue.

Interestingly, since the 12.10 updates of about two months ago, and my activating the Proposed ppa, neither message has re-occurred.

Chao!, **bogan.**

---

