---
title: "Change Oneiric appearance like in Natty"
date: 2011-10-15
forum: Desktop Environments
---

### Post by endeavormac on 2011-10-15
I never used Unity much. In Ubuntu Natty, I could go to Gnome Classic and then through Appearance I had a lot of options to change around the look of... I guess thinks? I could set preferences for GTK. Things like window backgrounds, text colors.

In Oneiric, a lot of things have changed. I got my gnome classic back... but it's a bit different, and I can't change around these colors. For example, I can't move around any of the taskbars.

Is there something out there that I can *read* that will help me through this process?

---

### Post by robertmf on 2011-10-15
> **endeavormac said:**
> I never used Unity much. In Ubuntu Natty, I could go to Gnome Classic and then through Appearance I had a lot of options to change around the look of... I guess thinks? I could set preferences for GTK. Things like window backgrounds, text colors.

In Oneiric, a lot of things have changed. I got my gnome classic back... but it's a bit different, and I can't change around these colors. For example, I can't move around any of the taskbars.

Is there something out there that I can *read* that will help me through this process?

[COLOR="DarkRed"]Same question for me.  [/COLOR]

---

### Post by disco.sleeze on 2011-10-15
I am having a similar issue.

I am running Ubuntu 11.10 with Gnome Shell. I have found ways to change the GTK, Icon, and Shell themes but I am a little bothered by the fact that I can't change the color of the "X" that closes a window! lol. I know that sounds petty.

It is a lovely shade of Ubuntu ORANGE right now, and I would like to change it to something that fits my theme more. Any ideas?

---

### Post by robertmf on 2011-10-16
> **disco.sleeze said:**
> I am having a similar issue.

I am running Ubuntu 11.10 with Gnome Shell. I have found ways to change the GTK, Icon, and Shell themes but I am a little bothered by the fact that I can't change the color of the "X" that closes a window! lol. I know that sounds petty.

It is a lovely shade of Ubuntu ORANGE right now, and I would like to change it to something that fits my theme more. Any ideas?

:guitar:  There is not yet much choice in [Appearance]|[Themes] for Gnome3.

And related thread: [http://ubuntuforums.org/showthread.php?p=11349185](http://ubuntuforums.org/showthread.php?p=11349185)

---

### Post by floborg on 2011-10-16
The GNOME Tweak Tool offers some of the old settings, but not everything.  Maybe that Ubuntu Tweak guy will push out an update soon for 11.10 with more settings.

---

### Post by dragonzuela on 2011-10-19
> **disco.sleeze said:**
> I am a little bothered by the fact that I can't change the color of the "X" that closes a window! lol. I know that sounds petty.

Oh me too!  I really don't like the orange highlight color and had it changed to purple with Natty, and it is driving me bonkers that I'm stuck back with orange in Oneiric.

---

### Post by mnamutso on 2011-10-21
its such an annoying color...the whole blackish color aint cool at all!!! 

someone pse save me...

---

### Post by yanes on 2011-10-21
the same problem for me too !??? :(
I want to change applications fonts type and size and gnome menu fonts , in Natty this was possible from 
"Appearance" --> "Fonts" 
in Oneiric that's not possible  

what have I to do ?

---

### Post by kalos on 2012-01-02
Hi! I had these problems in previous versions of ubuntu and maybe you can use the same methods I used to fix them. Looks like the files are still there, but I haven't had time to give it a try.

> **dragonzuela said:**
> I really don't like the orange highlight color and had it changed to purple with Natty, and it is driving me bonkers that I'm stuck back with orange in Oneiric.
You could try modifying the theme settings. Copy it to your home first:
```
mkdir -p ~/.themes/Ambiance/gtk-2.0
cp /usr/share/themes/Ambiance/gtk-2.0/gtkrc ~/.themes/Ambiance/gtk-2.0/.
cp /usr/share/themes/Ambiance/index.theme ~/.themes/Ambiance/.
``` (Not sure if the last one is necessary.)
Then edit that gtkrc file. Make big changes first to see if it has any effect (you might need to log out and log in). I think the above should work for unity and you should use gtk-3.0 instead of gtk-2.0 for Gnome Shell. Not sure.

> **disco.sleeze said:**
> I am running Ubuntu 11.10 with Gnome Shell. I have found ways to change the GTK, Icon, and Shell themes but I am a little bothered by the fact that I can't change the color of the "X" that closes a window!
You could try modifying the image itself. There are several images named close in /usr/share/themes/Ambiance/unity I'd recommend making a lightweight icon theme as [described here]("http://askubuntu.com/a/42571/9411"). Then you can try photoshopping them to your heart's desire. Be warned that I don't know if this will work in Gnome Shell so make big changes so you know if it's working. The folder does say unity, but the gtk-3.0 folder doesn't have images.

---

