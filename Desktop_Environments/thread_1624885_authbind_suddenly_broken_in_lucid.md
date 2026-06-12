---
title: "authbind suddenly broken in lucid"
date: 2010-11-18
forum: Desktop Environments
---

### Post by fdelin on 2010-11-18
Hello all,

I've been using authbind to allow tomcat to bind to 80 on 64-bit Lucid since August and it's been working fine every morning following morning power-up on our developer workstations.  This morning (11-18-2010 13:00GMT) at boot up authbind isn't allowing tomcat to bind to 80.

Checked /etc/default/tomcat AUTHBIND=yes is still set
/etc/authbind/byuid still matches the id for tomcat6 in /etc/passwd and is set to 0.0.0.0/0:1,1023 on the one I've been debugging, 0.0.0.0/32:1,1023 on the remainder.

I added in 80 to /etc/authbind/byport and made it owned by tomcat6 and gave it u+rwx

When I run /etc/init.d/tomcat6 start the java process created is owned by tomcat6.

I'm out of ideas.  Any help would be greatly appreciated.

Thanks,

Frank

---

### Post by fdelin on 2010-11-18
OK,
I did a couple set -x tp find the actual command being run through authbind for my setup but when I run it as tomcat6 I don't get any error thrown.  I ran it as root without the authbind and then the following showed up in my LISTEN list:

tcp6       0      0 :::80                   :::*                    LISTEN

Now I need to figure out why the workstations are trying to use ipv6 for my tomcat listen since authbind isn't compatible.

---

### Post by fdelin on 2010-11-18
OK,

Per [http://linux.derkeiler.com/Mailing-Lists/Debian/2009-12/msg01264.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2009-12/msg01264.html) I added address="0.0.0.0" to my tomcat connector but still don't know which of last night's updates caused the change in behavior.

---

