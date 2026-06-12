---
title: "Just want to install a game :("
date: 2011-04-15
forum: Gaming &amp; Leisure
---

### Post by Jinx13 on 2011-04-15
Heyy :)
I've not been using kubuntu long and determined to stick with it :)
I'm running kubuntu 10.10 and trying to install a game.

The game is located at /home/jinx13/Documents/SimCity 3000 Linux Edition/Game/

The read me says this,
```
(2) INSTALLATION
----------------

Mount the SimCity 3000 Unlimited CD and change the current directory to where
it is mounted. Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
  $ mount /mnt/cdrom
  $ cd /mnt/cdrom
  $ sh setup.sh
```

I have tried all sorts of commands can some one please give me the right command to open setup.sh and install this game lol 


Thanks in advance,

JInx13

---

### Post by mips on 2011-04-15
You need to provide more details. what happens when you follow the instructions, what error messages do you get etc.

---

### Post by tgm4883 on 2011-04-15
> **mips said:**
> You need to provide more details. what happens when you follow the instructions, what error messages do you get etc.

What files are in this directory?
```
 /home/jinx13/Documents/SimCity 3000 Linux Edition/Game/
```

Where is setup.sh?

---

### Post by Jinx13 on 2011-04-15
> **mips said:**
> You need to provide more details. what happens when you follow the instructions, what error messages do you get etc.

That's just it I only think i'm getting errors as i'm using the wrong command

> **tgm4883 said:**
> What files are in this directory?
```
 /home/jinx13/Documents/SimCity 3000 Linux Edition/Game/
```Where is setup.sh?

Setup.sh is in /home/jinx13/Documents/SimCity 3000 Linux Edition/Game/setup.sh

Attached is the files in that folder

Thanks,

JInx13

---

### Post by tgm4883 on 2011-04-15
> **Jinx13 said:**
> That's just it I only think i'm getting errors as i'm using the wrong command



Setup.sh is in /home/jinx13/Documents/SimCity 3000 Linux Edition/Game/setup.sh

Attached is the files in that folder

Thanks,

JInx13

I'd run that file then. It may need to be run with sudo

```
cd '/home/jinx13/Documents/SimCity 3000 Linux Edition/Game/'
sudo sh setup.sh
```

---

### Post by Jinx13 on 2011-04-15
Thanks for your reply,
Now I get 
> sh: Can't open setup.sh

---

### Post by tgm4883 on 2011-04-15
> **Jinx13 said:**
> Thanks for your reply,
Now I get

odd, try this

```
chmod +x setup.sh
sudo ./setup.sh
```

---

### Post by Jinx13 on 2011-04-15
```
jinx13@jinx13-Aspire-8935G-Laptop:~$ chmod +x setup.sh
chmod: cannot access `setup.sh': No such file or directory
jinx13@jinx13-Aspire-8935G-Laptop:~$ sudo ./setup.sh
sudo: ./setup.sh: command not found
jinx13@jinx13-Aspire-8935G-Laptop:~$ cd '/home/jinx13/Documents/SimCity 3000 Linux Edition/Game/'
jinx13@jinx13-Aspire-8935G-Laptop:~/Documents/SimCity 3000 Linux Edition/Game$ sudo sh setup.sh
sh: Can't open setup.sh
jinx13@jinx13-Aspire-8935G-Laptop:~/Documents/SimCity 3000 Linux Edition/Game$ chmod +x setup.sh
chmod: cannot access `setup.sh': No such file or directory
jinx13@jinx13-Aspire-8935G-Laptop:~/Documents/SimCity 3000 Linux Edition/Game$ sudo ./setup.sh
sudo: ./setup.sh: command not found
```

---

### Post by GWBouge on 2011-04-15
Looking at that attachment, it's SETUP.SH, not setup.sh.  Capital letters make a different file ... for example:  a.txt, A.txt, and a.TXT would all be different files.

In that directory, try:
```
$ chmod +x SETUP.SH
$ ./SETUP.SH
```

---

### Post by tgm4883 on 2011-04-15
> **GWBouge said:**
> Looking at that attachment, it's SETUP.SH, not setup.sh.  Capital letters make a different file ... for example:  a.txt, A.txt, and a.TXT would all be different files.

In that directory, try:
```
$ chmod +x SETUP.SH
$ ./SETUP.SH
```

Ah I didn't look at the screenshot. Yes it will be case sensitive so please follow the commands posted by GWBouge

