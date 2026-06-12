---
title: "Gnome: appearance changed to &quot;classic&quot; theme after 20 seconds (vmware tools missing)"
date: 2011-07-19
forum: Desktop Environments
---

### Post by pmorch on 2011-07-19
After a completely fresh install of Natty I tried to log in. Unity didn't work because my hardware didn't support it, so I went with "Ubuntu Classic" / gnome 2.0.

After login, things looked relatively ok (first screenshot), but after 20 seconds, the theme changed to something I call "classic" - looks like a bare-bones gnome theme (second screenshot).

EDIT: As noted in the comment below, the following solution doesn't *really* work:

It turned out that it was because I hadn't installed any VMware tools for my virtual machine.

$ sudo apt-get install open-vm-tools

and all was well (last screenshot).

Just wanted to post my findings.

---

### Post by pmorch on 2011-07-20
Oh, no! After a reboot it did work. But now it is back to misbehaving again. I fiddled with re-installed open-vm-tools a couple of times and it somewhat worked, but not reliably. In the end it failed consistently. 

I tried installing the original vmware-tools, and that didn't work either. Installing the vmware tools did fail some of the components, but continued anyway.

So bottom line: This *isn't* solved. Any pointers welcome.

And by the way, how do I mark a thread as unsolved, after it (erroneously) was marked solved?

Peter

---

### Post by Krytarik on 2011-07-20
That is related to this bug:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Please try this workaround first:
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

If this doesn't work, see these earlier threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

And this is another workaround that may work with Natty 11.04:
[http://ubuntuforums.org/showthread.php?p=10800526#post10800526](http://ubuntuforums.org/showthread.php?p=10800526#post10800526)

Greetings.

---

### Post by pmorch on 2011-07-21
> **Krytarik said:**
> That is related to this bug:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)
...
And this is another workaround that may work with Natty 11.04:
[url]http://ubuntuforums.org/showthread.php?p=10800526#post10800526[/url

From there, I got the suggestion to install lightdm instead of gdm and even though it looks less nice, it works flawlessly.

I tried the suggestion to put a delay in gnome-settings-daemon.desktop, but I had to have > 30 seconds delay for our setup here, and that meant:

1. After initial login I have a black-ish look
2. After a little while that turns grey
3. After the > 30 seconds it turns black correctly.

Very annoying. lightdm saved the day! :-) Thanks!

---

### Post by Krytarik on 2011-07-21
LOL:-D Yeah, that is a great workaround, too! And since LightDM is set to replace GDM from Oneiric 11.10 on anyway, why not switch right now!? ;-) Of course its appearance still needs a bit of polishing, though.

---

