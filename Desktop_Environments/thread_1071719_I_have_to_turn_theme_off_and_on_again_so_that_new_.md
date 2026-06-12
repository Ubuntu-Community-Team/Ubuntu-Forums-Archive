---
title: "I have to turn theme off and on again so that new windows get themed"
date: 2009-02-16
forum: Desktop Environments
---

### Post by mrpacman01 on 2009-02-16
I hope the title isn't too long. I was trying to be as descriptive as I could :)

The problem is (as the title describes) that when I power on my laptop, the theme I have installed on gnome is not set automatically.

I took some screen shots because I'm afraid that I won't make myself understandable :P

[LIST]
[*][This is what Firefox looks like after I have applied the theme after a restart and _then_ fired up firefox]("http://dl.getdropbox.com/u/616082/clear_looks.png")
[*][To fix the theme I fire up Appearance]("http://dl.getdropbox.com/u/616082/clear_darklooks.png")
[*][Apply any other theme and then apply the original theme ]("http://dl.getdropbox.com/u/616082/clear_darklooks2.png")
[/LIST]
You see the problem?

Thanks in advance,
mrpacman

---

### Post by mrpacman01 on 2009-02-17
No one seen anything like this? :neutral:

---

### Post by cptr13 on 2009-02-17
You're saying that you set your theme to something specific in appearence (say "clearlooks") and when you reboot...it doesn't keep that theme?  Or it DOES keep the theme, but when you open new windows or apps they don't have that theme?  

Can you be a little more specific?  The only thing I'm understanding is that something is not keeping your theme setting.

---

### Post by mrpacman01 on 2009-02-17
> **cptr13 said:**
> You're saying that you set your theme to something specific in appearence (say "clearlooks") and when you reboot...it doesn't keep that theme?
YES! Exactly :). But also when I change the theme to the theme I want after a reboot and then open up a new app, the new app doesnt have the theme :/

I hope this is more understandable :)

---

### Post by Yashiro on 2009-02-17
Does this only happen with the Darklooks theme that you have installed?

---

### Post by mrpacman01 on 2009-02-17
> **Yashiro said:**
> Does this only happen with the Darklooks theme that you have installed?
Funny that I didn't think of checking this out. :D

Actually this problem only applies to the DarkLooks theme.

---

### Post by Yashiro on 2009-02-17
The problem maybe lies with the way you've installed it and the permissions on the files.

How did you install the theme?

---

### Post by mrpacman01 on 2009-02-17
> **Yashiro said:**
> The problem maybe lies with the way you've installed it and the permissions on the files.

How did you install the theme?
I installed the Hardy Theme 2.0 ([LINK]("http://gnome-look.org/content/show.php/Hardy+Theme?content=74045")) I used the .deb link.

---

### Post by Ng Oon-Ee on 2009-02-17
I've heard that there's some bugs on a few colours in DarkLooks. I recommend the Ubuntu-studio theme for a dark theme (though I agree DarkLooks is great). I can't seem to remember where I saw the workaround for DarkLooks though, it involved changing the Hex colors in some config file.

---

### Post by duanedesign on 2009-03-06
The darklooks theme is broken... but it can be fixed. In a terminal enter:

    gksudo nautilus

then navigate to /usr/share/themes/Darklooks/gtk-2.0

You should find a file called gtkrc.

Edit this and search for an entry (in style "clearlooks-tooltips") which reads:

    bg[NORMAL] = @tooltip_bg_color
    fg[NORMAL] = @tooltip_fg_color

Change this to read:

    bg[NORMAL] = @tooltip[COLOR="Red"]s[/COLOR]_bg_color
    fg[NORMAL] = @tooltip[COLOR="Red"]s[/COLOR]_fg_color

[COLOR="Red"]Note all we've done is add the extra 's'.[/COLOR]

Save and exit and you should have your darklooks back. I did not want to have to install a different theme so I am glad this worked:)

See the bug report at [https://bugs.launchpad.net/ubuntu/+s...as/+bug/215472](https://bugs.launchpad.net/ubuntu/+s...as/+bug/215472) for more.


EDIT: Notice when you enter gksudo nautilus into the Terminal there is an error msg related to the problem.

duanedesign@duanedesign-laptop:~$ gksudo nautilus
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier
Initializing nautilus-share extension
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier

---

