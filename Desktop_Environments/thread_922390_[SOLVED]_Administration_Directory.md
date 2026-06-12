---
title: "[SOLVED] Administration Directory?"
date: 2008-09-17
forum: Desktop Environments
---

### Post by stargirl51 on 2008-09-17
Hi again!

Ok so I've been trying to get to pure Xubuntu seeing as I've had the previous problem of gnome settings bleeding into Xubuntu.

But apparently, I can't get rid of gnome for some reason. And when the computer starts up, it shows the ubuntu load screen.

So I thought I'd try to get pure gnome but when I went into terminal and typed in the instructions on how to get rid of Xfce (And yes, I have gone [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) )

But the message of:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Could that be the reason why my gnome settings have been bleeding over to Xfce?

How would I go about getting just xubuntu? (or if it's possible just xubuntu with a gnome option?)

---

### Post by mali2297 on 2008-09-17
> **stargirl51 said:**
> 
But the message of:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Could that be the reason why my gnome settings have been bleeding over to Xfce?

No, that message usually shows up when you run apt-get with Synaptic or Add/Remove open. You can't use these programs simultaneously.

> 
How would I go about getting just xubuntu? (or if it's possible just xubuntu with a gnome option?)

Open Xfce's settings manager and go to *Sessions and Startup -> Advanced*, you will see an option to *Launch Gnome services at startup*. Disable that.

Open xfce autostart editor (the command is *xfce4-autostart-editor*) and check that there aren't any Gnome applications listed.

Remove the hidden directory .cache in your home folder. It contains saved sessions.

If you use nautilus, start it with the command
```

nautilus --no-desktop

```
Otherwise it will take over the desktop from Xfce's desktop manager.

To change the load screen (usplash theme), see here
[http://ubuntuforums.org/showthread.php?t=344033](http://ubuntuforums.org/showthread.php?t=344033)

---

### Post by stargirl51 on 2008-09-17
I've tried all of your suggestions already and though they are appreciated, they just didn't work.

So what I did was reinstalled ubuntu and reinstalled xfce and so far it's been working pretty well.

I guess I got a little too excited learning how to write code in terminal and got carried away, hahaha...

PS: How do I mark this post as solved?

---

