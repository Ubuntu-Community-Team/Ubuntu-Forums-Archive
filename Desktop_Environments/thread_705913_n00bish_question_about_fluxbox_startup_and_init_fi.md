---
title: "n00bish question about fluxbox startup and init files"
date: 2008-02-23
forum: Desktop Environments
---

### Post by phuturism on 2008-02-23
Very new to fluxbox so stay with me...

When I boot I get a standard fluxbox interface - no background etc.

I have configured my startup file at ~/.fluxbox/startup but these settings do not take effect until I go slit>windowmanagers>fluxbox - then I get correct theme and background.

How do I get these settings booting at login rather than manually?

Thanks

---

### Post by drcranium on 2008-02-24
First install Feh or Nitrogen.
Then go to
~/.fluxbox/init
with your favorite editor.  Go to the line session.screen0.rootCommand and add your command so it looks like this

session.screen0.rootCommand:    fbsetbg -f ~/path/to/pic

EDIT:

For the theme go to 
session.styleFile:    ~/path/to/theme

---

### Post by phuturism on 2008-02-24
OK that's working!!!!   Thanks.

Quick followup though - I have conky & in my ~/.fluxbox/startup and it's the same deal as above - it won't run until I manually hit slit>windowsmanagers>fluxbox
this tells me that the startup doesn't run til I kick it.  What's the deal?  Do I need to point to the startup file somewhere else?

Hope that makes sense.

---

### Post by RedSquirrel on 2008-02-24
Make sure you start fluxbox with command 'startfluxbox' and _not_ 'fluxbox'.

If you login via gdm, make sure /usr/share/xsesssions/fluxbox.desktop has 

```
Exec=/usr/bin/startfluxbox
```

or if you login on the console, make sure you have

```
exec startfluxbox
```

at the bottom of your ~/.xinitrc.

---

