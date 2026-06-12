---
title: "transparent fullscreen borderless aterm below other windows at startup in KDE"
date: 2006-01-29
forum: Desktop Environments
---

### Post by key on 2006-01-29
I like to run 'top' in a borderless aterm window behind all my other windows. That way it looks the same as if I were running top on my desktop. 

I have everything all set up - fullscreen transparent borderless aterm - but  I have to do it all after I startup kde. Its a bit annoying. 

How do I run an application (an aterm from the command line in this case) while specifying that I want it to run both below all other apps and in a full screen window? 

many thanks,

key

---

### Post by obibok on 2006-01-29
Create *Link to Application* in **.kde/Autostart**. Then, adjust window behaviour in  *Advanced->Special Window Settings* (rightclick on app title bar if visible) or type in Konqueror **settings:/Desktop** and select *Window-Specific Settings*). You'll find lots of options there.

---

### Post by key on 2006-02-01
thanks obibok -

another strategy is to just set things up the way I like - then log out of KDE and save the session. Then KDE reloads everything the way I like when I restart. I still have to type 'top' but I think there is a way to work around that. 

key

---

### Post by Hikaru79 on 2006-11-03
Just out of curiosity, could you post the actual line you use to call aterm to make it transparent, fullscreen, borderless, etc? :)

---

### Post by AustinMarton on 2007-11-07
I very much would also like to know how you made your aterm borderless??

When I run
```
aterm -tr +sb +bl
```
or
```
aterm -tr +sb -bl
```

It's transparent without a sidebar - but I still have a border!!!

Actually want to do this in Blackbox, but doesn't work in gnome either.

---

