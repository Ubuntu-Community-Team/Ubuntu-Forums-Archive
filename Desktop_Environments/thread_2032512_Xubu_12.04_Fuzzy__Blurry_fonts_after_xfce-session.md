---
title: "Xubu 12.04 Fuzzy / Blurry fonts after xfce-session"
date: 2012-07-24
forum: Desktop Environments
---

### Post by Janiporo on 2012-07-24
There is similar thread --> [http://ubuntuforums.org/showthread.php?p=12126303#post12126303](http://ubuntuforums.org/showthread.php?p=12126303#post12126303)

But did not solve my problem.

So, I visited xfce-session ( And Lubuntu, gnome classic, gnome + cairo dock with effects). Result is here.

Xubuntu 12.04 "screenshot" (upper)
And Ubuntu 10.04 "Screenshot" (lower)

[IMG]http://kuvaton.com/k/Ym7B.jpg[/IMG]
(Obviously I could not take screenshots the regular way, since It seems to be rendering problem)

I appeared first in xfce-session, so I bet that was the one that is not my friend.

This problem looks just like when I have wrong resolution on my LCD (Usually you must use native resolution [or multiplier / divider of it I think]) but monitors own info says it is correct.

Any Ideas how to "reset" this? :-s

Is the folder/file path correct (in that post)? Seems That I have only .config/xfce4 -named folder. I will try to remove that folder and see what happens.

---

### Post by Janiporo on 2012-07-24
Solved the problem my self.

I deleted following directories:
```
~/.config/xfce4
```
Reset ALL settings concerning desktop (at least), so you are in "just installed operating system"-state.


```
~/.cache/sessions
```
Removes saved sessions


I deleted the xfce-folder, but the problem was the settings was recorded also in sessions-folder. Deleting both got rid of problem.

If anyone can pinpoint the proper file in ~/.config/xfce4 -directory which should be deleted, someone in the future will be thankful.

---

### Post by spazzeri on 2012-08-27
In my case, it was enough to remove ~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml (and ~/.cache/sessions). I still don't know the real reason for the problem though.

---

