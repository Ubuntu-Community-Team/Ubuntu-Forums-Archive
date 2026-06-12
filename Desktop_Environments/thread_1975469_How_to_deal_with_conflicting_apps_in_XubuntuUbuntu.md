---
title: "How to deal with conflicting apps in Xubuntu/Ubuntu?"
date: 2012-05-07
forum: Desktop Environments
---

### Post by neu5eeCh on 2012-05-07
Xubuntu is my primary DE, but every now and then I'd like to log in to Ubuntu on the same computer and partition. 

The only conflicts concern the use of xbindkeys and nautilus. When I log into Ubuntu, I'd like to run a script that kills xbindkeys *after* startup.

Also...

Since Xubuntu is my primary DE, I use the following to kill the Nautilus desktop:

dconf write /org/gnome/desktop/background/show-desktop-icons false

However, Ubuntu doesn't like this.

I'd like to be able to issue the following command after Ubuntu has started up:

> dconf write /org/gnome/desktop/background/show-desktop-icons trueAnd, when Xubuntu starts up:
> 
dconf write /org/gnome/desktop/background/show-desktop-icons falseCan anyone spell out how to do this or point me in the right direction?

---

### Post by mips on 2012-05-07
Can't help you out with any of your issues but why not run ubuntu in a VM?

I've got 11.10 running in a VM.

---

### Post by neu5eeCh on 2012-05-07
> **mips said:**
> Can't help you out with any of your issues but why not run ubuntu in a VM?

I've got 11.10 running in a VM.

I might do that, although it's just as easy, if not easier, to issue the commands (listed above) in a terminal as soon as Ubuntu has started up. Just thought there ought to be an easy way to automate. I think a script is what I need to create, but I've never done that before. I'm going to start googling.

---

### Post by brainwash on 2012-05-07
One solution would be to create a .desktop file for each command and place them in ~/.config/autostart or /etc/xdg/autostart (system-wide).

The key is to specify the environment by adding following parameter:
```
OnlyShowIn=GNOME;Unity;

**OR**

OnlyShowIn=XFCE;
```

---

### Post by neu5eeCh on 2012-05-07
> **brainwash said:**
> One solution would be to create a .desktop file for each command and place them in ~/.config/autostart or /etc/xdg/autostart (system-wide).

The key is to specify the environment by adding following parameter:
```
OnlyShowIn=GNOME;Unity;

**OR**

OnlyShowIn=XFCE;
```

Thanks! That's exactly the kind of advice I'm looking for. Saves me an hour of Googling.

---

### Post by neu5eeCh on 2012-05-07
Hey, once I got the right combination of Google search terms, I found the solution from [here]("http://askubuntu.com/questions/112784/de-specific-startup-applications") **DE Specific Startup Applications**:

> This can be a starting point for your  question. You can place a conditional statement withing the command to  execute field in the Startup Application. This command will check what  is the current desktop session and will act based on that. E.g.  
  [INDENT]   if [ "$DESKTOP_SESSION" == "ubuntu" ]; then (echo "Unity"); else (echo "Gnome") ; fi
 [/INDENT]  The condition checks if it is Unity session and prints Unity if true. Otherwise, it will print Gnome.
You can replace the echo commands with any command you wish to execute or omit the else part.
Another example:  
  [INDENT]   if [ "$DESKTOP_SESSION" == "ubuntu" ]; then (shutter); fi
 [/INDENT]  This will run Shutter application only in Unity.


---

