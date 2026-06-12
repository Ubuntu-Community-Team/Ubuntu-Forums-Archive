---
title: "Thunderbird Closes Prematurely"
date: 2006-09-10
forum: Desktop Environments
---

### Post by BobBlum on 2006-09-10
As soon as several unread messages accumulate in Thunderbird, when I click to open it, it checks for new messages on the server, then immediately closes without giving me a chance to view the messages.  This started several weeks ago.  Has anyone else encountered this problem?  Any solutions?  Thanks in advance for any help.

---

### Post by aysiu on 2006-09-10
I have no idea what this could be, but have you tried launching Thunderbird from the terminal? The terminal output may give you a better idea what's going on.

---

### Post by BobBlum on 2006-09-10
> **aysiu said:**
> I have no idea what this could be, but have you tried launching Thunderbird from the terminal? The terminal output may give you a better idea what's going on.

Thanks.  I'll give that a try and see what happens.

---

### Post by BobBlum on 2006-09-10
When I invoke Thunderbird from the terminal, I get the following error message:

DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1
** (Gecko:5375): CRITICAL **: eazel_engine_image_render: assertion `width > 0' f ailed
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  5375 Segmentation fault      "$prog" ${1+"$@"}

Any idea on what might be causing this?

---

### Post by aysiu on 2006-09-10
Well, I did a Google search for your error (the part about /usr/lib and segmentation fault).

Didn't find a whole lot.

What I did find--[this thread](http://ubuntuforums.org/showthread.php?t=75185) and [this thread](http://ubuntuforums.org/showthread.php?t=64717)--seem to indicate a type of uninstall/reinstall might help.

---

### Post by BobBlum on 2006-09-11
Thanks.  I'll try it.  I had performed a removal/reinstallation with Synaptic, but I didn't remove the profile.  I'll give it a try and see what happens.

---

### Post by lottes70 on 2006-09-24
I developed a similar problem. I'd click and the window would open then immediately close.

I've determined that the problem is a corrupted prefs file.

Go to your home directory and go to the view menu and turn on show hidden files and find the .mozilla-thunderbird directory. Inside there is a file named prefs.js that is somehow corrupted.

So, hopefully you've made a backup (ha, ha, right, right, sure I did...](*,) . If you did, just copy that sucker right on in there. Otherwise you have to rebuild your corrupted profile (assuming you've still got it somewhere).

Anyway, I haven't done it yet, but I thought I put some clues on the thread...

[http://www.desktoplinux.com/articles/AT3034613099.html](http://www.desktoplinux.com/articles/AT3034613099.html)
[http://kb.mozillazine.org/Profile_Manager#See_also](http://kb.mozillazine.org/Profile_Manager#See_also)
[http://kb.mozillazine.org/Profile_Manager#See_also](http://kb.mozillazine.org/Profile_Manager#See_also)
[http://forums.mozillazine.org/viewtopic.php?t=82400&postdays=0&postorder=asc&postsperpage=15&start=0](http://forums.mozillazine.org/viewtopic.php?t=82400&postdays=0&postorder=asc&postsperpage=15&start=0)

---

### Post by lottes70 on 2006-09-24
Ok, well, I'm finished. Here's what I did.

My situation was that for some reason, my prefs file simply go corrupted in some way and so thunderbird would quit immediately after launching.

So, make sure tbird isn't running.

First I went to the hidden .mozilla-thunderbird directory in my home directory and copied the contents somewhere else (my desktop).

Then I went to a terminal window and ran: mozilla-thunderbird -profilemanager and deleted my original profile. Then, I created a new one and named it Default.

Then I launched t-bird and it started up ok, but no mail was in it and it ran the create account wizard. I recreated the two accounts I had on there, and before I finished each account, I made sure to uncheck the box that asks if you want to get your email right away.

Then, I opened the old .mozilla-thunderbird folder where my old stuff was and the new .moz-tbird folder where the new stuff is. Inside each of these folders is some folder with a random generated name of letters and numbers (different in each folder). I copied the contents of this folder from the old into the new, *except for the prefs.js file*. 

Then, when I launched tbird, everything was there. But, in my case, the old emails got imported into the wrong accounts (I had my wife's email, she had mine.) So, I changed the account settings so that they were correct.

In retrospect, it might have worked a little smoother if I had created the accounts with bogus info (names, etc), then after the email got recovered, changed the bogus data to be the correct data for the account.

Anyway, that's what worked for me.

Gotta go, time to backup my prefs file!

---

