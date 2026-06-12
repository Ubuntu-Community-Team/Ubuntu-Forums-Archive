---
title: "Installing Flash"
date: 2009-04-12
forum: General Help
---

### Post by MinatureCookie on 2009-04-12
Hey guys,
Well I'm trying to install Flash on my PC.. But I've run into a rather annoying problem (I'm very new to Ubuntu, chances are I'm just being stupid).
So [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) here you can install Flash, and I've tried using every single type of install option, but none work. All coming up saying that i386 isn't supported, for example using the .deb - "Status: Error: Wrong architecture 'i386'"
So... Umm... I'm stumped.

Any help would be greatly appreciated :)

---

### Post by SuperSonic4 on 2009-04-12
I'm guessing you're using 64 bit ubuntu

You can get an alpha (actually rather stable) plugin of adobe flash from [Adobe]("http://labs.adobe.com/downloads/flashplayer10.html").

I then extracted it and copied it to ~/.mozilla/plugins (you may need to create that folder) and restart firefox with success

---

### Post by taurus on 2009-04-12
Are you running a 64bit (x86_64) Ubuntu?

Applications -> Accessories -> Terminal
```
uname -m
```

---

### Post by MinatureCookie on 2009-04-12
Will I get this problem a lot? If so I'm happy just changing my Ubuntu version?

---

### Post by SuperSonic4 on 2009-04-12
No, it's quite unusual, especially if you use the repositories for most of your programs.

---

### Post by MinatureCookie on 2009-04-12
> **SuperSonic4 said:**
> No, it's quite unusual, especially if you use the repositories for most of your programs.
Ahh that's great,

What does the '~' mean in that location? "~/mozilla"

---

### Post by lovinglinux on 2009-04-12
> **MinatureCookie said:**
> Ahh that's great,

What does the '~' mean in that location? "~/mozilla"

It means "*/home/you/*". You can use "~/" instead of the full path to your home directory.

---

### Post by MinatureCookie on 2009-04-12
Ahh, that's brilliant - got it working now :)
Thankyou all :)

---

