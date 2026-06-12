---
title: "iceauth:  timeout in locking authority file"
date: 2005-12-02
forum: Desktop Environments
---

### Post by goodchild on 2005-12-02
The situation:

Unable to login to the default Gnome session from GDM; there is a slightly longer pause than usual and the system returns to GDM without giving an error message.

The Cause:

My desktop is gnome, but I have been using some KDE apps like K3B and amaroK.  I was using kcontrol to configure some of the global options:

1) Sound system (using ALSA)
2) The Components Chooser (set to use certain apps as default for functions; evolution for email, opera for web, gnome terminal as terminal)

Really, I was trying to avoid the "kfmclient" helper app as it doesn't exist on my system.  It was because I was clicking web links in amaroK and it didn't know to use Opera and kept whining.  Thus, setting Opera as the default Web Browser in kcontrol and setting the rest while I was around there.

And then problems.

I can still login into a terminal and from there launch things (like Opera, which is how I'm doing this right now).  However, it's pretty messed up as I have to do things like launch metacity manually.

Obviously, not workable.

The problem:

1) Immediatley, it's the KDE communications server, DCOP.  

```
 DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
iceauth:  timeout in locking authority file
```

2) Only guessing:  The damn double-speed clock problem (It's a laptop and I'm not turning off ACPI as I'm afraid that equals stupid).  It was probably too far ahead or something and was synchronized.  Things like this happen; sudo and gksudo either don't work or complain that timestamps are too far in the future.  Maybe this is similar?

I don't have a clue how to actively fix this.  I thought maybe I would just wait until the future when the time issue would have been solved simply because I sat there cursing the samn computer for a few hours.  This didn't work.

The Solution:

[Insert clever, well-informed and helpful ideas here]

---

