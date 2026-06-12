---
title: "boot to text screen, and maybe later start graphics mode"
date: 2012-03-13
forum: Desktop Environments
---

### Post by sudodus on 2012-03-13
I want to boot to a text screen, but have the possibility to start a graphics DE. Let's say LXDE unless there is a strong reason to use something bigger.

I think it can be a good idea when running a server, because most of the muscles can be used for the server jobs. But when I want to log in and do something, it would be nice to be able to run graphics via the console. (I already know how to run graphics via ssh remote login, but that can be sluggish.)
 
How should such a system be configured and what command should I use to start the graphics DE?
-- 
Decades ago I was running Unix in Sun workstations like this:
 - login to a text screen
 - run ***x*** to get graphics

---

### Post by sudodus on 2012-03-13
> **oldfred said:**
> There have been several threads with users asking how to boot to command line. I have not followed but found this one.

[http://ubuntuforums.org/showthread.php?p=9227346](http://ubuntuforums.org/showthread.php?p=9227346)
Which is edit grub
gksudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash text&#8221;
I often search the forum with this from google as its search is better than the forum search. Just append this to any search to restrict it to the forum.
site:ubuntuforums.org
or for all linux sites:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Minimal install is just that. Only a kernal and enough drivers to connect to the Internet to download just what you want.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Not sure how all the somewhat different versions are updated to include efi. Servers have had UEFI a lot longer than desktops, so I am surprised that efi does not work better.

gksudo gedit /etc/default/grub
 GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash text&#8221;
or simply adding temporarily ***text*** to the command line in the grub menu makes the computer boot text mode, even if there are DE drivers installed.

and then
```
startx
```
does the trick, according to

> **oldfred said:**
> @sudodus
It may be worthy of its own thread to get the latest info from someone who knows.
The old way always was 
startx

But then (with gnome2) they said this was better:
#or now preferred to restart gdm, I have seen all of these as preferred but do not know if one is better or not.
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm

But you do not have gdm and I do not know now with Unity and gnome3 what is correct.
You could look in /etc/init.d and see if you have something??

My gdm is just a link to a script that has this in it:

And it works!

By the way, I just discovered a parallell thread about the same thing, but with another title
[[COLOR="SeaGreen"]_Server to GUI (on demand)_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1940309")

---

