---
title: "Updated to Kubuntu - Now Have Problems!"
date: 2005-05-16
forum: Desktop Environments
---

### Post by CrazyDelta on 2005-05-16
Hi guys,

Hope I can get some help here.

Well, I had been using 4.10 ubuntu on my uncle's computer for while and thought I'd update to this. The one reason I wanted to update was because I could never get the refresh rate to be above 60Hz on a new ViewSonic 17" CRT monitor.

So I updated, and now I am really stuck. Firstly, I don't see any "games" for my little cousins to play. There is no Firefox that my uncle was really accustomed to. The refresh rate is still a problem.

For the refresh rate - Even though I know I can change the setting in the xorg.conf file to fix this - for some reason I can't save the changes...?

I tried to install the Firefox linux package but the console won't listen to any commands I give it.

Some advise would be really really appreciated.

---

### Post by NTolerance on 2005-05-16
[QUOTE=CrazyDelta]Hi guys,

Hope I can get some help here.

Well, I had been using 4.10 ubuntu on my uncle's computer for while and thought I'd update to this. The one reason I wanted to update was because I could never get the refresh rate to be above 60Hz on a new ViewSonic 17" CRT monitor.

So I updated, and now I am really stuck. Firstly, I don't see any "games" for my little cousins to play. There is no Firefox that my uncle was really accustomed to. The refresh rate is still a problem.

For the refresh rate - Even though I know I can change the setting in the xorg.conf file to fix this - for some reason I can't save the changes...?

I tried to install the Firefox linux package but the console won't listen to any commands I give it.

Some advise would be really really appreciated.[/QUOTE]


```

sudo apt-get install menu
update-menus

```

---

### Post by Rodrigo on 2005-05-16
Kubuntu doesnt have any "games", sorry dude. If you want any good games, download frozen-bubble and wesnoth other games can be found here : [http://www.ubuntuforums.org/showthread.php?t=5153](http://www.ubuntuforums.org/showthread.php?t=5153) (thank jdodson for that!), install firefox with "apt-get install mozilla-firefox", and be sure to be in the sudoers file. Try searching before posting and good luck  :razz:

---

### Post by philipacamaniac on 2005-05-16
No games?!? What about the kdegames package? It is in the main repository. See what it has: [http://packages.ubuntu.com/hoary/kde/kdegames](http://packages.ubuntu.com/hoary/kde/kdegames)

To install, go to System --> Kynaptic, then go the KDE section. Select kdegames for installation, then commit the changes. Another way to do this is open a Konsole and type **sudo apt-get install kdegames**. This will install the KDE Games package, which has plenty for your cousins to play with.

For more games, enable the Universe repository (see [http://kudos.berlios.de/kf/kisimlar/swmgmt.html](http://kudos.berlios.de/kf/kisimlar/swmgmt.html) for instructions), then you can install SuperTux, TuxRacer and a whole lot more.

---

### Post by CrazyDelta on 2005-05-17
Thanks guys.

I will try to get things rolling today.

Cheers.

---

### Post by CrazyDelta on 2005-05-17
Ok, the games worked perfect. Thanks. (1 down, 2 to go)

Still got no luck in installing firefox.
Seems I get no permission for anything.

I tried sudo root
then added my password.

Keep getting authentication faliure.

I am also not allowed to make any changes to xorg.conf

How do I switch to a root/adminstrator login?
And if so, what would be the password?

I am going in circles over these two things. I have been searching the forums, but can't get a straight answer.

Some help would be appreciated.

---

### Post by GeneralZod on 2005-05-17
[QUOTE=CrazyDelta]

How do I switch to a root/adminstrator login?
And if so, what would be the password?

[/QUOTE]

To get a root shell, do 

```

sudo -i

```

For a one-shot root-level command (the recommended way), do e.g.

```

sudo nano /etc/X11/xorg.conf

```

Hope this helps,
Simon

---

### Post by Gezzer on 2005-05-17
[QUOTE=GeneralZod]To get a root shell, do 

```

sudo -i

```

For a one-shot root-level command (the recommended way), do e.g.

```

sudo nano /etc/X11/xorg.conf

```

Hope this helps,
Simon[/QUOTE]
 i have just downloaded and installed FF1.0.4 from the mozilla site using there installer it installed first time
works just fine ...

---

