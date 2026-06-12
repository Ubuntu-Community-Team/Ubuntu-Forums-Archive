---
title: "xmms gDesklet problem"
date: 2006-01-01
forum: Desktop Environments
---

### Post by jackwhite on 2006-01-01
Hi folks,

I've just installed this cool looking xmms gdesklet called "osxcornerxmms". Its appeared where it should but I can't actually use it. When gdesklets starts up I get an error message which tells me the following:
```
No Control could be found for interface IKXmms2:701uz5p7uot652wbszeprbeev-2
/home/padraic/.gdesklets/Displays/tmph8Dasx/osxcornerxmms-bottomright.display
```

Any time I click on a button i get an error message like this:
```
name 'xmms' is not defined                                                           
/home/padraic/.gdesklets/Displays/tmph8Dasx/osxcornerxmms-bottomright.display        
>   1 xmms.action = 'play'; self.uri = 'gfx/play0.png'
```

Now that kinda makes sense but I don't know what to do about it. Where can i define xmms?

all help gratefully accepted!

---

### Post by Gsundbrunn on 2006-01-02
Hi,

probably an code error. Some of the desklets are buggy. Additionally you should try to find out the prerequisits od the desklet you&#341;e using. Some of them need some kind of sensor packages installed.

Regards

Stefan

---

### Post by jackwhite on 2006-01-02
You were right - I needed to install pyxmms- Found it in synaptic under python - xmms.

Thanks for your help!

---

