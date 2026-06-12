---
title: "Teamspeak 3 has arrived! (With cross-platform QT based client and all)"
date: 2009-12-19
forum: Gaming &amp; Leisure
---

### Post by Sammi on 2009-12-19
We've been waiting for it for a looong time now. But it's here, and it's not leaving us Linux users behind with only OSS no more :D

No easy deb package yet, but we'll get by a few days more ;)

Main sire is already being hammered and is replaced with a static page with torrent download links of TS3: [http://teamspeak.com/](http://teamspeak.com/)

Here's a page with more info on TS3, if you want it: [http://www.planetteamspeak.com/content/view/79/93/](http://www.planetteamspeak.com/content/view/79/93/)

---

### Post by DeadSuperHero on 2009-12-19
That is awesome. Downloading to check out...

---

### Post by baizon on 2009-12-19
Nice, thanks for the info. HP is down :P Will try it soon.

---

### Post by Vadi on 2009-12-19
Gonna give it a shot.

---

### Post by brechdurchfall on 2009-12-19
Got it and already tried it.
Is anyone else having a problem with the 64bit client?
The CPU load of the linux client raises very quickly (few minutes) from ~10% to 100%. Client is Ubuntu 9.10/64bit.

---

### Post by Vadi on 2009-12-19
I can't use it all on 64bit, it quickly starts eating up all CPU during the voice activation test.

They also hardcoded a style unfortunately - anyone see a way to have it use the default system?

---

### Post by Cultrure on 2009-12-20
I'm having same problem with CPU usage. At start CPU is around 10% and everything works fine expect some random decoding problems. While using client, CPU usage will raise up to 180%(according to top) and the client crashes. After this I have to reboot computer to get it work again. Strange isn't it?

I'm running Ubuntu 9.10 64bit and Teamspeak3 64bit. I have tried also 32bit version on 64bit Ubuntu but the result is same.

---

### Post by Sindwiller on 2009-12-20
I'm pretty sure it's as resource-hogging as ever - I still prefer Mumble. Or even Vent if it's really necessary. :P

---

### Post by Vadi on 2009-12-20
Yeah, completely unusable for me unfortunately. Just dies to fast when trying to make the sound input work.

---

### Post by sorabsuperstar on 2009-12-21
It starts up over here (Kubuntu Karmic), but sound capturing produces nothing but crackled noise.

I guess this thing does not want to work with pulseaudio.

It is a beta yet. Fair enough.

I just hope that will not *again* stay like this, i.e. not run under pulseaudio till Teamspeak **4**, which will be released in 
[s]December 2010[/s]
[s]March 2011[/s]
[s]November 2012[/s]
[s]May 2013, together with Duke Nukem forever[/s]
[s]spring  2015[/s]
[s]late 2018[/s]
...finally arriving on December 19, 2019 at 13:37 and 38 seconds CET, about four months after the last mainstream Linux Distribution ceased their legacy support for pulseaudio (of course not supporting the then-soundstandard under Linux). 

Hey, I am not complaining. I just express my hopes :)

---

### Post by Sahkolihaa on 2009-12-21
Same CPU usage problem on Ubuntu Studio Karmic (32-bit).

---

### Post by Raiju on 2009-12-21
Getting a error at launch(im sure i just installed wrong)
```
eric@raiju-desktop:~$ sudo -i
root@raiju-desktop:~# cp -r /home/eric/TeamSpeak3-Client-linux_amd64 /usr/lib/teamspeak3
root@raiju-desktop:~# cd /usr/lib/teamspeak3/
root@raiju-desktop:/usr/lib/teamspeak3# ln -s /usr/lib/teamspeak3/ts3client_linux_amd64 /usr/bin/teamspeak3
eric@raiju-desktop:~$ teamspeak3
teamspeak3: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory
```

---

### Post by Sindwiller on 2009-12-21
So, TS3 is officially rubbish. They have to go GPL if they don't want to become even sh**tier than they already are :)

---

### Post by Technophobia on 2009-12-21
Works for me. The only real big difference between Teamspeak and Mumble is file transfer. At least they post binaries on their front page unlike the Mumble team.

---

### Post by Sammi on 2009-12-24
> **Sindwiller said:**
> So, TS3 is officially rubbish. They have to go GPL if they don't want to become even sh**tier than they already are :)

Bah, you always hear the complainers the loudest and TS3 is still beta.

---

### Post by Sindwiller on 2009-12-24
> At least they post binaries on their front page unlike the Mumble team.

[IMG]http://ultraxs.com/image-57AB_4B33DD02.jpg[/IMG]

> Bah, you always hear the complainers the loudest and TS3 is still beta. 

Even though that's true - we're in a Linux/FOSS community, TS for Linux has always been kind of b0rked in one way or another, we have a GPL replacement that runs smoother on all platforms - what were the benefits of using TS again? Even if they manage to smooth TS3 out for the gold release on Linux, what do we gain? Except for the obvious fact that we can use TS3 smoothly, since a lot of people still use it and it's often a must if you play multiplayer games, let alone MMORPG's. If I had the choice though, I'd go with something else.

---

### Post by Onyx_47 on 2009-12-24
I can confirm it didn't work and just ate CPU like crazy until I recompiled ALSA from source. I have ALSA 1.0.22 installed now, ran alsaconfig, set my card up in it, works like a charm now. 

If you have problems with it try recompiling ALSA, worked for me.

---

### Post by molafish on 2010-06-09
> **Raiju said:**
> Getting a error at launch(im sure i just installed wrong)
```
eric@raiju-desktop:~$ sudo -i
root@raiju-desktop:~# cp -r /home/eric/TeamSpeak3-Client-linux_amd64 /usr/lib/teamspeak3
root@raiju-desktop:~# cd /usr/lib/teamspeak3/
root@raiju-desktop:/usr/lib/teamspeak3# ln -s /usr/lib/teamspeak3/ts3client_linux_amd64 /usr/bin/teamspeak3
eric@raiju-desktop:~$ teamspeak3
teamspeak3: error while loading shared libraries: libfmodex64.so: cannot open shared object file: No such file or directory
```

I copied ts3client_runscript.sh to /usr/bin/ts3 instead of the symlink you did. Then I edited the script to point to the proper directory instead of the '.' char.

It worked fine out of the box on lucid (also moved it to /usr/lib as you did).

---

