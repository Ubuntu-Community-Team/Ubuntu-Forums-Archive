---
title: "Help screwed up my xserver won't start"
date: 2006-03-01
forum: Desktop Environments
---

### Post by markymarknz on 2006-03-01
Hey,

I'm afraid I have accidently stuffed up big time.
I had my gnome desktop running sweet then randomly found that my xmms wouldn't run coz it couldn't find liblighthouseblue.so
So I foolishly thought I would uninstall it (coz already had gtk-liblighthouseblue) and didn't ready the unistall properly then noticed it was uninstalling ubuntu-desktop and a whole lot of other important stuff too. To I cancelled out of it and then when I tried reloading the x-server it just crashed and went to terminal. I tried apt-get install ubuntu-desktop and it said I had to do apt-get -f install to fix up some dependencies first.
So I did that and it tried to install ubuntu-sounds but I got this annoying message and it wouldn't install it:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 15775 package 'ubuntu-sounds':
      missing version
E: sub-process /usr/bin/dpkg returned an error code (2)

So yeah I'm pretty screwed and not sure what to do.

Any help or suggestions would be very welcome.
I still have all my home directory and everything intact, I'm pretty sure if I can get the ubuntu-desktop up and running again I will be back in business.

Thanks heaps everyone

---

### Post by angkor on 2006-03-01
Did you cancel it during the removal of the packages? Then try reinstalling ubuntu-desktop.

sudo apt-get install ubuntu-desktop

---

### Post by markymarknz on 2006-03-01
thanks for your reply angkor
actually I already tried that and it says I have to do apt-get -f install to fix the problems and its then that it tries to install the ubuntu-sounds package which has a problem

---

### Post by markymarknz on 2006-03-01
Phew I have finally got the system up and running again !! 
That was an interesting experience

If anyone goes through a similar situation here is what I did

To initially get rid of the dpkg: parse error, in file '/var/lib/dpkg/status' message I found something on google which helped.
Just did:
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

Once that was fixed things got better.
After checking that all the basics programs were installed I still couldn't get X to start.

I reverted back to an old xorg.conf file and changed to nv drivers and X started again !!! :D:D:D

After that I reinstalled my nvidia drivers, reloaded my normal xorg.conf file and was back in business.

Hope this helps someone

---

