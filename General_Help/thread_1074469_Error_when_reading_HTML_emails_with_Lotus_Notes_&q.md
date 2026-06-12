---
title: "Error when reading HTML emails with Lotus Notes &quot;MOZILLA_FIVE_HOME...&quot;"
date: 2009-02-19
forum: General Help
---

### Post by chouf on 2009-02-19
Hi all,

I'm experiencing the same problem as described in this post ([http://ubuntuforums.org/showthread.php?p=5435560](http://ubuntuforums.org/showthread.php?p=5435560))

I've Lotus Notes 8.0.1 installed on Intrepid Ibex and each time I want to view an HTML email in Lotus Notes, the following message is displayed:

> The value of MOZILLA_FIVE_HOME : /usr/lib/xulrunner-addons, is not a correct path of Mozilla verion 1.8.* or later. DOMBrowser can not work

In the post mentionned above, Rever75 said he found the solution

[QUOTE=Rever75]Well I solved the problem by pointing my MOZILLA_FIVE_HOME to /usr/lib/xulrunner. I did this by putting a script in /etc/X11/Xsession.d/ telling it to export MOZILLA_FIVE_HOME=/usr/lib/xulrunner. I did not need Mozilla installed it was looking for the runtime environment to display HTML pages.[/QUOTE]

This is like chinese to me as I'm new wth Ubuntu.
I've tried to post on the original thread, but it's marked as read-only. I've also sent rever75 a message but didn't get a reply.

Could someone detail for me the steps to take in order to implement the fix suggested by Rever75? (or any other fix to solve my problem)

thanks all in avdance for your help

have a nice day

chouf

---

### Post by dcstar on 2009-02-19
> **chouf said:**
> 
.........
Could someone detail for me the steps to take in order to implement the fix suggested by Rever75? (or any other fix to solve my problem)

Try this, open a terminal and type the following:

```
sudo gedit /etc/X11/Xsession.d/59Notes
```

Put the following in the file and then close and save it:

```
export MOZILLA_FIVE_HOME=/usr/lib/xulrunner
```

Log out and log in again and see if it works.

---

### Post by chouf on 2009-02-20
hi dcstar and thanks for your answer.:)

I've did exactly what you've explained but unfortunately it didn't work.
When I open an email In Lotus Notes it still comes up with

> The value of MOZILLA_FIVE_HOME : /usr/lib/xulrunner, is not a correct path of Mozilla verion 1.8.* or later. DOMBrowser can not work.

Would you have another idea?

Tx and have a nice day

chouf

---

### Post by chouf on 2009-02-23
Anyone an idea?
Unfortunately I do need Lotus Notes to read my company emails.
Having this bug is the only reason why I canot switch to Ubuntu.

Tx in advance

---

### Post by chouf on 2009-03-09
nobdy is inspired by this problem?
this is really blocking me using Ubuntu.... :(

---

### Post by NemoFox on 2009-08-12
I used export MOZILLA_FIVE_HOME=/usr/lib/xulrunner-1.9.0.13 and it worked for me :)

---

