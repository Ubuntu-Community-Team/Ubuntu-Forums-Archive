---
title: "Ubuntu 10.04 Customisation"
date: 2010-05-12
forum: Desktop Environments
---

### Post by .Daniel on 2010-05-12
Hi all, this is my first post :) I'm new to Linux so don't shred me up :P

Okay, so I've installed Ubuntu 10.04 and I wanted to customise it a little (splash screen, login screen, window theme) - problem is, all of the tuts on the net have been written for 9.xx or lower and none of them seem to work with the version that I am running (I can't remember why right now because I looked this up a few days ago but there was a tab missing in 10.04 that was there in 9.xx and below).

So anyway, could someone kindly tell me how to customise these things running Ubuntu 10.04?

Thanks in advance for any help,
Daniel

---

### Post by jamoncillo on 2010-05-12
check this thread regarding thesplash screen ;)


[http://ubuntuforums.org/showthread.php?t=1446949](http://ubuntuforums.org/showthread.php?t=1446949)

or, if you want just the precise info that worked there:


```

sudo update-alternatives --config default.plymouth

```

```

gksu -u gdm dbus-launch gnome-appearance-properties 

```


about changing the theme:

this themes are great for me, I just love them. give them a try, and if you don't like any let me know and I'll tell you where to get even more

adde the bisigi repository key
```

 sudo add-apt-repository ppa:bisigi/ppa && sudo apt-get update

```

and install the Bisigi themes:
```

sudo apt-get install bisigi-themes

```

I think they were like 200Mb, can't remember exactly. But they do add a lot of options.
Once installed just right click anywhere in your desktop ->change desktop background -> Tab 'Theme'

---

### Post by .Daniel on 2010-05-14
Thanks alot for the reply - I've downloaded the themes and applied one that I like so that's great :) But I'll probably end up getting bored of them after a while so more would be good :P

The splash screen code didn't work for me but I'm alright with the default to be honest - I'm more keen on changing the login to one of the ones that you find on Gnome-look.org - any ideas how I could apply one of those in 10.04?

---

### Post by .Daniel on 2010-05-16
Bump :)

---

### Post by steveneddy on 2010-05-16
Look here and bookmark the page - it will help you immensely for you to read this page to get a handle on what Ubuntu can do and what you can do with Ubuntu.

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Desktop_Add-ons](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Desktop_Add-ons)

Bookmark this page:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

---

### Post by .Daniel on 2010-05-19
Thanks for the links, they're really informative - I guess this means that there isn't a way to customise the login screen then? :(

---

### Post by wojox on 2010-05-19
This is the old hack I use for changing the login screen:

```

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. Then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F8
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

```

---

### Post by spydeyrch on 2010-05-19
> **.Daniel said:**
> Thanks for the links, they're really informative - I guess this means that there isn't a way to customise the login screen then? :(

Yes there is. I do it all the time. I would say that the easiest way would be to use ubuntu tweaks. Check out their website. Just add their ppa to your sources and then install it. The website is this:

[http://ubuntu-tweak.com/source/ubuntu-tweak-stable/](http://ubuntu-tweak.com/source/ubuntu-tweak-stable/)

If you need help installing/adding the ppa's just ask. :-)

-Spydey

---

### Post by spydeyrch on 2010-05-19
apart from being able to change the splash screen, loging screen, background, theme, visual candy, etc. You can install programs, sources, and tweak (hence the name) other features about ubuntu. It is SUPER simple to use and awesome. Plus, the only real cli work that you have to do is to add the ppa. That is all. Simple, easy, efficient, and does what you want plus more.

-Spydey

---

### Post by .Daniel on 2010-05-24
> **wojox said:**
> This is the old hack I use for changing the login screen:

```

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. Then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F8
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

```

Doesn't work for me... Through searching with Google, it looks as though that only works for Ubuntu 9.xx

> apart from being able to change the splash screen, loging screen, background, theme, visual candy, etc. You can install programs, sources, and tweak (hence the name) other features about ubuntu. It is SUPER simple to use and awesome. Plus, the only real cli work that you have to do is to add the ppa. That is all. Simple, easy, efficient, and does what you want plus more.

-Spydey

This gives the ability to change the background of the login screen but doesn't allow you to install themes from gnome-look.org - cool program anyway though :)

...

Anyone else have any other ideas? :confused:

---

### Post by Skara Brae on 2010-05-24
> **jamoncillo said:**
> I think they were like 200Mb, can't remember exactly.
It said 265 Mb, to be precisely :)

That is very nice! Thank you, jamoncillo (*thumbs up*)

---

### Post by fullexplorer on 2010-05-24
nice, i was looking for something like that too :)

---

### Post by friTTe81 on 2010-05-24
Yeah thanks, just installed and changed the theme =)
noticed that in some of them the "close" "minimize" etc appeared to the right now

---

### Post by gfxguy on 2010-05-29
I just upgraded to 10.04 also, and while I'd love to play and tweak the appearance, there are a few functional differences that I'm not really happy about and can't seem to figure out how to fix.  I didn't want to start a new thread.

The first thing is that I want a just plain text login screen.  I have two users on my computer, they're both me, but one is a lower UID (less than 1000) matching what I have at work.

So what happens is the login screen doesn't display that user name.  It was just simpler and faster with a text prompt that said "username:" and I didn't even need the mouse at all.

The other thing is switching users... with a tweak that I used before, the user switcher would list other accounts, so I'd just use the user switcher applet and immediately be prompted for the password for that account... and I could switch back and forth really easily, keeping both sessions alive.  Now I need to login all over again each time I switch back and forth.

TIA for any help.

---

### Post by hok00age on 2010-05-29
Download this tutorial:
[http://dl.dropbox.com/u/6786897/ubuntu_customization.tar.gz]("http://dl.dropbox.com/u/6786897/ubuntu_customization.tar.gz")

Hope it helps you

Regards :)

---

