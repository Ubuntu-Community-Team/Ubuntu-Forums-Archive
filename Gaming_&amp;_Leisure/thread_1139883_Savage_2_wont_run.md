---
title: "Savage 2 wont run"
date: 2009-04-27
forum: Gaming &amp; Leisure
---

### Post by Zoyberk on 2009-04-27
I just downloaded Savage 2 from official website, installed it through terminal and all went well till i tryed to run it.
When i run it, screen just goes black for second and nothing happens, i can continue work normaly and savage 2 don't run.
...i also installed it as root, and cant unistal it now, if i go to savage2 directory and run unistal it shows me that there was fatal error and it cant be done, if i want just delete all files it wont allow me to, since i instaled as root.

So could anyoen help me how to fix that, so i would be able to play it =)

---

### Post by Clopin on 2009-04-27
Did you try to read the terminal output?
I think the problem might be the OpenGL version (which I had problems with aswell), but I'd like to know the terminal output anyways.

---

### Post by Zoyberk on 2009-04-27
could you tell how to do that (I'm quite noob in ubuntu XD)

---

### Post by Clopin on 2009-04-27
Start terminal and navigate to your savage 2 folder, which in my case was:
/home/moller/Savage2/

As I assume you're already in your home folder when starting terminal, just do:
cd Savage2

In there you'll find savage2.bin, execute that using:
./savage2.bin

After doing that, Savage 2 should be executed, but since you got errors, it will post it inside terminal.

---

### Post by Zoyberk on 2009-04-27
Thats what i got:

```
zoyberk@greznica:~$ cd Savage2
zoyberk@greznica:~/Savage2$ ./savage2.bin
./savage2.bin: error while loading shared libraries: libk2.so: cannot open shared object file: No such file or directory
zoyberk@greznica:~/Savage2$ 
```


and i have savage2.bin in my savage2 folder

---

### Post by Clopin on 2009-04-27
Well, now you have the reason to your error, unfortunatly, I've got no experience with that error.
I suggest you look around on the net. It should be fairly easy to find a solution, when you know the reason to the crash.

---

### Post by Zoyberk on 2009-04-27
hehe magic of google XD, 
well, thanks for helping pointing out the problem =)

---

### Post by Vadi on 2009-04-27
Sounds like you need a reinstall - K2 is their graphics engine they made for the game.

---

### Post by maheshjr2000 on 2009-04-27
If you want to remove something you installed as root just run the uninstall script as root. sudo whatever the uninstaller is
Oh and if you want to delete something that you created as root. sudo rm -rf it.

---

### Post by Firestem4 on 2009-04-28
If you need to update the system and do an itegrity check run the Dedicated-Server.sh script. It will output a lot of code to the terminal and do nothing for a while but eventualyl will update the system. This may fix your current issue.

I had an OpenGL issue due to my system having OpenGL3.0 and their checker could not realize 3.0 was better than 2.1 lol.

---

### Post by Firestem4 on 2009-04-28
> **maheshjr2000 said:**
> If you want to remove something you installed as root just run the uninstall script as root. sudo whatever the uninstaller is
Oh and if you want to delete something that you created as root. sudo rm -rf it.

Be **EXTREMELY** careful about using "rm -rf". If used improperly it will more than likely disable your entire system. rm -rf will recursively delete a directory and the "f" arguement means non-verbose and will assume yes to all actions.

