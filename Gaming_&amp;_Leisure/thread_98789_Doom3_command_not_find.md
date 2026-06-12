---
title: "Doom3: command not find"
date: 2005-12-04
forum: Gaming &amp; Leisure
---

### Post by Matt Houston on 2005-12-04
I have followed the how to [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)  but seem to have trouble starting Doom3. 

I have used the installer to install usr/local/games/Doom3, done the md5sum on the the five pk4 files and copied these to the base directory, but when I type Doom3 at the command I get "command not found".

Am I forgetting something?

---

### Post by Matt Houston on 2005-12-04
I just noticed usr/local/bin has links ot Enemy Territory and Nexuiz and these both work but no link to Doom3, could this have something to do with it?

---

### Post by mcrosmar on 2005-12-04
[quote=Matt Houston]I have followed the how to [http://zerowing.idsoftware.com/linux/doom/]("http://zerowing.idsoftware.com/linux/doom/")  but seem to have trouble starting Doom3. 

I have used the installer to install usr/local/games/Doom3, done the md5sum on the the five pk4 files and copied these to the base directory, but when I type Doom3 at the command I get "command not found".

Am I forgetting something?[/quote] 
Do you type "Doom3" or "doom3"?
Type doom3 to run the game.....

---

### Post by Matt Houston on 2005-12-04
Tried both, among other things. maybe I need to remove it and try again. How do I remove it, uninstalling software not installed through synaptic is something I have never got to griups with.

---

### Post by Zeroedout on 2005-12-04
[quote=Matt Houston]Tried both, among other things. maybe I need to remove it and try again. How do I remove it, uninstalling software not installed through synaptic is something I have never got to griups with.[/quote]

just delete /usr/local/games/doom3 , and delete ~/.doom3 and it'll be like you never installed doom

---

### Post by Matt Houston on 2005-12-04
excuse my ignorance, but ~/. means? Home?

---

### Post by jwenting on 2005-12-04
yup. It's your home.

---

### Post by Matt Houston on 2005-12-04
Thanks. Reason I ask is I couldn't find a doom folder in my home directory (yes I used ctrl + h). So I just deleted the Doom3 folder from games, did the install again and still no joy, command not found. I looked in my home folder and again there is no ~/.doom3. I must be doing something wrong here but I can't think what.

---

### Post by Matt Houston on 2005-12-04
OK, just tried again for the third time. I'm using the right installer right: doom3-linux-1.3.1302-sdk.x86.run ?

So should a ~/.doom3 directory appear after running the installer, because it doesn't, just a /usr/local/games/doom3-sdk. Obviously I should be running the installer as root?

---

### Post by mcrosmar on 2005-12-04
[quote=Matt Houston]OK, just tried again for the third time. I'm using the right installer right: doom3-linux-1.3.1302-sdk.x86.run ?

So should a ~/.doom3 directory appear after running the installer, because it doesn't, just a /usr/local/games/doom3-sdk. Obviously I should be running the installer as root?[/quote] 
I think that you have to run doom3-linux-1.3.1302.x86.run and not doom3-linux-1.3.1302-sdk.x86.run.

Yes, you must run installer as root: 
sudo sh doom3-linux-1.3.1302.x86.run

I think that .doom3 directory will be created after the firtst time that you'll run Doom3.

---

### Post by Matt Houston on 2005-12-04
I'm sure I just posted a reply....anyway, was using the rong installer, cheers for that, very satisfying feeling when I typed doom3 in the terminal and it started.

---

