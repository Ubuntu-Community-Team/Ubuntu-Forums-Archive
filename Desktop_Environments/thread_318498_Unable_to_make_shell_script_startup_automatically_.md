---
title: "Unable to make shell script startup automatically at login"
date: 2006-12-14
forum: Desktop Environments
---

### Post by mannih2001 on 2006-12-14
Hi,

I have this little shell script that will start a Windows up using wine. I'd like to be able to run this script as soon as I login, i.e. as a startup program. So I used the session applet and added the script to the startup programs, but I never see wine running after I've logged in. The script itself works just fine and I can run it after I have logged in by simply double-clicking a launcher I created on my desktop that will call the script.

Is there any reasons why shell scripts or shell scripts that run wine can't be made startup applications? Can I do anything do debug this? Is there a logfile that holds information about errors when starting ups in gnome?


Regards,
Manni

---

### Post by mcduck on 2006-12-14
errors should be in ~/.xsession-errors

---

### Post by mannih2001 on 2006-12-14
Thanks. Nothing unusual in that file. 


Manni

---

