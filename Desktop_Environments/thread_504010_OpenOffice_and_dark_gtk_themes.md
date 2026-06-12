---
title: "OpenOffice and dark gtk themes"
date: 2007-07-18
forum: Desktop Environments
---

### Post by _saiko on 2007-07-18
hi all

In ubuntu 7.04 when i set some dark gtk theme, OpenOffice isn't affected at all by the change but continues to have it's default color theme and icon style.
That's awesome and solves the problem with the dark themes in OO
[U]
I would like to know how is this possible?[/U]
It must be some option that's enabled in ubuntu unlike in other distros.

In my Arch Linux distro my OpenOffice gets all messed up, the icon style is always in hi-contrast mode and cannot be changed and the whole thing gets a black background and all toolbars are black. 

I indeed managed to change the background to white using the Appearance options in OO but that doesn't solve much since it's hard to navigate like that...

I hope sombody knows what i'm talking about

thanks in advanced

---

### Post by mcduck on 2007-07-19
If I remeber right you can just go to OO's settings and choose the icon theme you want it to use.. There are at least couple of themes already installed for it.

---

### Post by _saiko on 2007-07-19
> **mcduck said:**
> If I remeber right you can just go to OO's settings and choose the icon theme you want it to use.. There are at least couple of themes already installed for it.
yes exactly there are a few icon themes in OO u can choose

but from some weird reason OO doesn't let me change a icon theme when i'm using a dark gtk theme

it's always on that hicontrast theme whatever i choose

i tried disabling  that automatic detection of hicontrast mode in accesibility options

doesn't help...


but all of this i'm talking about is a scenario on a different distro

the ubuntu distro comes with OpenOffice that ignores the gtk theme of the system and maintains it's own
That feature is what i want!
but i hope somebody from the developers team or whoever is responsible for that has an answer for me HOW they did it
i just need to know what option they used that's per default enabled so that i get that behavious or OO

---

### Post by _saiko on 2007-07-22
ok i found the solution!

for me to continue using my favourite dark theme, all i needed is to be able to run programs the are messed up with dark themes with some OTHER theme
so i searched for that and found the answer

use "env <path_to_some_gtkrc_file> *command*"

then just create a launcher for such an app u want to run with diff theme and voilá!

enjoy :>

---

### Post by tamias on 2007-07-31
Just to update, the above solution in more depth and with more correct information can be found at [http://ubuntuforums.org/showthread.php?p=3109273](http://ubuntuforums.org/showthread.php?p=3109273)

---

### Post by liquidstate on 2007-07-31
I'm using a dark GTK theme with 7.04, and OO also uses this theme, but its not a problem, as the theme is a dark grey rather than black, its still got enough contrast to be useful. Also, there is the option to change colours individually rather than with a theme.

---

