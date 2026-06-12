---
title: "Turn off the login screen user name picker thing."
date: 2009-10-29
forum: Desktop Environments
---

### Post by RalphSleigh on 2009-10-29
Hey

So I just upgraded to Xubuntu 9.10 and it's replaced the login prompt with a widget where I have to click my username and then enter my password. How can I change it back to the old prompt? I have looked though the settings guis without luck.

This is one of the 1st things I turn off on any windows install as well. It has a GUI to control the behaviour. 

-Ralph

---

### Post by crazyone on 2009-10-29
ditto here. i would liek to know hwo to do this too. i jsut perfer the typing on my laptop

---

### Post by slumbergod on 2009-10-29
same here. it's like an extra step

---

### Post by minaev on 2009-10-30
Same for me...

---

### Post by dj-toonz on 2009-10-30
I've found a post how to hack it somehow it says its about the dell mini 9 but might works on other machines but YMMV so it's up 2 you to try it

[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

---

### Post by slumbergod on 2009-10-30
I'd be happy if the XFCE team changed their logo too. It doesn't look like a small, fast mouse - it looks like a stumpy, fat pig. Now that Xfce4.6 has become such a great environment they need something more sleeker.

---

### Post by laxdad8992 on 2009-10-31
I found this on a different ubuntu forum, and it works, though I still have to click a little "login" button - after clicking the login button it gives me the "name" screen, followed by the "password" screen. At those screens I can simply type my login, hit enter, then password and hit enter. If I can figure out how to make it automagically open the screen where I type the login name, I will re-post.

```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter /disable_user_list true

```

---

### Post by minaev on 2009-11-02
**laxdad8992**,
It works. With the only correction that there is no whitespace between 'greeter' and '/disable', that is it should be:

```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

Thank you!

---

### Post by preetamkumar on 2009-11-02
> **minaev said:**
> **laxdad8992**,
It works. With the only correction that there is no whitespace between 'greeter' and '/disable', that is it should be:

```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

Thank you!

Hi,
Recently I upgrade from Ubuntu 9.04 to 9.10 through online upgrade. But after upgrading my login screen has been changed to xubuntu splash screen. I want my ubuntu login screen how to change the login screen from xubuntu splash screen to ubuntu login screen.

---

### Post by crazyone on 2009-11-02
well this works for now. im hoping to figure out how to make it like it was in ubuntu 9.04. or in gdm 2.26. with jsut a box for username and than a new box for password. would be nice to figure this out without having to uninstall the gdm and install the older version. thanks though

---

### Post by XubuRoxMySox on 2009-11-02
I'm still waiting for my upgrade to arrive in the mail (bandwidth issue here), but I've read that in Karmic you get *only one* opportunity - when you first install the OS - to choose automatic login. Thereafter it's always and forever auto-login. I auto-login anyway (sure speeds things up) and never bother with the user name picker thing. So um, couldn't you just re-install Xubuntu (don't format the /home partition) and choose "Login Automatically" to be rid of the user name picker thing? Not that you would want to on a shared 'puter though.

-Robin

---

### Post by kjur on 2009-11-04
no, you can choose it later in the settings. login screen settings are much simpler tough than in the previous versions

---

### Post by robobot on 2009-11-04
Actually, you can just start typing your username and a little box pops up for text entry. you don't need to touch the mouse.

I still want to get rid of the name browser, though. It's a security risk.

---

### Post by beercz on 2009-11-05
Anyone know how to change the login screen?

---

### Post by Elviswind on 2009-11-07
> **robobot said:**
> Actually, you can just start typing your username and a little box pops up for text entry. you don't need to touch the mouse.

I still want to get rid of the name browser, though. It's a security risk.

Yeah, I'm not happy with the name browser either.

---

### Post by lol197282 on 2009-11-16
> **minaev said:**
> **laxdad8992**,
It works. With the only correction that there is no whitespace between 'greeter' and '/disable', that is it should be:

```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

Thank you!

cheers code works a treat (solved a security issue & personal peeve).

---

### Post by slumbergod on 2009-11-18
I finally gave up on the default login window too. It is attractive looking but it really bugs me and having a list of account names to choose from essentially halves the security. The code above worked for me too so my thanks for that.

---

### Post by cd-r80 on 2010-02-12
More solutions?

---

