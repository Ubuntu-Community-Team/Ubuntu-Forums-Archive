---
title: "Cool beryl effect"
date: 2006-11-18
forum: Desktop Environments
---

### Post by hornett on 2006-11-18
Saw this on digg:
[http://digg.com/linux_unix/Cool_beryl_notification_effect_for_Linux](http://digg.com/linux_unix/Cool_beryl_notification_effect_for_Linux)

Looks great,but has anybody actually got it to work on Edgy?

Here's what I'm getting:
> $ ./waterPing.sh 0 0 
Applications can not close shared connections.  Please fix this in your app.  Ignoring close request and continuing.

Script available for copy/paste in the Digg comments, by "FloHimself".

---

### Post by ThrobbingBrain66 on 2006-11-18
asking questions on forums on the weekends is sort of a bummer cause not a lot of people are around, but i'd ask this at beryl-project.org, you may get a better/faster response.

---

### Post by d3v1ant_0n3 on 2006-11-18
That really is very cool! I wish I had pixel shaders :( no water effects at all for me.

The new 3d world plugin is very cool tho.

---

### Post by jackhynes on 2006-11-18
Could someone please post a step-by-step of how to do this? I made waterping.sh and put in it:

```
#!/bin/bash
#./waterping.sh 0 0
#If you want to ping the coordinates x0, y0
dbus-send --type=method_call --dest=org.freedesktop.beryl /org/freedesktop/beryl/water/allscreens/point org.freedesktop.beryl.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'` string:'amplitude' double:1 string:'x' int32:$1 string:'y' int32:$2
```

Then did:
```
sudo chmod a+x /home/jack/waterping.sh
```

Then made a link to the file under Configure Notifications in Kopete, in the Execute a program box.

But nothing happens, what have I done wrong?

---

### Post by spockrock on 2006-11-19
> **hornett said:**
> Saw this on digg:
[http://digg.com/linux_unix/Cool_beryl_notification_effect_for_Linux](http://digg.com/linux_unix/Cool_beryl_notification_effect_for_Linux)

Looks great,but has anybody actually got it to work on Edgy?

Here's what I'm getting:


Script available for copy/paste in the Digg comments, by "FloHimself".

I have the same error, I have no Idea why, I have beryl-dbus installed, but I dont see dbus in beryl-settings..... I edited the settings file to load dbus but still no dice.

---

### Post by KnevetS on 2006-11-19
If you run beryl-settings directly, do you get an error?

I get "can not load vtable from dbus.so" or something similar.  Seems like there's a problem with dbus in SVN - although I'm not sure what.

---

### Post by spockrock on 2006-11-19
yes, I was about to say that I get the same error, the error can be fixed if libdbus.so is recompiled..... how ever I get the error that dbus.h is not found, I do have libdubs-1-dev installed.  when I edit dbus.c with the full path to dbus.h, dbus.h then complains that it cant find the other dbus header files.......I dont think I should be editing header files..... anyone got any ideas.....??  for some reason I when compiling its not finding the /usr/include/dbus-1.0 folder......


ok I have it compiled.....it shows up in beryl-settings now, but it causes beryl to segfault. :(

---

### Post by KnevetS on 2006-11-20
I got dbus compiled and working - I ended up having to download the whole repository and compile it all together to make it work.

In beryl-dbus, I had to run autogen.sh, then ./configure --prefix=/usr
make
sudo make install

I still get the Applications can not close shared connections error, but dbus is working.

My 3d World plugin is not working anymore though. :(

---

### Post by KnevetS on 2006-11-20
I figured out how to do this in GAIM - 

add a "buddy pounce" under tools->buddy pounces.  

then run the process - /usr/local/bin/waterping.sh 0 0 

(or for me I like it as /usr/local/bin/waterping.sh 1230 20 )

I suppose you could quickly write a gaim plugin to do it for all users, but I don't have the inclination to read yet another API doc today :)

---

### Post by Thaigor on 2006-11-27
Sorry, I'm a noob here who's trying to get this water ping work as well ... 

after I run waterping.sh 0 0

I got

bash: /usr/local/bin/waterping.sh: /bin/bash'M: bad interpreter: No such file or directory



What can I do ?




Thank you

---

### Post by kopiluwak on 2006-12-02
How did you create your script? Looks like a ^M on the end from a Microsoft new line. 

vi /usr/local/bin/waterping.sh

then

:%s/(ctrl-v)(ctrl-m)//g
:w!

to get rid of them.






> **Thaigor said:**
> Sorry, I'm a noob here who's trying to get this water ping work as well ... 

after I run waterping.sh 0 0

I got

bash: /usr/local/bin/waterping.sh: /bin/bash'M: bad interpreter: No such file or directory



What can I do ?




Thank you

---

