---
title: "Compiz at startup"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Beej on 2006-09-19
Hi I recently installed compiz from quinns repos and even on my low spec system it rocks. I have one problem though, I added compiz-start to my startup as the wiki entry says, but every time I start my XGL session, it starts with metacity, I have to run compiz-start from the terminal. 

I've played about and it seems that that the compiz-start entry is not being saved when I close the sessions manager, as if I reopen it is missing. Can any one help?

Thanks,


Beej.

---

### Post by its_me_gb on 2006-09-19
try compiz-manager now instead

---

### Post by Beej on 2006-09-19
thanks for the quick response I will give it a go when I get back from from work.

---

### Post by factor on 2006-09-19
which wiki entry? can you post a link? does compiz-manager works for 64 bits? thanks in advance for your help.

Regards.

---

### Post by Beej on 2006-09-19
its_me_gb,

I don't think the issue is with compiz-start but with the gnome session manager. It refuses to save entries to my start up programs. do you know if there is a terminal way to do this?

factor wiki entry is

[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

---

### Post by bulldog on 2006-09-19
Try,

/usr/bin/compiz-start 

in your sessions menu.

If you installed the latest updates with csm this is the right starter.

If you haven't done so,install cgwd cgwd-themes and cgwd-themes-extra.

Gives you nice borders to choose.

---

### Post by Beej on 2006-09-19
okay so I open system > preferences > sessions

i go to the right most tab, startup programs and add /usr/brn/compiz-start

i then close sessions and log out. When I log back in compiz does not start. the entry i put in sessions is no longer there. Running compiz-start from the terminal does start compiz.

What am I doing wrong?

---

### Post by bulldog on 2006-09-19
You're doing nothing wrong,at least I think so.

But did you follow all the steps in the tutorial?

And which tutorial did you use?

{maybe a typo,but it should be 

/usr/bin/compiz-start}

---

### Post by Beej on 2006-09-19
I used this tutorial
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

I used method A

---

