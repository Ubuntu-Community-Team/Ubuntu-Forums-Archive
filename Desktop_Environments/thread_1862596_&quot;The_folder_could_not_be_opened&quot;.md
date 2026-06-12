---
title: "&quot;The folder could not be opened&quot;"
date: 2011-10-16
forum: Desktop Environments
---

### Post by bhamrick on 2011-10-16
I'm sure this has been posted elsewhere, but I'm having trouble searching for this phrase.

I installed a fresh install of Xubuntu 10.04, and then upgraded to 11.04 and then to 11.10. I have everything set up and it all seems to be working, but when I try and launch the file manager, it hangs for 20 - 30 seconds and then displays a Launch Error "The folder could not be opened." The folder I'm attempting to open shows up, but this happens every time I attempt to open a folder. I'm on Xubuntu 11.10 now, so I'm running Xfce 4.8 and Thunar 1.2.3. Googling the error seemed to bring up similar issues that were supposedly resolved with Thunar 1.2.2, which doesn't help me.

Has anyone else seen this?

---

### Post by linuxcss on 2011-10-24
I am getting this too,

[B]The folder could not be opened
[/B]
*Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.*

happens when trying to open desktop folders, including trash

running xubuntu 11.10 ... xubuntu-session

any body got a fix for this ?

---

### Post by david12 on 2011-12-08
I am receiving the same message when I open Thunar for the first time in a new session after a shutdown or reboot.  However, it seems (sorry, I'm reporting an impression not a documented series of events) that the first opening of Thunar takes the 20-30 seconds described by bhamrick.  Thereafter, the speed is more 'normal.'

Glancing at the Task Manager during the first launch of Thunar shows some activity in the gvfs area, but I don't know how or if this might be related.

I'm using Thunar 1.2.3 in xubuntu 11.10.

I like this desktop.  I trust this will be worked out, although the lack of responses to this forum post indicates that the problem, whatever it might be, may need someone with some real xubuntu chops to address it.

Maybe it should be a bug report? :neutral:

bug report filed: [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/901673](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/901673)

---

### Post by maestrosteve on 2011-12-08
> **bhamrick said:**
> I'm sure this has been posted elsewhere, but I'm having trouble searching for this phrase.

I installed a fresh install of Xubuntu 10.04, and then upgraded to 11.04 and then to 11.10. I have everything set up and it all seems to be working, but when I try and launch the file manager, it hangs for 20 - 30 seconds and then displays a Launch Error "The folder could not be opened." The folder I'm attempting to open shows up, but this happens every time I attempt to open a folder. I'm on Xubuntu 11.10 now, so I'm running Xfce 4.8 and Thunar 1.2.3. Googling the error seemed to bring up similar issues that were supposedly resolved with Thunar 1.2.2, which doesn't help me.
[[color=#f8f8f3]_modificare poze_[/color]](http://www.fotoedit.ro/ro/modificare-poze)
Has anyone else seen this?

I had the same problem but i was verry nervous and i ereased all and put a fresh 11.10. Worked for me for a while.

---

### Post by david12 on 2011-12-08
There has been a bug report on this issue for a while: [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117).  

I received a reply to my posting regarding this issue at [COLOR=DarkSlateGray][EMAIL="xubuntu-users@lists.ubuntu.com"]xubuntu-users@lists.ubuntu.com[/EMAIL][/COLOR] which says:

> Your bug report is a duplicate of [https://bugs.launchpad.net/bugs/775117](https://bugs.launchpad.net/bugs/775117) , which is reported upstream. This is a known issue with Thunar, and is in work by the upstream developers.  So, it seems the matter is recognized and under repair. :)

---

### Post by circa on 2012-12-29
Well, it's over 1 year later since this thread was started, but the same issue still exists. The bug report even says that a fix was released, but I haven't received the update. There is a quick "band-aid" fix for anyone else stumbling upon this issue. The fix is located within the bug report... [https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117/comments/13](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117/comments/13)
It's a simple edit and works extremely well.

---

### Post by oldos2er on 2012-12-29
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

