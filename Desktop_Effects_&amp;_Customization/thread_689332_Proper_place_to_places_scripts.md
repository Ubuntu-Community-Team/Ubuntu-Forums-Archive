---
title: "Proper place to places scripts"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by ewanchic on 2008-02-06
I'm looking for some general advice here. I am writing some scripts that will perform various backups and alert emails. My thoughts are to make two directories:
> 
 /etc/backup
 /etc/alerts


From there I will setup various cron jobs...listed in the /etc/crontab file, to be fired.

Would this be a proper place/practice? Im going to assume any and all responses; there is not right or wrong answer, just professional opinions. 

Thanks

---

### Post by ewanchic on 2008-02-08
*Bump*

---

### Post by bcl1713 on 2008-02-08
I keep all my scripts in ~/bin

---

### Post by ebsbox on 2008-02-08
> **bcl1713 said:**
> I keep all my scripts in ~/bin

This is probably the best place to keep your scripts as you won't need to add a location to PATH. My suggestion:

Create a directory like: /home/yourName/myScripts

Place all your scripts in /myScripts so they're all in one place.

sudo cp/home/yourName/myScripts/yourScript /bin    # if you so choose.

---

### Post by ewanchic on 2008-02-08
> **ebsbox said:**
> This is probably the best place to keep your scripts as you won't need to add a location to PATH. My suggestion:

Create a directory like: /home/yourName/myScripts

Place all your scripts in /myScripts so they're all in one place.

sudo cp/home/yourName/myScripts/yourScript /bin    # if you so choose.

I should have specified that this is a server where many administrators would manage all, as opposed to a desktop environment. Would that make a difference?

---

