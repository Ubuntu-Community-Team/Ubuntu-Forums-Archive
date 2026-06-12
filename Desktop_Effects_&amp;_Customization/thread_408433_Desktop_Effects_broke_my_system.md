---
title: "Desktop Effects broke my system"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by Toby2 on 2007-04-13
I downloaded and did a fresh install of the Live CD of the Feisty Beta today, and I was impressed with the responsiveness and speed compared to my old Edgy install.

My first instinct was to try out Feisty's new features; I opened up the Desktop Effects panel, and enabled them. A whole portion of the screen over to the right was full of distortion, but the effects worked fine when I moved windows around and stuff. Being me, I clicked ok, and logged out, hoping that when I logged back in, the distortion would be gone and I'd have working Desktop Effects.

Well, I was wrong. When I logged back in, the portion of the screen to the right was white, and the gnome panels / desktop were 'cropped' off the screen to the left, and were blank. I couldn't do anything with the desktop or panels, so my only option was to go Ctrl-Alt-Backspace.

I've tried starting different session types from the gdm, but they don't seem to work. I'm quite stuck where to go now - is there any way to turn off the desktop effects from a terminal (ie. Ctrl-Alt-F1), and make metacity the default window manager again?

Thanks in advance,
- Toby

---

### Post by Toby2 on 2007-04-13
Fixed.

I somehow managed to open a nautilus window, create a launcher to gnome-terminal, and type metacity --replace. Then I went and disabled desktop effects. Whew.

---

### Post by kidders on 2007-04-13
Great :-) That was exactly the right thing to do (although you *could* have done it more easily by hitting CTRL+ALT+F1 first). Hitting ALT+F2 (in most desktop environments) is another way of executing a command quickly.

If you want to continue testing Feisty, I'm sure the community would appreciate it. I have to confess though, that I'm using a custom Beryl installation to handle my desktop eye candy, which is proving less hair-raising!

---

### Post by Toby2 on 2007-04-13
Ah, I've got to remember that Alt-F2 shortcut. I'm sure it'll come in handy one day.

I'll definitely continue testing Feisty. It's working a lot better for me than Edgy did (I got midis working!).

I still want to try and get Desktop Effects to work. They seem to run fine when I initially enable them, it's just that right part of the screen that goes all funny. I'm not risking restarting X with the desktop effects on again. Here's a screenshot of what it looks like (after you've dragged windows over it). Also, I think the maximized window doesn't have a border. Any ideas?

[ATTACH]29646[/ATTACH]

---

### Post by eggdeng on 2007-04-13
Looks to me as if you haven't got a theme for your windows. Click on the gem icon, then choose a theme in the Emerald Settings Manager.

---

### Post by Toby2 on 2007-04-13
What emerald? I haven't installed Beryl or anything, this is just a fresh install and that's what happened when I enabled desktop effects. All of the un-maximized windows have the correct theme, and the nice dragging effect works fine on them. It's just that part of the screen over to the right, and the maximized windows.

---

### Post by kidders on 2007-04-14
> **Toby2 said:**
> I still want to try and get Desktop Effects to work. They seem to run fine when I initially enable them, it's just that right part of the screen that goes all funny. I'm not risking restarting X with the desktop effects on again. Here's a screenshot of what it looks like (after you've dragged windows over it). Also, I think the maximized window doesn't have a border. Any ideas?
I couldn't even begin to explain that one! :-( I wonder if (like me) eggdeng has abandoned Feisty's built-in desktop effects in favour of a fuller custom setup.

Even though *you* haven't, his suggestion may still be going somewhere though ... what happens if you relaunch your window manager, etc?

---

### Post by Toby2 on 2007-04-14
Last night I tried going crazy changing things in xorg.conf... probably not a good thing to do, but I did it anyway. :) 

When I changed defaultDepth from 24 to 16, the desktop effects started working perfectly. Unfortunately, the color quality on some elements is slightly lower, but I can live with that! ^^

I might experiment with a custom installation of Beryl a bit, just to see which desktop effects thing I like better, but otherwise I'm really loving Feisty!

---

### Post by kidders on 2007-04-14
> **Toby2 said:**
> When I changed defaultDepth from 24 to 16, the desktop effects started working perfectly.Curious... I would've expected the opposite to happen heh! It's nice to see you're having some measure of success though. :-)

---

