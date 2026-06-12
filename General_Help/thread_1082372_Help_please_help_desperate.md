---
title: "Help please help desperate"
date: 2009-02-27
forum: General Help
---

### Post by kennyhall on 2009-02-27
my situation:(i know nothing about ubuntu) theres a computer at my work that some dude loaded ubuntu on and made a username, logged out and moved across the country and won't answer his phone or email. is there anyway to bypass the login? anything helps

---

### Post by taurus on 2009-02-27
When you first turn on your machine, you would be greeted with GRUB menu.  If you don't see the menu, press ESC within 3 seconds that you see the word GRUB.  Scroll down to recovery mode and boot from that.  Once you're at root shell, look to see what is your login name, username, is.

```
ls -la /home
```
Assuming it's john, change the password to something that you can remember.

```
passwd john
```
Once you have reset the password for john, reboot and see if you can login now.

```
shutdown -r now
```

---

### Post by FrancesL on 2010-02-03
Pretty annoying but ..firstly I blamed my memory but now think it is something else,
I cant get past log in screen, will accept log in name but not password, 
I have followed the instructions here.[http://ubuntuforums.org/showthread.php?t=1093682&highlight=bypass+login+username+Ubuntu%3F..twice](http://ubuntuforums.org/showthread.php?t=1093682&highlight=bypass+login+username+Ubuntu%3F..twice) and still it wont accept password...oh..9.04 is the version. 
Suggestions?
thanks

---

### Post by stinkeye on 2010-02-03
[_**[COLOR="DarkRed"]How to reset your password in Ubuntu[/COLOR]**_]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by FrancesL on 2010-02-03
> **stinkeye said:**
> [_**[COLOR="DarkRed"]How to reset your password in Ubuntu[/COLOR]**_]("http://psychocats.net/ubuntu/resetpassword")

Nope, that didn't work either! exasperation has now set in..I actually remember the rotten password! and even the new changed one I carefully wrote down..it is just NOT being accepted!

---

### Post by Jackzor on 2010-02-03
What do you need off of this computer?

Is this guy coming back? Did he work there?

Did he randomly walk in and format and install ubuntu and run away as if it were a joke?

---

### Post by lisati on 2010-02-03
An aside: user names and passwords are case sensitive.

---

### Post by FrancesL on 2010-02-03
Dont worry about it..I am going to reinstall, had only just installed in an attempt to get Ubuntu running on HP, still doing ok, but mighty slow with Win XP..will hope it is fixed with reinstall.

---

