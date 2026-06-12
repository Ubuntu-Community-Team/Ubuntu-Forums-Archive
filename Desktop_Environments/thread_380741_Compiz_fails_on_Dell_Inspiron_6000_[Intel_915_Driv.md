---
title: "Compiz fails on Dell Inspiron 6000 [Intel 915 Driver]"
date: 2007-03-10
forum: Desktop Environments
---

### Post by sarath_it on 2007-03-10
All beloved Ubuntu-ers,

I have just begun unbuntuing and I am so much in love with ubuntu, I did not restart windows the whole last weekend and I guess it will be the same this weekend.

But I have a small problem with Compiz. 


I have:
Dell Inpiron 6000
Ubuntu Edgy
Intel 915

since AIGLX is already installed, I just  installed compiz.

Followed the Instructions on
[https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy)
then those on
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)
[sudo apt-get install compiz compiz-gnome]

And when i run (this is what i get..)
sarath@sarath-laptop:~$ compiz --replace gconf
sarath@sarath-laptop:~$ libGL warning: 3D driver claims to not support visual 0x5b
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

and i lose everything ;) i mean the window frames, .. i managed to get a screenshot.. Adn I am also adding the xorg.conf file.. check that one too..

Can the "some" Ubuntu-er, help me get my laptop look kooool!!

Sarath.

---

### Post by FyreBrand on 2007-03-10
I don't think you need to implicitly enable AIGLX anymore and I think AIGLX is getting enabled twice..  As best as I can understand it AIGLX is enabled by default in xserver-xorg.  So backup your xorg.conf file and try commenting out that line where you enable AIGLX.  Restart the xserver and see what happens.

Here is a link to gandalfn's blog: [**HowTo compiz + aiglx on Edgy**]("http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/").

Here is a great thread to bookmark for future reference: [**One Thread To Rule Them All!**]("http://ubuntuforums.org/showthread.php?t=272104")

---

### Post by sarath_it on 2007-03-10
Thanks a BUNCH!! your link worked AWESOME.

My laptop is the coolest now, I have a whole week ahead to boast it off to my friends.

Sarath.

---

### Post by FyreBrand on 2007-03-10
Glad I could help.  I love having desktop effects when the Windows users stroll in.

---

### Post by sarath_it on 2007-03-10
Yet there is one thing, Everytime I log in, I have to start the GL Desktop from preferences and Enable it. It does not get loaded automatically. Also, the preferences wont stay saved. 

cool part is, I have already made 3 more fans of Ubuntu, and they will soon move to ubuntu.

---

### Post by FyreBrand on 2007-03-10
> **sarath_it said:**
> Yet there is one thing, Everytime I log in, I have to start the GL Desktop from preferences and Enable it. It does not get loaded automatically. Also, the preferences wont stay saved. 

cool part is, I have already made 3 more fans of Ubuntu, and they will soon move to ubuntu.What you're saying is that you have to start compiz everytime you log in to gnome.  Is that right?  I'll do a forum and documentation search for enabling compiz on startup and please do the same.  It's in a gnome settings area.  I actually use Beryl and Kubuntu so I'm not sure how exactly to make compiz startup at login on gnome, but I've seen it in several threads.  I'll report back tomorrow.

---

### Post by sarath_it on 2007-03-12
I got it.. For some reason, Gnome is not auto saving the session. I can go to session preferences, and save it once.

---

