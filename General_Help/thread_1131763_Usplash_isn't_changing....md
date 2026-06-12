---
title: "Usplash isn't changing...?"
date: 2009-04-21
forum: General Help
---

### Post by HaydenGribble on 2009-04-21
Hi, I am a Gnome user and recently i have installed xubuntu-desktop and I think it is very good. When I shut down my computer that day, the splash screen that showed was the xubuntu screen and I thought that it looked pretty cool and better than the regular ubuntu one so I was glad it was there. When I started up the computer, it showed the original ubuntu splash screen again.

I tried the command ```
sudo update-alternatives --config usplash-artwork.so
``` and selected the xubuntu splash file and it said it was confirmed, but still the computer shows the xubuntu splash only on shutdown.

How can I get it to replace the ubuntu splash at startup?
Thanks for your help.

---

### Post by HaydenGribble on 2009-04-23
Sorry to bump, but are there any suggestions before this thread is crowded upon by hundreds of others?
Thanks for any help given...

---

### Post by drs305 on 2009-04-23
Try selecting it via StartUpManager, a gui app used for tweaking startup options in grub. It has a section on usplash as well.

Install StartupManager and start it:
```

sudo apt-get install startupmanager
gksudo startupmanager  # or System, Administration, StartUp-Manager

```

Go to the second tab, Appearance tab, and select the desired usplash theme in the bottom section.

For more info on StartUp-Manager, see the link in my signature line.

---

### Post by HaydenGribble on 2009-04-24
I'm afraid that that suggestion didn't work for me. It still only changes the shutdown splash screen, the startup one is still the regular 'ubuntu' one. Thankyou for the reply.
Any other suggestions? Thanks.

---

### Post by drs305 on 2009-04-24
My only other suggestion would be to run:
```
sudo apt-get install --reinstall usplash
```
While it runs watch the terminal and make sure it goes through updating the intitramfs. If it doesn't, run this to update it:
```
sudo update-initramfs -k all -u
```

---

### Post by HaydenGribble on 2009-04-29
I'm sorry, but as frustrating as it is, this did not work for me. Thanks for any further help.

---

### Post by drs305 on 2009-04-29
I installed xubuntu-artwork-usplash via synaptic and then ran:

```
sudo update-alternatives --config usplash-artwork.so
```
and selected the xubuntu splash option.

When I shutdown, I got the xubuntu splash, but when it restarted I got the same result as you - the ubuntu splash screen. :-(

I did some experimenting and got it working correctly (xubuntu splash on boot and shutdown) after running this command:
```
sudo dpkg-reconfigure -phigh usplash
```

It will probably work for you as well, hopefully ending your frustration.

:-)

---

### Post by HaydenGribble on 2009-05-01
Nope, frustration still here... I tried exactly what you did but did not work. Thanks for your time anyway.

---

### Post by drs305 on 2009-05-01
The only other piece I can add to the puzzle is that this is where the files are located on my computer:

> 
/usr/lib/usplash/usplash-artwork.so
/usr/lib/usplash/usplash-theme-xubuntu.so
/usr/lib/usplash/usplash-theme-ubuntu.so
/etc/alternatives/usplash-artwork.so
/var/lib/dpkg/alternatives/usplash-artwork.so


I hope you get this resolved.

---

