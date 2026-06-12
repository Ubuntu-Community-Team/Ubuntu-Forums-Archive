---
title: "Gnome vs KDE + other questions"
date: 2005-08-29
forum: Desktop Environments
---

### Post by igabriel on 2005-08-29
Hello everybody and greetings from Romania!

I want to switch from WindowsXP to Linux.
After a brief documentation I decided to install Ubuntu/Kubuntu.
From what I've read I noticed that the only difference between the two is that one uses Gnome, the other KDE. From the screenshots, Kubuntu has a much better windows-like desktop than Ubuntu.

Before I install one of them please tell which desktop environment is the best: Gnome or KDE? Do the applications of Gnome run on KDE and vice-versa? Regarding stability, which would you consider best? Which of them has the best applications suite?

This is my system's hardware:
- ABIT NF7-S with nVidia nForce 2 Chipset
- AMD Barton 2600+
- 2x256 MB RAM GEIL PC3200 DDR (working in Dual Channel)
- HDD Seagate 120GB 7200.7 Plus SATA150
- GeCube ATI RADEON 9550 with TV-OUT( feature that I intend to use under Linux)
- Sound on board (AC97) & Ethernet on board
- I have a permanent connection to the Internet by CATV using a Thomson transparent modem.

Please tell me if I can encounter problems, like compatibility issues, when installing Ubuntu/Kubuntu on my system.

Is it true that when the new version of Ubuntu/Kubuntu is released I can simply upgrade to it by Synaptic ?

Thank you for your answers!
Have a nice day!

---

### Post by npaladin2000 on 2005-08-29
> **igabriel]Hello everybody and greetings from Romania!

I want to switch from WindowsXP to Linux.
After a brief documentation I decided to install Ubuntu/Kubuntu.
From what I've read I noticed that the only difference between the two is that one uses Gnome, the other KDE. From the screenshots, Kubuntu has a much better windows-like desktop than Ubuntu.

Before I install one of them please tell which desktop environment is the best: Gnome or KDE? [/QUOTE]

There's no better way to start a war then by asking that question.  Personally I prefer GNOME, but others prefer KDE.  Best advice is to go look at screenshots for each one ([www.gnome.org](www.gnome.org) and [www.kde.org](www.kde.org)) and decide which one looks like something you'd be more comfortable with.   Fact is, they can co-exist fine anyway, and you can log into one one day and the other the next day if you really want to

[QUOTE=igabriel]Do the applications of Gnome run on KDE and vice-versa?[/QUOTE]

Yes.  When an app is for one DE, that means the libraries need to be installed for it. You don't necessarily have to be running the desktop at that point in time, just have it installed.  Of course, if you're in GNOME and launch a KDE app, several things may/will happen:  it will load a lot slower because the KDE components are not already in memory said:**
> Regarding stability, which would you consider best?

Again, matter of opinion and individual situation. 


[QUOTE=igabriel]Which of them has the best applications suite?[/QUOTE]

See above.

[QUOTE=igabriel]Please tell me if I can encounter problems, like compatibility issues, when installing Ubuntu/Kubuntu on my system.

Is it true that when the new version of Ubuntu/Kubuntu is released I can simply upgrade to it by Synaptic ?[/QUOTE]

You're better off using the CLI to do that (the command for it is sudo apt-get dist-upgrade I believe, but first you have to replace your repositories with the repositories for the new distribution).

Fronm your system specs, you won't have any problem running either desktop environment.  For the most part, most consider to be KDE the more eye-candy-like distro with a lot more features and components, while GNOME is considered a bit more lightweight and direct (KDE, being so filled with "stuff," is a bit more bloated. There's no avoiding this...if you want more features, you pay for it with more bloat).  

Since Ubuntu is the primary distro (Kubuntu is a distro based off of Ubuntu) you might be best off installing Ubuntu and trying GNOME.  If you don't like it so much, you can launch Synaptic and look for the "kde" package, which will install a large percentage of the KDE stuff. Or you can go to the terminal and type "sudo apt-get install kde" if you prefer.

---

### Post by f1dave on 2005-08-29
Fair comment i suppose. 

And once you've gotten used to kde or gnome, you can use a /real/ environment like XFCE ;)

---

### Post by Unix_Wizard on 2005-08-29
[QUOTE=f1dave]Fair comment i suppose. 

And once you've gotten used to kde or gnome, you can use a /real/ environment like XFCE ;)[/QUOTE]
 XFCE!? I tried that on suse linux a few weeks ago and I was thinking who on earth would use this? Can you please explain the benefits of XFCE for a top of the range pc user like me?

---

### Post by f1dave on 2005-08-29
Hehe... it was meant to be a joke, as I really use KDE.

But in all honesty, XFCE is a very good, lightweight desktop. It doesn't have the candy that KDE and gnome does, but as a result, will run very well on older pcs and is great for those who like a clear and simple desktop. It's certainly not for everybody, but it's definately a viable alternative for those seeking something more compact.

---

### Post by bizzaroMike on 2005-08-29
As a KDE fan, I'll put in my thoughts.

In my experience, Gnome feels slower than KDE, but I'm not entirely sure if that's because of latency or actual efficiency.  On my little computer, the ubuntu gnome desktop was nearly unusable, but KDE runs reasonably well.

I'd say Gnome is visually more appealing.  There's been a lot of effort to make the menus friendly and well laid-out.  Gnome also has great default settings on many programs.  

But KDE has lots of features I find useful.  It's also more easily configurable in my experience.  You can make KDE work many different ways.  I really think konqueror is a program to be proud of too.  It's useful enough that I run it even when using a lightweight environment like Pekwm.  

