---
title: "Trackpad changes workspaces."
date: 2013-05-10
forum: Desktop Environments
---

### Post by pdxken on 2013-05-10
The right vertical edge of the track pad has a vertical scroll feature which is nice, but changing to different workspace when the pointer is over the desktop is kind of annoying for me. So far I can't find a way to disable this feature. Seems to be new in 13.04.

Xubuntu I have on another partition has a setting for that. Can someone point to the right setting in Lubuntu. for me Lubuntu works best on my aging laptop.

Thanks.
Ken.

---

### Post by pdxken on 2013-05-10
Couldn't find a GUI for this but after much googling I finally edited this file:

/home/ken/.config/openbox/lubuntu-rc.xml

and commented out this section:

```
<!--      <mousebind button="Up" action="Click">
        <action name="GoToDesktop">
          <to>previous</to>
        </action>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="GoToDesktop">
          <to>next</to>
        </action>
      </mousebind> -->
```

After logout and login the touch pad action no longer switches desktops. The desktop pager in the panel still works fine as I like it.:p

As an aside. Finding stuff on google is getting more and more challenging for me. Is it a trackpad, a mouse pad or a touch pad? Is it a workspace or a desktop? The more info out there in cyberspace the more confusion this old man has to deal with. Too many terms, words, and synonyms.:p

Ken.

---

