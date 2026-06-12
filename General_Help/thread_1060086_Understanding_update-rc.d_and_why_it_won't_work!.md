---
title: "Understanding update-rc.d and why it won't work!"
date: 2009-02-04
forum: General Help
---

### Post by Twizzle on 2009-02-04
I have posted a similar post in Beginners but people are suggesting things that are not what I want and now the post is lost. I have also tried something further and think I almost have the solution.. I apologise of this is considered double posting:

I have written a script that I would like to run on shutdown and / or reboot. It just backs up my documents to my server. I want it to work at shutdown as it seems the most appropriate time to ensure I protect my work (If it runs at boot but the system wont boot, I loose what I did the day before...)

I 'just' understand the run levels and think that I should have the script run at run level 0.

I have copied it to /etc/init.d and ensured that it will run.

I am now trying to use update-rc.d as follows:

> sudo update-rc.d daily_backup.sh start 0 .

but I get the following error:

> update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)

And so I am stuck. Can someone tell me what I am doing wrong? I feel like I am very close!

---

### Post by Twizzle on 2009-02-05
Ok. After a bit more reading I found that I needed to do:

> sudo update-rc.d daily_backup.sh start 02 0 6 .

which does work BUT the script still will not run and I have no idea why! :(

---

### Post by Coreigh on 2009-02-05
First a pointer; If you click the Search menu along the top of the forums page you can select "Find all your posts" to re-locate old posts you have made. Depending on how old they are it is ok to make a new post in an effort to solve your problem. If you do it can be helpful to reference or link to the old post in the new one, and if you are feeling really generous add a link to the old one for the new one. This helps when others are searching.

Regarding your shutdown script, when you update the rc does a link get created in rc.0 pointing to the scrip in init.d? You can do a detailed listing of rc.0 to find out:
```
 sudo ls -l /etc/rc.0
```
this will display a directory listing of rc.0 including link targets.

---

### Post by Twizzle on 2009-02-05
Thank you for the reply and tips - I had never noticed the search for my posts option before! I have always tried to remember what key words I had used!

As for your question, yes now there is an entry in /etc/rc0.d that is S02daily_backup.sh

It is shown as a link and I have checked it's contents and can see that it is all correct (meaning I did not accidentally create a blank file somehow)

Oh and did you mean rc0.d instead of rc.0?

---

### Post by mpsii on 2009-02-05
Isn't runlevel 0 equivalent to shutdown?

---

### Post by jocko on 2009-02-05
> **mpsii said:**
> Isn't runlevel 0 equivalent to shutdown?
Yes.

---

### Post by Twizzle on 2009-02-05
> Isn't runlevel 0 equivalent to shutdown? 

Yes I believe it is and it is what I want. I want my backup script to run when I tell the computer to shutdown, so basically to be the first script to run when the shutdown scripts start. (I am of course assuming that they run one at a time and wait for the previous one to finish)

---

### Post by Coreigh on 2009-02-05
If you enter the command below in a terminal does the script run and does it work correctly?
```
/etc/rc0.d/S02daily_backup.sh
```
it may or may not need to be executed as sudo.

---

### Post by Twizzle on 2009-02-05
Yes it works fine and without being run as sudo.

---

