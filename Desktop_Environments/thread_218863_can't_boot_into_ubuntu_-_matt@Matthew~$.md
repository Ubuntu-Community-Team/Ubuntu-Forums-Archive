---
title: "can't boot into ubuntu - matt@Matthew:~$"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Zephyr on 2006-07-19
Hey guys, 

yes, I am absolutely awesome at windows Os's, but I am a complete noob to linux and I decided to install ubuntu.

So the installation went ok, and I am dual booting atm, so GRUB came up alright and everything, but then it starts to load some stuff (ok, fine), and then I have to enter my username and password (not in the nice linux screen, just on the black screen, as if it were msdos format). Once I have entered my username and password, it just stops with the following message:

matt@Matthew:~$

Above that is some stuff about admins and 'root' or something.

What is this, but more importantly, how am I able to actually get into the ubuntu OS?

HELP! 

/noob.

---

### Post by lordlollo on 2006-07-19
> **Zephyr said:**
> What is this, but more importantly, how am I able to actually get into the ubuntu OS?

Ehmmmm, most probably you have already got into your ubuntu os...
What kind of installation did you perform? Server? Desktop? Just try to enter a command and see what you get. Try for instance

```
uname -a
```

Good luck.

---

### Post by Ramses de Norre on 2006-07-19
Do ```
sudo /etc/init.d/gdm start
``` (replace gdm by kdm if you installed kubuntu)
It'll ask you for a password, this is the same password you logged in with and you wont see any signs when you type but that's perfectly normal, just type and enter;)

This should either give you the graphical log in screen, give you just a new "matt@Matthew:~$" line (try to press ctrl-alt-F7 then) or give you a bunch of errors (post them back).

Depending on the output we can help you further.

---

### Post by Zephyr on 2006-07-19
Ah, well, I don't see the OS login screen or anything.

I think I may have been given the server version... is this wrong.

I am only a noob to this so...

EDIT: righto

i did the sudo /etc/init.d/gdm start and it said command not found.

With the uname -a it came back with

Linux Matthew 2.6.15-23-server #1 SMP Tue May 23 15:10:35 UTC 2006 1686 GNU/Linux.

Should I just go for the desktop version?

Does that get installed onto my PC's hard drive?

---

### Post by Ramses de Norre on 2006-07-19
Ok, boot into ubuntu and pop in the installation disc, then run ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ubuntu-desktop
```
You then have the graphical desktop installed and you can run ```
sudo /etc/init.d/gdm start
```
it should give you the graphical log in screen now, if you get a new prompt you need to press ctrl-alt-F7 to see the log in screen.

---

### Post by Lunar_Lamp on 2006-07-19
Just to explain what happened - it appears you installed the server version of Ubuntu, which by default does not have a graphical interface (to reduce system resources).  The fix for this is above :)

---

### Post by Zephyr on 2006-07-19
HAHA awesome!

I cant thank you guys enough, all you guys that put in.

Now I just need to figure out how to use it I suppose.

Can you use say, MSN or xfire, or teamspeak on it... I cant seem to be able to run any apps?

---

### Post by Ramses de Norre on 2006-07-19
MSN: use gaim (allready installed) or aMSN (which I like better personally, it's in the repos)
I don't know the other two apps.

To install software from the repos: use synaptic (system > administartion > synaptic packet manager) or aptitude from the command line.

---

### Post by bluenova on 2006-07-19
To find out all the basics take a look here:

[Ubuntu Desktop Guide](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html)

it's a great starter guide.

---

### Post by T700 on 2006-07-19
> **Zephyr said:**
> Hey guys, 

yes, I am absolutely awesome at windows Os's, but I am a complete noob to linux and I decided to install ubuntu.



No one cares and it won't help you in your experience with Ubuntu/Linux.  I'm not trying to sound harsh, but you've got to let go of 80% of what you already know.  Linux is not Windows.  The way you did things, the programs you used, all that is different.  Just keep plugging away at it, *read the forums, *read the stickies at the top of the forums, check out the links in people's sigs, and you'll be up to speed in no time.

Linux is an amazing OS and I think you'll really like it.  Welcome and keep posting!

Paul

---

### Post by Zephyr on 2006-07-19
> **T700 said:**
> No one cares and it won't help you in your experience with Ubuntu/Linux.  I'm not trying to sound harsh, but you've got to let go of 80% of what you already know.  Linux is not Windows.  The way you did things, the programs you used, all that is different.  Just keep plugging away at it, *read the forums, *read the stickies at the top of the forums, check out the links in people's sigs, and you'll be up to speed in no time.

Linux is an amazing OS and I think you'll really like it.  Welcome and keep posting!

Paul

Sorry about that guys. I realise now I didn't have to say anything about windows at all.

The help and the speed that it comes at on these forums is amazing... I think I will try and learn as much as I can about Linux, as Paul and many other have said, it is an amazing OS.

Cheers guys.

---

### Post by mewt on 2006-07-21
hmm seems ur a gamer like me...well you can install teamspeak quite easily and use it normally..however it will occupy all ur sound system and thus while ur using it, you wont be able to listen to music or any other stuff..( i heard this should be fixed with ts3) 

to install it just dl it from [here]("http://www.goteamspeak.com") and then follow the instructions in the readme file and ull be fine... if u need help add mewt to ur xfire and ill try help you if im on windows.

xfire im afraid you wont be able to use...the devs of it havent released a version for linux afaik..

---

