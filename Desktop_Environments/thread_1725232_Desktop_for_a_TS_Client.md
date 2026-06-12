---
title: "Desktop for a TS Client"
date: 2011-04-09
forum: Desktop Environments
---

### Post by securitymeddler on 2011-04-09
Hey guys, 

So far I am loving Ubuntu , still very new though so I want to apologize up front if I ask anything silly. 

My job is currently an Windows XP shop for the most part. In spite of our efforts a malware breakout happened in our sales department and our CEO is finally on board with cleaning things up. We have several windows apps we are stuck on and WINE wouldn't work. But I went ahead and mentioned Linux anyway, to my shock he was interested having read about it recently. 

Also worth mentioning we lack desktop support staff so Virtualbox was out. It was just too complicated to the older ladies. 

We decided to go Microsoft's Terminal Server/RemoteApp server for cost and performance issues with our apps (Citrix XenApp wouldn't work). We purchased 10 ThinClients from HP running a Debian distro and we couldn't be happier. I can now centrally control everything. 

Rather than buy dozens more of these ThinClients I was hoping I could just install Ubuntu/Xubuntu on our old IBM desktops (p4/512ram/20gig) lock down the interface to just Firefox and a terminal server client (rdesktop I believe it's called?). 

How would I go about this? Are there any better options? 

thanks in advance,

---

### Post by whatspaz on 2011-11-29
> **securitymeddler said:**
> Hey guys, 

Rather than buy dozens more of these ThinClients I was hoping I could just install Ubuntu/Xubuntu on our old IBM desktops (p4/512ram/20gig) lock down the interface to just Firefox and a terminal server client (rdesktop I believe it's called?). 

How would I go about this? Are there any better options? 

thanks in advance,

For your particular case, I would do a few things. First I would make a custom session script that loads only parts of the desktop manager but without panels and so on. Instead of launching a regular navigable user interface, launch rdesktop instead.

This has more details about how you might do this.

[http://maketecheasier.com/customize-the-gdm-sessions-list/2010/08/08]("http://maketecheasier.com/customize-the-gdm-sessions-list/2010/08/08")

The next thing I would do is on the server side, I would edit at either the system-level or user-levels, the Winlogon\Shell registry key value to load only Firefox and set up Group Policy to further lock down the terminal. You may have to write a script that logs off the user whenever the Firefox app goes down. This would (hopefully) disconnect rdesktop and return you to the login screen.

This is how you set up different shells for different users.

[http://msdn.microsoft.com/en-us/library/ms838576(v=winembedded.5).aspx]("http://msdn.microsoft.com/en-us/library/ms838576(v=winembedded.5).aspx")

You may want to have a look at the upcoming FreeRDP v1.0. It now supports Remote Desktop Services RDS / Terminal Services TS RemoteApps, but it is still a little buggy for now. If you could get this to work instead of rdesktop, then you might not have to alter the Windows registry on the server and instead rely on the client to break the open window and then force it to log off from the session script.

Check out FreeRDP's web site and have a look at their wiki to find out how to get it to work:

[http://www.freerdp.com/]("http://www.freerdp.com/")

I have written a FreeRDP-GNOME integration script that might make it marginally easier to setup a RemoteApp launcher. My scripts are really more designed for integrating RemoteApps onto the GNOME Main Menu and for Nautilus association-based application launchers. Still, have a look, it may reveal some obstacles you may need to overcome on the client.

[http://www.daball.me/2011/11/windows-meet-linux-linux-meet-remoteapp.html]("http://www.daball.me/2011/11/windows-meet-linux-linux-meet-remoteapp.html")

---

