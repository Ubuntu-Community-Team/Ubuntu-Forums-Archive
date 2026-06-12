---
title: "&quot;Could not read network connection list&quot; error"
date: 2005-04-12
forum: Desktop Environments
---

### Post by bigblop on 2005-04-12
When I type this in a shell:

konqueror --profile Myview

I get this error in a box:

Could not read network connection list.
/home/bigblop/.DCOPserver_ubuntu_0

Please check that the "dcopserver" program is running.


In the shell I get this error:
kdeinit: Aborting. No write access to '/home/johs/.ICEauthority'.
KThemeStyle cache seems corrupt!


I have tried to delete the .DCOPserver_ubuntu_0 file in my home dir and reboot the computer but it does not help.

After these errormessages konqueror opens as it used to. How do I fix this problem??

---

### Post by nebula on 2005-09-26
Got the same problem here, no idea where it came from. I did chmod the .ICEauthority to 77, but that doesn't help too. 
Any help anyone?

---

### Post by Paperjam on 2005-09-26
[QUOTE=bigblop]
In the shell I get this error:
kdeinit: Aborting. No write access to '/home/johs/.ICEauthority'.
KThemeStyle cache seems corrupt!
[/QUOTE]

What does ```
ls -al .ICEauthority
```
show you? Does the file belong to the root user? If yes, do
```
sudo chown *YourUsername* .ICEauthority
sudo chgrp *YourUsername* .ICEauthority
```

If that doesn't help, try resetting all the files in your home-directory to your username, because there might be other files that belong to the root-user, whereas they should belong to you.
```
sudo chown -R *YourUsername* *
sudo chgrp -R *YourUsername* *
```

---

### Post by nebula on 2005-09-26
Yeah tried that, got annoyed, issued the following commands:
su
rm -rf /tmp/
mkdir /tmp
chmod 777 /tmp
rm -rf ~/.ICE
startx

And it's working again :)

---

### Post by petethechop on 2007-01-26
All it took for me was the following:

```
sudo chown -R *user* /tmp/.ICE-unix
```

That fixed the problem.

---

### Post by ganglia on 2007-04-08
it may be to write or read access to .kde directory in your home folder
try this thread, i hope it helps:
[http://ubuntuforums.org/showthread.php?t=261872](http://ubuntuforums.org/showthread.php?t=261872)

---

### Post by beanland on 2007-07-11
> **nebula said:**
> Yeah tried that, got annoyed, issued the following commands:
su
rm -rf /tmp/
mkdir /tmp
chmod 777 /tmp
rm -rf ~/.ICE
startx

And it's working again :)

Nebula, that was a lifesaver.  I don't know why I didn't try this first...  I've been working on this for at least two hours.  I had the same problem as described, but this was the only one that worked for me.

During that time, I:

--Lost control of sudo
--Got a headache
--Ran into some very lame webcomics
--Attempted to change my hostname, and have it stick, to no avail.

I think I ran into this problem after changing my hostname from "Linux" to "Linux Upstairs" in the network settings thing.  That might not have been the problem, but thats what came after the .DCOP string, and, well, you know.  Whatever.  I'd like to think it's because I had a space in the string I used, but who knows.

Anyway, thank you SO MUCH!!

EDIT:

Unfortunately, my mysql.sock file was in that folder, and now I'm having trouble connecting to my MySQL server--or even starting it, for that matter.  Does anyone have any idea how to replace this file?  I've seen suggestions on sites to reset the location of the mysql.sock file, but, seeing as how I don't have one anymore, how will that work?

Thanks!

EDIT 2:

I believe my problem has [escalated to something I hadn't even imagined]("http://ubuntuforums.org/showthread.php?p=3002778#post3002778").  I believe it rests on the bit of code I blindly copied and pasted from Paperjam:

> sudo chown -R YourUsername *
sudo chgrp -R YourUsername *

Not that it was bad advice--it just wasn't right for me, or I did something with it that I shouldn't have.  I believe this is what lost me control of sudo as well, but I could be completely wrong.  I'd like to consider myself experienced with this stuff, but, at heart, I guess I'm still a newbie.

---

