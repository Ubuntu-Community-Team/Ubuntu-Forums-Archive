---
title: "Problem with VNCserver"
date: 2006-06-06
forum: Desktop Environments
---

### Post by phoenixy on 2006-06-06
Hi,

I'm hosting a vnc server on 5901. I'm having trouble launching a windows manager after I log in.

in the account that I ran vncserver, I modified ./vnc/xstartup to contain icewm &. But all I get is a greyish checkerboard background(no wm at all)

I placed some code in xstartup that create a temp file. But turned out the temp file is never created. So xstartup is never ran. 

Anyone know what's going on?


Thanks

---

### Post by xaverx on 2006-06-06
try blackbox

---

### Post by phoenixy on 2006-06-06
I don't think another wm has anything to do with the problem I have. As I explained, the trouble comes from the fact that ~user/.vnc/xstartup is not being run after I successfully log in to vnc using the ~user account

---

### Post by phoenixy on 2006-06-06
And also, why does gnome's built-in vnc use so much bandwidth...

---

### Post by nocloud on 2006-06-06
i am having some problems connecting to a server with vnc viewer in kubuntu

it gives me an error about RFB protocol version not matching....

does anybody know how to fix that?

---

### Post by phoenixy on 2006-06-07
[QUOTE=nocloud]i am having some problems connecting to a server with vnc viewer in kubuntu

it gives me an error about RFB protocol version not matching....

does anybody know how to fix that?[/QUOTE]

Maybe you can get an answer in the kubuntu forum?

---

