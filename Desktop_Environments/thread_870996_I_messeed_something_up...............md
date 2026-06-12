---
title: "I messeed something up.............."
date: 2008-07-26
forum: Desktop Environments
---

### Post by fluhartz on 2008-07-26
Hello All,

I am new to Linux and I really enjoy the OS...  I have been able to customize it to look look really cool and I love a lot of the features...BUT.

I tried installing Google Earth just for the heck of it and now I just want of get rid if it/fix what ever i did.
Fist off I couldn't even get it to work, I downloaded it and when I try to run it I get  [COLOR="Red"]Failed to execute child process.."googleearth" No such directory.[/COLOR]..  I put a screen shot in here.

It then says I have an update, and it is for Google Earth.  When I try to do the update I get another error... Something about dpkg was interrupted..  I put another screen shot in for it...  I serched and tried to do what this thread suggested..[http://ubuntuforums.org/showthread.php?t=388348](http://ubuntuforums.org/showthread.php?t=388348)...... and no dice..

It is like it isn't even installed... How do I just totally get rid of it from my system?
I would like to go back to the way it was before I even tried this....

Any help will be very much appreciated....
Thanks in advance....
Flu

---

### Post by pytheas22 on 2008-07-26
How did you install Google earth?  If you used the repository, then:
```

sudo apt-get remove --purge google-earth
```

should get rid of it.

To fix dpkg, try:
```

sudo dpkg --configure -a
```

Does it help?

---

### Post by fluhartz on 2008-07-26
pytheas22,

I found it on the forum...someone explaining how to install it.  I just tried the "sudo dpkg --configure -a" again and it seemed to fix my problems.

The Google Earth update worked this time... It is working now, so I might keep it for a while...

Thanks for your help.
Flu

---

