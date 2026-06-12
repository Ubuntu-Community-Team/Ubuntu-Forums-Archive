---
title: "quick firefox question"
date: 2009-06-21
forum: General Help
---

### Post by v1nsai on 2009-06-21
I've got a pretty big screen, so I don't run firefox maximized, I like it in the middle of my screen so I can interact with desklets, but every time I open firefox it opens at the size I left it on which is good, but on the left of the screen instead of the center.  Is there an about:config tweak or something I can do that will make it pop up front and center every time?

---

### Post by Johnny B on 2009-06-21
you could try using a program called devilspie, which allows you to control things like that

[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/")

---

### Post by v1nsai on 2009-06-21
is it command line only?  I'm cool with that, but the man page is, in the author's own words: "Bugs: this manpage is almost useless, as it was thrown together on a train" lol.  I've been picking through it but haven't figured out how to do much of anything, much less attach a rule to a specific program.

<edit>
just saw the link you posted, checking that out now
</edit>

---

### Post by v1nsai on 2009-06-21
ugh, can't get this to work for anything.  Created a file in .devilspie/firefox.ds as such:

```
(if
(is (application_name) "Firefox")
(begin
(center)
)
)
```

And used alt+f2 to run devilspie, but while it will center the window if firefox is open, it does nothing when I open a new one.

---

### Post by lovinglinux on 2009-06-21
You could use Compiz "Window Rule" and "Place Window" plug-ins. You can do whatever you want with the windows.

---

### Post by v1nsai on 2009-06-21
using another program seemed unnecessary to me for such a simple task, did you mean using gconf-editor to access compiz options?  I found a plugin labeled winrules in here, but I don't see anything about place windows, could you fill me in a little more on what you mean?

---

### Post by lovinglinux on 2009-06-22
> **v1nsai said:**
> using another program seemed unnecessary to me for such a simple task, did you mean using gconf-editor to access compiz options?  I found a plugin labeled winrules in here, but I don't see anything about place windows, could you fill me in a little more on what you mean?

Using [CompizConfig Settings Manager](apt:compizconfig-settings-manager) [apt-get]

System >> Preferences >> CompizConfig Settings Manager

---

### Post by MarkBoucher on 2009-06-22
U have to Use " devilspie " ... i hope it will solve ur problem

---

### Post by v1nsai on 2009-06-23
Devilspie won't work for me, I posted my code and ran it with alt+f2 as I said, I know it was running.

Place Window worked great, I love this settings manager, its a lot easier to deal with than gconf-editor thanks a lot for the tip.  I finally got the window to center, the slider that goes with the Place Windows dialog is very misleading though, I was getting very annoyed because no matter where I put the slider the window was either all the way on the left or all the way on the right.  I tried thinking of it in terms of pixels, and did the math and split my screen up the way I wanted it, then plugged in the number in the box and it centered it beautifully.

A lot of effort for something small, but it was really getting under my skin.

---

### Post by lovinglinux on 2009-06-23
> **v1nsai said:**
> Devilspie won't work for me, I posted my code and ran it with alt+f2 as I said, I know it was running.

Place Window worked great, I love this settings manager, its a lot easier to deal with than gconf-editor thanks a lot for the tip.  I finally got the window to center, the slider that goes with the Place Windows dialog is very misleading though, I was getting very annoyed because no matter where I put the slider the window was either all the way on the left or all the way on the right.  I tried thinking of it in terms of pixels, and did the math and split my screen up the way I wanted it, then plugged in the number in the box and it centered it beautifully.

A lot of effort for something small, but it was really getting under my skin.

Good to know it worked for you. I really like those plug-ins to organize my windows ;)

---

