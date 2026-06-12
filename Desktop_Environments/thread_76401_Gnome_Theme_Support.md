---
title: "Gnome Theme Support"
date: 2005-10-15
forum: Desktop Environments
---

### Post by unexpected on 2005-10-15
Ok, I don't really like the brown theme...

So, I've gone to [www.gnome-look.org](www.gnome-look.org).

Can anyone give me instructions on how to install these themes once i've downloaded them?

Say, for example, this one:

[http://www.gnome-look.org/content/show.php?content=26050](http://www.gnome-look.org/content/show.php?content=26050)

it comes out as a tarball, and i untar is, but GNOME gives me an error saying that it's an "invalid file type"

---

### Post by manicka on 2005-10-15
You don't need to untar it. Start the Themes control panel

system-->Preferences-->Theme


and then drop the tarball onto it to start the install sequence

---

### Post by bionnaki on 2005-10-15
I prefer [http://art.gnome.org](http://art.gnome.org)
use the theme manager thing
system>preferences>theme
"install new theme"

---

### Post by bvc on 2005-10-15
When a theme has more than one version in a tarball you have to extract its contents into the proper directory. These being metacity themes should go in .themes in your user home directory. You could also extract them (theme directories) anywhere, say the Desktop, and drag/drop them into .themes. Double-clicking or using epiphany on the tarball should cause file-roller to to open the archive.

Oh, using the gnome-theme-manager to install a multi-theme usually causes only the last one to be intalled, or nothing with the error mentioned above. I haven't used the gnome-theme-manager in years.

---

### Post by ArukiRei on 2005-10-19
I've been getting the same error message as unexpected. I've been trying to use the Dream of Ubuntu theme.

[Found here]("Gnome Themeshttp://www.gnome-look.org/content/show.php?content=24907")

I've tried to install this theme through the "install new theme" but keep getting the "invalid file type" error whether I select the tar.gz or the folder. I've tried another theme just to see if this one was a problem, but I'm still getting the same error. Any help is appreciated :D

---

### Post by manicka on 2005-10-19
Try the themes at gnome-look.org. They are usually reliable

---

### Post by ArukiRei on 2005-10-19
[QUOTE=manicka]Try the themes at gnome-look.org. They are usually reliable[/QUOTE]

That's whre I got it from... but still getting error message :confused:

---

### Post by unexpected on 2005-10-19
Do you get this error when you just drag it over to the Theme manager?

Don't untar it or anything. As soon as you d/l it, just drag it over.

---

### Post by ArukiRei on 2005-10-19
Nope... whether I click the "install theme" button or drag it into the theme box I still get the same error.

---

### Post by bvc on 2005-10-20
only gtk, metacity, and icon themes can be installed with the gnome-theme-manager. GDM themes? I don't use a dm but when I did it was gdm, and themes had to be extracted to /usr/share/gdm/themes or similar.

---

### Post by RAOF on 2005-10-20
There's actually a nice app which will let you preview, download, and install gnome themes automatically.  I believe it's called gnome-art or something.  Search for that in synaptic.  It adds an icon to the "system->preferences" menu, called "art manager"

---

### Post by Tachikoma on 2005-10-21
[QUOTE=ArukiRei]Nope... whether I click the "install theme" button or drag it into the theme box I still get the same error.[/QUOTE]
I tried just dropping in the theme manager and still got the same error as you did.  

finally i just put the *.tar in /usr/local/share/themes/ 
and tar -xf

they showed up in theme manager right after that and work fine.

Hope that helps

---

### Post by tmadsen on 2005-10-21
As tachikoma said ... tar -xf <filename> when it lies in i.e. ~/home/<username>/.themes ... Heard several people complain about the gnome theme manager being some sort "out of order" including myself, but this works fine `:)

---

