---
title: "3 problems :( [not working menu button, vsftpd, 'make' command]"
date: 2006-06-06
forum: Desktop Environments
---

### Post by ForceAbuser on 2006-06-06
ok first RESPECT on the new 6.06 release of (x)ubuntu!!!

now my 3 problems...

1)
i installed some extra packages on my xubuntu machine (multimedia, make, vsftpd, NL language), but now my "start" button doesnt work anymore :(, i think the problem is that somehow the XML file of the menu is erased.
does anyone have a idea where to find a backup for this XML file, or does anyone have clue how to solve the menu again?

2)
i've installed vsftpd trough the syntaptic tool, and now i want to configure it, my guess is that i have to text edit some configuration files, but where do i find those? and is there a GUI available for this program, or even another program with a GUI?

3) (ubuntu related, on my 2nd UBUNTU machine)
i tried to follow [this]("http://www.xs4all.nl/~pschram/") guide on 'how to make the alcatel speedtouch 330 usb modem work' (in dutch), and i come upon these commands:
```

cd /tmp/speedtouch/
./configure
[B]make
make install[/B]

```
now the problem is, that nothing happens when i type 'make'....

so does anyone now how to fix this? or does anyone now another command/trick that can help me out? 
(apt-get or synaptic doesnt work for me yet, since that i still have to setup my modem drivers)

---

### Post by nerkman on 2006-06-06
Same thing happened here.  I even went into backup mode, and voila!  No more menu after changing some settings.

Arrrrgghhh.

---

### Post by ForceAbuser on 2006-06-06
so....

anyone who can help me out?

---

### Post by pradeep79 on 2006-06-06
I had the same problem some time ago. This is a known issue as per xubuntu site. When you try to run menu-editor tool this happens. I did run that tool and no more menu button. There solution is to remove ~/.config/xfce4/desktop/menu.xml, log out from Xfce and then log in again. I did  that and still no luck.

The menu file is in /etc/xdg/xfce4/desktop/menu.xml. I even tried giving this as the path to execute when you click the menu button, but still no luck. When you right-click the munu button you get the option to change this configuration. I think the menu button is not responding to the click. If anyone finds the solution please post it.

---

### Post by pradeep79 on 2006-06-06
I found the answere in the following link, haven't tries yet but hope it helps you:p 

[http://www.ubuntuforums.org/showthread.php?t=184984](http://www.ubuntuforums.org/showthread.php?t=184984)

---

