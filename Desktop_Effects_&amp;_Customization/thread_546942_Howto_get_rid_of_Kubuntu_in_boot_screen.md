---
title: "Howto get rid of Kubuntu in boot screen?"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by somu on 2007-09-09
Hi,
just recently I installed the KDE desktop but I do not use it any more but stay at Gnome.
Since then I have to stare at the "KUBUNTU" screen wile booting. I did not tell Kubuntu to change my boot screen and also I find it somewhat arrogant from Kubuntu to simply change the boot screen without asking me and without providing any easily visible option in Gnome to get rid of that. After testing it, I really don't like that Kubuntu thing and the way it obviously tries to push away Gnome on my desktop, which started with setting Kubuntu as the default desktop, which is however easy to change, fortunately.
How can I change back the boot screen to "Ubuntu"?

kind regards

Peter

---

### Post by andreid on 2007-09-09
Hello, 
To change back to the classic ubuntu splash screen type
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu.so /etc/alternatives/usplash-artwork.so
To check that the old splash screen was installed, without rebooting, type
sudo usplash
(Press Alt-F7 to return to X)
Cheers

---

### Post by somu on 2007-09-09
Thank you!

---

### Post by Quid on 2007-09-23
Hi - I was installing some of the Graphics Apps from Edubuntu and must have picked up more than I knew ( Synaptic is great that way if you don't pay attention).

I ended up with the Edubuntu Startup bar at the Boot screen, the Edubuntu Theme for login, and Edubuntu logoff splash.

Using the previous post - I was able to get the Logoff Splash to go back to Ubuntu - and I got my Ubuntu Login Screen. ( Splash test worked - and showed the Ubuntu logoff).

I still get the pretty Edubuntu Splash at boot and the Edubuntu Splash again after login!!?
I reset my themes so my user looks like Ubuntu. 

In searching the posts I could only find this one.

Thoughts on ressetting back to Ubuntu?

Thanks

---

### Post by FuturePilot on 2007-09-23
Try```
sudo apt-get remove edubuntu-artwork
```
Then
```
sudo apt-get install --reinstall ubuntu-artwork
```

If that doesn't work it might be this one
```
sudo apt-get install --reinstall feisty-session-splashes
```

---

### Post by Quid on 2007-09-23
Thanks for the quick reply, FuturePilot

The Remove/Install fixed the Edubuntu splash AFTER login - but the Bootsplash remained...

I tried the reinstall --- no additional change, the Edubuntu bootsplash remains.

This link:
[http://ubuntuforums.org/showthread.php?t=516032](http://ubuntuforums.org/showthread.php?t=516032)

was used to get the shutdown splash to work ( before this post)...

Sigh... 

Any other thoughts?

---

### Post by FuturePilot on 2007-09-23
Try
```
sudo apt-get remove edubuntu-artwork-usplash
```
```
sudo apt-get install usplash-theme-ubuntu
```

---

### Post by Quid on 2007-09-23
No Joy FuturePilot

Msgs back..

Package edubuntu-artwork-usplash is not installed, so not removed

usplash-theme-ubuntu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Thanks for the suggestions... ](*,)

---

### Post by FuturePilot on 2007-09-23
Ah, I think I know
```
sudo apt-get install --reinstall usplash-theme-ubuntu
```

---

### Post by Quid on 2007-09-24
Let me get back to you.. I am out of town for a few days...
Thanks mutchly... looks like it is a good direction!

---

### Post by Quid on 2007-09-28
FuturePilot - You rock - Yes this is exactly what we needed!

Thanks A bunch

:KS:KS:KS:KS:KS

---

### Post by FuturePilot on 2007-09-28
Glad I could help:D

---

### Post by bigbrovar on 2007-09-29
in fact u dont have to go true all that stress just download usplash switch and you will be able to change any usplash u want through a nice simple gui interface ....usplash switcher is a  small utility that allows to easily switch your usplash (boot theme). It is useful only if you have installed multiple usplash-artwork packages. u can download it here                                                        

                [http://www.getdeb.net/app.php?name=usplash-switcher](http://www.getdeb.net/app.php?name=usplash-switcher)

---

### Post by GoodGuy98 on 2008-01-11
Thank you for the info on usplash-switcher. I couldn't figure out how to give you an official thank you, so I did it this way.

---

