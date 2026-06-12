---
title: "Hotmail in Thunderbird"
date: 2009-01-21
forum: General Help
---

### Post by tegnoto89 on 2009-01-21
Can somebody help me set this up?  I've tried two tutorials online, and neither of them worked.

---

### Post by jrusso2 on 2009-01-21
It used to work with Webmail addon and the hotmail add on.  But it stopped working around the time Microsoft made some changes so outlook express users could no longer access hotmail.

This occurred on every PC I have even the Windows ones.

---

### Post by meho_r on 2009-01-21
Well you should check again. I'm still using Thunderbird with [Webmail]("http://webmail.mozdev.org/") for Hotmail and Yahoo and everything is working fine.

---

### Post by tegnoto89 on 2009-01-21
Okay, one specific issue I'm having is accessing the webmail preferences.  I installed the add on by saving it to my computer, then installing it through Thunderbird.  Now what?

---

### Post by meho_r on 2009-01-21
Here's complete procedure:

1. Install main webmail plugin and then the one for hotmail.

2. In TB Tools > Add-ons > Webmail set POP and SMTP ports to some numbers above 1024 (i.e. 1110 for POP, and 1111 for SMTP); close and restart TB, and then check if Webmail states "Running" for POP and SMTP.

3. Set your mail account through standard procedure (Edit > Account Settings > Add Account), but in "Incoming Server" put **localhost**, and in "Incoming username" your full mail address (that is WITH @hotmail.com or @live.com).

4. Go to Edit > Account Settings again and in the "Server Settings" for the created account set the port for POP Server to the same number as in Webmail (i.e. 1110).

5. In the "Outgoing Server (SMTP)" in "Account Settings" (on the bottom) create new SMTP Server, in "Server Name" put **localhost**, "port" should be the same as in Webmail (i.e. 1111), and "Username" should be your full mail address.

6. Make sure that just created SMTP Server is used: click on your account name in "Account Setting" and check if it uses correct SMTP server (on the bottom).

---

### Post by tegnoto89 on 2009-01-21
Perfect.  Thanks so much!

---

### Post by slimx3m on 2009-02-16
thnx for the little tutorial it was really helpful :D

---

### Post by SamNSane on 2009-02-17
Depending on where you live the following link may provide an alternative for folks having problems with Webmail/Hotmail extensions:

[https://windowslivehelp.com/solutions/settings/archive/2009/01/13/pop3-availability-in-windows-live-hotmail.aspx](https://windowslivehelp.com/solutions/settings/archive/2009/01/13/pop3-availability-in-windows-live-hotmail.aspx)

I've been using Webmail/Hotmail extensions for some time. They periodically get broken so users have to update the extensions, or sometimes we just have to switch between using WebDAV and the "new Hotmail" settings in the Hotmail extension.

I haven't tried the use of the POP3 procedure with Hotmail yet. I probably will the next time Webmail stops working for me.

---

### Post by tegnoto89 on 2009-02-18
Hm, yes I've noticed that hotmail in thunderbird recently stopped working (I began getting a "negative vibes" message).  I'll try to update the extension; Though I think last time it failed for some reason.

---

### Post by bertles86 on 2009-07-12
I'm having problems, the webmail extension won't install with Thunderbird 3. Can anyone help me get it to work?

---

