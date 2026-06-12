---
title: "Determine exact application to whitelist in panel"
date: 2011-11-16
forum: Desktop Environments
---

### Post by gamblor01 on 2011-11-16
Hi all,

I just got davmail setup to connect our MS online services and I can finally access my email in Thunderbird via IMAP instead of POP3!!  This is great so I don't have duplicated garbage on every machine, and furthermore I have direct access to the folders I created!  Hooray!


The davmail program has an indicator icon that is supposed to run in the systray area, but obviously this was killed in 11.04.  I know that I can simply whitelist 'all' and it will work, but I am not looking to do that.  I really don't need the icon, but it's nice to know that davmail is running by simply seeing the icon there.  Plus I can access logs, etc.

I have gone into dconf-editor and attempted to append to the current desktop > unity > panel > systray-whitelist, but nothing I put in there seems to work.  I tried both 'davmail' and 'DavMail' but neither one of those worked.  It's actually a java application, and /usr/bin/davmail is just a shell script to invoke it:

```

#!/bin/sh
export LD_LIBRARY_PATH=/usr/lib/jni
for i in /usr/share/davmail/lib/*; do export CLASSPATH=$CLASSPATH:$i; done
java -Xmx512M -cp /usr/share/davmail/davmail.jar:/usr/share/java/swt.jar:$CLASSPATH davmail.DavGateway "$@"

```


Thus, I tried to whitelist 'java' as well and this doesn't seem to work either.  Is there some particular algorithm to determine the exact string that should be placed into the whitelist in order to allow a specific application to show up in the panel?  I would like to avoid using 'all' (even though I have confirmed this does work and displays the davmail icon correctly -- unfortunately it displays a bunch of other clutter too).


Just FYI, I did add /usr/bin/davmail to my list of startup applications so it should always be running when I login, but this whole thing just got me curious.  Instead of just whitelisting everything, how can I determine the exact string to enter into the systray-whitelist to allow an application's icon there?  There has to be a way to do this...I'm curious now to know what that method is.  :)

---

### Post by oliver369 on 2012-02-15
I ran into exactly the same problem and discovered that the magical value is 'SWT'
More info here:
[http://sourceforge.net/tracker/index.php?func=detail&aid=3295001&group_id=184600&atid=909904](http://sourceforge.net/tracker/index.php?func=detail&aid=3295001&group_id=184600&atid=909904)

---

### Post by claytronic on 2012-11-15
Thanks for posting the answer, oliver369. It was quite helpful.

---

