---
title: "Making Sudo Nautilus Look Nicer"
date: 2008-10-16
forum: Desktop Environments
---

### Post by joey-elijah on 2008-10-16
Hey all!

A superfluous question no doubt, but whenever i have to run a programme or need to copy a file as root, nautilus looks... very windows 3.1. 

Is there anyway to change the default look of sudo nautilus to match that of the general gnome desktop?

---

### Post by Pogeymanz on 2008-10-16
This is because the root user account is using a crappy gtk theme.

Open a terminal and login as root:
```
sudo su
```

And then run whatever program you use to set the gtk-theme. I'm not sure what it is in Gnome, so maybe someone else can help here...

---

### Post by shawnrgr on 2008-10-16
sudo ln -s /root/.themes/ ~/.themes

I think. Check the dirs first im at work and can't look ;)

---

### Post by joey-elijah on 2008-10-16
hmm. I'm lost. lol

---

### Post by shawnrgr on 2008-10-16
Did you try anything that was suggested? If so can you show us the output?

---

### Post by jhernandez1270 on 2008-10-16
> **joey-elijah said:**
> hmm. I'm lost. lol

basically, the themes you have set as 'your' username are not the themes set for the root username...so when you launch a root nautilus window it uses root's theme (which I think is no theme).

So, you can either create a symlink ( sudo ln -s /home/root/.themes ~/.themes) or log in as root ( sudo su ) then use System>Preferences>Appearance and change the theme.

Even easier reboot, log in a root and change your theme

---

### Post by kerry_s on 2008-10-16
press alt+f2, type> gksudo gedit /root/.gtkrc-2.0

put:
gtk-theme-name = "yourtheme"
gtk-icon-theme-name = "yourtheme"


example:
gtk-theme-name = "Tango"
gtk-icon-theme-name = "Tango"

---

### Post by shawnrgr on 2008-10-17
> **jhernandez1270 said:**
> ...create a symlink ( sudo ln -s /home/root/.themes ~/.themes)...

I believe root user resides under / not /home

---

### Post by wizard10000 on 2008-10-17
> **joey-elijah said:**
> Hey all!

A superfluous question no doubt, but whenever i have to run a programme or need to copy a file as root, nautilus looks... very windows 3.1. 

Is there anyway to change the default look of sudo nautilus to match that of the general gnome desktop?

The way I do it is to create a launcher with this command line -

gksu nautilus /

Works fine and keeps my theme  ;)

---

### Post by Pogeymanz on 2008-10-17
> **shawnrgr said:**
> sudo ln -s /root/.themes/ ~/.themes

I think. Check the dirs first im at work and can't look ;)

This is actually the best way to do it, IMO. If you type this command into a terminal, root nautilus will always have the same theme as non-root nautilus.

If you want root to have a different theme, then my way is the best.

---

### Post by joey-elijah on 2008-10-17
hmm. 

i've tried all of the suggestions but it's still using its own Windows 3.1 loving homage. 

> sudo ln -s /home/root/.themes ~/.themes
tells me 
> ln: creating symbolic link `/home/joey/.themes/.themes': File exists

which is awesome. but launching nautilus it hasn't changed.

creating a launcher (gksu nautilus /) doesn't change it either..

followed the, er, follwing:

> press alt+f2, type> gksudo gedit /root/.gtkrc-2.0

put:
gtk-theme-name = "yourtheme"
gtk-icon-theme-name = "yourtheme"


still no comprendez!

---

### Post by cwizman on 2008-10-17
Try this:

sudo ln -s /home/joey/.themes /root/.themes

---

### Post by joey-elijah on 2008-10-19
> **cwizman said:**
> Try this:

sudo ln -s /home/joey/.themes /root/.themes

> ln: accessing `/root/.themes': Too many levels of symbolic links

Hmmmph.

---

### Post by KOld Iron on 2008-10-19
I agree the theme for Nautilus run with root looks not very nice, but to be quite honest, that's the best way for me to be aware that I am doing things with root permissions.

I am afraid, if I would run it with the same theme as my regular one, I would lose track, what I am doing with what permissions. So every time I start Nautilus and I see the ugly theme, I KNOW that every single action I do can have a real impact.

My recommendation would be to use at least a different theme than your regular user account is using.

---

### Post by aysiu on 2008-10-19
First of all, it should be ```
gksudo nautilus
``` and **not** *sudo nautilus*. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Secondly, you want to link the user's theme to root's, not vice versa. Since you already tried all those other commands, there are too many symbolic links, so we have to fix that: ```
sudo mv /root/.themes /root/.themes.old.link
mv ~/.themes ~/.themes.old.link
``` Go back to System > Preferences > Appearance and fix your user theme to how you would like it.

Now we can make the symbolic link properly: ```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

