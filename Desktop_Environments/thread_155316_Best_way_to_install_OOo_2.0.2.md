---
title: "Best way to install OOo 2.0.2"
date: 2006-04-04
forum: Desktop Environments
---

### Post by dgermann on 2006-04-04
Hi--

Recently I downloaded OpenOffice 2.0.2 from their website and installed it using alien, and that went without incident. 

However...

When I went to start it up, it did not come up from the gnome menus nor from clicking a file. I had to [edit the wrapper file]("http://www.ubuntuforums.org/showthread.php?t=153168") to make that work.

Then I tried on another machine, first using synaptic to remove the prior instance of OOo. Then install via alien. When I was done, OOo was not on the menus, nor would it start at all from clicking an .odt file.

So, what is the best way to get it installed and then get the prior version off the machine?

Thanks!

---

### Post by Ted_Smith on 2006-06-05
sudo gedit /etc/apt/sources.list

Then add this line:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

Save & close the file, & then run the following commands:

sudo apt-get update

sudo apt-get upgrade

Sourced from : [http://lxer.com/module/newswire/view/53395/index.html](http://lxer.com/module/newswire/view/53395/index.html)

---

### Post by dgermann on 2006-06-08
Thanks, Ted. 

I'll give it a go right after I upgrade to 6.06 Ubuntu!

---

### Post by dgermann on 2006-06-20
Ted and others--

After upgrading tonight to 6.06, I find that my OpenOffice.org is not working at all.

It is not on the menus, and clicking on an .odt file produces only a list of its files available for extract. Clicking on open with produces a cannot find ooffice2 error message.

I tried your method--the new repository--and it says there is nothing to upgrade.

This app is critical to me--it is a production environment.

Any ideas?

Thanks!

---

