---
title: "screenlets"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by shadowboxer_k on 2007-04-30
hi,

i have a pretty weak machine - 128 RAM, 20GB harddisk, and thus i don't believe i could run beryl. i do, however, want to make my desktop a bit prettier, so i was wondering if installing screenlets requires running beryl. and do screenlets only work for KDE? 
thanks in advance. sorry for the newbie questions.

---

### Post by Rospo Zoppo on 2007-04-30
Screenlets requires compiz, not beryl... I'm using it in Gnome so I think that it don't run only on KDE :)

---

### Post by shadowboxer_k on 2007-04-30
bummer. i can't install compiz on a weak machine like mine, can i?

---

### Post by rhennigan on 2007-04-30
> **shadowboxer_k said:**
> bummer. i can't install compiz on a weak machine like mine, can i?

What type of video card do you have?

---

### Post by sorcererx84 on 2007-04-30
Screenlets doesn't require Compiz, you can use it with Beryl also. Generally Compiz is a bit faster in the same hardware than Beryl.

---

### Post by kpolice on 2007-04-30
You can also run it without Compiz or Beryl, you can try it with xcompmgr but it runs better on Compiz

---

### Post by shadowboxer_k on 2007-04-30
thank you for the replies, everyone. i tried gdesklets, but to be honest, i don't quite like the look. and some of the essential ones don't work anyway. that's why i decided to go for the screenlets.

rhennigan: i am a computer dummy and quite frankly i have no idea what my video card is. i use an IMB T21 thinkpad, so it must be whatever comes with it. a friend of mine once told me i don't even have a videocard, but a chip. he is probably right. 

kpolice: > You can also run it without Compiz or Beryl, you can try it with xcompmgr but it runs better on Compiz

now, what exactly do you mean by xcompmgr? :) i am a rookie. please bear with me.

---

### Post by rolf-c on 2007-04-30
> **shadowboxer_k said:**
> now, what exactly do you mean by xcompmgr? :) i am a rookie. please bear with me.

No worries.  In your Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) do a search on xcompmgr.  Or, if you do not have the GUI running, you can do it from the command line:
```
sudo apt-cache search xcompmgr
```

You should see this among other results:
```
xcompmgr - X composition manager
```

To install, type:
```
sudo apt-get install xcompmgr
```

---

### Post by shadowboxer_k on 2007-04-30
okay. i did exactly as you said and managed to install it. any idea what to do now about the screenlets? i'm sorry i need someone to walk me through simple tasks like this but i really appreciate your help and so does my ancient laptop.

---

### Post by FuturePilot on 2007-04-30
```
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
```
There's a repo for Feisty screenlets.

Don't forget to add the gpg key
```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add -
```
```
sudo apt-get update
```

Then ```
sudo apt-get install screenlets
```

---

### Post by sloggerkhan on 2007-04-30
A question: does xcompmgr run by default once installed? (Just curious)

---

### Post by FuturePilot on 2007-04-30
You have to add a command to the sessions start up programs. But you have to have the right command so it starts the way you left it. There's a nice How To for xcompmgr here [http://ubuntuforums.org/showthread.php?t=75527]("http://ubuntuforums.org/showthread.php?t=75527")

---

### Post by shadowboxer_k on 2007-04-30
okay. i followed your directions and basically everything went smooth until i tried  to install the screenlets at the end. here's what it says:

```
kris@91-190kris:~$ deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
bash: deb: command not found
kris@91-190kris:~$ sudo gedit /etc/apt/sources.list
Password:
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4

kris@91-190kris:~$ wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add -
--06:08:54--  http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
           => `-'
Resolving hendrik.kaju.pri.ee... 195.222.13.21
Connecting to hendrik.kaju.pri.ee|195.222.13.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,353 (1.3K) [text/plain]

100%[====================================>] 1,353         --.--K/s             

06:08:55 (21.99 MB/s) - `-' saved [1353/1353]

OK
kris@91-190kris:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-security/restricted Packages
Hit http://us.archive.ubuntu.com feisty-security/main Sources
Hit http://us.archive.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-security/universe Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
kris@91-190kris:~$ sudo apt-get install screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package screenlets
kris@91-190kris:~$ 

```

can anyone please tell me what i am doing wrong?

---

### Post by shadowboxer_k on 2007-05-01
*bump*

---

### Post by Rospo Zoppo on 2007-05-01
You have to add these lines tpo /etc/apt/sources.list 

# Screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty all
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty all

---

### Post by shadowboxer_k on 2007-05-01
okay, i added these things to the source list and it still doesn't work. this is the message i get: 

```
kris@91-190kris:~$ sudo aptitude install screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "screenlets"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
kris@91-190kris:~$ 

```

it's driving me nuts. :(

---

### Post by WinterWeaver on 2007-05-01
hmm

I just installed it via that method, and it's working fine...

waiting for the install to finish atm.

Try the following...

open your sources.list again, and remove the last two you added.

then do a:
```
sudo apt-get update
```

then, go back to post #10. The first line there is the source to be added to your sources.list
or you can add the two which Rospo gave.

Then just follow the rest of the instructions there.

hope that helps.

---

### Post by airtonix on 2007-05-01
after adding those two line did you then do this again: 

> sudo apt-get update if not do it again to rebuiild the list of possible software to isntall.

then to reveal what is available for screenlets : 

