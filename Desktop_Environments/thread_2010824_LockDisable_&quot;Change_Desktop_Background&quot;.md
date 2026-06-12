---
title: "Lock/Disable &quot;Change Desktop Background&quot;"
date: 2012-06-26
forum: Desktop Environments
---

### Post by stiV on 2012-06-26
Hello!

Is there any way to make it impossible for a user to change its desktop background image? Or even better - change the Theme at all?

We have a few surf stations, which are relatively "open", but users keep changing the background image... And no they are not pretty ;)

Can I stop that somehow?

Ubuntu 12.04 and 11.10

---

### Post by MG&amp;TL on 2012-06-26
I think you're after *dconf keys*. [http://askubuntu.com/questions/132175/how-to-store-a-dconf-key-as-read-only](http://askubuntu.com/questions/132175/how-to-store-a-dconf-key-as-read-only)

...the one you're after is *org.gnome.desktop.background.picture-uri* , I think.

---

### Post by stiV on 2012-06-26
Can you help me a little more?

There is no "/etc/dconf", and what I have tried in a virtual machine ended up destroying the machine ... (at least Gnome did not start anymore)

I don't really know what files/folders I need to create to make that work ... one user (which can't use "sudo") should not be able to change the background image...?

---

### Post by MG&amp;TL on 2012-06-26
Okay, my bad, I don't have that on my system either.

One thing you could do (instead of stopping users changing the background) is to reset it every login-is that a problem or not? The command you'd put in *startup applications *would be:

```
gsettings set org.gnome.desktop.background picture-uri "file:///usr/share/backgrounds/warty-final-ubuntu.png"
```

...and I've tested this myself this time. :)

I'm not really sure how to accomplish this as you wish, as it's not something ubuntu's been designed to do.

---

### Post by stiV on 2012-06-26
Thank you! ... I guess I'll create a cronjob that runs every few minutes that exectues that command, should be enough.

I love ubuntu and have loved ubuntu for years, but it really does lack features and seems seriously unfinished at times. A task like this is not easy in windows, but it is possible ... without such a bad workaround.

---

### Post by MG&amp;TL on 2012-06-26
> **stiV said:**
> Thank you! ... I guess I'll create a cronjob that runs every few minutes that exectues that command, should be enough.

I love ubuntu and have loved ubuntu for years, but it really does lack features and seems seriously unfinished at times. A task like this is not easy in windows, but it is possible ... without such a bad workaround.

*gsettings* is per-user...I'm guessing a cronjob will only affect cron's background. :lolflag:
Maybe a "while true" in the startup thing? I agree with you about the workaround bit...but you'd really have to rewrite a lot of stuff to get that done.

---

### Post by stiV on 2012-06-26
It works if I execute it as root using "su USERNAME -c 'COMMAND' ", the background gets set ;)

---

### Post by MG&amp;TL on 2012-06-26
> **stiV said:**
> It works if I execute it as root using "su USERNAME -c 'COMMAND' ", the background gets set ;)

Fair enough. Whatever works. :)

---

### Post by wittyman37 on 2013-02-14
Thank you this works for me as a workaround for now.  I really want to be able to completely block the user (student in my case) from being able to change the desktop background at all.  We already had one student put a dirty picture as the background.

I used this for Edubuntu 12.04 with gnome fall back desktop with no effects:

```

gsettings set org.gnome.desktop.background picture-uri "file:///usr/share/backgrounds/edubuntu_default.png"

```
This  will change the desktop background back each time the user logs in (or  boots up).  This is not perfect, but it will work until I find a real  way to completely block the user from changing the background image like  I can in Windows 7.

---

