---
title: "[SOLVED] loss of gnome panals after crash"
date: 2008-03-22
forum: Desktop Environments
---

### Post by leona on 2008-03-22
Hi there

My system just failed on me, and I had to restart.
When I restarted I was presented with my desktop icons, but no panels, no menus nothing else.

did a quick search and found the commend
```

metacity --replace&

```
But I get 
[quote=my broken computer]
unable to open x display.
[/quote]
Can you help a gal in distress?

---

### Post by scragar on 2008-03-22
try pressing alt+F2, then type:
```
killall gnome-panel && gnome-panel
```
no guarentee's though.

---

### Post by leona on 2008-03-22
Thank you but that gives me
[quote=my broken computer]
gnome-panel: No processes killed
[/quote]

---

### Post by scragar on 2008-03-22
fine, gnome-panel isn't running, so just start it again:
```
gnome-panel
```

---

### Post by leona on 2008-03-22
Thank you, but again I get
[quote=my broken computer]
unable to open x display.
[/quote]
I restarted and tried to log in.
Entered my user and pass and now get presented with the orange ubuntu screen and mouse pointer :(
Its not looking good

---

### Post by scragar on 2008-03-22
alt+F2 for box:
```
gnome-terminal
```or```
xterm
```
for terminal if you can't get one up normaly, let's try checking running processes:```
system-monitor
```and check **processes**, enable **dependencies**(view > dependencies) then look at what's under **X-session monitor**

---

### Post by leona on 2008-03-22
Thanks.
I Tried alt+F2 I get nothing, no response.
The only way I can get a terminal, is to reboot and select "session options" on restart and then I can get a term window up, shall I do that?
Arr got around this, a file manager window opened so I navigated to /usr/bin and ran xterm from there, that seemed to work, but no keyboard commands are working.

system-monitor gives me "command not found" :(

---

### Post by leona on 2008-03-22
Ok thank I've solved it. strange thought, bit unnerving.
I shutdown, turned the pc off, walked away and had a drink came back, turned it on.
Logged in, this time it gave me the proper background, but still not panels, but it did give me a terminal window, so I ran your list of commands again in sequence, and hey, all my panels came back.
I logged out and back in to check it was still ok and way hey it is.
Thank you so much, I'm happy gal again now. :)

---

