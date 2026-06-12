---
title: "kde or gnome"
date: 2008-06-29
forum: Desktop Environments
---

### Post by potatopuff on 2008-06-29
is it possible to switch ubuntu to kde and is it worth it?

---

### Post by FFighter on 2008-06-29
Yes, it is possible. Just google it and you'll find some good tutorials.

KDE4 is a really good DE in my opinion. But I'm too used to Gnome and I'm lazy, so I just keep using Gnome. I'm considering XFCE though, which is very similar to Gnome but much lighter and faster. KDE4 is fast and great, but sucks up much more memory and CPU cycles than Gnome and XFCE.

---

### Post by Spaceman9 on 2008-06-29
The short answer is yes. Take a look at these threads 

[http://ubuntuforums.org/showthread.php?t=809318](http://ubuntuforums.org/showthread.php?t=809318)

[http://ubuntuforums.org/showthread.php?t=844472](http://ubuntuforums.org/showthread.php?t=844472)

[http://ubuntuforums.org/showthread.php?t=843344](http://ubuntuforums.org/showthread.php?t=843344)

[http://ubuntuforums.org/showthread.php?t=844020](http://ubuntuforums.org/showthread.php?t=844020)

[http://ubuntuforums.org/showthread.php?t=842683](http://ubuntuforums.org/showthread.php?t=842683)

I installed KDE into Ubuntu cus of Krusader and other cool stuff in KDE that does more then the stuff in Gnome. One of the best things about linux is that it doesn't have to be one or the other, it can be everything you want. I install Gnome and KDE into all of my distros. Xfce is a good desktop too.

---

### Post by kaldor on 2008-06-29
sudo apt-get install kubuntu-desktop

I think that's the command. If you want a stable DE, do NOT get KDE4... still too restrictive and buggy. Just use KDE 3.5 which is what you get with that command. I prefer it over Gnome. Easier to customize :)

---

### Post by jeremy1138 on 2008-06-29
> **FFighter said:**
> Yes, it is possible. Just google it and you'll find some good tutorials.

KDE4 is a really good DE in my opinion. But I'm too used to Gnome and I'm lazy, so I just keep using Gnome. I'm considering XFCE though, which is very similar to Gnome but much lighter and faster. KDE4 is fast and great, but sucks up much more memory and CPU cycles than Gnome and XFCE.

I've been wondering about this too.  Is it possible to have both gnome and kde installed and switch between the two at startup or whatever?  Thanks!

---

### Post by aysiu on 2008-06-29
> **jeremy1138 said:**
> I've been wondering about this too.  Is it possible to have both gnome and kde installed and switch between the two at startup or whatever?  Thanks!
Yes, it's possible. Follow these instructions:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by nsramkishen on 2008-06-30
I have KDE installed along with Gnome. KDE works fine; in fact the UI is better than Gnome. The only problem I am facing is this: To shut down the system, I have to log off (from either Gnome or KDE) and select 'Shut Down' from the Login window. Can somebody tell me how to shut down without logging off from the currently used desktop environment?

Another minor glitch is, when I wanted to install the Kubuntu Desktop, I ended up installing both KDE and KDE4. Now, which is related to Kubuntu? I don't want to retain both.

---

### Post by Tomatz on 2008-06-30
> **nsramkishen said:**
> I have KDE installed along with Gnome. KDE works fine; in fact the UI is better than Gnome. The only problem I am facing is this: To shut down the system, I have to log off (from either Gnome or KDE) and select 'Shut Down' from the Login window. Can somebody tell me how to shut down without logging off from the currently used desktop environment?

Another minor glitch is, when I wanted to install the Kubuntu Desktop, I ended up installing both KDE and KDE4. Now, which is related to Kubuntu? I don't want to retain both.

```
sudo shutdown -h now
```

---

### Post by katiad on 2008-06-30
> **nsramkishen said:**
> I have KDE installed along with Gnome. KDE works fine; in fact the UI is better than Gnome. The only problem I am facing is this: To shut down the system, I have to log off (from either Gnome or KDE) and select 'Shut Down' from the Login window. Can somebody tell me how to shut down without logging off from the currently used desktop environment?

Another minor glitch is, when I wanted to install the Kubuntu Desktop, I ended up installing both KDE and KDE4. Now, which is related to Kubuntu? I don't want to retain both.

Odd. When you go to logoff, it doesn't just give you the option to shutdown instead? In both gnome and kde, I can choose to log off, change user, restart, or shutdown without ever going back to the main login screen. 

KDE4 is still pretty restricted and unstable enough not to use it. You want KDE 3.5.x. But both are related to Kubuntu - it's just giving you the option to use either the brand new KDE4 or the older, stable, more widely used KDE 3.5. Both are KDE. One is just newer.

---

### Post by nsramkishen on 2008-06-30
> **katiad said:**
> Odd. When you go to logoff, it doesn't just give you the option to shutdown instead? In both gnome and kde, I can choose to log off, change user, restart, or shutdown without ever going back to the main login screen. 

The Logoff screen doesn't display the Shutdown icon after I installed KDE. I want to know how to get it back.:confused:

> **katiad said:**
> KDE4 is still pretty restricted and unstable enough not to use it. You want KDE 3.5.x. But both are related to Kubuntu - it's just giving you the option to use either the brand new KDE4 or the older, stable, more widely used KDE 3.5. Both are KDE. One is just newer.

Thanks for this info, but now I want to uninstall KDE4 without affecting the earlier KDE.

---

### Post by nsramkishen on 2008-06-30
> **Tomatz said:**
> ```
sudo shutdown -h now
```

Thanks; now, I will have to link this command to an icon and place the icon in the Logoff window so that my wife can log off without landing on the Terminal. I am wondering what happened to that icon after I installed KDE:confused:

---

### Post by Tomatz on 2008-06-30
> **nsramkishen said:**
> Thanks; now, I will have to link this command to an icon and place the icon in the Logoff window so that my wife can log off without landing on the Terminal. I am wondering what happened to that icon after I installed KDE:confused:

You could do this to create a script:

**Open a terminal and copy and paste these commands...**

```
sudo touch /usr/bin/killmykde
```
```

sudo gedit /usr/bin/killmykde
```

**copy and paste the following into the file:**

```
kdsu shutdown -h now
```

**SAVE** the file

**now go back to the terminal and copy and paste the following:**

```
sudo chmod a+x /usr/bin/killmykde
```


Now create a panel launcher using the command **killmykde** you should be able to give it a nice powerbutton icon ;)

---

### Post by nsramkishen on 2008-07-01
Tomatz, do I need to create a *killmygnome* command if I am using Gnome and want to shut down the system? Is there no other way to get the Shutdown icon back on the Logout window, irrespective of the desktop I am using?

---

### Post by Tomatz on 2008-07-01
> **nsramkishen said:**
> Tomatz, do I need to create a *killmygnome* command if I am using Gnome and want to shut down the system? Is there no other way to get the Shutdown icon back on the Logout window, irrespective of the desktop I am using?

So you cant shutdown gnome either? I thought it was just kde that was the problem.

---

### Post by ramaswamyps on 2008-07-01
try alt+ctl+bkspace keys combination.
it should get you to login screen.

alt+ctl+F1 will get you to console login
root login and shutdown/powerdown/halt you can do.

---

### Post by nsramkishen on 2008-07-02
I found a solution (well, sort of) to this. I made *gdm* as the default desktop manager (insted of kdm) and restarted the machine. Now, I can shut down and restart.

This thread ([http://ubuntuforums.org/showthread.php?t=95275](http://ubuntuforums.org/showthread.php?t=95275)) helped me change the desktop manager.

---

