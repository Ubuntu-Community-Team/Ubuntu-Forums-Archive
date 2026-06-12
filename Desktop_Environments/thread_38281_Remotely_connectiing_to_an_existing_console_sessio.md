---
title: "Remotely connectiing to an existing console session"
date: 2005-05-30
forum: Desktop Environments
---

### Post by btdown on 2005-05-30
I left home with a session running on the console (with some apps running). While I am remote, is there a way to access THAT particular session while Im logged in with either Freenx or VNC or something? I notice when I log in via Freenx, it creates a whole new session and Im not sure how to connect to the session that may already running. Any ideas?
 
When I do a who, I get one of me on :0 (which I assume is the local session) and one of me on pts/1, which I assume is me on Freenx remote.
 
Any ideas?
 
Thanks!
BT

---

### Post by btdown on 2005-05-30
OK...I am a goober... I found that if I forwarded port 5900,  (which corresponds to display :0) to the box from the firewall, I can log into the existing running session.  Guess I should have played with it a while longer before I asked the question, huh?
 
BT

---

