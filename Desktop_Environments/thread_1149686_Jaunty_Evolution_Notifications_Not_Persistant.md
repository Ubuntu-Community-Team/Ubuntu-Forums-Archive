---
title: "Jaunty Evolution Notifications Not Persistant"
date: 2009-05-05
forum: Desktop Environments
---

### Post by Zenguy on 2009-05-05
I know there are a ton of postings regarding the new notification in Jaunty. For the most part, the new notification system is ok by me.

Except for Evolution. 

If I am away from my computer, the email notification will be long gone by the time I return. Is there a way to make the notifications persistent, so I see it when I get back to my computer? Alternately, I could revert to the old Evolution notification if there is no solution. (Some instruction on either of these solutions would be appreciated.)

Also, there are other posts that reference a program that will allow the user to customize the notification system, but on my clean install of Jaunty, I could find no such program.

Thanks.

---

### Post by meho_r on 2009-05-05
No customizations for now. But, in case of new emails, indicator applet (that little envelope on the notification area) should have a little yellow star on it telling you this way that you have an unread message. Just click on it and see which app has new message (Evolution, Pidgin or other).

---

### Post by Zenguy on 2009-05-05
That's odd. I never get an indicator on my panel. (I used to get a small email icon with previous Ubuntu releases.)

Synaptic shows "indicator-applet" is installed though. Does it have to be configured? If so, how?

---

### Post by meho_r on 2009-05-05
Starts automatically when Pidgin or Evolution is started. I have it in Startup Applications with this entry:

```
sh -c "sleep 60 && python /usr/share/gnome-panel/add-indicator-applet.py"
```

And, of course, you can simply add it to any of panels. It will be hidden until you open some of apps that needs its attention.

---

### Post by Zenguy on 2009-05-05
Thanks for pointing me in the right direction.

This might have been user error. I cleaned up my panel after installing Jaunty and might have accidently deleted that panel app. It might have seemed redundant to have two notification systems at the time.

---

