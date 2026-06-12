---
title: "Compiz not working"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by MonsterDuc on 2007-06-23
Newbie alert...

Ok, so I am new to this and installed Ubuntu only a few weeks ago.  Couple days ago I followed the sticky post instructions for installing Compiz.  I did this while the laptop was connected to my Samsund DLP bigscreen TV.  It looks nice, although the resolution was not that great.  I then disconnected from the DLP and used the laptop standalone.  I rebooted the laptop and now I don't have any of the features of Compiz enabled (i.e. can't use ctrl+shif combinations or super key combinations anymore.  Not even moving the mouse to the top right corner tiles my windows anymore).

What are some basic things I should be checking?

Thanks for any help!

Monster

---

### Post by llamakc on 2007-06-23
Did you set up compiz to run after logging in to a new session? Sounds like you just need to run it.

compiz --replace &

emerald --replace &

---

### Post by MonsterDuc on 2007-06-23
>  	Did you set up compiz to run after logging in to a new session? Sounds like you just need to run it.

compiz --replace &

emerald --replace &

Thanks for the quick feedback.  Yes, that was what I was missing :)  (I even figured it out myself!!).  Running sudo compiz --replace gives me this though:
> 
XXX@XXX:~$ sudo compiz --replace
Password:
Adding plugin resizeinfo (resizeinfo)
Adding many more plugins...
Adding plugin cubereflex (cubereflex)
Backend     : ini
Integration : true
Profile     : default
Initializing core options...done
Initializing move options...done
Initializing resize options...done
Initializing zoom options...done
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
Initializing wobbly options...done
Initializing fade options...done
Initializing cube options...done
Initializing switcher options...done
Initializing expo options...done
Initializing rotate options...done
Initializing scale options...done
Initializing cubereflex options...done
Active Plugin List update

The replace never exits and just sits at the Active Plugin List Update.  Not sure what is happening here.  If I control+c out of it it hoses my current session and my open windows only the terminal is usable.  I can use the environment just fine as long as I leave the terminal in that state.

Also, how can I add the compiz --replace to start when I logon?

Thanks!!

---

### Post by llamakc on 2007-06-23
You should not be running that command with "sudo". Leave "sudo" off.

---

### Post by MonsterDuc on 2007-06-25
Quick update to wrap the thread.

Ended up reinstalling as I screwed up something else, and I wanted to go through the complete setup from scratch again.  

I now have the desktop I always wanted :)

Thanks!

---

