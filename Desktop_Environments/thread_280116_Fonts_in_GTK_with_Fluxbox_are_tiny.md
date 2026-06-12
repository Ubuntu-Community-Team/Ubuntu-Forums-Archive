---
title: "Fonts in GTK with Fluxbox are tiny"
date: 2006-10-19
forum: Desktop Environments
---

### Post by intimidat0r on 2006-10-19
Well, it's like this. I started up fluxbox and noticed that in all gtk programs (or maybe it's every program, I don't quite know) had really really small font sizes in like the menus and buttons and well...pretty much every control.

I also discovered that if I start fluxbox from the command prompt with 'startfluxbox' or 'start' without letting gdm run at all, the fonts are very large in the menus and buttons and all the controls.

I googled and everything but to no prevail. Any idea how I might fix this?

Thanks. :)

---

### Post by Drone4four on 2007-12-26
I'm having this same problem on Gutsy.  The fonts for the menus in Fluxbox are so tiny too.  The only Fluxbox theme that has a readable font size is Artwiz.

---

### Post by Drone4four on 2007-12-26
Odd-rationale in #Ubuntu suggests deleting the  ~/.fluxbox folder and then  logging in again.  
Odd-rationale also suggested reinstalling fluxbox in synaptic.


I'll try those two things now and report back.

---

### Post by Drone4four on 2007-12-26
Niether worked.

Odd-rationale now suggests contacting an expert on fluxbox named RedSquirrel.

---

### Post by -grubby on 2007-12-27
if you install gtk-chtheme you can change the font size for GTK apps

---

### Post by RedSquirrel on 2007-12-29
> **Drone4four said:**
> I'm having this same problem on Gutsy.  The fonts for the menus in Fluxbox are so tiny too.  The only Fluxbox theme that has a readable font size is Artwiz.

What sort of an Ubuntu system do you have? Are you setting up Fluxbox on a command-line system or a server or something? It's possible you are missing some font packages.

---

### Post by Drone4four on 2007-12-30
> **RedSquirrel said:**
> What sort of an Ubuntu system do you have? Are you setting up Fluxbox on a command-line system or a server or something? It's possible you are missing some font packages.

I'm on a Gutsy 7.10 used as a desktop system.

btw RedSquirrel: I am so happy to see you respond to my post.  I tried sending you a private message but it wouldn't let me.  Apparently you can't receive message because your inbox is full or for some other reason.

---

### Post by Drone4four on 2007-12-30
> **nathangrubb said:**
> if you install gtk-chtheme you can change the font size for GTK apps I made changes to GTK font size using gtk-chtheme.  I changed it from font 8 or 10 to 22.  Attached are before and after shots   Notice how the firefox File/Edit/View buttons are larger, but the font in the gnome terminals are unchanged?

---

### Post by Drone4four on 2007-12-30
I just installed xfce4.  The fonts of GTK apps are even tinier than in Fluxbox.  See attached for a screenshot.

---

### Post by urukrama on 2007-12-30
> **Drone4four said:**
> I'm having this same problem on Gutsy.  The fonts for the menus in Fluxbox are so tiny too.  The only Fluxbox theme that has a readable font size is Artwiz.

That would be because of the font settings of the theme you use. Open the theme.cfg file of your theme (either in /usr/share/fluxbox/styles or /home/USERNAME/.fluxbox/styles) and look for the font settings. Change to whatever font and size you like. Reconfigure fluxbox and the changes should be visible.

> **Drone4four said:**
> I made changes to GTK font size using gtk-chtheme.  I changed it from font 8 or 10 to 22.  Attached are before and after shots   Notice how the firefox File/Edit/View buttons are larger, but the font in the gnome terminals are unchanged?

The fonts inside the gnome-terminal are controlled in the preferences settings of gnome-terminal itself, not by the gtk theme you use. Go Edit > Current Profile  and you will see an option to change the fonts and size (as well as colours, background image, etc.)

---

### Post by Drone4four on 2007-12-30
Thanks urukrama.  

If the solution is to adjust the font size in every gtk app, then I'll have adjust the font size for gnome-terminal, firefox, and abiword every time I switch window managers.  

urukrama: rather than solving the problem of global font size in Fluxbox or xfce, you've given me a workaround.

---

### Post by RedSquirrel on 2007-12-30
Maybe your DPI is too small. I use 96.

Just add the following line to your ~/.Xresources file (create that file if it does not exist):

```
Xft.dpi:        96
```If you use gdm to login, the ~/.Xresources file should be loaded automatically by gdm.

If you login on the console, you can add

```
 xrdb -merge $HOME/.Xresources
```to your ~/.xinitrc file.

You can make sure the setting was applied with this command (on the command line):

```
xrdb -query | grep dpi
```

Here is the top portion of my ~/.xinitrc:

```
#!/bin/sh

userresources=$HOME/.Xresources
userdefaults=$HOME/.Xdefaults
usermodmap=$HOME/.Xmodmap

# merge in defaults and keymaps

if [ -f $userresources ]; then
    xrdb -merge $userresources
fi

if [ -f $userdefaults ]; then
    xrdb -merge $userdefaults
fi

if [ -f $usermodmap ]; then
    xmodmap $usermodmap
fi


```

---

### Post by urukrama on 2007-12-30
> **Drone4four said:**
> If the solution is to adjust the font size in every gtk app, then I'll have adjust the font size for gnome-terminal, firefox, and abiword every time I switch window managers.  

urukrama: rather than solving the problem of global font size in Fluxbox or xfce, you've given me a workaround.

Sorry, I don't think I understand what you are saying. You mentioned earlier (as also shown in your screenshots that you can change all fonts in your gtk apps, except for gnome-terminal. I explained that this is because you have to set the fonts for that app seperately. Do you still have a problem, then? Firefox and Abiword don't allow you to change the font size independently so if you can control your gtk settings fonts, you don't need to worry about that.

Or am I missing something (always possible)? :confused:

Can you change the font settings in Xfce (using the xfce settings)?

---

### Post by Drone4four on 2007-12-31
urukrama: It's my fault.  I was unclear.  Basically, when I log in to xfce or Fluxbox, even if I change the font size using gtk-ctheme, gnome-terminal, firefox and xchat still have ultra tiny fonts.  I can change the font size for each app to 26 , but when I switch back to gnome from fluxbox, I'll have to change the font size for all 3 apps back to 8 or 10.  

Now I'll try RedSquirrel's suggestions and report back with results.

---

### Post by Drone4four on 2007-12-31
RedSquirrel fixed it.  See attached for what my gnome-terminal looks like in Fluxbox.

Thanks RedSquirrel.

---

