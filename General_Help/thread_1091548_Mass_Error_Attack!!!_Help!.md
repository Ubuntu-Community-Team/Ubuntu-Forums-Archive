---
title: "Mass Error Attack!!! Help!"
date: 2009-03-09
forum: General Help
---

### Post by McMajik on 2009-03-09
Help! My entire installation is killing itself! In firefox, i can't click the back button, i have to right click it to get the options, on the bar below, i can't open a new tab or windoe (The options are there, but i can't click them), my cookies keep getting deleted, and i have to log back in to sites i set to keep me logged in. The remember password option doesn't work either.

Amarok complains at me that an xml file is corrupt when i start it. Also, it complains that dcopserver isn't running (even though it is) and puts the amarok task bar icon in its own window! 

Amsn won't start unless i run it as root, and complains its configurations are corrupt when i do.

Half the games i have installed won't run unless i go to the directory in the terminal window and run them from there. And most of them come up with some errors.

*deep breath*

Ok, that's my predicament. Any suggestions?

By the way, this all started happening at the same time

Thanks in advance,
McMajik

---

### Post by heindsight on 2009-03-09
What did you do just before all this started?

---

### Post by computerjunkie on 2009-03-09
Edit any global configuration files or remove anything important?

---

### Post by gibxam on 2009-03-09
This sounds like the behavior of a root kit. I just had one on my computer little more than a couple days ago, which is what made me decide to completely switch to ubuntu :D. Perhaps a full reinstall?

---

### Post by benjobe on 2009-03-28
I have the same problem with Firefox and Amarok.  It all started happening this morning after I updated my system and restarted.

I'm running Intrepid Ibex 8.10 Kernel Linux 2.6.27-11-generic GNOME Version 2.24.1 on an ASUS P5KPL-CM mobo with an 2GHz Intel Core 2 Duo.

Amarok gives me the message that it couldn't find /home/user/.DCOPserver_ComputerName_0 and asks me to make sure that dcopserver is running (it is). Then it begins to suck of 100% of my CPU as it continues to load.  Then it gives me the message that XML in transfer list is invalid.  All my playlists are gone.  All my history is gone.

Firefox, before the browser pops up, runs through three iterations of Add-On updates (so quickly that I can barely read them as they flash by).  Once it's running neither the Forward or Back buttons work.  I doesn't remember any of my bookmarks.  However, it remembers my URL history; go figure.

I tried restoring Firefox to an earlier version with no effect.  I tried looking at my system log but couldn't understand what all the code jargon meant.  

Is there some way to remove all the updates I made this morning and then re-update them one by one to determine if they're the cause of these problems?

Thanks in advance for any ideas/help you can give me.

---

### Post by kubug on 2009-03-28
> **gibxam said:**
> This sounds like the behavior of a root kit. I just had one on my computer little more than a couple days ago, which is what made me decide to completely switch to ubuntu :D. Perhaps a full reinstall?

How would one go about and get a root-kit on ubuntu? Just curious? Could these come from non-approved Repositories? Or a vulnerability in some code?

---

