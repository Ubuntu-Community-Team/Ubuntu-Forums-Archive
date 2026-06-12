---
title: "America's Army HELL!! (v2.3)"
date: 2005-05-12
forum: Gaming &amp; Leisure
---

### Post by DutchLau on 2005-05-12
What is up with this??

```
 discom@discom:~$ armyops
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error
discom@discom:~$ sudo armyops
Password:

```

What's going on here? Why must I run armyops as a superuser? I don't really care, but it's a pain for my little brothers who aren't superusers. Can "sudoing" America's Army cause harm to my system? 

Thanks already,

DutchLau

PS: I have my /home installed on a different partiton than my America's Army directory (which is installed on my /root).

---

### Post by ubuntu UsER on 2005-05-12
[QUOTE=DutchLau]PS: I have my /home installed on a different partiton than my America's Army directory (which is installed on my /root).[/QUOTE]
AA doesn't need to be installed using root privilages, you can (and in my opinion you should) install AA as "normal" user.

---

### Post by crane on 2005-05-12
Did you install it with sudo command? Be sure to check the permissions or the files.

Does the user have rights to run and read all the config files in there.

As a suggestion , because it sounds like you have a few different users playing the game. Creat a directory in your home directory and symlink to it.

[color=blue]mkdir ~/armyops
cp -Rs /usr/local/games/armyops/* ~/armyops[/color]

this would allow each user to add what ever files they needed with out damaging the original install.

I just checked my install and it is all owned by root but group and others have executable rights on some of the files.

---

### Post by DutchLau on 2005-05-12
Hello again and thanks for the speedy replys, I'm out to frag tonight and I don't want to mess up my system doing it. 

[This](http://aaotracker.4players.de/usertracker.php?userid=82835)  is my America's Army tracker account btw (if anyone's interested). Should I just uninstall America's Army and install it without sudo? Can I install without sudo? (From the replies I'm assuming that's a yes). Will this link also be sufficient should I link the launcher to ~/armyops/armyops ? (I didn't install it to /root - I didn't explain properly - I installed it to /usr/local/games/armyops - the default) but I guess because I "sudoed" it I can only run it under sudo!  :grin:  Stoopid me!  ](*,) 

Thanks already,

DutchLau

---

