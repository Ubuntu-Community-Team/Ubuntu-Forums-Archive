---
title: "open shared folder of windows using fedora"
date: 2008-04-04
forum: Fedora/RedHat and derivatives
---

### Post by Auston on 2008-04-04
can anyone tell me how i can open a shared folder on others computer through lan using his ip address...
actually when both the users are using windows its not a big deal ..one guy shared his folder just by right clicking on it and enabling the sharing option...and the other guy type this in his run to open that folder through lan..\\ip address [enter]...

i am using fedora 8 and my frnd is using windows xp...he has shared a folder ..now how can i open hi folder and access it using my fedora..

---

### Post by Antman on 2008-04-04
> **Auston said:**
> can anyone tell me how i can open a shared folder on others computer through lan using his ip address...
actually when both the users are using windows its not a big deal ..one guy shared his folder just by right clicking on it and enabling the sharing option...and the other guy type this in his run to open that folder through lan..\\ip address [enter]...

i am using fedora 8 and my frnd is using windows xp...he has shared a folder ..now how can i open hi folder and access it using my fedora..

This site will solve most of your Fedora issues:
[http://www.fedorasolved.org/network]("http://www.fedorasolved.org/network")
Samba (windows file sharing) issues are in the networking section.

:guitar:

---

### Post by Antman on 2008-04-04
Oops... sorry, you want to open a windows share.
You will need to install the samba client if it is not already installed.

Then just Open file browser and click on "File">"Connect to Server"
Under "Service Type" select "Windows Share"
Populate the server field and share info.

---

