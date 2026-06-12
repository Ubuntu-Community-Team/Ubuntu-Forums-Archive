---
title: "Ubuntu 22.04 - Settings -&gt; Online Accounts -&gt; Google is blurry"
date: 2022-06-24
forum: Desktop Environments
---

### Post by nathan-gautrey on 2022-06-24
Hey,

Trying to setup my Google Online account in Ubuntu - Settings -> Online Accounts -> Google however as you can see from the screenshot it is unreadable.

Any thoughts on how to fix / troubleshoot this?

Running Ubuntu 22.04 all updates on a Pi 4 with Gnome / wayland.

Have tried various simple things like reboots and updates etc...

---

### Post by TheFu on 2022-06-26
Because nobody else has posted, I'll throw out the idea that google started mandating Oauth2 authentication be used this June.  The normal method to authenticate with OAuth2 is through a website controlled by google, in this situation.  That means any prior automatic connection possibility has been removed.

Complain to google.

I haven't check gmail this month, since Oauth2 was mandated.  For years, I only kept gmail accounts for security, privacy research and because they are mandated to access the google-app store on Android.  For the last 10 yrs, I've been replacing google services with less intrusive options and self-hosting everything I can to improve privacy.  Not everyone feels the same, but I can still access my email and my file servers and my read-it-later server and my nextcloud server with whatever authentication I prefer - including OAuth or userid/password or PKI.  It is up to me to decide, not somebody else.

---

### Post by deadflowr on 2022-06-26
It's more likely a wayland issue.
Try switching to an Xorg session.
Should have an option at login to switch sessions.

(To switch sessions at the login screen,
typically you first select the user, 
before entering the password look to the bottom right corner.
In the bottom right corner should be an cog-like icon.
Click on the cog to open the dropdown menu.
It should show options for Ubuntu and Ubuntu on Xorg.
select Ubuntu on Xorg, and maybe click the cog again to close.
Then enter the password as usual.)

See if that helps.
Or make sense.

Note, I do not have a pi so I do not know what sessions it would have available.
I would ant to assume it has both available, but I just don't know.

---

