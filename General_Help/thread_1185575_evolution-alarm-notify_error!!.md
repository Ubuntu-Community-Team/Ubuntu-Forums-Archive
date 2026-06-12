---
title: "evolution-alarm-notify error!!"
date: 2009-06-12
forum: General Help
---

### Post by ade234uk on 2009-06-12
Wondering if someone could help me solve this weird error. Every so often a will get a warning appear on the screen

=========== ERROR BELOW ========
An error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.

======= AND CLICKING THE DETAILS BUTTON GIVES ME ============
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-8GFKPqutfI: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-8GFKPqutfI: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-8GFKPqutfI: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-8GFKPqutfI: Connection refused)

---

### Post by jward3010 on 2009-06-24
I'm using Karmic and after recent updates I'm getting the exact same thing, except longer error and I can't even get to the desktop - I login and within seconds I'm kicked out again back to login. When I login to terminal I get that message you're talking about.

---

### Post by r.g. on 2009-06-24
> **jward3010 said:**
> I'm using Karmic and after recent updates I'm getting the exact same thing, except longer error and I can't even get to the desktop - I login and within seconds I'm kicked out again back to login. When I login to terminal I get that message you're talking about.

Same behaviour here but no failure message in Terminal.
Can not login to desktop at all, only sometimes it stays for this failure pop-up message. After trying to click somewhere I'm kicked out again.

---

### Post by RobertoM on 2009-11-22
I have the same problem.  Can anyone help fix this?

---

### Post by DarkMerlin on 2009-11-23
I have this problem and i realy haven't any ideas how to solve her, please help me.

---

### Post by majikins on 2009-11-23
After ALOT of googling, came across this:

[http://810intrepid.wordpress.com/2008/11/09/a-rather-nasty-crash/#comments](http://810intrepid.wordpress.com/2008/11/09/a-rather-nasty-crash/#comments)

Solved it for me.

:popcorn:

Cheers

---

### Post by kvarley on 2009-12-25
> **majikins said:**
> After ALOT of googling, came across this:

[http://810intrepid.wordpress.com/2008/11/09/a-rather-nasty-crash/#comments](http://810intrepid.wordpress.com/2008/11/09/a-rather-nasty-crash/#comments)

Solved it for me.

:popcorn:

Cheers

Thank you so much for this. Worked a treat!

---

### Post by me13221 on 2010-03-10
Just for completeness, the fix seems to be to rename 'saved_state' in the .gconfd directory:

```

cd ~/.gconfd 
mv saved_state saved_state.old

```

Then you need to restart gnome (logout and log back in) for the change to take effect.

---

