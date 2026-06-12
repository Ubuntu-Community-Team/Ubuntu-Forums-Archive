---
title: "[SOLVED] Foo Noob"
date: 2009-01-06
forum: General Help
---

### Post by i81b4u on 2009-01-06
Hi, I hope someone can help me. I have installed ubuntu version 8.04 (Hardy Heron) on my computer. Works perfectly. On a magazines cover disc i downloaded a game for linux, foobillards 3.0a, the actual file name was foobillard_3.0a.orig.tar.gz. Which i have uncompressed to my desktop which seemed to go ok, when i open it,  there are files inside , stuff like data,src,decomp and a heap more. 
The one that says install says "simply type": configure
                                              make
                                              make install 
if you want to enable the use of SDL instead of GLUT type: configure --enable-SDL
make
make install
                                                          

The only place i can find to type this stuff is in the terminal and when i do this it does nothing anyway, just an error message saying  bash: configure: command not found
Any help will be greatly appreciated, i'm trying to get away from MS altogether.

---

### Post by doug1212 on 2009-01-06
Hi,
I think that foobillards is in the repos, no need to build from source.
Doug.

---

### Post by redilyn on 2009-01-06
doug1212 is right, foobillards are in the repo and it is the same version as you are trying to install. I think it would be better to install from the repos.

```

sudo apt-get install foobillards

```

In case you want to learn how to do it here is what you would do.

Open a terminal and cd to the game folder. Then type the following

```

./configure

```

Then
```

make

```

Then
```

make install

```

If you get a permission denied error message, then you want to run the command with sudo

```

sudo make install

```

---

### Post by i81b4u on 2009-01-06
Thankyou for trying to help me.
I went and typed ./configure in the terminal, but when i hit enter i get an error saying configure: error: c compiler cannot create executables. I also tried putting sudo in front of it but same error.

---

### Post by blazemore on 2009-01-06
```
sudo apt-get install build-essential
```

---

### Post by redilyn on 2009-01-06
Okay, that just means you didn't have all the tools needed to build the program.

as blazemore says just run the command
```

sudo apt-get install build-essential

```

Then try to compile your program again. If you still get errors about missing dependencies you can run the following to download all the files you will need to compile foobillards

```

sudo apt-get build-dep foobillards

```

---

### Post by i81b4u on 2009-01-06
I have just tried that and it come back with errors again.It said couldn't find package build-essential.

---

### Post by redilyn on 2009-01-06
Okay try this

```

sudo apt-get update

```

```

sudo apt-get install build-essential

```

---

### Post by blazemore on 2009-01-06
2 options:

1. Go to Synaptic and search for build, then sort alphabetically and install the package that way.
Why do you need to compile, since its in the repos?

2. You could try apt-build:
```
sudo apt-get install apt-build
```
```
apt-build update
```
```
apt-build install **packagename**
```

This downloads the source, compiles it for you and sets up the menu entries.

---

### Post by i81b4u on 2009-01-06
I typed what you said, it did a heap of stuff in the terminal then i think it wanted to connect to the internet, it come up with errors like failed to fetch http:// etc etc
I could hook it up to the net with dial-up if i really have to.
But at the moment it has no modem in it.
Surely i shouldn't have to connect to the net just to install a game when i already have the file on cd.

---

### Post by i81b4u on 2009-01-06
"Couldn't find package" error when i tried the sudo apt-get install apt-build

---

### Post by redilyn on 2009-01-06
Ahh i see the problem now!

When installing things in ubuntu a internet connection is needed a lot of the time. Even if you have the source (which is what you have on cd) you will still have to download the tools needed to build that source from the internet.

The good news is you only have to install those tools once.

Wait, after looking further build-essential is on the ubuntu cd

Insert your cd and do the following
```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

```

---

### Post by blazemore on 2009-01-06
Okay now I see the problem.
The problem is you don't have the right files needed to compile the program. If I were you I would connect to the Internet and install the version from the repos. It shoudln't take more than 5 or 10 minutes.

---

### Post by i81b4u on 2009-01-06
Thankyou everybody for helping me, i'm going to connect it to the net and see what happens then.As Arnie says "I'll Be Back"

