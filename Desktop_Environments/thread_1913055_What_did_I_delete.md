---
title: "What did I delete?"
date: 2012-01-21
forum: Desktop Environments
---

### Post by z0rr099 on 2012-01-21
I installed lubuntu and removed quite a few packages through synaptic in order to remove things that I will never use and to make it smaller. I did this over a couple of weeks, so I have no idea what I removed.

My problem is that in either xterm or lxterm, I have lost the ability to press the 'up' arrow key and scroll back in my command history. No combination of keys work either. All that shows are things like the actual escaped key codes for the up arrow or any of the arrow keys when pressed.

Does anyone know what I might have deleted to have this behavior happen? Since it affects both terminals, I assume it has something to do with bash, but I have no clue. I have searched, but I guess I'm the only idiot that ever did this. 

I know it's something I did, but I've been customizing this for a few weeks now and haven't kept track of all the changes I made. I did reinstall both terminals, but I think I'm barking up the wrong tree there. It probably doesn't have anything to do with the terminals or their configuration files.

Can anyone tell me what files might affect this? What might I have deleted or what can I try to reinstall to get the up/down arrows working again?

Thanks

---

### Post by 73ckn797 on 2012-01-21
You could try to find the package and dependencies for the affected terminals.

May want to look around here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by |{urse on 2012-01-21
The command

> history

is what you want :)

So far as the up and down arrows, hopefully looking through your command history will help you rectify that.

---

### Post by z0rr099 on 2012-01-21
|{urse,

History doesn't work.

$ history
sh: history: not found
$
Is that a clue? Does that tell you anything that might be of help?
--------------------
73ckn797,

Thanks, I've looked around the packages and haven't found anything that seems to help. I'll google each package and see if that will give me more information as to what each one manages or what it influences.

Hey, I just noticed something from the output of 'history'. It shows that it's using the 'sh' shell. When I type in 'bash', now everything works as expected. What sets the terminals to use 'sh' instead of 'bash'?

Edit again - In the /etc/passwd file, it shows that the user I created when I installed it, is using /bin/sh instead of /bin/bash. Is that normal? This looks like it has to do more with how it got installed to hd or the default shell for new users, than anything I removed.

---

### Post by Krytarik on 2012-01-22
> **z0rr099 said:**
> Hey, I just noticed something from the output of 'history'. It shows that it's using the 'sh' shell. When I type in 'bash', now everything works as expected. What sets the terminals to use 'sh' instead of 'bash'?

Edit again - In the /etc/passwd file, it shows that the user I created when I installed it, is using /bin/sh instead of /bin/bash. Is that normal? This looks like it has to do more with how it got installed to hd or the default shell for new users, than anything I removed.
You can safely change that setting there; for me it was automatically set to "/bin/bash", some others seem to have set "/bin/sh" instead, for whatever reason, you know the outcome. ;-)

Regards.

---

