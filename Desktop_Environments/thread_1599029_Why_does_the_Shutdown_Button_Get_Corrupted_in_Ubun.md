---
title: "Why does the Shutdown Button Get Corrupted in Ubuntu 10.04 LTS?"
date: 2010-10-17
forum: Desktop Environments
---

### Post by AlexanderDGreat on 2010-10-17
This usually happens when I login 3 out of 10 times.

I have to type:

killall gnome-panel

to fix it. Attached the photo explaining what I mean. Thanks.

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/ubuntu_gdm_bug.jpg[/IMG]

I believe it's called Indicator Applet Session 0.3.7

---

### Post by AlexanderDGreat on 2010-10-20
Please help!

---

### Post by teachop on 2010-10-20
Hey, that happens to me too, but in 10.10!  I got annoyed and deleted indicator applet session and put Shut Down on the panel instead.  Which isn't a good answer, I know.

---

### Post by hellnest on 2010-10-21
Something wrong with your display adapter? Never got that kind of problem until now using lucid :)

---

### Post by AlexanderDGreat on 2010-10-22
It's kinda strange because I manage almost 10+ computers in the office.

They use Intel Atom 330 built-in video and the other ones, Asus P5KPL-AM EPU built-in video as well. Happens 3 out of 10 times

At home I use nvidia 9500GT - Here it's just 1 of 10 times.

Man it's really painful, sometimes, I can't even SHUT DOWN because I can't click the damn thing! :(

---

### Post by Linux_junkie on 2010-10-22
Its happened to me a few times as well.  When it does happen and I want to log off I press CTRL-ALT-DEL then select shutdown.

p.s. has anyone reported this bug to Ubuntu?

---

### Post by rhersel on 2010-10-22
This happens on all of my 3 computers since 10.04 and also in 10.10. Not only the shutdown button is effected but sometimes the whole panel is messed up. I don't know how to fix this except the known workaround: killall gnome-panel

---

### Post by AlexanderDGreat on 2010-10-23
Yes, I think it's a bug.

I believe the developers should reWRITE the whole icon panel on the Desktop of Ubuntu, there's a lot of problems going on here ever since 8.04!

Sometimes when you change the resolution.

---

### Post by AlexanderDGreat on 2010-10-24
I found a dirty workaround.

Startup Applications:

```
sh -c "sleep 10 && killall gnome-panel"
```

There!

It will automatically fix itself 10 seconds after Booting to your Desktop session.

---

### Post by AlexanderDGreat on 2010-10-24
> When it does happen and I want to log off I press CTRL-ALT-DEL then select shutdown. - Oh yeah, never thought of it. Now, I can prevent damage by just TURNING OFF my machine and No ShutDown, of course, only in Ubuntu and my lack of knowledge. Thanks.

---

### Post by AlexanderDGreat on 2010-10-24
Even my trash can doesn't want to stay in 1 place!

---

### Post by heavy metal on 2010-10-24
was having same issue, fixed it by changing the themes to clearlooks and now everything is fine... you can try to change the default theme to see if it works and please tell me if it worked.:guitar:

---

### Post by AlexanderDGreat on 2010-10-25
OK I'll try that but it's only 3 of 10 times.

---

### Post by AlexanderDGreat on 2010-11-07
@heavy metal - Sorry I didn't like the Clear Looks theme so I switched back to the default one, after switching back I immediately got this:

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/corrupt_icons.jpg[/IMG]

Still happens to me.

---

### Post by CyberBaggage on 2011-02-22
I happened to have the same problem. Except its not only the shutdown button. But the whole part of the panel on the right side that gets corrupted. This happens almost every month( Insane periodicity, I must say). I usually go to ~/.gconf/apps and delete the complete panel folder and that does the trick.

But the worse part is all the items that I have added to the panel are lost and the default panel kicks in. 

I really hope they fix this issue.

---

### Post by RussellEngland on 2011-02-25
Happens to me in 10.10 - only occasionally though

I'm using the default theme

---

### Post by AlexanderDGreat on 2011-02-25
Well, as a fix, try adding this to your System > Preferences > Startup Applications

sh -c "sleeep 20 && killall gnome-panel"

Simply means, after 20 seconds upon logging in, reload the WHOLE gnome panels. It works, try it.

:)

---

### Post by RussellEngland on 2011-02-25
Thank you for the fix, I'd prefer a more permanent solution though.

Cheers, Russ

---

