---
title: "Sideways Black"
date: 2009-07-25
forum: Desktop Environments
---

### Post by robeis1822 on 2009-07-25
About every 6 months or so for the past 5 years, I get this wild urge inside of me to use Linux. So, I grab one or the other distribution and do an install. For the first couple days I feel like a kid in a candy store. I'm always wowed by the progress that has been made since my last attempt at being a Linux user. The amount of available software is mind boggling. I tell my friends and family. I want to show people my new installation of Linux. But soon the inevitable happens. 

Linux commits suicide.

Well, this time I don't want to give up on it as fast, so I have come here for help. Here's the situation.

I'm using the brand spanking new Ubuntu 9.04 installed on an IBM ThinkPad T30.

Somewhere in Ubuntu Display Options, I found this fun looking option for turning my screen sideways. Having the personality that I have, I really wanted to see my screen sideways. So, I tried it. Screen went black. I waited. I waited some more, more, still waiting, still black, waiting, black. You get the idea. Okay no problem. I'll reboot. Login screen - great! Logging in... Screen black. Waiting... Okay. Linux has once again committed suicide on me within the first couple days. Well, here's an option: Recovery Mode. Nope. Okay Google will know: Nope...

So, my concern is twofold... One has priority, of course, and that is, how in the world do I fix this black screen..?

Secondly, how in the world can this problem even exist? I can't be the only fun-loving guy who wants to see my screen sideways and trying this renders the computer unusable. I'm a professional developer. If I released software with a bug this huge, I'm not sure I would have a job the next day. Now I know this comparison doesn't exactly work, because Linux is free and you get what you pay for, but still... How does a ridiculous problem like this make it out the door? I'm trying not to rant here, but seriously... :confused:

---

### Post by synapsys on 2009-07-25
After login press ctrl+alt+f1 to drop to a terminal. Type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
reboot
```

---

### Post by robeis1822 on 2009-07-25
> **synapsys said:**
> After login press ctrl+alt+f1 to drop to a terminal. Type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
reboot
```

Thank you very much for your suggestion, but sadly, no dice, and I tried it twice...

The feedback here looks like the same thing I got when I tried Recovery Mode.

"xserver-xorg postinst warning: overwriting possibly-customised configuration file;"

---

### Post by RD1 on 2009-07-25
```
sudo nano /etc/X11/xorg.conf
```

remove: Option "Rotate" "CW"

---

### Post by robeis1822 on 2009-07-25
> **RD1 said:**
> ```
sudo nano /etc/X11/xorg.conf
```remove: Option "Rotate" "CW"

Thank you very much for your suggestion but sadly... that did not work.

There is nothing in xorg.conf that mentions anything about rotate. It is very small and just basic stuff is in there...

I created a new user and was able to log in without a black screen, but the main user still gets only the black screen on login...

---

### Post by RD1 on 2009-07-25
Sorry. I should have realized. It's not an xorg problem because you are getting a graphical logon screen.

How about if we return your gnome settings to a fresh state?

At the login screen, drop to a terminal by hitting CTRL + ALT + F1, login to your account, and run this command:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Get back to your GUI desktop by hitting CTRL + ALT + F7.
Login and VOILÀ! Just like the first time you ever logged into your Gnome desktop.

---

### Post by robeis1822 on 2009-07-25
> **RD1 said:**
> Sorry. I should have realized. It's not an xorg problem because you are getting a graphical logon screen.

How about if we return your gnome settings to a fresh state?

At the login screen, drop to a terminal by hitting CTRL + ALT + F1, login to your account, and run this command:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```Get back to your GUI desktop by hitting CTRL + ALT + F7.
Login and VOILÀ! Just like the first time you ever logged into your Gnome desktop.

Thank you very much again but that didn't fix it either...

---

### Post by wojox on 2009-07-25
Try booting to recovery mode and choose the option "xfix fix video" or whatever it says exactly.

---

### Post by robeis1822 on 2009-07-25
> **wojox said:**
> Try booting to recovery mode and choose the option "xfix fix video" or whatever it says exactly.

Thank you, but I believe I already tried that a couple times.

Like you said, I forget exactly what it called it, but I tried whatever display or video fix option it had in Recovery Mode.

Also, I know exactly what I did to cause this now.

I went to System > Preferences > Display > Rotation > Left

Then everything went black and has stayed that way for the main user account...

The new user account I created actually works, so that makes me think there is some setting specific to the user this happened for. My wife is currently using the secondary account to play some music for the baby. Sadly, it's not quite calming the baby yet, and he is very whiny...

However, I must say Firefox on this Ubuntu runs YouTube magnificently well...

---

### Post by RD1 on 2009-07-25
Play this for the little one ... [http://www.youtube.com/watch?v=ocfR3CIPFJo]("http://www.youtube.com/watch?v=ocfR3CIPFJo")

---

### Post by robeis1822 on 2009-07-25
Thanks for the link. He actually started dancing to that one and appeared to like it, but our goal right now is to get him to sleep, so we're going to stick with what usually works.

Bedtime Baby
[http://www.youtube.com/watch?v=d81N9KtLh5Y](http://www.youtube.com/watch?v=d81N9KtLh5Y)

I guess in another time and place parents might actually sing their kids to sleep...

---

### Post by RD1 on 2009-07-25
> I guess in another time and place parents might actually sing their kids to sleep...

You're right ... Blue Christmas was my little girl's favorite ... 20 some years ago.

---

