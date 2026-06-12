---
title: "Unreal Tournament 2004 9 (Can't find 'ini:Engine.Engine.GameEngine' in configuration)"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by ade234uk on 2006-06-14
I installed Unreal Tournament 2004 and it worked a treat. I then went to restart and got the following error:-

ade@ade-desktop:~$ ut2004
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error

Has anyone else experienced this problem before?

Thanks for your help

---

### Post by Dfects on 2006-09-03
It was a lonnnnnnnnnng time ago when you posted this, but just incase anyone else gets this error, Its probably caused because you installed as root (using sudo) then ran it without. As you installed as root, the files belong to root only and your current user won't have permission. chown the files to the user you want or run sudo ut2004 :)

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-25
Indeed, this is correct -- Either chown the files or type 'sudo ut2004' at the shell. 

I haven't played this game in quite some time -- I just finished installing it on a fresh build of Dapper and man does this it seem smooth. I've had the same hardware for almost 2.5yrs and can't ever recall the game running this good. 

--Noice!

---

### Post by Perfect Storm on 2006-09-25
Wrong.

You can install as root (global), without running the game as root. The problem is when installed as root and hit the play button which are displayed in the installation window you'll get permission problem when you try to start the game up afterwards.
If people exit the installation windows instead and write ut2004 in the terminal this problem won't show up without compremizing the security.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-25
> **Artificial Intelligence said:**
> Wrong.

You can install as root (global), without running the game as root. The problem is when installed as root and hit the play button which are displayed in the installation window you'll get permission problem when you try to start the game up afterwards.
If people exit the installation windows instead and write ut2004 in the terminal this problem won't show up without compremizing the security.

This has not been my experience! My install will not initialize without running with sudo credentials. 

This is the error that is invoked when attempting to run the game under non-root privledges. 

[COLOR="Red"]Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error[/COLOR]

I suppose long term you could make a few more tweaks to the game insofar as removing the offending lib(s), however, as a quick bandaid, the aformentioned solution should work as an immediate fix.

---

### Post by Perfect Storm on 2006-09-25
Did you tried removing/deleting .ut2004 in home folder before trying out my suggestion?

It's the suggestion I give people with such problems and it works for them (including myself)

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-27
> **Artificial Intelligence said:**
> Did you tried removing/deleting .ut2004 in home folder before trying out my suggestion?

It's the suggestion I give people with such problems and it works for them (including myself)

Thanks AI -- Everything worked as expected! Much appreciated...

Regards,

---

