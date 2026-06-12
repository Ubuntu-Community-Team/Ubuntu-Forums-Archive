---
title: "Talk to notifyOSD from Java"
date: 2009-06-13
forum: General Help
---

### Post by KingWilliam on 2009-06-13
Since I love to develop with Java, I was curious about how I could send messages to the brand new notification system in Ubuntu 9.04 Jaunty. 

I looked around a bit on the internet, and couldn't find any simple library on how to do this. That is why I decided to create my own very simple Java library to send messages to notifyOSD. 

Any suggestions on how to improve it are welcome, but what I did is simply calling the "notify-send" cli command from within a Java class. 

In the end, when the developer adds the jarfile to his application, he can simply call this method to show a notification:

```
NotifyOSD.show("title", "message", Urgence.low);

or


NotifyOSD.show("title", "message");
```

I will soon (in 2 days probably) update this thread with a link to our website where I will post the jarfile. Any ideas, suggestions or improvements are very welcome.

Since I am not very used to develop open-source stuff, could someone tell me what sort of license I should add to this, and how I do this?

Greets!!

---

### Post by tonyr1988 on 2009-08-16
I'd love to have this jar file. I'm working on a program that will let me control my media center via Wiiremote, and the NotifyOSD seems to be the best way to universally display text with fullscreen apps.

I've tried doing this myself (with just Runtime.getRuntime().exec), but I'm getting weird results. I'm printing the command out to the console, and it works fine when I run it in a terminal, but it's either not showing the noficiation, or showing it incorrectly.

If you've been able to get this working, I'd love to use it.

As far as licensing, I've got no idea on those.

---

### Post by KingWilliam on 2009-08-16
If you send me a PM with your email adress I'll send you the jarfile. (But first I'll have to do a little searching to find where I have put that thing :P)

---

