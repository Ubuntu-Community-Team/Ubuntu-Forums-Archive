---
title: "Where is System-&gt;Administration in Kubuntu?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Louisvdw on 2005-11-09
Where do I find System->Administration in Kubuntu? I need to get to the Login Screen Setup to Enable XDMCP to use VNC server. (thread [http://www.ubuntuforums.org/showthread.php?t=76638](http://www.ubuntuforums.org/showthread.php?t=76638))

---

### Post by shakin on 2005-11-09
[QUOTE=Louisvdw]Where do I find System->Administration in Kubuntu? I need to get to the Login Screen Setup to Enable XDMCP to use VNC server. (thread [http://www.ubuntuforums.org/showthread.php?t=76638](http://www.ubuntuforums.org/showthread.php?t=76638))[/QUOTE]

I'm not sure how to do what you want, but the KDE equivalend is the System Settings app. Kcontrol will also do it. System Settings is the default in Breezy. For me it's right in the K Menu without opening a submenu, but I'm not sure if that's the default or something I did.

---

### Post by Louisvdw on 2005-11-09
Thanks. I saw that but it does not quite have the settings I'm looking for. Will look around in there. Maybe it's under my nose and I can't see it.

---

### Post by mod187 on 2006-06-26
I think you were wanting to enable to vnc? 
In K menu, go to 'System Settings'

Under Internet & Network, goto 'Sharing'

Under Desktop Sharing, goto access. 
Check 'Allow uninvited connections'
Uncheck 'Confirm uninvited connections before accepting'
(If you leave this checked, when someone tries to connect, a window will pop-up and ask you if this is ok. If you are setting this up for remote management, you will not be there to ok the connection!)
Check 'Allow uninvited connections to control the desktop'
Set a password

Under the Network tab: 
Select the correct port number you need.

If this wasn't for vnc, then, sorry...
I hope this helps!

---

### Post by whatalotta on 2006-09-06
Well, I was looking for a good VNC solution to be able to see my desktop while at work.  I followed your advise.  I'll let you know tomorrow how it turned out when I get to work.

-whata

---