[http://ubuntuforums.org/announcement.php?f=11](http://ubuntuforums.org/announcement.php?f=11)

---

### Post by maheshjr2000 on 2009-04-28
I apologize I did assume proper usage and did not provide a warning. My post was not intended as malicious.

---

### Post by Zoyberk on 2009-04-28
> **Vadi said:**
> Sounds like you need a reinstall - K2 is their graphics engine they made for the game.

could you explain how to do that? XD

> **Firestem4 said:**
> If you need to update the system and do an itegrity check run the Dedicated-Server.sh script. It will output a lot of code to the terminal and do nothing for a while but eventually will update the system. This may fix your current issue.

I had an OpenGL issue due to my system having OpenGL3.0 and their checker could not realize 3.0 was better than 2.1 lol.
 
Did that, left it for about 10 min, nothing helped

---

### Post by maheshjr2000 on 2009-04-28
Ok Zoyberk: explain what EXACTLY you did when you installed and I or someone else on this board should be able to help you safely uninstall and reinstall.

---

### Post by sim-value on 2009-04-28
use :
```
sudo Savage2/uninstall-Savage2.sh
```

will uninstall savage then install it again ...

Do you have an ATI card ?

/me

---

### Post by Perfect Storm on 2009-04-28
Maybe a faulty download, so also try with a new download. Sounds like it's missing something from the game.


Installation;

```

mkdir ~/.Games
cd ~/Desktop
chmod +x Savage2Install-1.5.0-x86_64.bin
./Savage2Install-1.5.0-x86_64.bin
```

Destionation: /home/**USERNAME**/.Games/Savage2
Options: Default (selected) 

Should do it.

---

### Post by Zoyberk on 2009-04-28
After some trying i managed to uinstall  and install, tryed do this few times it didn't help. 
I have GeForce 8600 GT.

When i was installing i used exactly same steps as[COLOR=Black] Artifactal Intelegence posted:

[/COLOR]mkdir ~/.Games
cd ~/Desktop
chmod +x Savage2Install-1.5.0-x86_64.bin
./Savage2Install-1.5.0-x86_64.bin

> **Artificial Intelligence said:**
> Maybe a faulty download, so also try with a new download. Sounds like it's missing something from the game.

I'll trythat

---

### Post by Perfect Storm on 2009-04-28
..and you don't need to sudo anything, as you're installing it in your home directory. ;)
(Which is more safe system wise and security wise)

---

### Post by Vadi on 2009-04-28
Zoyberk, does it say anything different now?

---

### Post by Zoyberk on 2009-04-28
Currently re-downloading, will try reinstal it in about hour or two, when i get home, hope it will work :)

---

### Post by Zoyberk on 2009-04-28
Installed fresh downloaded version agen, same crap as before BUT error changed.
I runed it in terminal and got this:
```

zoyberk@greznica:~/Games/Savage2$ ./savage2.bin
Savage2 - Fatal Error: OpenGL 2.1 not available
```.

any suggestions:)

---

### Post by Zoyberk on 2009-04-28
Tried to run : savage2_update.bin < --- got same error as when i was trying to run savage
                      dedicated_server.sh <---- left like 10 mins, nothing changed

---

### Post by Perfect Storm on 2009-04-28
Try run the update bin again.

---

### Post by Zoyberk on 2009-04-28
Tried like 20 times, no luck, still same error

---

### Post by Zoyberk on 2009-04-28
wow, 
I almost gived up, just left dedicated_server.sh running in background, and refreshing this site every min if someone post solution. 
Like 20 mins after runing dedicated_server.sh computer started to lag liter and some winow poped up saying -updading Savage2-

tried to run savage 2, and eureka! its working! XD

thanks to all for all the help =):):):):):):)
Have nice day XD

---

### Post by Firestem4 on 2009-04-28
Glad you got it working. I should have mentioned it takes a VERY long time, so apologies on that part.

---

### Post by oldrocker99 on 2009-04-29
OK, here's one I haven't seen. I start the tutorial, practice charging as I am instructed, and just as another text box comes up, the game exits. I HAVE updated to 2.01.


Here's the terminal output:

./savage2.bin
warning: The VAD has been replaced by a hack pending a complete rewrite



Anyone seen this?

Toshiba L305d-S5895
ATI Radeon X1200 :(
AMD Turion TL-60

:guitar:

---

### Post by Vadi on 2009-04-29
Skip the tutorial for now, play on the newbie server - I think they haven't updated the tutorial yet and it still teaches you about interrupt which is removed now.

---

### Post by oldrocker99 on 2009-04-29
I'll give it a try in a couple of hours or so after I finish a few jobs around the house.

Thanks for the info about the tutorial.:)

:guitar:

---

### Post by izizzle on 2009-04-29
How long is the update supposed to take? Iv'e left mine running for about an hour and it lagged alot but nothing changed.

---

### Post by Zoyberk on 2009-04-30
Mine started in about 30 mins - I left terminal open for about 30 min, but only updating took about minute or less

---

### Post by Vadi on 2009-04-30
Try running the "CheckForUpdates" command too, although in my experience it didn't make it check right away

---

