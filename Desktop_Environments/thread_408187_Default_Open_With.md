---
title: "Default Open With"
date: 2007-04-13
forum: Desktop Environments
---

### Post by Neecapp on 2007-04-13
I am not sure if this belongs here, but I am pretty sure it does.

Okay so I am running Feisty Fawn (Gnome)... when I right click go to properties > open with > choose program from list

I can't change the program. I can click a different program, but it doesn't change.

What's up with that?

It was working perfectly.

Any ideas?:confused:

Thanks in advance!
-Neecapp

---

### Post by NikoC on 2007-04-13
Right click the file, choose properties, Open with tab and there you can change or add another application to open your file.

---

### Post by Neecapp on 2007-04-13
> **NikoC said:**
> Right click the file, choose properties, Open with tab and there you can change or add another application to open your file.

Yeah, I know.. but it won't change it... even if I add another program. The radio button next to it won't move and the program doesn't change.

I am confused as to why it's not.

Thanks,
-Neecapp

---

### Post by jdubiner on 2007-04-17
I have the same problem... The radio options don't take the new value.  

Anyone know what the underlying config settings are?

Thanks

-- joel

---

### Post by jdubiner on 2007-04-17
Aha!  It was a permissions problem.

make sure you have permissions on ~/.local

su
cd /home/joel
chown -R joel .local
chgrp -R joel .local

Now I'm able to set the preference.

---

### Post by lagartoflojo on 2007-07-10
Hmm... I'm having the same problem and changing the permissions on .local didn't do anything...
Any help?

PS: I ran: sudo chown -R hernan:hernan .local/

**Edit:**
Ok, I fixed it. I ran chmod -R 777 .local/
Now it works.

---

