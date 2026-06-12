---
title: "How do I uninstall mplayer?"
date: 2005-03-18
forum: Desktop Environments
---

### Post by inphlict on 2005-03-18
I followed this guide to install it, I don't like it anymore and want to uninstall it.

[http://www.ubuntuforums.org/showthread.php?t=94&page=1&pp=10&highlight=uninstall](http://www.ubuntuforums.org/showthread.php?t=94&page=1&pp=10&highlight=uninstall)

So far I did 

cd /home/inphlict/MPlayer-1.0pre5
sudo make uninstall

Then I got this output:

rm -f /usr/local/bin/mplayer /usr/local/bin/gmplayer /usr/local/man/man1/mplayer.1
rm -f  /usr/local/bin/mencoder /usr/local/man/man1/mencoder.1
Uninstall completed

I tried to open it from the shortcut I made and it didn't work, which means it was uninstalled

I then deleted all the other files I had downloaded from that guide

However I still have /usr/local/etc/mplayer and I don't know how to delete

Can someone please help me? I'm new to linux so please keep the steps simple. Thank you in advance.

---

### Post by inphlict on 2005-03-18
Can someone please suggest something? I really need help :(

---

### Post by lorap on 2005-03-18
hi friend!
i propose you use VLC player for everything.
VLC's its own codecs built in in the simple executable.
to install in do this Computer-->System Configuration-->Synaptic Package Manager.
after you get inside it go to the Settings-->Repositories.after the repositories window shows up,mark there all options ignoring warning messages then press Ok button.
after the repositories window closes up press the Reload button at the left up corner and wait.once the process's complete press the Search button and write in VLC then press Ok button.
once the synaptic's found it out for you mark it for install and press Apply button.
now you're done.
have a nice day.
pavel

---

