---
title: "xcompmgr issues"
date: 2006-08-17
forum: Desktop Environments
---

### Post by basvgils on 2006-08-17
Dear all,

Today I've been playing with composite for the first time. I got some help from my buddy to set it up. Here's what I did:

[LIST]
[*]added an option-line to the device section of xorg.conf with *Option "AllowGLXWithComposite" "true"*
[*]added a section to xorg.conf with:
  *Section "Extensions"*
  *  Option "Composite" "Enable" *
  *  Option "RENDER" "true" *
  *  Option "DAMAGE" "true" *
  *EndSection*
[*]installed ‘transset’ and ‘xcompmgr’
[*]restart X
[*]run *xcompmgr -f -F -c -I 1 -C &* and *transset* on an urxvt
[/LIST]

So far so good, things seemed to work just fine. However, I noticed some problems with gnome. First I noticed that some icons disappeared under the panel. Also, maximized windows went on top of the panel, effectively hiding it. After some googling I found out that I could fix this by running a *killall metacity*. Not an option that sounds appealing but it seemed to work. I also ran into the infamous logout-panel issue. Clicking the logout button effectively seems to freeze the box as for some silly reason the logout panel doesn't appear. Haven't been able to fix that one yet.

My question at this point is: has anyone gotten it to run smoothly on Dapper? What are the odds to get it to work? Software still in alpha fase perhaps? 

Any help is greatly appreciated

  Bas

---

### Post by bulldog on 2006-08-17
Well it runs relatively without errors :) 
It's a Beta and not error free.

I installed mine by the following link:

[http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)

I have an nVidia card but there are tutorials for ATI as well.
It runs always and I never had to turn it off,although there are some small issues,but I can live with that.:p

For Ati cards look here:

[http://ubuntuforums.org/showthread.php?t=145068](http://ubuntuforums.org/showthread.php?t=145068)

---

### Post by basvgils on 2006-08-18
I also have an nvidia card and here it doesn't work fine... The only issue I have now is that the logout panel doesn't appear :( well... hope I'll find a fix for that soon

---

### Post by samoht on 2006-08-19
The logout-panel doesn`t really frezze, it`s just not shown. You can get back to your desktop with the keystroke "ALT + F4".
But I have no workaround to the problem either. :( We have to wait until metacity supports xcomposite...

---

### Post by twstokes on 2006-11-08
If you shutdown from the panel, here's a script that I made to solve the issue for me.

```
#!/bin/sh

killall xcompmgr
gnome-session-save --kill
```

Replace the logout applet with a Custom Application on the panel that is the path to this script, and change the icon to the logout icon.

---

