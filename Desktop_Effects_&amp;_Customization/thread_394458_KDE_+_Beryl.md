---
title: "KDE + Beryl"
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by Error47 on 2007-03-26
Hello all, this is my first post on these forums. I have been using Ubuntu for about 3 days, and I love it. I switched to Linux because I was frustrated with Windows. It stopped working on me.

Well anyway, I installed Beryl, then decided to go further and installed the kubuntu desktop thing from synaptic. After restarting, I saw a new splash or login screen that says kubuntu. When it boots up, beryl loads and I don't see anything new. I don't think I am seeing that KDE theme thing on the bottom like I am suppose to. Right clicking on that beryl logo, > select window manager, it shows it's on beryl. And there is an option for KDE. Clicking on that deselects  and disables the nice beryl theme. And I still don't see any difference. Is it possible to get both working at the same time? Or should I have just installed Kubuntu then install beryl, I don't want to do that because I spent hours installing beryl, mounting my windows and external HD, installing programs etc. 

Also another problem with Beryl, I downloaded an image for the skydome feature, whenever I check that skydome option, it disables beryl. Why doesn't it work?
Oh, and I hope I posted in the right section :)

Thanks.

---

### Post by Error47 on 2007-03-27
Well, if I can't get it to work then the "k"ubuntu is usless. Can I return to the way it was before since the kubuntu package didn't do anything? Or is it possible to make it work?

---

### Post by compmodder26 on 2007-03-27
To get to Kubuntu you need to:

1. Logout
2. At the login prompt, select options->select session.
3. Select KDE from the resulting dialog.
4. Click "Change Session"
5. Re-login

---

### Post by Error47 on 2007-03-28
Alrighty, that worked. I don't really like it now because it doesn't really work the way I want it. Is there a way to remove that package or un-install it?

---

### Post by maddog39 on 2007-03-28
You should be able to just run this command from 'Terminal' and it should return to normal:
```

sudo aptitude uninstall kubuntu-desktop

```
Try that and see if it helps any, but it should.

---

### Post by Error47 on 2007-03-29
No I still have "Kubuntu". There is the load splash, the login, and the windows manager. I disabled KDE but I don't want to see "Kubuntu" When I start up. 

sudo aptitude uninstall kubuntu-desktop  -   did not work.

---

### Post by mendingo84 on 2007-03-29
try this one :

> 
sudo apt-get remove kde-desktop

---

### Post by Error47 on 2007-03-31
Here is the output of that :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde-desktop

```

I think I already un installed it, It is still there and keeps messing things up that I wanted to keep.

---

### Post by bdogg64 on 2007-03-31
```
sudo update-alternatives --config usplash-artwork.so
```

and select the ubuntu splash instead of kubuntu

---

### Post by Error47 on 2007-03-31
Maybe that would work, but it still wouldn't remove kubuntu.

---

### Post by Perfect Storm on 2007-03-31
If you install kubuntu with aptitude it's easy to uninstall, otherwise check synaptic history for libs/applications you installed and then move them one by one.

---

### Post by bdogg64 on 2007-03-31
> **Error47 said:**
> Maybe that would work, but it still wouldn't remove kubuntu.

That was to change your splash image back to the ubuntu

I used this to remove kubuntu completely after trying it out

```
sudo apt-get --purge remove kubuntu-desktop
```

you could also try

```
sudo apt-get --purge remove kde*
```

---

### Post by K.Mandla on 2007-03-31
(Shifting to Desktop Effects & Customization. ;) )

---

### Post by Error47 on 2007-04-02
I tried   "  sudo apt-get --purge remove kubuntu-desktop  " . All I noticed was that the shudown screen went from kubuntu to ubuntu again. I can still see it at startup / log-in.   I set it up so that my computer would log me in automatically, it worked good, but I have to input a password now at the kubuntu log-in screen, and it won't go.

---

### Post by bdogg64 on 2007-04-02
> **Error47 said:**
> I tried   "  sudo apt-get --purge remove kubuntu-desktop  " . All I noticed was that the shudown screen went from kubuntu to ubuntu again. I can still see it at startup / log-in.   I set it up so that my computer would log me in automatically, it worked good, but I have to input a password now at the kubuntu log-in screen, and it won't go.

Did you check your 

```
/etc/X11/default-display-manager
``` 

to see if it was ```
/usr/sbin/gdm
```

I ran into this problem before also... I also ran

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

And it changed by kubuntu splash screen back to ubuntu

Also check

```
sudo update-alternatives --config usplash-artwork.so
```

And make sure the ubuntu splash is chosen instead of kubuntu

---

### Post by Error47 on 2007-04-03
Great, the startup splash is working fine now, and so is the shutdown. The only thing and most important to me is the log in window. I chose for my computer to auto-login. Now when I start-up my computer I see the ubuntu splash, followed by the kubuntu login screen. I would like to remove that log-in screen, and reset it to what I had before (the original).

---

### Post by bdogg64 on 2007-04-03
> **Error47 said:**
> Great, the startup splash is working fine now, and so is the shutdown. The only thing and most important to me is the log in window. I chose for my computer to auto-login. Now when I start-up my computer I see the ubuntu splash, followed by the kubuntu login screen. I would like to remove that log-in screen, and reset it to what I had before (the original).

```
sudo nano /etc/X11/default-display-manager
```

make sure its 

```
/usr/sbin/gdm
```

---

### Post by Error47 on 2007-04-03
That's probably it, my says "  /usr/bin/kdm  ". So how do I change that?

---

### Post by bdogg64 on 2007-04-03
> **Error47 said:**
> That's probably it, my says "  /usr/bin/kdm  ". So how do I change that?

change it to 

```
/usr/sbin/gdm
```

and reboot

---

### Post by Error47 on 2007-04-04
That did it, everything is back to normal now. Thanks guys!

---

