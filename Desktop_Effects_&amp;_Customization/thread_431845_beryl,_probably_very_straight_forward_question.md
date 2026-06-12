---
title: "beryl, probably very straight forward question"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by snobby500 on 2007-05-03
Hi, ive just been fiddling with beryl to try and stop it sorta jittering at the last moment when it minimises and resizes (its smooth until the last bit of animation), and I forced it to use, the last option, (not automatic, not nvidia, not the one below tht i think, but the last option in my attempt to make it run smoother) then it crashed on me and now whenever i bott it simply freezes, all id like is a way to make it go back to automatic through the command line which i will acces in the login screen or to force nvidia, either one will be ok. 

    thanks a lot, and I did a search for other posts bnefore i wrote this so sorry if there is another post on it :S

---

### Post by hyperair on 2007-05-03
Run this command in the start dialog or in the terminal:
```
gedit ~/.beryl-managerrc
```

Replace all the contents with this:
```

[wm-settings]
active_wm=0
fallback_wm=0
active_dm=0
iconsize=24
use_fallback_wm=true

[beryl-settings]
render_path=0
cow_mode=0
rendering_mode=0
platform=0
binding=0
no_gl_yield=false

```

Hope that helps.

---

### Post by snobby500 on 2007-05-03
u legend

thanks, working again

---

