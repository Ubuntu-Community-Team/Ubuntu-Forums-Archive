---
title: "nm-applet not appearing on panel"
date: 2013-11-07
forum: Desktop Environments
---

### Post by Roberto.Lionello on 2013-11-07
Hello, 

I am running Ubuntu 13.10 with the Mate desktop environment on my laptop. I noticed that, although the network manager applet /usr/bin/nm-applet is listed in the startup applications, the familiar icon with the bars does not appear on the panel. I need to launch nm-applet manually in order for the icon to appear and to be able to see the different wireless network available at my location. How can I make nm-applet appear whenever I log in? Thank you!):P

---

### Post by Roberto.Lionello on 2013-11-08
I fixed it myself. The file /etx/xdg/autostart/nm-applet.desktop has this line
AutostartCondition=GNOME3 unless-session gnome

So I put a copy in my directory

/home/lionel/.config/autostart/

with that line commented out. Now the network manager starts whenever I log in. :)

---

### Post by vasa1 on 2013-11-08
Thanks for taking the trouble to come back and answer your own question and mark it "Solved" :)

---

### Post by Roberto.Lionello on 2013-11-08
You're welcome! We are all here to help each other, after all. :-)

---

### Post by mrfabulous on 2014-04-05
> **Roberto.Lionello said:**
> You're welcome! We are all here to help each other, after all. :-)
Worked!!!!!!

---

### Post by dafyddabiago on 2015-03-23
> **Roberto.Lionello said:**
> I fixed it myself. The file /etx/xdg/autostart/nm-applet.desktop has this line
AutostartCondition=GNOME3 unless-session gnome

So I put a copy in my directory

/home/lionel/.config/autostart/

with that line commented out. Now the network manager starts whenever I log in. :)


Thanks for this.
There's a small typo.
Actually, you should open 

/etc/xdg/autostart/nm-applet.desktop    

In Linux Mint 17.1 (Ubuntu 14.10, right?)

I did:

```
sudo gedit /etc/xdg/autostart/nm-applet.desktop
```

And then just changed true 

NoDisplay=true

to 

NoDisplay=false

Works for me now.

---

### Post by bapoumba on 2015-03-23
regarding graphical programs run as root, please have a look here :
[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)
[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832) and in particular : [http://ubuntuforums.org/showthread.php?t=2225832&p=13032745#post13032745](http://ubuntuforums.org/showthread.php?t=2225832&p=13032745#post13032745)

---

