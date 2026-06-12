---
title: "ubuntu menus/button/icons"
date: 2010-07-26
forum: Desktop Environments
---

### Post by jcroyle on 2010-07-26
hello everyone i just upgraded to ubuntu 10.04 the netbook distro.  at the desktop view there is a list of about 10 buttons/menus listed on the left hand side, is there anyway to control what buttons/menus are listed and which icons are listed under each of them?  having a netbook i would like to remove and unclutter the desktop view as much as possible but i dont want to remove those apps i still want to be able to open those apps if i want to even if by removing those icons and menus/buttons makes it a pain.  any help would be great thanks.

---

### Post by UberStudent on 2010-07-26
I've never used the netbook edition so don't know if alacarte will work for you, but you can press CTL+F2 and type in alacarte and hit enter to try to see if hiding programs in alacarte works. It's the preferred way, but like I said I don't know about netbook edition and alacarte.

For a solution system wide open a terminal and type ```
sudo gedit
``` and enter your password and leave the terminal and gedit open. Then type ```
sudo nautilus
``` and enter your password then navigate to ```
/usr/share/applications/
``` and scroll to the file for the program you want to hide. Drag it onto gedit and drop it there and then at the bottom line of the text you'll see add ```
NoDisplay=true
``` and click save. Add that text for all the programs you want to hide. You'll need to repeat this procedure after the programs update.

---

