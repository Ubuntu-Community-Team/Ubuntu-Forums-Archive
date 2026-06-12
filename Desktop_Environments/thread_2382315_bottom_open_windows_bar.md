---
title: "bottom open windows bar"
date: 2018-01-11
forum: Desktop Environments
---

### Post by ivanlrojales on 2018-01-11
Hi everyone, i don't know if this is the best place to post my problem.
I have ubuntu 17.10 and I want to remove the bottom bar which shows the open windows and I have tried to disable the window list gnome extension but nothing occurs. The fact is that I have the dash-to-dock extension enabled but when the dock appears the open windows bar is above the dock and it is horrible. Could anyone tell me how to remove this bar? I am running gnome shell 3.26.2.

---

### Post by Frogs Hair on 2018-01-11
Have you logged out or rebooted since disabling the extension ? When you login there is more then one session available please add what session you are logged into .

---

### Post by ivanlrojales on 2018-01-11
I have restarted the pc and the bar continues appearing. What do you mean with the session I'm logged into?

---

### Post by again? on 2018-01-11
Appears to be a couple of posts on the [extension page]("https://extensions.gnome.org/extension/602/window-list/") about not being able to turn off in 17.10.
You could delete or move the extension folder @ ~/.local/share/gnome-shell/extensions/window-list@gnome-shell-extensions.gcampax.github.com
Also check you are not using the Taskbar extension which can show a bottom panel.
Log out.

---

### Post by ivanlrojales on 2018-01-11
I have deleted the folder and rebooted the laptop and the bar is still there. It looks like the bar is part of the system and not an extension.

---

### Post by again? on 2018-01-11
You may not have seen this which I edited in later.
"Also check you are not using the Taskbar extension which can show a bottom panel."
By default there is no bottom panel.

As per Frogs Hair's reply, post the output of
```
echo $DESKTOP_SESSION
```

---

### Post by ivanlrojales on 2018-01-11
No, I am not using taskbar extension. And I'm in gnome classic

Is there any way to change the session? I mean, can I change gnome classic?

I have seen that I can change to gnome vanilla for example. But I would like to remove the bar in the classic. Is it possible?

---

### Post by again? on 2018-01-11
Try holding down the keys Super+alt and right click on the panel.
Should get a menu where you can delete.

Still got me confused though???
You said you were using the gnome-shell dash to dock extension
but you appear to be not using a gnome-shell session.

---

### Post by ivanlrojales on 2018-01-11
No menu appears with this key combination

---

### Post by again? on 2018-01-11
> **ivanlrojales said:**
> No menu appears with this key combination
Output from
```
echo $DESKTOP_SESSION
```
and
```
ps -ef | grep [p]anel
```

---

### Post by ivanlrojales on 2018-01-11
If I put on the shell the command echo $DESKTOP_SESSION the output is gnome-classic. So I think I am using this gnome shell session. Why the key combination doesn't work for me??

---

### Post by ivanlrojales on 2018-01-11
This is the output to the command ps -ef | grep [p]anel
gdm        853   802  0 ene11 tty1     00:00:00 ibus-daemon --xim --panel disable
ivan      1224  1199  0 ene11 tty2     00:00:00 ibus-daemon --xim --panel disable

---

### Post by again? on 2018-01-11
Try ctrl+Super + right click.

---

### Post by ivanlrojales on 2018-01-11
I have tried all the possible combinations and no menu appears. When I'm going to log in I can choose between classic, Ubuntu, or Ubuntu xorg. Ubuntu and Ubuntu xorg let me remove the bar, but the classic session still shows the bar.

---

### Post by again? on 2018-01-11
> **ivanlrojales said:**
> I have tried all the possible combinations and no menu appears. When I'm going to log in I can choose between classic, Ubuntu, or Ubuntu xorg. Ubuntu and Ubuntu xorg let me remove the bar, but the classic session still shows the bar.

OK I'm just installing vanilla-gnome-desktop and will take a look.

---

### Post by ivanlrojales on 2018-01-11
Ok, thank you for your time.

---

### Post by Frogs Hair on 2018-01-11
> [COLOR=#000000][INDENT]the classic session still shows the bar. [/INDENT]


[/COLOR]
The bottom panel/window list is a feature of the classic session . [COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by ivanlrojales on 2018-01-11
Okay, then I will consider changing to other session. Thanks everyone!

---

### Post by again? on 2018-01-11
Testing here I can remove by renaming the window-list system extension.
```
sudo mv /usr/share/gnome-shell/extensions/window-list@gnome-shell-extensions.gcampax.github.com /usr/share/gnome-shell/extensions/window-list@gnome-shell-extensions.gcampax.github.com.bak
```
Log out.

To revert the changes
```
sudo mv /usr/share/gnome-shell/extensions/window-list@gnome-shell-extensions.gcampax.github.com.bak /usr/share/gnome-shell/extensions/window-list@gnome-shell-extensions.gcampax.github.com
```

---

