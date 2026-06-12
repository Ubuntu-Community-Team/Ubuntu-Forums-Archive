---
title: "Flashing window border with Beryl"
date: 2007-01-19
forum: Desktop Environments
---

### Post by Mega_slayer on 2007-01-19
Hey guys, I'm using Dapper with Xgl/Beryl and everytime I log in the borders of my windows are flashing on and off. I have checked out some other threads but havn't found a solution. Has anyone figured this one out? Thanks in advance,

- Scott

---

### Post by tuxmap on 2007-01-19
open terminal and kill beryl-manager, or simply quit the beryl-manager tray icon. dont worry beryl wont stoprunning.

---

### Post by Mega_slayer on 2007-01-21
Thanks a lot tuxmap, I havn't had the chance to try it out yet, but I will the next time my border is going nuts. I will let you know how it goes...

- Scott

---

### Post by neo_reloaded on 2007-02-01
+1
yes, I also have the same problem. Beryl used to work perfectly earlier.
My default session is Gnome, when I want some candy I switch to XGL/Beryl settings.
I am not sure but it might have to do with the fact that I have installed latest ATI drivers in my computer.
Hm!!!!!

---

### Post by Mega_slayer on 2007-02-04
> **neo_reloaded said:**
> +1
yes, I also have the same problem. Beryl used to work perfectly earlier.
My default session is Gnome, when I want some candy I switch to XGL/Beryl settings.
I am not sure but it might have to do with the fact that I have installed latest ATI drivers in my computer.
Hm!!!!!

Yeah, I'm inclined to agree with you. I'm wondering if it would work better with AIXGL (I forget what it is called) instead of XGL. Anyways, I got rid of XGL and Beryl. It was also taking up major cpu usage, sometimes up towards 60-80%.

---

### Post by neo_reloaded on 2007-02-20
I just got around this problem..and this really sucks.

First, start your default gnome session and login.
Then, logout and from sessions chose XGL and log back in.
Then everything works just fine. Otherwise, the flashing window border appears if you straight go into XGL session after system start up.
This is wierd and nasty

---

### Post by eriK-B on 2007-04-21
I also had this problem with my dapper,
i found a way to stop this.
just add "emerald --replace" to System>Preferences>Sessions>Startup Programs

the running emerald process will be stopped and a new one will be put instead.
This works fine for me.

hope this helps

---

