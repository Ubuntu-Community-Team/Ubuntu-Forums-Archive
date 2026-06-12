---
title: "Screen Resolution damaged"
date: 2008-12-23
forum: General Help
---

### Post by leacher on 2008-12-23
Hi,

New to ubuntu 8.10 installed and using successfully,  but last night i changed the screen resolution to 1024x768 from 1280x768. and suddenly my screen view damaged. like color transitions and noise even cant see any word, so I could get back or do anything else.

My Monitor is Fujitsu (Siemens) 17".

I am newbie to ubuntu should I reinstyall it or is there any short key regarding this?

Hope i would get it fixed without reinstall.

---

### Post by Zorael on 2008-12-23
No need to reinstall. This could be the monitor not liking your refresh rate, and it sounds to me like you should turn it off until you can figure out a solution unless you want to really damage your monitor. Then again, it could be some chance hardware failure that was triggered by you changing resolution. Electronics fail too.

How did you change the resolution? Via GNOME's menus, or by editing X configuration files?

The worst thing that can happen, in case you can't find where the changes were saved, is that you'd have to create a new user and copy your (non-GNOME) settings to it.

---

### Post by leacher on 2008-12-23
Thanks Zorael!

I Changed it from Gnom Menu. I am now using WinXp on same monitor it;s running fine on 1024x768. How do I create account or whatever ehen I cant see anything? hope you will help me out further.

---

### Post by Zorael on 2008-12-23
You'd need to do it in a terminal. Boot into recovery mode and pick "root shell", or boot normally and hit Ctrl+Alt+F1 when you get to the GNOME login screen (or the desktop if you've set it up to login automatically). Login in the text interface, then enter the following.
```
$ sudo newuser nameofnewuser
$ sudo service gdm restart
```

---

### Post by leacher on 2008-12-23
thx again, I'll give it a try and let you know.

---

### Post by leacher on 2008-12-23
It could not help me. it says bad command.. should i replace some thing with 'nameofnewuser'

---

### Post by Zorael on 2008-12-23
Oh, blast, that's supposed to be **useradd**, I don't know what I was thinking. And yes, replace *nameofnewuser* with whatever you want to name the new user.

```
$ sudo **useradd** *nameofnewuser*
$ sudo service gdm restart
```

---

### Post by leacher on 2008-12-23
yeah.i've added user but now it's saying username is not sudour.. what else can I do? I have updated ubuntu after fiest installation that was 203 MB, and that was time taking. I dont need more bothering... any command via sudo that can help without creating user?

---

### Post by redilyn on 2008-12-23
This should fix your problem.

Boot ubuntu until you get to the login prompt.

Login with your original user which has the messed up screen resolution. 

Even if you can't see the login window just wait a while until you think it has reached that point and then enter your username press enter, enter your password and press enter.

If you still have sounds turned on wait for the login music plays. If you don't have sound just wait till your hard drive stops working.

Next press ALT+F2

Type the following

```

xrandr -s 1280x768

```

Then press enter. Hopefully your screen should change back to the proper resolution and you will be good to go.

You will have to do all of this without being able to see so please follow these steps very closely 

Hope this helps.

---

### Post by leacher on 2008-12-24
Thanks both of you. redilyn! this was\nt useful for me, well I\ve reinstalled ubuntu. this experience cant make me move to Windows..

but what should I do to change resolution to 1024x768 without any problem?

---