---

### Post by orlox on 2009-01-06
Are you sure you have the neccesary repositories enabled. You could open synaptic (system->administration->synaptic package manager) and go to configuration->repositories. From the first tab that appears (ubuntu software) check everything. Then close that window and press the reload button. after this you could do two things. Look for foobillard using synaptic, or, look for build-essential and compile foobillard from source. 

However, I would change your steps a bit to compile them. it's better to use checkinstall instead of make install because with chekinstall you create a package that is installed and that can be managed with synaptic. So, install checkinstall with synaptic, and then, instead of "sudo make install" use "sudo checkinstall".

Also, notice that the package name for the game is foobillard.  If you look for foobillards it wont show. If you're not too used to compiling programs, or using a terminal, I really reccomend you to install foobillard with the package manager. It never hurts to learn something new, but if you want to do it the simple way, just use the package manager.

---

### Post by jakeofspades on 2009-01-06
Well, I may be wrong but if you really don't want to connect to the internet then I think the build-essentials package will be included on the ubuntu cd. To install things from the Ubuntu CD:

**Installing from the Ubuntu CD**
Try inserting the cd (ignoring any options that pop up). 
Go to synaptic package manager in Applications->System->Synaptic
Go to settings at the top
Click repositories
Go to the "Third Party Software" tab
If the tick box beside cdrom:[Ubuntu....] is not ticked - tick that
Then close the settings box
Click 'Reload' at the top right - and ignore the error messages concerning failing to connect to the internet
Then try searching for 'Build' and install build-essentials (I hope it is there lol)
Thennnn you can go to the directory of your game and
./configure
make
sudo make install

**Option 2.**
But - connecting to the Internet is MUCH easier and generally a good idea in terms of keeping all your software up to date in terms of security releases etc.

If you connect to the internet you only need to go to synaptic manager, click reload, then search for the name of your game and select to install it (it will even install all the software the game may require that you might not have installed)

ps. Yea I wasn't intentionally paraphrasing the previous post

---

### Post by blazemore on 2009-01-06
Orlox, have you read the whole thread? ;P

---

### Post by redilyn on 2009-01-06
Hey thanks, i never knew about the checkinstall package. I will definitly look into that!

---

### Post by orlox on 2009-01-06
> Orlox, have you read the whole thread? ;P

Well, he seemed to be a little lost so I wanted to explain to him how to activate the repos so he could install the game directly with synaptic. Also, no one mentioned checkinstall, wich I think is a far better option than make install.

---

### Post by i81b4u on 2009-01-06
Yes Orlox, i am not a little, but completely lost.
I have pluged in a dial-up modem and now i don't know how to connect to the internet or set up the modem for that matter.
I tried what you said about the thing all the boxes are ticked, but needs internet to reload.

---

### Post by blazemore on 2009-01-06
ohh... now we've got dial-up issues.
I forgot. Linux hates dial-up.

Try installing from the CD (instructions above)

---

### Post by redilyn on 2009-01-06
btw i81b4u, while it is nice to receive thanks. It is not necessary to thank every post :)

---

### Post by orlox on 2009-01-06
Wvdial is the simplest way to get dialup if you cant get connected to the internet. Here is a howto from the ubuntu community documentation:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#Alternative%20Way%201%20(using%20wvdialconf%20&%20wvdial)]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#Alternative%20Way%201%20(using%20wvdialconf%20&%20wvdial)")

That should also allow you to see if there are no problems with youre modem. I used to have quite a hard time trying to make my modem detected four years ago, but it's probably better now.

---

### Post by i81b4u on 2009-01-06
Problem solved, a person named Reed gave me a link [http://packages.ubuntu.com/hardy/i386/foobillard/d](http://packages.ubuntu.com/hardy/i386/foobillard/d)...
It a binary file, not source code and i just downloaded it on a windows computer and put it on a flash drive, then copied it across to ubuntu desktop, right clicked it and went install.
It installed perfectly, it didn't need internet connection, which i still haven't got working anyway. So thankyou everybody for helping me and taking the time to answer.

---

