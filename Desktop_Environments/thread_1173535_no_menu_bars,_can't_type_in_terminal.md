---
title: "no menu bars, can't type in terminal"
date: 2009-05-29
forum: Desktop Environments
---

### Post by Zom-b on 2009-05-29
I don't even know what I did, I figured it was something I did by uninstalling compiz or emerald, but I reinstalled them and it hasn't fixed it, the only way I can us my terminal is if I log out and use the failsafe terminal at log in.

---

### Post by anarchyinc on 2009-05-29
You must create a new session, or log into a different desktop environment in order to repair. Last time your session saved, you had compiz as your window manager instead of nautilus, thunar or whatever that came with your desktop environment. This resulted in you logging into your xsession without a manager. Compiz's repo has a package called icon-fusion or something like that which resolves this issue and provides better management for the program as well as better switching between the two.

---

### Post by Zom-b on 2009-05-29
alright, now I just need to figure out how to fix it, but everything is working at least works, but where should I look to fix my other session?

---

### Post by anarchyinc on 2009-05-30
under your home folder .session <-- hidden folder, I do believe. But I can be mistaken.

---

### Post by kerry_s on 2009-05-30
in that terminal run> **rm -rf ~/.config/xfce4**
type> **exit**
then try logging into your xfce4.

that command will put you back to scratch, it will be like the first time you started xfce4.

---

### Post by Brandon Williams on 2009-05-30
If you go the route of deleting .config/xfce4, you probably also want to delete .cache/sessions and then make sure that 'Automatically save session on logout' is unchecked in the 'Session and Startup'dialog. Then log out and log back in.

---

### Post by kerry_s on 2009-05-30
> **Brandon Williams said:**
> If you go the route of deleting .config/xfce4, you probably also want to delete .cache/sessions and then make sure that 'Automatically save session on logout' is unchecked in the 'Session and Startup'dialog. Then log out and log back in.

good idea:
[B]rm -rf ~/.cache
rm -rf ~/.config/xfce4-session[/B]
just incase
**rm -rf ~/.config/autostart**

to make sure nothing starts thats not suppose to.
ohh, and don't worry, everything will be recreated when you log in.

---

### Post by trench.me on 2009-05-30
I've a problem related to the answers being given here I believe.

Two of my startup items have recently went nuts. On login Mobloquer opens up 2 and sometimes 3 instances of itself, and Tomboy Notes throws a "applet-fail" error at me while ceasing to load.

I think the problem originated from [Ubuntu Tweak]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fubuntu-tweak.com%2F&ei=itkhSofVHJ7uMo3w2bkJ&usg=AFQjCNFogdSEcgLy1FzQRfFTSG1Bl_BDCQ&sig2=vQfDfT0gdmvMUBZwVgkZ0A"). I'd installed it, tweaked a few things, decided I didn't like it much and removed it and it seemed to have left things a bit messy. Another example is I turned off desktop icons using it and can't figure out how to return them. This isn't much of a problem seeing as I'd like them to stay "gone", but I'd much enjoy actually knowing how to control the on & off valve.

Anyway, point-being, it sounds like the problem resides in this .cache directory you are speaking of. Is rm -rf .cache/ recommended in my situation as well?

EDIT: ... and also [B]rm -rf ~/.config/autostart ?
[/B]

---

### Post by kerry_s on 2009-05-30
the icons, right click the desktop> desktop-settings> icons
it's simple check/uncheck what you want.(see pic)

look through your folders, programs always leave crap behind even though you uninstall it. i go through every now and then and clean up the crap.

i don't know if it will help but i'll do pic's of the relevant xfce4 folders, might help you compare.
see, i have a wicd file and don't even have wicd anymore. deleted it. :)

---

### Post by Zom-b on 2009-05-30
> **kerry_s said:**
> good idea:
[B]rm -rf ~/.cache
rm -rf ~/.config/xfce4-session[/B]
just incase
**rm -rf ~/.config/autostart**

to make sure nothing starts thats not suppose to.
ohh, and don't worry, everything will be recreated when you log in.

thanks, that fixed the problem, btw, would it make sense that in a gnome session things run faster in xubuntu than they do in a xfce4 session? because it seems that way, when I was using gnome, everything seemed to be a bit more responsive, I mean the whole reason I switched to xubuntu was because I am using an older laptop and I wanted it to be a bit faster 

well that and this video... [http://www.youtube.com/watch?v=eNTchxbUR8g](http://www.youtube.com/watch?v=eNTchxbUR8g)

---

### Post by kerry_s on 2009-05-31
> **Zom-b said:**
> thanks, that fixed the problem, btw, would it make sense that in a gnome session things run faster in xubuntu than they do in a xfce4 session? because it seems that way, when I was using gnome, everything seemed to be a bit more responsive, I mean the whole reason I switched to xubuntu was because I am using an older laptop and I wanted it to be a bit faster 

well that and this video... [http://www.youtube.com/watch?v=eNTchxbUR8g](http://www.youtube.com/watch?v=eNTchxbUR8g)

xubuntu is the most bloated of xfce4 distros, so yes it makes sense. i use debian base+xfce4 and it is truly light.
gnome is not that bad and it can be made to be as light as xfce4.
any which way if you want to run light, then a custom install is the way to go.

my startup ram use is around 43, my just browsing ram use is around 100. i'm a serious multi-tasker though, i have the ram on this desktop and do use it. my laptop on the other hand only has 256mb ram so that i keep truly trim and try not to do to much at one time.

---

