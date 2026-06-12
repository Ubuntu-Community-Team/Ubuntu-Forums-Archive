---
title: "Hardy Heron Cli plus Openbox."
date: 2008-05-19
forum: Desktop Environments
---

### Post by kagashe on 2008-05-19
Hi,

I have done Hardy Heron Cli install from alternate CD and have added openbox obconf fbpanel firefox and Synaptic so far and I like what I see with:
$ free -m
       total      used    free
Mem:    312        247      64
-/+ buffers/cache   88     223
Swap    996          0     996

I am going to add wallpaper, try some other panel instead of fbpanel, menu and othet software and will need all the help.

Although I have started openbox with startx command I can't find .xinitrc to add fbpanel. I am starting it from openbox terminal.

kagashe

---

### Post by urukrama on 2008-05-19
> **kagashe said:**
> 
Although I have started openbox with startx command I can't find .xinitrc to add fbpanel. I am starting it from openbox terminal.

You can just create that file if you don't have one now. See [here]("https://wiki.ubuntu.com/CustomXSession") for more details.

---

### Post by kerry_s on 2008-05-19
> I have done Hardy Heron Cli install from alternate CD and have added openbox obconf fbpanel firefox and Synaptic so far and I like what I see with:
$ free -m
total used free
Mem: 312 247 64
-/+ buffers/cache 88 223
Swap 996 0 996

right, jwm rocks, panel included, does backgrounds, all with out adding extra programs.

---

### Post by kagashe on 2008-05-19
> **urukrama said:**
> You can just create that file if you don't have one now. See [here]("https://wiki.ubuntu.com/CustomXSession") for more details.Thanks. This is how the file looks like at present:
> #!/usr/bin/env bash

lxpanel &
exec openbox

Now I get lxpanel on openbox.

I have added pcmanfm and using Tango icon themes. I have also added a wallpaper in pcmanfm Preferences.

kagashe

---

### Post by kagashe on 2008-05-19
> **kerry_s said:**
> right, jwm rocks, panel included, does backgrounds, all with out adding extra programs.
I know jwm rocks but I don't like menu configuration method through complicated file.

I find that the menu on lxpanel auto updates as I add applications.

kagashe

---

### Post by kerry_s on 2008-05-19
> **kagashe said:**
> I know jwm rocks but I don't like menu configuration method through complicated file.

I find that the menu on lxpanel auto updates as I add applications.

kagashe


you probably didn't install "menu" (uses update-menus)jwm can use the same thing like fluxbox and openbox. that's okay though openbox rocks just as hard, i used openbox for a long while way back when. it's good to try different things. :)

---

### Post by kagashe on 2008-05-19
Another reason going for openbox and pcmanfm was my fascination for the new LXDE. I was having some difficulty installing it on Cli but finally resolved them. Here is [my post]("http://ubuntuforums.org/showpost.php?p=4993178&postcount=101") regarding that on LXDE thread.

kagashe

---

### Post by kagashe on 2008-06-08
> **kerry_s said:**
> you probably didn't install "menu" (uses update-menus)jwm can use the same thing like fluxbox and openbox. that's okay though openbox rocks just as hard, i used openbox for a long while way back when. it's good to try different things. :)I installed jwm. The latest version is available in Hardy repositories. I used update-menus and it works. Thanks.

kagashe

---

