---
title: "Problems with yakuake/gnome-terminal"
date: 2009-01-13
forum: General Help
---

### Post by Dirjel on 2009-01-13
On Yakuake's default settings, when you launch a program, say, firefox, from yakuake, you have to leave that session open in the terminal or else it will close the firefox window that you have open.  When you enter the same command, "firefox," into the gnome-terminal, it opens Firefox independently of the terminal dialogue, so I can continue to use the terminal normally, or simply close the terminal without affecting my Firefox session.  I went into the Yakuake settings and changed the environment to TERM=gnome-terminal.

Now, if I launch a program (again, Firefox), I can continue to enter more commands without opening a new tab, and I can close that tab and still use firefox.  However, when I try and use top in yakuake, it gives me an error message.
dirjel@dirjel-comp:~$ top
'gnome-terminal': unknown terminal type.

How can I fix that?  When I open gnome-terminal, IT can run top fine, and yakuake was able to run top perfectly before I changed the settings.  Is there a way to have yakuake behave as gnome-terminal and still run top?

---

### Post by Dirjel on 2009-01-13
Oh, and all the other commands I can think to use work fine.

apt-get install
free
firefox
gimp
pcmanfm
nautilus

Just not "top" for some reason.

EDIT:  info won't work either.  It says:
info: Terminal type `gnome-terminal' is not smart enough to run Info.

---

### Post by Dirjel on 2009-01-16
Weird... I changed the terminal type back to xterm, and now it behaves like the gnome-terminal, but is able to run top and info.

I don't really understand what happened, but I guess this thread is done?

*mark as solved*

EDIT:  The forum won't let me mark this thread as solved, go figure.

---

### Post by hikaricore on 2009-01-16
If you have any further issues with yakuake I suggest trying out guake.

```
sudo apt-get install guake
```

It's not quite as advanced as yakuake but it behaves as a gnome-terminal and supports transparency properly. ^_^

---

### Post by Dirjel on 2009-01-16
I'll probably try that one, too.  I just installed Tilda, and while it lacks many of the features that Yakuake had (static tab bar, cntrl+shift+v for paste, option for underscore cursor), it's really pretty.  And by pretty, I mean incredibly basic looking.  There is no outline, toolbar, anything on it.  I set it up to fill the whole screen with 35% transparency, and told compiz to give it a fade animation on open and close.  It looks really nice.

---

### Post by hikaricore on 2009-01-16
Meh tilda is outdated and to the best of my knowledge unmanaged.

---

### Post by Dirjel on 2009-01-16
I tried Guake, but it's a lot uglier than Yakuake was.  Also, it isn't transparent, unlike yakuake is.  Guake just shows my desktop color when I turn it fully transparent, whereas I can see my currently-running applications through yakuake and tilda.

I think I'll stick with tilda for now, but if it gives me problems I'll probably go back to yakuake.  Thanks anyway, dude.

---

