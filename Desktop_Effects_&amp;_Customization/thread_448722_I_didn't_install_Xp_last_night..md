---
title: "I didn't install Xp last night."
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by rocketboys on 2007-05-19
I decided to install Xp but I changed my mind.

so I'm back to Ubuntu 7.04.

and I got situation now..

I changed my resolution by  going in to this:

sudo dpkg-reconfigure -phigh xserver-xorg

in terminal.

I changed my resolution to 1280 1024.

Then now what happens is, every window's bar at the top(where there is the 3 buttons like minimize, maximize, close, and now it's gone. and if I turn on terminal, it's just white screen
and I can't see anything..

Help me please! :)

---

### Post by rocketboys on 2007-05-19
> **rocketboys said:**
> I decided to install Xp but I changed my mind.

so I'm back to Ubuntu 7.04.

and I got situation now..

I changed my resolution by  going in to this:

sudo dpkg-reconfigure -phigh xserver-xorg

in terminal.

I changed my resolution to 1280 1024.

Then now what happens is, every window's bar at the top(where there is the 3 buttons like minimize, maximize, close, and now it's gone. and if I turn on terminal, it's just white screen
and I can't see anything..

Help me please! :)

I just tried to changing window manager with beryl manager, I changed it to Metacity,

then it came back, and I changed it to Beryl again, then it will mess up again..:'(

---

### Post by philbygr on 2007-05-28
do u find anything? i have the same problem.... when runs compiz or beryl i have this situation. when i run metacity or xfce everything is ok :s

---

### Post by nvteighen on 2007-05-28
Had you Beryl or Compiz activated when the screen went weird?

Notice that Beryl and Compiz are beta software; they're not finished! Try to deactivate "Desktop Effects" before trying anything else.

(As a golden rule, never use beta software unless you know exactly what you do). Tell me if you succeeded!

---

### Post by bone43 on 2007-05-28
> **rocketboys said:**
> I decided to install Xp but I changed my mind.

so I'm back to Ubuntu 7.04.

and I got situation now..

I changed my resolution by  going in to this:

sudo dpkg-reconfigure -phigh xserver-xorg

in terminal.

I changed my resolution to 1280 1024.

Then now what happens is, every window's bar at the top(where there is the 3 buttons like minimize, maximize, close, and now it's gone. and if I turn on terminal, it's just white screen
and I can't see anything..

Help me please! :)


Did you try logging out and back in this may fix it.

 Also try reloading the windows decorator right click on the beryl icon then click reload windows decorator.

---

### Post by srt4play on 2007-05-28
Do you have an nvidia graphics card? If so check the 9th post in this thread:

[http://ubuntuforums.org/showthread.php?t=307530&highlight=beryl+missing+titlebar](http://ubuntuforums.org/showthread.php?t=307530&highlight=beryl+missing+titlebar)

---

### Post by philbygr on 2007-05-28
the beryl manager run to my system. when i activate beryl or compiz i lost the title bars of windows and as u can guess i can't move them or switch widnows.... when i choose metacity everything is ok, i change windows-managers through beryl icon ;)to system->prefences i haven't desktop effects choice.... :p so i think there aren't activated....

---

### Post by nvteighen on 2007-05-28
> **philbygr said:**
> the beryl manager run to my system. when i activate beryl or compiz i lost the title bars of windows and as u can guess i can't move them or switch widnows.... when i choose metacity everything is ok, i change windows-managers through beryl icon ;)to system->prefences i haven't desktop effects choice.... :p so i think there aren't activated....

Aha. Maybe your video card doesn't want Beryl (or viceversa). The best would be to not use Beryl until a stable version is released. Sorry.

---

### Post by philbygr on 2007-05-28
but everything ok except title bars? *-) i think that desktop has most dificult for a video card such title bars? :p maybe i think like a baby :p

---

### Post by nvteighen on 2007-05-28
> **philbygr said:**
> but everything ok except title bars? *-) i think that desktop has most dificult for a video card such title bars? :p maybe i think like a baby :p

Yes... Weird things can happen with beta software! :-D Maybe it's a problem with the transparent title bars feature? Don't know... But if you see that turning Beryl off solves the problem, then it is far clear to me.

---

### Post by srt4play on 2007-05-28
> **nvteighen said:**
> Yes... Weird things can happen with beta software! :-D Maybe it's a problem with the transparent title bars feature? Don't know... But if you see that turning Beryl off solves the problem, then it is far clear to me.

This problem has been known for a very long time. Check the fix in my earlier post.

---

