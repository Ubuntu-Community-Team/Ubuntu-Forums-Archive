---
title: "cannot change gsettings for lightdm user"
date: 2013-08-14
forum: Desktop Environments
---

### Post by system76panp9 on 2013-08-14
on my Ubuntu 13.04 system I am trying to change some of the login screen
settings which can only be affected apparently by updating the dconf db that
the lightdm process reads when managing the login

I have tried different variations of this basic command:

sudo sudo -u lightdm dbus-launch --exit-with-session gsettings set ...

in each case I get error messages which make it clear that an attempt is
being made to update MY dconf database, that is, the one stored in my
OWN home directory and which would not have any impact on what
lightdm does (for instance, errors saying that the "user" file in the
dconf subdirectory under my home directory cannot be modified)

if I type

sudo sudo -u lightdm whoami

I get back "lightdm" so I have no clue why it still wants to try to
change the dconf settings of my user

I guess I could try to run this as a setup script on greeter launch?
then at least it would not have any reason to look in my home
directory presumably, but where would gsettings then try to look?
what directory is used to store the dconf db for "lightdm"? is it
looking at like the HOME env variable which is somehow copied
over despite the sudo -u to the context in which gsettings is run?

any help would be very much appreciated as I am completely
mystified

---

### Post by steeldriver on 2013-08-14
I must admit I've never thought about doing this, but it appears to work on my 12.04 box (although something - probably the X server? - complains about 'No protocol specified')

Check a property that I know is non-default in my user dconf DB:
```

$ gsettings get org.gnome.desktop.background picture-uri
'/usr/share/backgrounds/Winter_Morning_by_Shannon_Lucas.jpg'
$ 
$ sudo -u lightdm gsettings get org.gnome.desktop.background picture-uri
'/usr/share/backgrounds/warty-final-ubuntu.png'

```

Now try to set lightdm's background picture-uri to something else:
```

$ sudo -u lightdm dbus-launch --exit-with-session gsettings set org.gnome.desktop.background picture-uri /usr/share/backgrounds/Twilight_Frost_by_Phil_Jackson.jpg
No protocol specified
No protocol specified

```

Check that it got set
```

$ sudo -u lightdm gsettings get org.gnome.desktop.background picture-uri
'/usr/share/backgrounds/Twilight_Frost_by_Phil_Jackson.jpg'

```

Verify that my user background picture-uri wasn't affected
```

$ gsettings get org.gnome.desktop.background picture-uri
'/usr/share/backgrounds/Winter_Morning_by_Shannon_Lucas.jpg'

```

Can you post the actual error you are getting? What property are you trying to change?

---

