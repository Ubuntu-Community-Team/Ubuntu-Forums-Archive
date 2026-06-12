---
title: "Set Gnome 3 Window Rules, such as &quot;Always on Visible Workspace&quot;"
date: 2012-05-08
forum: Desktop Environments
---

### Post by Offlein on 2012-05-08
When using Compiz as my window-manager, I can set special window rules so that, say, a window with class "Gnome-terminal" can always be sticky, and consistently appear on all workspaces (desktops).

In Gnome 3's "Gnome Shell", Compiz rules do not seem to apply. Does anyone know how I can set these?

---

### Post by Offlein on 2012-05-08
Well I (unhappily) succeeded in what I was doing, although it's nowhere near as easy as in Compiz.

I downloaded [DevilsPie]("http://live.gnome.org/DevilsPie"):
```
sudo apt-get install devilspie
```

Then I created a Configuration directory to hold my "sticky window" rules file, which I'll describe later:
```
mkdir ~/.devilspie
```


And I used "xprop" to get the information about the windows I wanted to create rules for:
```

xprop

```

You run that command, and then click the window. In my case, I clicked on the gnome-terminal window I had open, and got a whole ton of stuff, which included this:
```

WM_CLASS(STRING) = "gnome-terminal", "Gnome-terminal"

```

That told me the class of the window was "Gnome-terminal".

So I then created my sticky windows rule file: (I use vim, but you could use anything)
```

vim ~/.devilspie/sticky.ds

```

Inside, I put exactly this, which covers both my Gnome-terminal window by class and my Empathy chat client by role:
```

(if
  (or
    (is (window_role) "chat")
    (contains (window_class) "Gnome-terminal")
  )
  (begin
    (stick)
  )
)

```

I saved that file and ran devilspie in my terminal, with -a to attach it to existing windows, and --debug to check for errors:
```

devilspie -a --debug

```

There were no errors, so I killed it (ctrl-c), and then hit alt-F2, and typed:
```

devilspie -a

```

Which runs it in the background, attached to all existing windows. Success!

---

### Post by kellemes on 2012-05-09
> **Offlein said:**
> Well I (unhappily) succeeded in what I was doing, although it's nowhere near as easy as in Compiz.


Indeed, but Compiz is nowhere near as powerfull as DevilsPie ;)

Since DevilsPie is unmaintained you may be interested in [DevilsPie2]("http://www.gusnan.se/devilspie2/")

---

### Post by markbl on 2012-05-09
> **Offlein said:**
> 
In Gnome 3's "Gnome Shell", Compiz rules do not seem to apply. Does anyone know how I can set these?

FYI - If you don't have 2 displays then you won't know this but in gnome-shell the default is that all windows on the secondary display are "sticky" across workspaces. It works out well - so consider getting a second display!

---

### Post by TheFuzz4 on 2012-10-22
While that may be true about the secondary display, for me I prefer to not have the sticky monitor and instead both of my displays change with the workspace.

---

