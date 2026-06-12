---
title: "Empathy Reporting that &quot;Google Talk account requires authorisation&quot;"
date: 2014-05-18
forum: Desktop Environments
---

### Post by pgn674 on 2014-05-18
I am running Ubuntu 14.04 with GNOME 3 (gnome-keyring-daemon is 3.10.1) and Empathy 3.8.6. In Empathy, I get an error saying "Google Talk account requires authorisation". If I hover my mouse over the error, a popup says "Network error". There is a button next to the error, which says "Online Accounts". If I click that button, the GNOME All Settings > Online Accounts dialog comes up. In there, I see my Google account that I had added, and there is no error displayed.

I ran empathy-debugger, and the below output seems relevant.
```
wocky/-DEBUG: 05/18/2014 17:52:51.412265: _end_element_ns: Received stanza
* features xmlns='http://etherx.jabber.org/streams'
    * mechanisms xmlns='urn:ietf:params:xml:ns:xmpp-sasl'
        * mechanism
            "X-OAUTH2"
        * mechanism
            "X-GOOGLE-TOKEN"
        * mechanism
            "PLAIN"
gabbleauthentication-DEBUG: 05/18/2014 17:52:51.412463: gabble_server_sasl_channel_start_auth_async (server-sasl-channel.c:836): Starting authentication
...
wocky/-DEBUG: 05/18/2014 17:53:51.574095: auth_failed: wocky-sasl-auth.c:274: Authentication failed!: Client aborted authentication.
gabbleconnection-DEBUG: 05/18/2014 17:53:51.574134: connector_error_disconnect (connection.c:1764): Interactive authentication error, reason 3, dbus error org.freedesktop.Telepathy.Error.AuthenticationFailed
```

The full log can be seen here: [http://pastebin.com/zMdMzc5Z](http://pastebin.com/zMdMzc5Z)

This feels like it's a problem with GNOME's Online Accounts rather than with Empathy (which is why I'm posting here), but I don't know where to find GNOME's logs for this.

My Google account has 2-step verification enabled. If I remove the Google account from Online Accounts, then re-add it, Empathy starts working again. But then Empathy breaks again on the next reboot.

Does anyone know what might be going on or any way to fix this? Or, are there more logs you need, or is there somewhere else I should go ask? Thanks.

---

### Post by captainskyhawk on 2014-05-22
Just wanted to report -- I'm having the same issue.  The only IM client that seems to work with Empathy post the 14.04 upgrade is AIM -- both Facebook and Google Talk no longer seem to work.  No errors are reported by the application -- they're just not appearing.  I don't have two-factor authentication turned on for either account.

---

### Post by chirag.goel25 on 2014-06-14
Reply #2 on the following link worked for me:
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1164939](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/1164939)

---

### Post by pgn674 on 2014-06-19
Thanks chirag.goel25. I tried that, but it didn't work. After a reboot, the problem comes right back.

---

### Post by pgn674 on 2014-06-20
Update: I've found that the command below will make the Google account work again until the next reboot. I'm trying it out different ways, and once I have a good work around, I'll post it here.
```
killall signond
```

---

### Post by davide-3 on 2014-09-11
> **pgn674 said:**
> 
```
killall signond
```

This worked for me too.

---