---

### Post by Jinx13 on 2011-04-15
Ah thanks for that explaination will keep that in mind as I was unaware :)

After all your help seems the game isn't even supported :( But thanks for all your help everyone :)

```
jinx13@jinx13-Aspire-8935G-Laptop:~$ $ chmod +x SETUP.SH
$: command not found
jinx13@jinx13-Aspire-8935G-Laptop:~$ $ ./SETUP.SH
$: command not found
jinx13@jinx13-Aspire-8935G-Laptop:~$ chmod +x SETUP.SH
chmod: cannot access `SETUP.SH': No such file or directory
jinx13@jinx13-Aspire-8935G-Laptop:~$ cd '/home/jinx13/Documents/SimCity 3000 Linux Edition/Game/'
jinx13@jinx13-Aspire-8935G-Laptop:~/Documents/SimCity 3000 Linux Edition/Game$ sudo sh SETUP.SH
This installation doesn't support glibc-2.1 on Linux / x86_64

Please contact Loki Technical Support at support@lokigames.com
jinx13@jinx13-Aspire-8935G-Laptop:~/Documents/SimCity 3000 Linux Edition/Game$ chmod +x SETUP.SH
jinx13@jinx13-Aspire-8935G-Laptop:~/Documents/SimCity 3000 Linux Edition/Game$ sudo ./SETUP.SH
This installation doesn't support glibc-2.1 on Linux / x86_64

Please contact Loki Technical Support at support@lokigames.com
```

```
This installation doesn't support glibc-2.1 on Linux / x86_64
```

Thanks very much guys,

JInx13

---

### Post by DoktorSeven on 2011-04-15
> **Jinx13 said:**
> 

```
This installation doesn't support glibc-2.1 on Linux / x86_64
```

Thanks very much guys,

JInx13

[http://www.linuxgamepublishing.com/faq.php?id=9&#faq_2_3](http://www.linuxgamepublishing.com/faq.php?id=9&#faq_2_3)

> 2.3 When I try and install the game, I am told: This installation doesn`t support glibc-2.1 on Linux / x86_64
 	Instead of typing ./setup.sh as shown in the manual, type: 

linux32 ./setup.sh 

so you'd need something like **sudo linux32 sh ./SETUP.SH**

A good thing to do whenever you encounter an error like that is to copy it into a Google search; you'll often find the answer since many others have been down the same road you're going down.

---

### Post by Jinx13 on 2011-04-15
Hmm beginning to think this game doesn't want to work lmao

```
jinx13@jinx13-Aspire-8935G-Laptop:~/Documents/SimCity 3000 Linux Edition/Game$ sudo linux32 sh ./SETUP.SH
This installation doesn't support glibc-2.1 on Linux / x86
```

The same error without "64" on the end :(

---

### Post by doorknob60 on 2011-04-17
Warning, this game is very tough to get running on modern systems, but it is possible. Last time I tried it (maybe a year or two ago), I basically did it by following instructions I found from other people that got it working, combining parts from different guides, and doing thigs until they worked. I wish I could help, but I don't remember what I did that made it work, sorry :( Here you go, good luck :) [http://www.google.com/search?q=how+to+install+simcity+3000+on+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=how+to+install+simcity+3000+on+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a)

---

### Post by Soulcage on 2011-04-17
I'm just wondering do you have ia32-libs installed? Idk if it will help.

---

### Post by decalguy on 2011-04-18
Isn't Sim City 3000 a windows game and need to be installed and ran though Wine?

---

### Post by Jinx13 on 2011-04-18
> **doorknob60 said:**
> Warning, this game is very tough to get running on modern systems, but it is possible. Last time I tried it (maybe a year or two ago), I basically did it by following instructions I found from other people that got it working, combining parts from different guides, and doing thigs until they worked. I wish I could help, but I don't remember what I did that made it work, sorry :( Here you go, good luck :) [http://www.google.com/search?q=how+to+install+simcity+3000+on+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=how+to+install+simcity+3000+on+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-a)

Thanks for the link was already trying to follow guides from google will just carry on trying :)

> **Soulcage said:**
> I'm just wondering do you have ia32-libs installed? Idk if it will help.

Yup i'm sure I have.

> **decalguy said:**
> Isn't Sim City 3000 a windows game and need to be installed and ran though Wine?

This is the linux version.

---