> sudo apt-cache search screenletthen to install : 

> sudo apt-get install screenlet-extra screenlets-core screenlets-utils screenletshope that helps

its best to put the deb-src there as well (in your /etc/apt/sources.list) for when you come round to do more "tweaking" you will like that you already brought down the list of support files as well.
just a timesaver is all.

---

### Post by shadowboxer_k on 2007-05-01
WinterWeaver, thanks so much! it finally worked!

airtonix, thanks for the tips, mate, but when i tried to do as you said, this came up at the last line:

```
kris@91-190kris:~$ sudo apt-get install screenlet-extra screenlets-core screenlets-utils screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package screenlet-extra
kris@91-190kris:~$ 

```

i guess i hadn't added it to the repos. any idea what to do?

---

### Post by shadowboxer_k on 2007-05-01
okay. deep breaths. i did install the screenlets but i have no idea how to start them now. they don't come up in accessories (like gDesklets which i had installed but removed). please help. i want to stick a pencil in my eye.

---

### Post by sloggerkhan on 2007-05-01
try typing screenletsd from a console
You will also have to had screenlets to the running screenlet session. I think they're is a guide somewhere on beryl-project.org .

---

### Post by shadowboxer_k on 2007-05-01
thanks, sloggerkhan.

when i type screenletsd in a terminal, i get this:

```
kris@91-190kris:~$ screenletsd
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Usage: screenletsd <action> [option(s)]
kris@91-190kris:~$ 

```

i guess it's a start, but i still don't get them to run. argh. i'll try to look for a solution with google.

---

### Post by shadowboxer_k on 2007-05-01
and typing screenletsd start in terminal gets me here:

```
kris@91-190kris:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
kris@91-190kris:~$ CachingBackend: Loading cache ...
Session-file /home/kris/.config/Screenlets/screenletsd.ses not found (will be created automatically).
kris@91-190kris:~$ 
```

sigh.

---

### Post by shadowboxer_k on 2007-05-01
okay, after quite a battle, i got them running. thank you, everyone, for helping! :)

---

### Post by fwojciec on 2007-05-01
To start the daemon (a program which sits in the memory and controls screenlets):

> screenletsd start

To add the control panel screenlet to your desktop

> screenletsd add Control

Now you should be able to add individual screenlets by right clicking the Control Panel screenlet

Note: if you don't have compositing manager installed *and enabled* they will look horrible (big black boxes around screenlets).  I noticed that someone suggested that you install xcompmgr - xcompmgr it is very tasking on the CPU, more so than either Compiz or Beryl which use video cards to do the rendering.  I'm not sure what your computer is exactly, but, oh well... try it and see how it works.

---

### Post by fwojciec on 2007-05-01
I guess I was too late :)

---

### Post by shadowboxer_k on 2007-05-01
hey, thanks for the tips. actually, xcompmgr is working just fine. i'm a little shocked myself. i installed the screenlets okay and i got to run them, but now i ran into another problem. i added the mail checking screenlet and it is faulty. which would be okay if it didn't freeze all my other screenlets. it disables all other screenlets from any form of editing, and i can't remove it. does anyone have any idea how to fix that?

---

### Post by ayoli on 2007-05-01
screenlets packages embed an tool called screenlets-tray
jsut put this in you Administration>System>Preferences>Session>Startup apps
then screenlets will be launched at each startup and you will have an icon in the systray which allow to manage graphically your screenlets.

---

### Post by kpolice on 2007-05-01
> **shadowboxer_k said:**
> hey, thanks for the tips. actually, xcompmgr is working just fine. i'm a little shocked myself. i installed the screenlets okay and i got to run them, but now i ran into another problem. i added the mail checking screenlet and it is faulty. which would be okay if it didn't freeze all my other screenlets. it disables all other screenlets from any form of editing, and i can't remove it. does anyone have any idea how to fix that?

Don't use it, it is the only way.

Right now the screenlets that need internet access are problematic because when something goes wrong the screenlet block the rest. This is because all the screenlets run on the same process.

---

### Post by shadowboxer_k on 2007-05-01
grr, so i spent the last two days configuring something i managed to bork within seconds of installing. ah...but i guess this is the beauty of linux. adds an edge. :)

i guess i'll wait and hope they get fixed.

---

### Post by kpolice on 2007-05-01
That's why I only use the album art screenlet :P

---

### Post by ayoli on 2007-05-01
seems to be simple to stop screenlets daemon via the systray icons, btw i use the clock and the weather screenlet (which requires network access) and i've never try to start it without network :)

---

### Post by WinterWeaver on 2007-05-01
THANKS!! for the tip about the screenlets-tray ^_^

Never knew it existed lol...

---

### Post by shadowboxer_k on 2007-05-02
does anyone know how to uninstall screenlets properly? 

i tried with sudo apt-get remove screenlets but it doesn't really seem to work. i'm hoping to remove them and then install them again and get them to work. and this time i won't be using the damn mail screenlet. :D

---

### Post by shadowboxer_k on 2007-05-02
okay, turns out there's no need to reinstall. [here's the solution,]("http://ubuntuforums.org/showthread.php?t=356314&page=18&highlight=screenlets") in case anyone else has messed up desklets like me:

post #176

thanks, reacocard!

---

### Post by jfigue09 on 2007-05-07
.

---

