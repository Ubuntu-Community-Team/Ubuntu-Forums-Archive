---
title: "Graphical login screen does not accept password"
date: 2004-10-28
forum: Desktop Environments
---

### Post by Faerine on 2004-10-28
Hi,

I have Warty on a G4 PPC.  I installed it in text mode, and I chose quite long passwords (over 15 symbols) for both the account I was prompted to create and the root account (with sudo).  I had no problem using them in text mode. However, after I set up GNOME and rebooted, I was prompted to login on a graphical screen. This screen seems to only accept 15 symbols in the password field, so there is no way for me to enter either of my passwords. I enter them up to the 15th symbol, and of course I cannot login. I haven't figured out how to reboot in text mode either. If anybody has experienced a similar problem or just knows how to fix it, I'll be grateful for any help!  :lol:

---

### Post by FLeiXiuS on 2004-10-28
[QUOTE=Faerine]Hi,

I have Warty on a G4 PPC.  I installed it in text mode, and I chose quite long passwords (over 15 symbols) for both the account I was prompted to create and the root account (with sudo).  I had no problem using them in text mode. However, after I set up GNOME and rebooted, I was prompted to login on a graphical screen. This screen seems to only accept 15 symbols in the password field, so there is no way for me to enter either of my passwords. I enter them up to the 15th symbol, and of course I cannot login. I haven't figured out how to reboot in text mode either. If anybody has experienced a similar problem or just knows how to fix it, I'll be grateful for any help!  :lol:[/QUOTE]

When GDM starts push
```

ctrl - alt - F2

```

This should open a CLI terminal.  From this menu log in with your standard username.  Then set the root password.

```

sudo passwd root

```

After this, time to edit your password.  

```

sudo passwd YOURUSERNAME

```

I don't know of any way to change the password length of the GDM Login Screen.  I was looking at the GDM configuration file, and I didn't see anything about a maxpassword length on the login screen.

---

### Post by Faerine on 2004-10-29
Thank you very much, FLeiXiuS!  :smile:

---

### Post by HungSquirrel on 2004-10-29
Well, I commend you for using such strong passwords, if that's any consolation!  :)

---

### Post by ghost on 2005-01-29
Hey, I am having a similiar problem. but not the same.]

I login via gdm, it accepted my username and password, then it went to the brown screen. It look like it's thinking for a while (10 seconds) Then it reboot back into the login screen.

Please help, I have used Ubuntu for a month now, I don't want to reinstall this again, or go for other distro.

Thanks in advance.

ps. I have changed the password again, via ctrl + alt + F2, but that didn't help.

---

### Post by bomba on 2005-09-28
[QUOTE=ghost]I login via gdm, it accepted my username and password, then it went to the brown screen. It look like it's thinking for a while (10 seconds) Then it reboot back into the login screen.
[/QUOTE]

Here too - in next boot after hitting the powerbutton! (Yes, I know not to do so - and I got my punishment)

Booting Grub > recovery console did regognized my passwords. I could add new users and change passwords.  But login in graphical or normal console just didn't accept any passwords.

Having heard sometimes a word "pam" I did "apt-get install --reinstall libpam-modules libpam-runtime libpam0g". 

Sure reinstalling just some of "pams" should had been enought, but I have no clue what they all do. Anyway that solved my problem.

---

