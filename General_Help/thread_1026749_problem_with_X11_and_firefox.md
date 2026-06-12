---
title: "problem with X11 and firefox"
date: 2008-12-31
forum: General Help
---

### Post by tcolden on 2008-12-31
I am using ubuntu pull back GUI's from a unix server at work to my desktop at home. I have successfully change the setting so X11 is working. My Gui's work but there are some apps that use firefox as an interface. I can pull back the browser and I can use the links on firefox. when I try to type in the nav bar the browser closes. I also get this error in my terminal window.



firefox
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  147 (XKEYBOARD)
  Minor opcode of failed request:  16 (XkbSetNamedIndicator)
  Serial number of failed request:  3148
  Current serial number in output stream:  3200




any Idea how to correct this?

I pull my gui's back by:

xhost +

ssh user@server

login
pass

export DISPLAY=myip:0.0

xterm
or
firefox

all of the above works only issue is when I try to type in nav area on browser.

---

### Post by tcolden on 2009-01-01
any idea why fire fox crashes?

Should I post this in a different area?

---

