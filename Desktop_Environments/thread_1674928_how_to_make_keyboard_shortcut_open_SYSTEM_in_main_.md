---
title: "how to make keyboard shortcut open SYSTEM in main menu"
date: 2011-01-24
forum: Desktop Environments
---

### Post by nrundy on 2011-01-24
When I assign a keyboard shortcut to open the main menu, it always opens the "Applications menu" by default. Is there a way to make the keyboard shortcut open the "System menu" by default?

---

### Post by Krytarik on 2011-01-24
I wonder why someone would like to have such function, besides some sort of a rescue thing if the wireless mouse is out of power, like mine recently;), I really didn't know that time how to get into the menu.

You could use xdotool to pretend an actual mouse action and bind it to a key combo:
[http://www.semicomplete.com/projects/xdotool/xdotool#mouse_commands](http://www.semicomplete.com/projects/xdotool/xdotool#mouse_commands)

If you have 10.10 running, you can install it right from the archive:
```
sudo apt-get install xdotool
```If you have 10.04, like me, you  have to activate a backports ppa to get a more recent version,  deactivate it after installing xdotool!:
[https://launchpad.net/~bdrung/+archive/backports]("https://launchpad.net/%7Ebdrung/+archive/backports")

---

### Post by nrundy on 2011-01-25
The reason is because is makes it easier to control the main menu with just key presses (without using the mouse). I've found that in general I can press Alt + F1 +S to go into the System Menu. But if I opened an application from the Applications Menu previously pressing Alt + F1 + S takes me into the Applications menu. I regularly use key presses to initiate log out and restart etc and so it would be much preferable to have the menu open up into the System Menu instead.

Another solution would be to somehow make Ubuntu always open the System Menu when I type Alt + F1 + S even after I've opened things from the Applications Menu. If you have any solutions to this, I'd be grateful. thanks.

---

### Post by Krytarik on 2011-01-25
At my machine Alt+F1 -> S always opens the System menu, no matter what I did before, consider that you cannot press them at the same time, but first Alt+F1 and then S.

If that turns out to be true for you also, then you can use the commands
- xsendkeys: [http://manpages.ubuntu.com/manpages/maverick/en/man8/xsendkeys.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/xsendkeys.8.html)
- xsendkeycode: [http://manpages.ubuntu.com/manpages/maverick/en/man8/xsendkeycode.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/xsendkeycode.8.html)

They are included in the package "lineakd".

Unfortunately "xsendkeys" doesn't work if you want to issue only a single key, so you have to use "xsendkeycode" for the "S". Therefore you have to lookup the keycode of "S" with the tool "xev", enter it in a terminal, then press "s" (lower case), and the keycode gets displayed, it's a number. That number may be different at your keyboard.

I actually use "xsendkeycode" to send keypresses to a TV/video application with my mouse, works good.

---

### Post by nrundy on 2011-01-25
Krytarik, try this:  Applications > Ubuntu Software Center.

once the software center opens (you can close it now if you want), type Alt + F1 + S and tell me if your key presses still go to System Menu. In my box, they now go to Applications Menu.

---

### Post by Krytarik on 2011-01-25
Ok, I have the same behaviour like you, although I replicated it with another (custom) menuitem in the Applications menu, since I have moved USC to Administration, because I never use it.

So it indeed seems to be a bug, that whenever you run a lauchner, which is located directly in the main "group" of Applications, from then on, if you use Alt+F1 and then press "s", you activate the corresponding menuitem in Applications instead of System, which is in that case "Sound & Video".

You could obviously workaround this by placing USC into another location, maybe into "System Tools" in your case, or into "Administration" like me.

---

### Post by stinkeye on 2011-01-26
One way is
```
xdotool key alt+F1; xdotool key Right Right
```

---

### Post by Krytarik on 2011-01-26
> **stinkeye said:**
> One way is
```
xdotool key alt+F1; xdotool key Right Right
```
Great, xdotool is a lot easier to use in that task!;)

---

### Post by nrundy on 2011-01-26
could this be reported as a bug?  what is xdotool? a program one has to download and install?

---

### Post by Krytarik on 2011-01-26
> **nrundy said:**
> could this be reported as a bug?  what is xdotool? a program one has to download and install?
Yes, I do believe it is a bug, as I mentioned earlier, of "gnome-panel", look if it's already reported before.

Look my first post in this thread on how to install "xdotool".

---

### Post by nrundy on 2011-01-26
Hey Krytarik and others, would you guys visit the bug report I submitted and mark that it affects you too? Hopefully they'll fix it!

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/708333](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/708333)

---

