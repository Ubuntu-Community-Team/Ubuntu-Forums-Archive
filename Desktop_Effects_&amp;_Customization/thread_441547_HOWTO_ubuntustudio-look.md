---
title: "HOWTO: ubuntustudio-look"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by MRiGnS on 2007-05-12
After seeing the the studio&#8217;s artwork I was quite amazed of the team&#8217;s great work. I wanted to get this artwork. I wanted it bad. So I searched for a way to get it and finally found one. You just need the gpg key and add the repository to your sources.list

This is how it works:

```
wget http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add -

sudo echo "deb http://archive.ubuntustudio.org/ubuntustudio feisty main" >> /etc/apt/sources.list

sudo apt-get update
```

now if you like the whole art work including splash and gdm theme type

```
sudo apt-get install ubuntustudio-look
```

otherwise

```
sudo apt-get install ubuntustudio-theme ubuntustudio-icon-theme ubuntustudio-wallpapers
```



this guide is from my blog: [http://mrigns.ath.cx/](http://mrigns.ath.cx/)

---

### Post by IT_Slave on 2007-05-12
I wanted to try it out.. thanks for the how-to

:guitar:

---

### Post by screaminj3sus on 2007-05-13
anyone reccomend a good firefox themne to go with it? I like the theme but it makes firefox look horrible.

---

### Post by MRiGnS on 2007-05-13
> **screaminj3sus said:**
> anyone reccomend a good firefox themne to go with it? I like the theme but it makes firefox look horrible.

[http://mrigns.ath.cx/index.php/2007/05/12/fix-for-dark-firefox-themes/](http://mrigns.ath.cx/index.php/2007/05/12/fix-for-dark-firefox-themes/)

there is a fix for dark themes.

---

### Post by eduardgrebe on 2007-05-14
Does anyone know how to install these themes on feisty AMD64? The repos aren't picked up.

---

### Post by mrcanard on 2007-05-14
> **screaminj3sus said:**
> anyone reccomend a good firefox themne to go with it? I like the theme but it makes firefox look horrible.

I like 708090 and 708090 lite.

---

### Post by Spalatum on 2007-05-15
I did exactly what you said and I got this:

```
wget http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add -
--15:31:48--  http://archive.ubuntustudio.org/ubuntustudio.gpg
           => `-'
Resolving archive.ubuntustudio.org... 208.97.169.99
Connecting to archive.ubuntustudio.org|208.97.169.99|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,710 (1.7K) [text/plain]

100%[====================================>] 1,710          9.08K/s             

15:31:49 (9.07 KB/s) - `-' saved [1710/1710]

OK
partizan@blackbox:~$ 
partizan@blackbox:~$ sudo echo "deb http://archive.ubuntustudio.org/ubuntustudio feisty main" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

```

And after I try installing the theme I get:

```
partizan@blackbox:~$ sudo apt-get install ubuntustudio-theme ubuntustudio-icon-theme ubuntustudio-wallpapers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntustudio-theme

```

Please help me out.

---

### Post by wtp on 2007-05-15
> **Spalatum said:**
> I did exactly what you said and I got this:

```

...
partizan@blackbox:~$ sudo echo "deb http://archive.ubuntustudio.org/ubuntustudio feisty main" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

```
...


There is a problem in the initial instructions.  Use:
```

sudo sh -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
Instead, & pick up from there (i.e., "apt-get update" again).

---

### Post by tennyis on 2007-05-15
I have it installed fine but nothing changed, no new themes, splash screens, etc.

---

### Post by tennyis on 2007-05-15
I have it installed fine but nothing changed, no new themes, splash scre

---

### Post by AThomsen on 2007-05-15
> **tennyis said:**
> I have it installed fine but nothing changed, no new themes, splash scre

Did you go to System -> Preferences -> Theme and select the Ubuntustudio theme?

---

### Post by diamondsw on 2007-05-15
If you take the "minimal" route and just install the window theme, wallpaper, and icons, you may be confused by the fact that there isn't a new theme listed in the control panel. All of the pieces are there; just not a preset theme that combines them. To fix this, all you have to do is customize an existing theme and select UbuntuStudio on each panel. And don't forget to change your wallpaper (black/blue doesn't go well with brown/orange)!

On a similar but not really related topic, is there any way to install the ubuntustudio-sounds package as well? I love the sound theme, but it appears to conflict with two heavyweight packages, including ubuntu-desktop. I sure as hell am not uninstalling *that* for a set of sound files!

PS - Damn, but that is a lovely theme. Reminds me of Apple's "Hi-Tech" from the mid-90's, in all the right ways. So few dark themes work, and work in such a way that I could look at them day in and day out. I think this one nailed it!

---

### Post by MRiGnS on 2007-05-16
> **diamondsw said:**
> If you take the "minimal" route and just install the window theme, wallpaper, and icons, you may be confused by the fact that there isn't a new theme listed in the control panel. All of the pieces are there; just not a preset theme that combines them. To fix this, all you have to do is customize an existing theme and select UbuntuStudio on each panel. And don't forget to change your wallpaper (black/blue doesn't go well with brown/orange)!

On a similar but not really related topic, is there any way to install the ubuntustudio-sounds package as well? I love the sound theme, but it appears to conflict with two heavyweight packages, including ubuntu-desktop. I sure as hell am not uninstalling *that* for a set of sound files!

PS - Damn, but that is a lovely theme. Reminds me of Apple's "Hi-Tech" from the mid-90's, in all the right ways. So few dark themes work, and work in such a way that I could look at them day in and day out. I think this one nailed it!

ubuntu-desktop is just a meta package. you can install the studio sound without problems and if you dont like the just reinstall ubuntu-sounds.

---

### Post by Spalatum on 2007-05-16
> **wtp said:**
> There is a problem in the initial instructions.  Use:
```

sudo sh -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
Instead, & pick up from there (i.e., "apt-get update" again).

Thanks a lot. This fixed my problem. Cheers :)

---

### Post by jo.pettitt on 2007-05-16
Unfortunately this fails on my AMD64:

Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

---

### Post by jjstarbot on 2007-05-17
> **jo.pettitt said:**
> Unfortunately this fails on my AMD64:

Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

If you are using a 64 bit version of ubuntu you can manually install the packages.


```

wget http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/ubuntustudio-theme_0.4_all.deb
wget http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/ubuntustudio-icon-theme_0.1_all.deb
wget http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/ubuntustudio-wallpapers_0.4_all.deb
wget http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/ubuntustudio-gdm-theme_0.4_all.deb
wget http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/ubuntustudio-session-splashes_0.4_all.deb

sudo dpkg -i ubuntustudio-theme_0.4_all.deb 
sudo dpkg -i ubuntustudio-wallpapers_0.4_all.deb 
sudo dpkg -i ubuntustudio-icon-theme_0.1_all.deb 
sudo dpkg -i ubuntustudio-gdm-theme_0.4_all.deb  
sudo dpkg -i ubuntustudio-session-splashes_0.4_all.deb 
sudo dpkg -i ubuntustudio-look_0.4_all.deb 

```

I installed them and it runs fine. It's mostly artwork so there doesn't seem to be anything specifically created or compiled for a 64bit platform. It should be fine but I haven't done any extensive testing.

---

### Post by diamondsw on 2007-05-17
> **MRiGnS said:**
> ubuntu-desktop is just a meta package. you can install the studio sound without problems and if you dont like the just reinstall ubuntu-sounds.

Well, yes, but Ubuntu seems very firm on NOT uninstalling ubuntu-desktop; wouldn't removing such a fundamental metapackage cause issues in future upgrades and such?

It seems the problem is that "ubuntu-desktop" specifies "ubuntu-sounds" as a dependency. Shouldn't the "ubuntustudio-sounds" simply provide that package to keep "ubuntu-desktop" (and all other desktop metapackages) happy? If anyone can tell me how to tweak the ubuntustudio-sounds package in the meantime, I'll change it myself and see if it works.

---

### Post by philipho on 2007-05-17
> **AThomsen said:**
> Did you go to System -> Preferences -> Theme and select the Ubuntustudio theme?


I installed ubuntu studio but i dont see it in System->Preferences->Theme... anyone knows the reason?

---

### Post by diamondsw on 2007-05-17
> **philipho said:**
> I installed ubuntu studio but i dont see it in System->Preferences->Theme... anyone knows the reason?

I believe [this](http://ubuntuforums.org/showpost.php?p=2663083&postcount=12) may be your problem.

---

### Post by philipho on 2007-05-17
Thank you Diamondsw, i will try it later when i boot into ubuntu...

---

### Post by teds on 2007-05-22
Just installed Studio look. I love the theme. I was able to choose the theme using GL Desktop, go to themes, then choose customize.

---

### Post by ukripper on 2007-06-02
Has anyone tried it with Edgy?

---

### Post by Fayte2071 on 2007-06-02
I dunno, if you guys like the theme so much, why not just install ubuntustudio? 
Granted, that's what i did after i saw it and saw what it came with (That might be just me, but I found alot of use for the audio & video programs).

---

### Post by johnc4510 on 2007-06-05
Usually not much of a dark theme person, but had liked Ubuntu-Studio's theme from the first. This made it simple to install, 

Thanks MRiGnS

---

### Post by seltak on 2007-06-06
> **tennyis said:**
> I have it installed fine but nothing changed, no new themes, splash scre
you must change settings in System -> Preferences -> Desktop Background, Theme, and etc.

---

### Post by eladner on 2007-06-06
Is there somewhere to post issues and comments with the themes themselves?

---

### Post by apoth on 2007-06-15
Superb theme.

---

### Post by ukripper on 2007-06-15
Good theme but I prefer Linsta not Vista theme. Goes well with Firefox themes

---

### Post by apoth on 2007-07-25
Installing this under Gutsy seems to want to install a package that requires removing ubuntu-desktop, which I'm not keen on doing because I probably won't remember to put it back in for my next dist-upgrade. Any suggestions?

Thanks

---

### Post by almtybudha on 2007-07-29
Hi guys...

I'm just a noob to linux. When I try to install the key for the repositories to "http://archive.ubuntustudio.org/ubuntustudio feisty main", my terminal window stops responding and I never get back to a prompt. Here is what it looks like...

```
asus-w3j:~$ wget http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add -
--23:43:41--  http://archive.ubuntustudio.org/ubuntustudio.gpg
           => `-'
Resolving archive.ubuntustudio.org... Password:208.97.169.99
Connecting to archive.ubuntustudio.org|208.97.169.99|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,710 (1.7K) [text/plain]

100%[====================================>] 1,710         --.--K/s             

23:43:41 (63.85 KB/s) - `-' saved [1710/1710]


```

I'd appreciate any help. Also, got any recommendations on good linux books that I could use to learn a thing or 2?

---

### Post by syko21 on 2007-07-29
i get that happening to me too quite a bit. This usually works for me, sudo apt-get update, and then when it yells at you about the missing gpg key try the previous command again.

---

### Post by cookiemonster0774 on 2008-03-05
Here is the package with the studio theme

[http://nighthacker.net/easy-way-to-install-the-ubuntu-studio-theme-on-plain-ol-ubuntu/](http://nighthacker.net/easy-way-to-install-the-ubuntu-studio-theme-on-plain-ol-ubuntu/)

Hope it helps.

---

### Post by amitabhishek on 2008-03-06
Hey! I like your signature ;).

---

