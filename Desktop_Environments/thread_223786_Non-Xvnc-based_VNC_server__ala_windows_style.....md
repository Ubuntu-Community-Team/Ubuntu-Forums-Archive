---
title: "Non-Xvnc-based VNC server?  ala windows style...."
date: 2006-07-26
forum: Desktop Environments
---

### Post by achillie on 2006-07-26
Greetings
[LIST]
[*] I just recently installed ubuntu. 
[*] I have many programs open and running that I need to connect to. 
[*] I recently installed TightVNC as was instructed to do. 
[*] Tightvnc works fine, except when launched it creates a new X server that allows me to connect, disconnect and reconnect. That's great
[*] The session running on the computer's physical monitor is separate from TightVNC's x server, (unless I vnc into the same machine )
[*] I'd like a vnc server that allows me access to my ?physical? x server...
[/LIST]
... a la what one would expect from running a vnc server in windows...

How may I accomplish such a task? Thank y'all in advance for this.

---

### Post by jimmygoon on 2006-07-26
> **achillie said:**
> Greetings[LIST]
[*] I just recently installed ubuntu.
[*] I have many programs open and running that I need to connect to.
[*] I recently installed TightVNC as was instructed to do.
[*] Tightvnc works fine, except when launched it creates a new X server that allows me to connect, disconnect and reconnect. That's great
[*] The session running on the computer's physical monitor is separate from TightVNC's x server, (unless I vnc into the same machine )
[*] I'd like a vnc server that allows me access to my ?physical? x server...[/LIST]... a la what one would expect from running a vnc server in windows...

How may I accomplish such a task? Thank y'all in advance for this.

WOW. I'm gonna be honest. I don't have a clue what you are talking about... but in case it is that you would like to VNC and see your current desktop? here are the instructions

Top Menu -> System -> Preferences -> Remote Desktop:
Check your desired options!

---

### Post by achillie on 2006-07-26
Wow, thanks, that's so much easier. I should beat some of the people on irc for what they put me through. Thanks a lot.

---

### Post by scxtt on 2006-07-26
vino (which is what "Remote Desktop" is) works fine, but i had issues w/ it not drawing the screen correctly (outside of my own network) -- if you have the same issue, you can install x11vnc to connect to your :0 session ... but if you're happy w/ vino, that's fine too :p

---

### Post by jimmygoon on 2006-07-26
> **scxtt said:**
> vino (which is what "Remote Desktop" is) works fine, but i had issues w/ it not drawing the screen correctly (outside of my own network) -- if you have the same issue, you can install x11vnc to connect to your :0 session ... but if you're happy w/ vino, that's fine too :p

Oh yea. By no means was I trying to say it was best... simply easiest. I hate how it renders the colors. Even on the same network ubuntu->ubuntu the coloring is off... and I have no idea why!!! I would like to see something else packaged with edgy or edgy+1

---

### Post by scxtt on 2006-07-26
i wasn't implying that @ all :) ... vino is always a good call for testing VNC connections, and it's simple to configure for a password and "just let them watch" access ...

---

