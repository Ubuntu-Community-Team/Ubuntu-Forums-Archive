---
title: "removing gnome3 gnome-shell"
date: 2011-04-01
forum: Desktop Environments
---

### Post by penguins916 on 2011-04-01
Hello all.

I thought with my new 11.04 beta install it would be fun to try out gnome3.

I found a quick guide: [http://norman.hooper.name/blog/post/58/ubuntu-natty-narwhal-gnome-3/](http://norman.hooper.name/blog/post/58/ubuntu-natty-narwhal-gnome-3/)

did it and changed my default session to gnome-shell in the login preferences.

After playing around with it didn't like it at all and went about trying to get to the login preferences gui from gnome classic. I couldn't find any.

I tried to sudo apt-get remove gnome-shell and that just didn't make anything launch upon reboot. 

I then messed with /etc/xdm/custom.conf and changed it so it wouldn't auto login. (i think xdm is right... not in ubuntu now)

Upon reboot, i could select ubuntu-classic and ubuntu(unity) but when i tried to run them they both failed. Gnome3 was the only thing that would work.

I then found: [http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

and followed there removal instructions and once again, gnome-shell, even though it was supposed to be removed, was the only session that would run.


So that's where i am. 
Any ideas on how to kill the monster that is gnome3 beta?


Thanks tons for saving my computer!

---

### Post by kio_http on 2011-04-02
If I remember well during the KDE 3 to 4 transition, there was a problem about install directory, so Kubuntu packaged KDE 4 to install to /XXX/KDE4 instead of /XXX/KDE. That way both versions could run alongside.

Maybe your GNOME-shell has overwritten GNOME 2 and you might have to remove it and install GNOME 2.

---

### Post by penguins916 on 2011-04-02
Is that just the gnome-session package? I tried sudo apt-get installed that and it said nothing needed to be changed or altered.

I can also go metacity --replace and that works as needed if that helps.

Thanks again everyone.

---

### Post by penguins916 on 2011-04-02
Just reinstalled a lot of stuff and I am now able to boot into gnome2 with like 5 error messages on start.

Gnome-shell did upgrade a lot of packages. All I had to do was remove them and reinstall. 

I am going to go with a fresh 11.04 install anyway because I am noticing some speed issues with gnome and still some oddities T don't want track down.

Thanks for the help.

Edit: 
This has been solved but I can't figure out how to mark it as such. Sorry...

Edit: Ok found it.

---

