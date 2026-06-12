---
title: "Quake3 Help."
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by X3zh on 2008-03-15
Hello.

I Just successfully installed Q3 on my Ubuntu (7.10), but when I am about to run it' nothing happens. I would appreciate if anyone would help me on this one.

Thank you.

---

### Post by Sockerdrickan on 2008-03-15
Run it from a terminal and paste the output here.

---

### Post by X3zh on 2008-03-15
I would like to ask you to write the run command. I have only been using Ubuntu for 3 days.

Thank you.

---

### Post by hessiess on 2008-03-15
'cd' into directory then run './programname'

---

### Post by X3zh on 2008-03-15
Sorry for this late reply.

I am getting an error message when I am about to start Q3. It looks like this:

------ FS_Startup -----
Current search path:
/home/xlv/.q3a/demota
/usr/local/games/quake3/demota
./quake3.x86/demota

----------------------
534 files in pk3 files
----- CL_Shutdown -----
xlv@xalvation-desktop:/usr/games/Quake3$ -----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: Couldn't load default.cfg


A solution to this would be great.

---

### Post by X3zh on 2008-03-16
Please, I really need to get this solved.

Thanks.

---

### Post by FrozenFox on 2008-03-16
I'm not sure if this will end up helping, but I will post it anyway. Your problem appears to be similar to what I had a little ways back.

I had the same error with tremulous (a mod made from the open sourced q3 engine). It happened when I changed the main game loader binary. The error seems to be that you are running the binary in a place that it should not be. For instance, in my case, tremulous had a run script located at /usr/games/tremulous or some such thing, whereas the real binary was at /usr/lib/tremulous/tremulous or something of the sort. In updating tremulous to an unofficial 1.2 patch (the official one will prolly never come, lawl), I replaced the script instead of the correct binary. So, the binary was trying to find all of the game files in the current directory it was located (/usr/games) but they were actually in another (/usr/lib/tremulous). The simple fix was to restore the original setup, and replace the correct binary. You may find your solution in a similar fashion. **To try to figure this out, please**: cd to the file the quake 3 binary is in and give is the results of the command ls please.

From just looking at your comment, it appears that your binary is in /usr/games/Quake3/, but your game files (default.cfg particularly) are not.

---

### Post by X3zh on 2008-03-16
Thanks! It really were similar to your problem. I didn't have my pak0.pk3 in the right place. Thank you so much for your help.

---

