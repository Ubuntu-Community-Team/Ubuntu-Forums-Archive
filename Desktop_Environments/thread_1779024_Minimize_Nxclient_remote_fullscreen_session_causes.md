---
title: "Minimize Nxclient remote fullscreen session causes blank local display"
date: 2011-06-09
forum: Desktop Environments
---

### Post by redthor on 2011-06-09
I'm running nxfree to log into my remote xubuntu PC from my local xubuntu laptop since the X protocol was broken.

Has been working fine. Recently upgraded from Lucid 32bit to Maverick 64bit Xubuntu.

Now when I run nxclient in fullscreen mode, if I minimize the window (or just log out) my local display does not return.

I'm left with just the background colour. The windows are still there but not visible. For example I can:
* randomly right-click and a menu pertaining to the invisible window appears;
* press alt-tab and cycle through the windows but activating one does not display it (it remains invisible);
* press ALT-F and bring up the current active (but invisible) application file menu;

Basically I press ALT-F and ALT-TAB and close everything and then log out and log back in to restore the windows/panels.

Thanks for viewing my problem and thanks for X/Ubuntu !
cheers,
r

---

### Post by Toz on 2011-06-09
How is the client configured? What command are you using to start the xfce session. Have a look at: 
[http://ubuntuforums.org/showthread.php?t=1344881]("http://ubuntuforums.org/showthread.php?t=1344881") (problem looks similar)
and
[http://geekyprojects.com/general/manage-mythtv-remotely-with-nx/]("http://geekyprojects.com/general/manage-mythtv-remotely-with-nx/")

---

### Post by redthor on 2011-06-09
Cheers for the response.

Actually the remote machine is absolutely fine! It's working just as it always did.

It's the local display I'm having a problem with.

I connect to the remote host in fullscreen mode. Then if I minimize the nxclient locally everything is gone.

(If you still want my remove command it is /usr/bin/startxfce4 - that's all good)

I've tested going fullscreen with evince and ristretto image viewer.. but they're fine. It's something nxclient does when it goes full screen...

---

### Post by Toz on 2011-06-10
Sorry for the misunderstanding. Perhaps the compositor is the problem. Do you have it enabled?

---

