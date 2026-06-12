---
title: "H(Y)elp!"
date: 2005-06-03
forum: Desktop Environments
---

### Post by breen92uk on 2005-06-03
I'm having problems with GNOME Yelp:

Initially Yelp would not run - no error messages, the starter would run, then nothing would happen. I tried running it in terminal, which gave an error message saying it was missing the file "libgtkbedmoz.so". I found that file and moved it to the directory it required ("/usr/lib").
Now it crashes with an error mesasge (in terminal) saying that it requires a file called "yelp-bookmarks.xbel". This file, nor any of that type, exists anywhere on my machine.
I have tried re-installing Yelp via synaptic - no difference. I think it's something to do with Thunderbird as the problem started when I installed it and the file "libgtkbedmoz.so" was in "/usr/lib/mozilla-thunderbird", but I'm not sure.

Has anyone got any ideas?

Thanks, 
breen92uk

---

### Post by ola on 2005-06-03
I'm not totaly shure on this idea.. but you might try to remove the package and reinstall it..

One way of doing so would be to use this commands
> 
sudo dpkg -P yelp
sudo apt-get install yelp


As I said.. I'm not sure that it doesn't do any harm.. I tried it on my computer and it worked..

Good luck

---

### Post by az on 2005-06-03
Look at the installer logs in /var/log and see if some package gave errors when installed...

Other than that, do you have any non-official repositories or funky packages installed?  If not, file a bug report.

bogzilla.ubuntu.com

---

