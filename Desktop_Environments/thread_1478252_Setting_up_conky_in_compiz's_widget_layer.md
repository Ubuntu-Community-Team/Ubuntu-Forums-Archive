---
title: "Setting up conky in compiz's widget layer"
date: 2010-05-09
forum: Desktop Environments
---

### Post by sagara on 2010-05-09
How do I set up conky in compiz's widget layer?

I know I have to set up the rule under *Widget Layer > Behaviour > Widget Windows* but i have not been able to identify the correct rule.

Any Ideas?

---

### Post by cwoolbright on 2010-05-28
BUMP hey I want the answer to this too =)

---

### Post by sagara on 2010-06-13
I was able to figure it out, here is what you do:

In your **conky setup file** , make sure the following settings are set:

```
own_window yes
own_window_type normal

```

In the CompizConig settings manager (CCSM), go to Widget Layer > Behaviour > Widget Windows and type

```
class=Conky
```

---

### Post by h4x0rmx on 2010-08-12
> **sagara said:**
> I was able to figure it out, here is what you do:

In your **conky setup file** , make sure the following settings are set:

```
own_window yes
own_window_type normal

```In the CompizConig settings manager (CCSM), go to Widget Layer > Behaviour > Widget Windows and type

```
class=Conky
```

I'm not really sure how the widget layer works, but is there a way to always have it there? I can toggle it on/off with a shortcut key... any suggestions?

---

### Post by Gaygerbil on 2010-08-12
There's a GUI for setting up Conky found here:

[http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html](http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html)

: D

It makes life easier.

My bad this post is completely irrelevant and retarded. <__<

---

### Post by h4x0rmx on 2010-08-12
> **Gaygerbil said:**
> There's a GUI for setting up Conky found here:

[http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html](http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html)

: D

It makes life easier.

Thank you, but I couldn't get it working, anyways, I do have corky working right, but with some limitations due to the fact that I have compiz on my machine.  I just want to have it in a widget (done) that always stays on the desktop, any suggestions?

---

### Post by simon_w on 2010-09-07
> **h4x0rmx said:**
> I just want to have it in a widget (done) that always stays on the desktop, any suggestions?

If you want it always on the desktop, why do you want it as a widget?  Sounds to me like you precisely *don't* want it on the widget layer at all.

Try removing the Compiz widget rule, and use this in your .conkyrc

```
own_window yes
own_window_type override
own_window_transparent yes
```

and see how that strikes you.

Good luck!

---

### Post by flyingbear on 2012-11-02
Thanks guys!! Used to have the same issue and this solved my problem :)

---

### Post by overdrank on 2012-11-02
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

