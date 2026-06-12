---
title: "I installed paintown, but it doesn't appear in unity dash, can't be run from terminal"
date: 2013-09-04
forum: Gaming &amp; Leisure
---

### Post by jonato-pik on 2013-09-04
When I try reinstalling, terminal will tell me its already installed, but when i try running paintown, it will say "command not found"

i then tried uninstalling and reinstalling, and did this whole cycle a few times lol (i suppose out of mild temporary insanity lol)

Nothing shows up in unity dash

but yet i'm told in terminal that it is installed.

does anyone know what to do?

---

### Post by MG&amp;TL on 2013-09-04
In your terminal, try running *paintown*. If that works, use that for now and we can work on getting it to show up in the unity dash.

---

### Post by jonato-pik on 2013-09-05
> **MG&TL said:**
> In your terminal, try running *paintown*. If that works, use that for now and we can work on getting it to show up in the unity dash.

 in terminal, when i try running paintown, it will say "command not found"

---

### Post by DarkAmbient on 2013-09-06
You could try their chatroom, asking a developer for help. [http://webchat.freenode.net/?randomnick=1&channels=paintown](http://webchat.freenode.net/?randomnick=1&channels=paintown)

If you catch one, ask them to update their ppa with packages for Ubuntu 13.04 too. ;)

---

### Post by BigSilly on 2013-09-07
Jonato, where are you installing PainTown from, because I don't see it in the software centre?

---

### Post by BigSilly on 2013-09-07
Hmmm, the official [PPA]("https://launchpad.net/~rafkind/+archive/paintown") doesn't have a package for Raring 13.04. If you're running that, then this may explain why it's not working.

I'll investigate further when I get back later. Unless someone beats me to it. :D

---

### Post by jonato-pik on 2013-09-07
> **BigSilly said:**
> Hmmm, the official [PPA]("https://launchpad.net/~rafkind/+archive/paintown") doesn't have a package for Raring 13.04. If you're running that, then this may explain why it's not working.

I'll investigate further when I get back later. Unless someone beats me to it. :D

Thanks, apprieciate it :)

i've actually tried it on 2 different laptops (one is running 12.04, the other 13.04), got the same exact results. 

i've also tried 2 methods of installing it. 

one method is here: [http://www.playdeb.net/updates/ubuntu/13.04/?q=paintown](http://www.playdeb.net/updates/ubuntu/13.04/?q=paintown)

the other method is here: [http://www.upubuntu.com/2012/08/install-full-paintown-360-from-ppa-on.html](http://www.upubuntu.com/2012/08/install-full-paintown-360-from-ppa-on.html)

---

### Post by jonato-pik on 2013-09-07
> **DarkAmbient said:**
> You could try their chatroom, asking a developer for help. [http://webchat.freenode.net/?randomnick=1&channels=paintown](http://webchat.freenode.net/?randomnick=1&channels=paintown)

If you catch one, ask them to update their ppa with packages for Ubuntu 13.04 too. ;)

yeah lol i never seem to find anyone on that chat thing

---

### Post by BigSilly on 2013-09-08
OK, so I installed the 12.10 package from the PPA, and got the following:

```
bigsilly@bigsilly:~$ cd '/usr/share/paintown-3.6.1' 
bigsilly@bigsilly:/usr/share/paintown-3.6.1$ ./paintown-bin
[0:paintown] Give 'help' to see all the command line options.
[0:paintown] Debug level: 0
[0:paintown] -- BEGIN init --
Data path is data/
Paintown version 3.6.1
Build date Aug 22 2012 17:34:00
SDL Init: Ok
[0:paintown] Could not find window icon: build/sdl/util/file-system.cpp:1570 Cannot find menu/icon.bmp. I looked in 'data/menu/icon.bmp', '/home/bigsilly/.paintown/menu/icon.bmp', 'menu/icon.bmp'
[0:paintown] Opened audio at rate 44100 channels 2 format 32784
[0:paintown] Notice: could not open configuration file '/home/bigsilly/.paintownrc': build/sdl/util/tokenreader.cpp:55 No tokens read from /home/bigsilly/.paintownrc
Set graphics mode: Ok
Initialize random number generator
Initialize network
-- END init --
[0:paintown] Init took 144.384 milliseconds
[0:paintown] Could not find the paintown default mod
terminate called after throwing an instance of 'LoadException'
  what():  std::exception
Aborted (core dumped)
```

"Missing default mod". My skills aren't good enough to fix this.

Jonato, might I recommend [OpenBOR]("http://www.chronocrash.com/forum/") (Beats of Rage)? I've been using this for some time and there's a metric crap-ton of side-scrolling beat 'em ups available for Linux. I love it personally. :)

Have a good mook about the site I've linked to, and see if you can't find some good stuff there.

---

### Post by BigSilly on 2013-09-08
[Source Forge link too]("http://sourceforge.net/p/openbor/wiki/Home/"). :)  It can seem a bit complex at first, but it's worth a look imho.

---

### Post by jonato-pik on 2013-09-09
> **BigSilly said:**
> OK, so I installed the 12.10 package from the PPA, and got the following:

```
bigsilly@bigsilly:~$ cd '/usr/share/paintown-3.6.1' 
bigsilly@bigsilly:/usr/share/paintown-3.6.1$ ./paintown-bin
[0:paintown] Give 'help' to see all the command line options.
[0:paintown] Debug level: 0
[0:paintown] -- BEGIN init --
Data path is data/
Paintown version 3.6.1
Build date Aug 22 2012 17:34:00
SDL Init: Ok
[0:paintown] Could not find window icon: build/sdl/util/file-system.cpp:1570 Cannot find menu/icon.bmp. I looked in 'data/menu/icon.bmp', '/home/bigsilly/.paintown/menu/icon.bmp', 'menu/icon.bmp'
[0:paintown] Opened audio at rate 44100 channels 2 format 32784
[0:paintown] Notice: could not open configuration file '/home/bigsilly/.paintownrc': build/sdl/util/tokenreader.cpp:55 No tokens read from /home/bigsilly/.paintownrc
Set graphics mode: Ok
Initialize random number generator
Initialize network
-- END init --
[0:paintown] Init took 144.384 milliseconds
[0:paintown] Could not find the paintown default mod
terminate called after throwing an instance of 'LoadException'
  what():  std::exception
Aborted (core dumped)
```

"Missing default mod". My skills aren't good enough to fix this.

Jonato, might I recommend [OpenBOR]("http://www.chronocrash.com/forum/") (Beats of Rage)? I've been using this for some time and there's a metric crap-ton of side-scrolling beat 'em ups available for Linux. I love it personally. :)

Have a good mook about the site I've linked to, and see if you can't find some good stuff there.

Hey, i just really appreciate the effort! Thanks 

I'll definitely check out those suggestions, appreciate it!

---

