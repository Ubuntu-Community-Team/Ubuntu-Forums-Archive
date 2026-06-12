---
title: "Theme for root applications"
date: 2005-04-11
forum: Desktop Environments
---

### Post by idn on 2005-04-11
Im using gnome and I use the d3a theme and it works fine in the applications apart from those which require root login, such as firetstarter or the network configuration app. It just defaults to the normal theme. Any explanation?

---

### Post by Whiffle on 2005-04-11
[QUOTE=idn]Im using gnome and I use the d3a theme and it works fine in the applications apart from those which require root login, such as firetstarter or the network configuration app. It just defaults to the normal theme. Any explanation?[/QUOTE]
 When the program looks for config files, like those dealing with how it looks, they look in the home directory of the current user.  When you run a program as root, they look in the home directory of the root user ( /root ).  Since all the configs that you do to change the look as an ordinary user are saved in your home directory, the programs that run as root will never see those configs and use their default settings.  I hardly ever run any root programs so I havn't tried to come up with a solution, but I suppose a guy could simlink all the config files in your home directory to  files of the same name in the /root directory, never tried it though.  Or just copy them all over.

---

### Post by Spark* on 2005-04-11
Because they run as a different user, they can't find the themes you install as a user. You have to put them manually into /usr/share/themes (instead of $HOME/.themes) to make them work.
I wonder how this problem could be fixed in the future.

---

### Post by idn on 2005-04-11
Thanks, but there is no root account on my machine, I just use sudo if I want to do something as root, so theres no way to put it in the root home directory. Its wierd how some themes work and other dont though.

How would I go about resolving the situation if there is no /home/root folder?

---

### Post by Buffalo Soldier on 2005-04-11
Refer to [http://ubuntuforums.org/showthread.php?t=23798](http://ubuntuforums.org/showthread.php?t=23798)

[QUOTE=Artificial Intelligence]Are you tired of that your root applications doesn't match your desktop theme?

Here's the answer, this show with the D3a GTK2 theme. Just change D3a with your favorite GTK theme:

```

cd /home/orion/.themes
sudo cp -r  d3a /usr/share/themes
sudo gedit /etc/gdm/gdm.conf

```

Now I changed under [gui]

GtkTheme=d3a
GtkThemesToAllow=d3a

Check the attached snapshot of Package Manager, it's now with D3a theme instead of human theme.
This will also change the Standard greeter GTK theme.[/QUOTE]

---

### Post by idn on 2005-04-11
Success! thanks alot works fine

---

### Post by nocturn on 2005-04-12
I actually like the fact that they look different.  It reminds me to watch what I'm doing more carefully in those apps.

---

### Post by idn on 2005-04-12
I guess, but I can now use a more eyecandy theme instead of the standard ones. Having said that I normally have firestarter running and its nice that it fits in with my current theme

---

### Post by maqi on 2005-04-12
[QUOTE=idn]Thanks, but there is no root account on my machine, I just use sudo if I want to do something as root, so theres no way to put it in the root home directory. Its wierd how some themes work and other dont though.

How would I go about resolving the situation if there is no /home/root folder?[/QUOTE]

Whether you have a root account or not, root's home folder is not under /home. If you look in the top level directory "/" you will see a folder "/root". This is root's home directory. You should find it there on all linux distros. I suspect it will be there whether you have created a root account or not.

So if you did want to copy configurations from your home directory to root's this is where you would copy them to - as root :)

maqi

---

