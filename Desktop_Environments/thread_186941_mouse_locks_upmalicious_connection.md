---
title: "mouse locks up/malicious connection?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mad_phoenix on 2006-06-02
Howdy All,
  I've run into a very strange problem with Dapper for about the last week.  From time to time, the interface would just not respond to mouse clicks, either with the built-in trackpad on my IBM T30, or with an external usb mouse.  I found that no desktop widgets were active except for the last one I had clicked.  For example, if the last thing I had clicked on was the system clock when this occured, the only active widget on the desktop would be the system clock button.  Clicking furiously other places on the screen would eventually remedy this, or I would kill the X server and login again.  Then today, it happened again when I clicked on the Update button by the system clock.  This time, however, I actually got a message that popped up in a simple dialog box:

```

Could not grab your mouse.

A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus.

Try again.

```
The first thing I checked out was what ports were open on my system, since it mentioned a possible malicious client.  Netstat reports that smtp, www, mysql and ipp are active.  I dont believe any of these could be the source of a malicious client, at least not to take over the desktop.  This is a laptop machine, so somebody would have to be scanning me to see that, for example, Apache is running.  However, this has happened on both large networks, and on my home lan behind a firewall.

Has anybody else been having this problem, or possibly know what that cryptic error message means?  Any help would be greatly appreciated.  Thanks!

--mad_phoenix

---

### Post by Hugo Magic on 2006-06-05
I just installed xubuntu in my hp pavilion 513c and just like you said, I also try to click on the apps button and nothing happens. This happened after I played a bit with the system configuration. Does this mean that I have to reinstall xubuntu?

---

### Post by Hugo Magic on 2006-06-05
The only item that I'm able to click is firefox on the menu bar. 
Can this be a bug. And if it is will they fix it soon. 
Anyway, is there a way to inform the developers about these trobubles?

---

