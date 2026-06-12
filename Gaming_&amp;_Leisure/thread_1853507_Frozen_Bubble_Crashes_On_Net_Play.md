---
title: "Frozen Bubble Crashes On Net Play"
date: 2011-10-02
forum: Gaming &amp; Leisure
---

### Post by LonelyAspie on 2011-10-02
When I start up Frozen Bubble, it says connecting, then it crashes before it actually does, and does this every time.

I tried contacting the folks on the Frozen Bubble website, but no luck. I am using Ubuntu 11.04 (32 Bit).

---

### Post by donkyhotay on 2011-10-02
Try launching the game in CLI and post the crash dump.

---

### Post by LonelyAspie on 2011-10-03
What does you mean by CLI?

---

### Post by donkyhotay on 2011-10-03
> **LonelyAspie said:**
> What does you mean by CLI?

CLI = Command Line Interface - Terminal

Launch the game from terminal, it usually provides error information when a program crashes that helps with figuring out why it crashed. Copy/paste that information here.

---

### Post by LonelyAspie on 2011-10-03
"Problem with server jeux.ced117.net:1511: Could not create socket.
Can't call method "shutdown" on an undefined value at /usr/share/perl5/fb_net_discover.pm line 373."

---

### Post by donkyhotay on 2011-10-03
Are you trying to play it online? The error indicates it is failing when attempting to connect to a server. I just tried launching frozen-bubble myself and didn't have issues but I am also running 10.04 of ubuntu. It's possible the libraries may no longer be compatible. The version of PERL I have is 5.10.1 however the PERL website has 5.14.2, I'm not certain what version is in the 11.04 repositories. Post the results of
```

perl -version

```
Ultimately you will need someone else with version 11.04 to confirm whether or not this is a dependency issue or not. I couldn't find any bugs related to this in launchpad but that doesn't necessarily mean anything.

---

### Post by vikrant82 on 2011-12-18
Crashing here as well, on 5.14.2 (version of perl) in oneiric.

---

