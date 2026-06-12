---
title: "Empathy Facebook Authentication"
date: 2013-10-11
forum: Desktop Environments
---

### Post by phil-u on 2013-10-11
Hi,

I'm trying to get the Facebook Chat with Empathy to work. In Settings -> Online-Accounts I have successfully added my Facebook-Account using my Username (Not E-Mail Address). Ubuntu App has been granted all rights in Facebook and they are all enabled in Settings. When I try to connect with Empathy I get the message: Facebook-Account requires authentication.
I have already checked '/usr/share/accounts/providers/facebook.provider'. It already contains http as you can see here:

...
        <group name="user_agent">
          <setting name="AllowedSchemes" type="as">['https','http']</setting>
...

Is anyone else having problems at the moment or did FB change something? Are there any hidden settings in Facebook itself that have to be set to get it to work?
I'm on Ubuntu 13.04 using Empathy 3.6.4 which is already included in the System-Installation.


Thanks in advance

phil-u

---

