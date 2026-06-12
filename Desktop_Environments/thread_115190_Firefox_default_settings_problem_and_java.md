---
title: "Firefox default settings problem and java"
date: 2006-01-10
forum: Desktop Environments
---

### Post by naruto11111 on 2006-01-10
Hi, I'm new to linux.  I've been working through all the setup and slowly learning.  

I upgraded to firefox1.5  but when I tried to set the hotkey for opening a browser, it opens the old version of firefox instead.

Also, I can't get java to work in firefox.  If there's any java applet in the page, it wont load.  I installed the sunjava package but it doesn't do anything.  I suspect it has to do with my system still having the old firefox as the default but I'm not sure.  

Any thoughts?  Thanks!

-Michael

---

### Post by harisund on 2006-01-10
A couple of things : 

1. Could you post the output of ```
which firefox
``` here? 
2. Do you know where you installed Firefox 1.5? 
3. Do you know where you installed Sun Java? 

Because you could do this 
```

sudo rm -f /opt/firefox/plugins/libjava*
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

```
if firefox is installed in /opt and java libraries are in the /user/lib/j2re1.5-sun folder

Of course, you could also search for libjavaplugin_oji.so in your file system and link it in the firefox plugins folder. 

Similarly you can change it by looking for keyboard shortcuts in the options somewhere (I am sorry, I am not quite used to the GUI, but for me the commands for java plugin did work)

---

### Post by irosenbl on 2006-01-11
Hello!
I am a complete novice so please bear with me...  I found out I could not successfully run applets that display graphics inside FIrefox. The output asks me to install additional plugins and when I try it knows it is missing Java Runtime Environment.  When I continue those steps and ask it to install it, it cannot find it.  
This thread looked to me like it was related so I tried the steps above and got:
sudo rm -f /opt/firefox/plugins/libjava*
Password:
mima@ubuntuPC:~$ sudo ln -s /usr/lib/j2rel.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins
ln: creating symbolic link `/opt/firefox/plugins' to `/usr/lib/j2rel.5-sun/plugin/i386/ns7/libjavaplugin_oji.so': No such file or directory

Idid:
mima@ubuntuPC:~$ which firefox
/usr/bin/firefox

By the way, I am working with the original install of Ubuntu version 5.04 and whatever Firefox came with it.

This is not urgent, but I would like to use Ubuntu and Firefox rather than Windows installed on my portable and so far doing all of this OK :-(

Thanks!
Isabel

---

### Post by irosenbl on 2006-01-11
Hello!
I am a complete novice so please bear with me...  I found out I could not successfully run applets that display graphics inside FIrefox. The output asks me to install additional plugins and when I try it knows it is missing Java Runtime Environment.  When I continue those steps and ask it to install it, it cannot find it.  
This thread looked to me like it was related so I tried the steps above and got:
sudo rm -f /opt/firefox/plugins/libjava*
Password:
mima@ubuntuPC:~$ sudo ln -s /usr/lib/j2rel.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins
ln: creating symbolic link `/opt/firefox/plugins' to `/usr/lib/j2rel.5-sun/plugin/i386/ns7/libjavaplugin_oji.so': No such file or directory

Idid:
mima@ubuntuPC:~$ which firefox
/usr/bin/firefox

By the way, I am working with the original install of Ubuntu version 5.04 and whatever Firefox came with it.

This is not urgent, but I would like to use Ubuntu and Firefox rather than Windows installed on my portable and so far doing all of this OK :-(

Thanks!
Isabel

---

### Post by harisund on 2006-01-11
The thing is, you need to know where Firefox is installed, and you need to know whether java is installed. 

Can you check both?

---