I think it isn't correct to say KDE is bloated.  KDE is built out of embedable components.  The same text-editor engine runs in konqueror, kedit, and kate.  That means that while those programs present it differently, it only exists in memory once.  The slew of programs using it represent different levels of interface, from viewer to simple to advanced.  I like that KDE gives me two programs for every task: a simple program for ordinary tasks and an expert program for tricky work.  That these programs share most of their code is good engineering in my book.  If this sort of thing seems frivolous to you, then I think KDE would seem bloated.  

I do wish the KDE team would spend some time refining the default setup for their programs.  Konqueror starts with a sidebar and like three icon bars.  There's barely any screen left to do work in!  Also, the default kicker (the panel, like a start bar) is sad, really.  The default gnome panel is a work of genius.

---

### Post by f1dave on 2005-08-31
Yes, you're absolutely right.

KDE has the prettiness factor in terms of eye candy over gnome, but then when you look at the kmenu, the konqueror interface, etc when compared to their gnome counterparts, it pales in comparison. All this time spent with beautiful looking Qt windows, and then this horrible squashed kmenu in the corner! 

Compare this to gnome where all menu entries and toolbars have sufficient whitespace around them to make them a) easy to see and b) easy to click. Fitts' law, people!

---

### Post by JLTB on 2005-09-01
haha ... prediction: flame war .... ;)

But seriously, I've used both Gnome and KDE extensivly and they are both really good.  I would, unlike many other comments, warn that the screenshots don't always tell the whole truth.

In both Gnome and KDE panels can be moved around at will.  You can make it look like windows if you want, like a mac ... whatever you feel like.

Also, although I am a KDE user primarily .. I have to admit that Gnome's Theme and skinning ability's leave KDE in the dust!  One system to manage icons, window themes and decorations and so simple to use (yea yea i know the control center is okay ... but come on .. Gnome's has 3 buttons and a textbox :o).  Oh, and (yea i know .. flame on) Gnome in my experience does themes much better and across a broader range of applications (sure you can install gtk-qt stuff .. but its messy often).

**Edit:**
*Forgot to mention ... Gnome by default will skin Firefox with the rest of the system ... I have never seen KDE do that..*


Well, in all honesty I have been using KDE for the last 3 or 4 years .... I'm a KDE user dreaming of Gnome i guess (dreaming cause i installed it last week... broke it ... and haven't bothered to fix it .. lol)

PS: (everyone loves eye-candy right?)
Gnome brushed: [http://gnome-look.org/content/pre1/20972-1.jpg](http://gnome-look.org/content/pre1/20972-1.jpg)
KDE brushed: [http://kde-look.org/content/pre1/8692-1.jpg](http://kde-look.org/content/pre1/8692-1.jpg)

Pick your poison i guess.

---

### Post by Elv13 on 2005-09-01
If you like simple environement, gnome will be the best, but if you want complete environement with full customisation option, the nice konqueror tabs file manager 
konqueror will open alot of dot.
Gnome= simplicity
KDE= Compatibility

KDE brussed (this is my screen)
[img]http://img288.echo.cx/img288/2568/capture57qt.png[/img]

---

### Post by DarkT on 2005-09-02
[QUOTE=f1dave]
Compare this to gnome where all menu entries and toolbars have sufficient whitespace around them to make them a) easy to see and b) easy to click. Fitts' law, people![/QUOTE]
I agree but in KDE under the fonts config, for menus select the "gargi 1.3 r3" font - if it's installed for you - as this leaves plenty of whitespace on menus.
 
As for the Gnome vs KDE thing, I'm no KDE fanboy but I dislike the direction of the gnome project, it seems to be trying to get users to adopt a new way of window and file managing that I find unuseable and far slower than the single window, address bar method. I like the way I manage my files, I've grown into it and the new nautilus seems like a step back in usability (and yes I gave it a try for a long time, and I know you can turn it off through the configs, but it's forcing people who don't know that). 
So I find KDE more useable than gnome (it still has plenty of problems though) but in the end it's down to what you like, so give each a try and see how it goes.

---

### Post by f1dave on 2005-09-02
Good tip, thanks!

---

### Post by picturesqueweb on 2005-09-02
I started out liking Gnome, but found some apps I wanted didn't run properly under Gnome. I tried XFCE and other slim DE's but all were lacking in Gnome features. I installed KDE and suddenly the weird business apps that would run under Gnome were running fine under KDE. I'm not certain why, but I'm now a convert. I can have my specialized apps and my eye candy too.

---

### Post by casperl on 2005-09-02
As one ex-Windows user to another would-be ex-windows user, may I say:
Welcome to Ubuntu!
> I want to switch from WindowsXP to Linux.

> the only difference between the two is that one uses Gnome, the other KDE

In a nutshell, those are your two choices.

Personally I use Gnome, but I use many KDE programs as well.  In my view there are some KDE programs that make my web development work more productive, and there are no alternatives available in Gnome.

However, I really believe Gnome is a nicer and more beautiful environment.  Is KDE more productive than Gnome?  I don't know, you work comfortably in the environment that you know the best and for me that is Gnome.

You certainly have the PC hardware to run Gnome without noticeable performance issues.  

A personal (and subjective) reason that I chose Ubuntu / Gnome over IceWM (or even KDE) on Debian Linux is that I felt that I should choose a system that is not merely similar to Windows but is much superior to Windows, both in performance and in appearance!

I hope this post helps you.

---

### Post by Perfect Storm on 2005-09-02
Gnome user here (and Enlightenment too for experiments).


In the past I've used KDE alot but found out that gnome covers my need, without to many adjustments. It's clean and doesn't distract the me for what I really want to use my PC to: Work. In the end it's all about taste.

A good advise would be try them both, and follow your heart ;)

---

