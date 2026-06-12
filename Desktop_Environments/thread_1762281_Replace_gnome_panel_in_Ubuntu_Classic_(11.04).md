---
title: "Replace gnome panel in Ubuntu Classic (11.04)"
date: 2011-05-19
forum: Desktop Environments
---

### Post by rimez on 2011-05-19
Hi,

In previous releases of Ubuntu it was possible to replace the gnome panel (with AWN for example) by going into gconf-editor and replacing gnome-panel with the panel of my choice (see screen)

Unfortunately this doesn't seem to have an affect on Ubuntu Classic desktop. 

Does anyone know how to do it with Natty (replace gnome-panel with AWN)?

[IMG]http://img6.imagebanana.com/img/bwumxxpq/Selection_043.png[/IMG]

---

### Post by beyondwithinitself on 2011-05-19
I am having a similar issue.  My system has 2 user accounts, both admin.  Prior to upgrading to Natty, I had panels disabled and only AWN loaded on startup.  Upon upgrading, gnome-panel is back to loading on both accounts.  I went with the gconf-editor approach, and it worked for my girlfriend's account, although I can't get rid of the one persistent gnome-panel (I made it transparent and removed all applets from the panel, auto-hide and threw it in bottom-left corner so she won't notice a difference)

My account, however, will only load gnome-panel.. the only way to load AWN at all is through an "avant-window-navigator" command in Terminal (and it only stays open as long as Terminal does).  

I'm surprised Ubuntu would mess with our settings like this!

---

### Post by kerry_s on 2011-05-19
Run the command with alt+f2, not the terminal.

---

### Post by Copper Bezel on 2011-05-19
If the gconf-editor setting isn't being read, then there are two options. The first is to use Compiz's Widget Layer plugin to make Gnome Panel a widget object - you'll theoretically never see it, but it's not ideal, because it still loads. The other is to locate the binary and simply disable it by unmarking it as executable. It's in /usr/bin .

For AWN, just make it a startup application. You might need to delay it, as 

sleep 40s; avant-window-navigator

because it may be loading but coming up invisible, an odd and unpredictable error I never found the cause of before I stopped using a full Gnome session.

---

### Post by rimez on 2011-05-19
> **Copper Bezel said:**
> If the gconf-editor setting isn't being read, then there are two options. The first is to use Compiz's Widget Layer plugin to make Gnome Panel a widget object - you'll theoretically never see it, but it's not ideal, because it still loads. The other is to locate the binary and simply disable it by unmarking it as executable. It's in /usr/bin .

For AWN, just make it a startup application. You might need to delay it, as 

sleep 40s; avant-window-navigator

because it may be loading but coming up invisible, an odd and unpredictable error I never found the cause of before I stopped using a full Gnome session.

Thanks Copper Bezel, I was hoping to avoid a situation like that as it's a pretty dirty hack, but alas, I have no other option. I'll change the binary.

---

### Post by kerry_s on 2011-05-19
the problem is there was a change, you guys have old settings, on a clean install it looks like this.(see pic)

i looked at the script, no setting for panel.

---

### Post by Copper Bezel on 2011-05-19
I have similar feelings about disabling the binary, which is why I hope someone using 11.04 will drop in with a real solution for the new gconf. It never occurred to me that gconf, necessarily, can't clean out old entries for depracated settings. Yuck. This is the sort of thing that makes me want to have as little to do with gconf as possible (and I thank God for CompizStandalone on this.)

---

### Post by rimez on 2011-05-19
I disabled the binary by marking it as not executable. It worked BUT I lost my alt-f2 run dialog. 

Reverting back to gnome-panel. 

I must say, I'm getting a little bit more ticked off by some of the changes made to Ubuntu in 11.04 -- I won't even begin to talk about Unity. It feels as if users are being locked down more and more. One of the beauties of Ubuntu (and Linux in general) is the fact that it's so customizable.

Sure I can move to another distribution but I really think the Ubuntu community is the best. I don't want to loose that. 

Anyway, I guess I need to find new ways of working within Ubuntu.

---

### Post by Copper Bezel on 2011-05-19
Oh, Alt+F2 is a Gnome Panel feature, so you can't have the one without the other. Alternatives exist, however - xfce4-utils includes xfrun4, which is comparable to the Gnome Run Dialog, and KDE's krunner works quite handily as well, sort of how you'd expect an AWNish replacement for Gnome's to behave. I've taken to using Synapse as a replacement for both the Run Dialog and the Main Menu - it's very smart and quick.

---

### Post by kerry_s on 2011-05-19
okay, i found where they moved it to.
look in "/usr/share/gnome-session/sessions" you'll see "classic-gnome.session" open that with a root text editor.

ps: i use gexec for alt+f2 when i disable gnome-panel, just disable the stock & create with gexec as the command.

---

### Post by Copper Bezel on 2011-05-19
Excellent find, but if that's the case, then it's a bad move, since it applies to all users. I suppose that, to avoid being messy, one would need to create a third Gnome session just for AWN.

Edit: Oh, wait, I'm a moron. Why are we doing this from a Classic session? Disable the Unity plugin and restart Compiz, and we should get the same effect.

---

### Post by rimez on 2011-05-19
> **kerry_s said:**
> okay, i found where they moved it to.
look in "/usr/share/gnome-session/sessions" you'll see "classic-gnome.session" open that with a root text editor.

ps: i use gexec for alt+f2 when i disable gnome-panel, just disable the stock & create with gexec as the command.


thanks for finding the proper config file and the alt-f2 replacement. It's very much appreciated.

Now if I can find a replacement for Window Applets (puts the title bar and window control buttons in the task bar) I will be set :)

---

### Post by rimez on 2011-05-19
> **Copper Bezel said:**
> ...
Edit: Oh, wait, I'm a moron. Why are we doing this from a Classic session? Disable the Unity plugin and restart Compiz, and we should get the same effect.

I'm the moron, are you telling me I can get what I want by using the standard Ubuntu desktop?

---

### Post by Copper Bezel on 2011-05-19
Well, it works either way, whether you want to use the Classic session or the Unity one, but as I understand it, yes, it would have been simpler to start with the Unity session and disable the Unity plugin in CompizConfig there rather than to start with the Classic session and disable the Gnome Panel. That would also mean that all the changes would be confined to the user account.

Edit: Ooh. I'm liking gexec. Thanks, kerry_s!

---

### Post by kerry_s on 2011-05-19
> **rimez said:**
> thanks for finding the proper config file and the alt-f2 replacement. It's very much appreciated.

Now if I can find a replacement for Window Applets (puts the title bar and window control buttons in the task bar) I will be set :)

google "namebar applet" i think thats what your looking for.

---

### Post by kerry_s on 2011-05-19
> **Copper Bezel said:**
> Well, it works either way, whether you want to use the Classic session or the Unity one, but as I understand it, yes, it would have been simpler to start with the Unity session and disable the Unity plugin in CompizConfig there rather than to start with the Classic session and disable the Gnome Panel. That would also mean that all the changes would be confined to the user account.

Edit: Ooh. I'm liking gexec. Thanks, kerry_s!

i agree using unity with out the plugin seems the easiest way now.

---

