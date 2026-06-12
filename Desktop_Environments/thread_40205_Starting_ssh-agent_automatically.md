---
title: "Starting ssh-agent automatically?"
date: 2005-06-08
forum: Desktop Environments
---

### Post by Nicolinux on 2005-06-08
Hi,

everywhere I read about Ubuntu and ssh-agent, it says the ssh-agent is automatically started by GDM. I have a smartcard (aladdin etoken pro). The steps I need to perform  are:
1. eval `ssh-agent`
2. ssh-add -s 0
3. enter passphrase

The downside of this procedure ist that I have to do this for every gnome-terminal that I open...

How is this supposed to work automagically with Ubuntu? Ssh-agent does not seem to be started because after login I get the following error message if I begin with step 2.
```

Could not open a connection to your authentication agent.

```

Thanks much

Stefan

---

### Post by WegDamit on 2005-10-05
Im not using a smartcard, only "normal" Keyphrases, but i think you 
have a look into [FONT="Courier New"]/etc/X11/Xsession.d/90xorg-common_ssh-agent [/FONT].
There is the startup code for ssh-agent.
I think you need to tweak these settings.
And put a "ssh-add" (or whatever is needed for youir smartcard) call in your startup items in the Gnome Desktop.
Then you should be asked every at Login to authenticate and this will work for all Applications which uses ssh-agent.

---

