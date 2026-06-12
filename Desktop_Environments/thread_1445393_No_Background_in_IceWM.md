---
title: "No Background in IceWM"
date: 2010-04-02
forum: Desktop Environments
---

### Post by sopranojam85 on 2010-04-02
This is just annoying - I've got no background desktop image in IceWM.

I've got Ubuntu 9.10 PowerPC installed. I did a bare-bones installation of Ubuntu, and installed the latest version of IceWM.

To make this work properly, I edited /etc/X11/default-display-manager to have no code whatsoever, so I just manually boot up, and type "startx."

To point startx to IceWM, I edited /etc/X11/Xsession to just say "exec icewm-session"

IceWM comes up, and does stuff that I need it to, but I can't for the life of me figure out how to configure a desktop background.

I've edited /home/myname/.icewm/preferences to say 
```
# Desktop background image
DesktopBackgroundImage="/home/myname/Downloads/IMG_1672.jpg"
```

This is a valid file path, and the image is displayed fine in Nautilus.

I've verified that /usr/share/xsessions/IceWM.desktop has the line 
```
Exec=/usr/bin/icewm-session
```
in it.

What the heck am I doing wrong here?

---

### Post by NightwishFan on 2010-04-02
Here is a link with some nice help on IceWM. (Scroll past the installation stuff)
[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

Also these threads:
[http://ubuntuforums.org/showthread.php?t=355541](http://ubuntuforums.org/showthread.php?t=355541)
[http://ubuntuforums.org/showthread.php?t=812627](http://ubuntuforums.org/showthread.php?t=812627)

---

### Post by sopranojam85 on 2010-04-05
Hello,

Thanks so much for the reply.

I did all of the suggestions in these articles. In fact, I'm sure that I found these threads before posting and tried those steps, to no avail.

I know that the image in question is viewable, as it shows up fine when I open it using feh.

I know that I have to be running icewmbg. But shouldn't icewm-session invoke that?

I opened the Icewm terminal and typed```
icewmbg
```

It then shows:
```
icewmbg: using /home/[username]/.icewm for private configuration files
```

Then nothing else happens. My cursor stays stationary on the far left, and I don't really know what the system is doing.

If I type ```
exec icewmbg
``` instead, same behavior.

I decided to open /home/[username]/.icewm/preferences, and comment out the desktop image line, and un-comment the desktop background color line, setting it to red, restarted IceWM, but no change - just black background.

Also, I have no desktop icons. The only way for desktop icons to appear is to launch Nautilus, which is painfully slow compared to PCManFM.


Any thoughts here?

---

### Post by Ibidem on 2010-05-03
Use PCManFM to do the background, then.
Edit-->Preferences-->Desktop
Then make a text file in <your home directory>/.icewm/, named "startup",  containing the line

pcmanfm&

Make the file executable (right-click-->"Properties" in PCManFM)

This will give you desktop background and icons.

---

