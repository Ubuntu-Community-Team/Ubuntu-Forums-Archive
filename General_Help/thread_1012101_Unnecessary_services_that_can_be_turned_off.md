---
title: "Unnecessary services that can be turned off?"
date: 2008-12-15
forum: General Help
---

### Post by tegwilym on 2008-12-15
I have one of my linux machines at home (8.04) running in my basement on a DMZ port so I can reach it from outside.  
I have no firewall on it, but since it's not a Windows machine, it just keeps running, and running without any problems. 

I recently got an email from Comcast saying that they detected that there was spammming happening on my account.  Funny, I got that email just after I got my girlfriends Hotmail account working again in Outlook Express!

I would like to try increasing the security of my Linux machine just in case it's been compromised.  Anyone know what services can be turned off and still have it functional?  
Or do I just set up the Firestarter firewall?  

I guess I'll admit that I haven't worked much with firewalls, so maybe that is where I should start. 

This computer is just my "expermental" box, so trashing it and starting over isn't a problem.   Especially when Ubuntu can install in just a few minutes!

Tom

---

### Post by gTinker on 2008-12-15
[QUOTE=tegwilym]I have one of my linux machines at home (8.04) running in my basement on a DMZ port so I can reach it from outside.  
I have no firewall on it, but since it's not a Windows machine, it just keeps running, and running without any problems.[/QUOTE]

Since you mention it is in a DMZ, that would presumably be done by the router which probably does have a firewall working. You had to forward a port to it for access didn't you? 

Hopefully you're logged in with a limited user (one without sudo rights).

[QUOTE=tegwilym]
I recently got an email from Comcast saying that they detected that there was spammming happening on my account.  Funny, I got that email just after I got my girlfriends Hotmail account working again in Outlook Express![/QUOTE]

Are you running a mail server? Or is your box compromised by someone else running a mail server on it? What exactly does Comcast mean by "spammming (sic) happening"? Or are they just referring to someone using your spoofed return address?

[QUOTE=tegwilym]
I would like to try increasing the security of my Linux machine just in case it's been compromised.  Anyone know what services can be turned off and still have it functional?  
[/QUOTE]

On a Internet connected machine run only the services you need. If it's been compromised, nothing but a complete restore from known good backup will be sufficient. "Functional" depends on what you want it to do.

---

### Post by tegwilym on 2008-12-15
I my router will allow an assigned IP address through the DMZ.  I have a static IP On that machine so it doesn't change on me.

I probably have hole open with the user, I use my own account to get in there, and am able to sudo whatever I want. 

No mail server is running on it.  As for Comcast, they kind of sent me a pretty vague email that didn't say much other than reminding me to update my antivirus software.  It may be my girlfriend's computer since she's running XP and Outlook Express.  
I did get this email from comcast before, and they ended up changing the port on my email to 587 (or something like that).  Seems to be a common thing since there is info on a FAQ on Comcast's site. 

Anyway, this is just an experimental computer that I beat up on a lot, so formatting and starting over isn't a problem if I need to do that.  Hey, an install of Ubuntu only takes about 15 minutes unlike Windows....bleah!

tom



> **gTinker said:**
> Since you mention it is in a DMZ, that would presumably be done by the router which probably does have a firewall working. You had to forward a port to it for access didn't you? 

Hopefully you're logged in with a limited user (one without sudo rights).



Are you running a mail server? Or is your box compromised by someone else running a mail server on it? What exactly does Comcast mean by "spammming (sic) happening"? Or are they just referring to someone using your spoofed return address?



On a Internet connected machine run only the services you need. If it's been compromised, nothing but a complete restore from known good backup will be sufficient. "Functional" depends on what you want it to do.

---

