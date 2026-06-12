---
title: "Some Enemy Territory helpful hints"
date: 2005-12-02
forum: Gaming &amp; Leisure
---

### Post by yetanothersteve on 2005-12-02
1. Install into your home folder through your regular user account. You will save yourself a lot of grief due to ET constantly trying to download things to folders created by the superuser if you install as superuser. I have ET installed to /home/me/enemy-territory and the et and etded links in /home/me/bin

2. Update your punkbuster after installing, open console

```
cd /home/me/enemy-territory/pb
chmod +x pbweb.x86
./pbweb.x86
```

Otherwise, up to date punkbuster servers will kick you, possibly causing your et client to crash on entering a server.

3. Expect to have sound problems, see here [http://alsa.opensrc.org/index.php?page=FAQ023]("http://alsa.opensrc.org/index.php?page=FAQ023")

4. Download the map packs from somewhere to limit the downloading from the server to which you are connecting. Mappacks I grabbed were nail.zip (110mb) and nail2.zip (22mb) and I extracted them to /home/me/enemy-territory/etmain
Just google for them using nail.zip and enemy as your search term.

5. Good reference point for Id games and linux
[http://zerowing.idsoftware.com/linux/]("http://zerowing.idsoftware.com/linux/")

---

### Post by Curufir on 2005-12-03
[QUOTE=yetanothersteve]1. Install into your home folder through your regular user account. You will save yourself a lot of grief due to ET constantly trying to download things to folders created by the superuser if you install as superuser. I have ET installed to /home/me/enemy-territory and the et and etded links in /home/me/bin
[/QUOTE]

This only happens because people use the installer option to start the game.

Install as root and do **_NOT_** start the game until you are using your normal account again. Reason for this is that sudo does not set the HOME environment variable to /root so if you start the game you end up with files owned by root lying around your home directory. Of course if you're on a single user machine there's no reason not to install into your home directory.

---

### Post by timzak on 2007-05-20
> **yetanothersteve said:**
> 1. Install into your home folder through your regular user account. You will save yourself a lot of grief due to ET constantly trying to download things to folders created by the superuser if you install as superuser. I have ET installed to /home/me/enemy-territory and the et and etded links in /home/me/bin

2. Update your punkbuster after installing, open console

```
cd /home/me/enemy-territory/pb
chmod +x pbweb.x86
./pbweb.x86
```

Otherwise, up to date punkbuster servers will kick you, possibly causing your et client to crash on entering a server.

3. Expect to have sound problems, see here [http://alsa.opensrc.org/index.php?page=FAQ023]("http://alsa.opensrc.org/index.php?page=FAQ023")

4. Download the map packs from somewhere to limit the downloading from the server to which you are connecting. Mappacks I grabbed were nail.zip (110mb) and nail2.zip (22mb) and I extracted them to /home/me/enemy-territory/etmain
Just google for them using nail.zip and enemy as your search term.

5. Good reference point for Id games and linux
[http://zerowing.idsoftware.com/linux/]("http://zerowing.idsoftware.com/linux/")

I keep getting permission errors when I try to install ET in my home directory.  I tried prefixing with sudo, etc.  Here's a transcript of my fumbling (I'm a newb):
```
tim@tim-desktop:~$ cd Desktop
tim@tim-desktop:~/Desktop$ dir
Documents              Filesystem.desktop  notes~       Terminal\ Commands~
et-linux-2.60.x86.run  notes               pbsetup.run  Terminal\ Commands.ods
tim@tim-desktop:~/Desktop$ chmod -x et-linux-2.60.x86.run
tim@tim-desktop:~/Desktop$ ./et-linux-2.60.x86.run
bash: ./et-linux-2.60.x86.run: Permission denied
tim@tim-desktop:~/Desktop$ ./et-linux-2.60.x86.run
bash: ./et-linux-2.60.x86.run: Permission denied
tim@tim-desktop:~/Desktop$ chmod +x et-linux-2.60.x86.run
tim@tim-desktop:~/Desktop$ su-c "./et-linux-2.60.x86.run"
bash: su-c: command not found
tim@tim-desktop:~/Desktop$ sudo et-linux-2.60.x86.run
Password:
sudo: et-linux-2.60.x86.run: command not found
tim@tim-desktop:~/Desktop$ et-linux-2.60.x86.run
bash: et-linux-2.60.x86.run: command not found
tim@tim-desktop:~/Desktop$ dir
Documents              Filesystem.desktop  notes~       Terminal\ Commands~
et-linux-2.60.x86.run  notes               pbsetup.run  Terminal\ Commands.ods
tim@tim-desktop:~/Desktop$ sudo "./et-linux-2.60.x86.run"
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install
```
didn't work.

```
tim@tim-desktop:~/Desktop$ dir
Documents              Filesystem.desktop  notes~       Terminal\ Commands~
et-linux-2.60.x86.run  notes               pbsetup.run  Terminal\ Commands.ods
tim@tim-desktop:~/Desktop$ ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install
```

got me a permission error again.

```
tim@tim-desktop:~/Desktop$ dir
Documents              Filesystem.desktop  notes~       Terminal\ Commands~
et-linux-2.60.x86.run  notes               pbsetup.run  Terminal\ Commands.ods
tim@tim-desktop:~/Desktop$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install
```

got me aother permission error.

```
tim@tim-desktop:~/Desktop$ dir
Documents              Filesystem.desktop  notes~       Terminal\ Commands~
et-linux-2.60.x86.run  notes               pbsetup.run  Terminal\ Commands.ods
tim@tim-desktop:~/Desktop$ sudo sh et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install
```

yet another permission error.  As you can see, I'm searching the forums, finding different instructions, and trying them all.  

The first time I tried installing, I stuck with the default directories that ET selects and it installed fine.  Afterward, I read a post that suggested it's better to install in your home directory.  That's when I started having the problems detailed above.  I'd get through the installation until it asked where to install, I'd select /home/tim/enemy-territory and /home/tim/bin as yetanothersteve suggests, and I get permission errors.

What I don't get is, why isn't there just one right way to do this?  I try something that works for someone else, and it doesn't work for me.  Please, can someone help me get ET installed in my home directory?

Thanks.

---

### Post by asipi on 2007-05-22
install et into your home is absolutelly dumb... whose idea was it, lol
installer started with sudo will install et into the proper place where it has been designed to be installed, then run it with your ordenary user without sudo. it will create the required directories in your home in ~/.etwolf

the game will download the required mods and maps what are needed to play on a server. that's all. do not mess the people's brain with such baseless and unrelevant posts dude...

and think twice before answer with anger...

---

