---
title: "X-lite asterisk help for a n00b - please!!"
date: 2009-02-12
forum: General Help
---

### Post by andonato on 2009-02-12
Hi, I'm still something of a noob, so please bear with me. I'm trying to get x-lite (2.0) up and running on my hardy installation. I have it installed and it runs fine. I have a SIP account through Apptix (appnat.onvoip.net). I can login and connect a call, but the problem is I only have one way audio. The person I'm calling can hear me, but I can't hear them. I can hear the dialtone and the keystrokes, so I know my speakers are working. I think this may have something to do with asterisk, but I'm not sure. I know I do not currently have asterisk installed (to be honest, I'm not really sure what it's for - told you I'm new at this). Or I'm also thinking this could be a firewall or port forwarding issue, but again, I have no clue where to start with that. Any suggestions are appreciated - this is really driving me nuts.

---

### Post by adalal on 2009-02-20
Assuming that you're behind a NAT (and/or firewall), you need to allow the SIP port (5038 by default i think) to be forwarded to your computer. And if you're running a firewall, you need to allow inbound connection on the SIP port as well!

---

### Post by andonato on 2009-03-02
> **adalal said:**
> you need to allow the SIP port (5038 by default i think) to be forwarded to your computer. 

This worked, thanks!

---

