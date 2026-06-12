---
title: "How to install savage?"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by Porta-Chaves on 2007-03-27
I donwloaded Savage form [http://www.happypuppy.com/s2games/Savage_with_sep3t.run](http://www.happypuppy.com/s2games/Savage_with_sep3t.run) and tried to follow this guide: [http://ubuntuforums.org/showthread.php?t=381732&highlight=savage](http://ubuntuforums.org/showthread.php?t=381732&highlight=savage) . But as mentioned there the links are broken and the versions are old, besides, the file is a .run and if I execute it it opens in gedit.

Does anyone know how to install it?

---

### Post by Porta-Chaves on 2007-03-27
I found some instruction teling me how to execute a .run file (here: [http://ubuntuforums.org/showthread.php?t=241098](http://ubuntuforums.org/showthread.php?t=241098))

But then I get this error:

```


cristiano@cristiano:~/Desktop$ sudo chmod +x Savage.run
cristiano@cristiano:~/Desktop$ sudo ./Savage.run
Verifying archive integrity... All good.
Uncompressing Savage and SEP3T Installer..........................................................
/home/cristiano/.setup12535: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

What's wrong?

---

### Post by Iarwain ben-adar on 2007-03-27
It's good to see that you went searching :D

So, it complains about libgtk not being found.. :wink:

```
sudo aptitude install libgtk1.2
```


Iarwain

---

### Post by Porta-Chaves on 2007-03-27
thnx! installation worked fine, but now I try to open it by going to Applications --> others --> Savage (I noticed in total 3 new icons: savage, savage graveyard and savage ded. server) but noting happend!!

---

### Post by Perfect Storm on 2007-03-27
Start'em through the terminal to watch for errors/output.

---

### Post by Porta-Chaves on 2007-03-27
I'm a bit new to all this... I can get to the Savage folder but I don't know how to execute it... i tried:

```

cristiano@cristiano:/usr/local/games/Savage$ savage
System_Init()
Game error during initialization:

Couldn't open scripts.log

(nothing happens)

```

and

```

cristiano@cristiano:/usr/local/games/Savage$ sudo savage
Password:
System_Init()
no startup.cfg found, generating one for you...
Unknown command: '/usr/local/games/Savage'

(screen goes black for 5 secs and then it closes)


```

---

### Post by Perfect Storm on 2007-03-27
Did you hit the launch savage from the savage installer(if it had any?)?

Something else;
```
cd /usr/local/games
ls -a
```

---

### Post by Porta-Chaves on 2007-03-27
i think it had but i didn't press it.. and the code you provided only gives a list of files in that folder...

---

### Post by Perfect Storm on 2007-03-27
OKay it seems the launcher is poining at the wrong place then, try go into the Savage folder and ls -a again

---

### Post by Porta-Chaves on 2007-03-27
This is what I got:

```

cristiano@cristiano:/usr/local/games/Savage$ ls -a
.                       dedicated_server.bin  libs          scripts.log
..                      eula.txt              licenses.txt  silverback.bin
agp_error.txt           game                  logo.png      uninstall
autoupdater             graveyard             .manifest     update
commander_controls.txt  Graveyard             README        updater
Dedicated_server        icon.xpm              Savage


```

---

### Post by Perfect Storm on 2007-03-27
okay, then;

```
./Savage
```

---

### Post by Porta-Chaves on 2007-03-27
same error:

```
cristiano@cristiano:/usr/local/games/Savage$ ./Savage
System_Init()
Game error during initialization:

Couldn't open scripts.log

```

---

### Post by Perfect Storm on 2007-03-27
I guess savage isn't build for global install then. Uninstall it and install it as a user (without sudo) in your home folder.

---

### Post by Porta-Chaves on 2007-03-27
can't uninstall it... or am I doing it wrong?

```
cristiano@cristiano:/usr/local/games/Savage$ ./uninstall
Could not find a usable uninstall program. Aborting.


```

---

### Post by Perfect Storm on 2007-03-27
sudo infront when you handle stuff outside your home.

---

### Post by Porta-Chaves on 2007-03-27
cristiano@cristiano:/usr/local/games/Savage$ sudo ./uninstall
Could not find a usable uninstall program. Aborting.

---

### Post by Perfect Storm on 2007-03-27
Okay, then uninstall it manually;
```
cd /usr/local/games
sudo rm -rf Savage
cd /usr/local/bin
sudo rm -rf Savage*
sudo rm -rf savage*
cd
sudo rm -rf .Savage*
sudo rm -rf .savage*

```

That should do it.

Now install it as user now.
(If you can wait, I'm going to write a howto on savage tomorrow).

---

### Post by Porta-Chaves on 2007-03-27
ok i wait for tomorrow, please notify (if you can) when your howto is online...
thanks in advance

---

### Post by Perfect Storm on 2007-03-28
Here's the howto: [http://gaming.gwos.org/e107_plugins/content/content.php?content.61](http://gaming.gwos.org/e107_plugins/content/content.php?content.61)

---

### Post by K.Mandla on 2007-03-28
If I could interject, there's a tgz package [here]("http://www.newerth.com/?id=downloads&op=displayDownload&category=1&file=SFE-Standalone.tar.gz") that you can decompress into your home directory and the shell script inside will start up Savage automatically. (Of course, your video drivers, etc., have to be set up already. ;) )

---

### Post by Porta-Chaves on 2007-03-28
isn't that version quite old??

---

### Post by Porta-Chaves on 2007-03-28
Installation finishes, but I get this error:

```

cristiano@cristiano:~/Desktop$ sh Savage.run
Verifying archive integrity... All good.
Uncompressing Savage and SEP3T Installer..........................................................

Gdk-WARNING **: locale not supported by C library

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkEntry'

Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkEntry'

Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.


```

If I try to run it trough menu, screen goes black for 3 secs and then closes...

if i run trough command:

```

cristiano@cristiano:~/.Games/Savage$ sh Savage
System_Init()
Unknown command: '/home/cristiano/.Games/Savage'


```

---

### Post by Porta-Chaves on 2007-03-28
I installed the tar you provided, extracted it and it worked... but i get a white screen! I followed [these]("http://ubuntuforums.org/showthread.php?p=1853705") instructions but it didnt work..

I can now see some text inlcuding "login" and "new accounts will be automaticly created", also my mouse leaves a trail, it looks more that my mouse is a brush...

---

### Post by K.Mandla on 2007-03-28
> **Porta-Chaves said:**
> isn't that version quite old??
Actually, I was under the impression that was the newest, patched version. It starts up perfectly and syncs with the servers immediately for me. It's off the Savage forums, too. :confused:

---

### Post by Perfect Storm on 2007-03-28
The one I made is straight off from their homepage which contains v2.00e + sep

---

### Post by Porta-Chaves on 2007-03-28
they are both from their website, the one mentioned by Arteficial Intelligence is from their download page, it contains Savage 2.00e + SEP3T, the one K.Mandla mentioned  is from the help page that links to a forum post found at the lower part of the same page of the above. It says it's a Linux Stand Alone version of Savage whith the latest SFE patch (if you click on the link that redirects you to the patch it says it's SEP3T) after install you can see at launch at the bottom right corned 2.00e

Strange thing is that I can only launch the one mentioned by K.Mandla, the contets seem to be different but I'm not shure of that.

But thats is not the problem, my problem is something related to the graphics or video quality or even my video card... any suggestions in how to fix this??

---

### Post by Perfect Storm on 2007-03-28
What video cad do you have by the way?

---

### Post by Porta-Chaves on 2007-03-28
My graphics card is simple... but savage works for me in WinXp...

(got this from toshiba.nl)
fabricatort : Intel®
type : Intel® 852GME
memory size : tot 64 MB
memory type : DDR RAM (UMA=shared) 


Here are the pictures I took whith the loading:

WHITH ORIGINAL STARTUP.CFG FILE:

While loading:
[ [IMG]http://www.imagehosting.com/out.php/t396717_nocodeload.jpg[/IMG]](http://www.imagehosting.com/out.php/i396717_nocodeload.jpg)

After loading:
[ [IMG]http://www.imagehosting.com/out.php/t396716_nocodeafterload.jpg[/IMG]](http://www.imagehosting.com/out.php/i396716_nocodeafterload.jpg)

CHANGED STARTUP.CFG and LOADING SCRIPT (according to [site]("http://www.ubuntuforums.org/showthread.php?t=313933&highlight=savage+white+screen")) :

While loading:
[ [IMG]http://www.imagehosting.com/out.php/t396719_whithcodeload.jpg[/IMG]](http://www.imagehosting.com/out.php/i396719_whithcodeload.jpg)

After loading:
[ [IMG]http://www.imagehosting.com/out.php/t396718_whithcodeafterload.jpg[/IMG]](http://www.imagehosting.com/out.php/i396718_whithcodeafterload.jpg)

see for yourselfses...

The one with code while loading looks exactly as in WinXp, but then it goes wierd again...

EDIT: my mistake :S u put up the tumbnails.. please wait until i fix this...(fixed!)

---

### Post by Porta-Chaves on 2007-03-29
I'm having no luck getting it running 100%, I changed many cvars at the /game/startup.cfg file (cvars related to vid compression and resolution, etc.) but I still get the same results. I also tried to get it running on window mode but I get the same problem...

---

### Post by Perfect Storm on 2007-03-29
I'm not sure how well the intel driver is for linux, but it could be related.
Sorry I can't you :-/
Do you have other problems with 3D stuff?

---

### Post by rajeev1204 on 2007-03-30
Hi

i cant get savage to run either .

I get error saying command not found /home/rajeev/Savage



Iam trying to get this working . will let u know if it does .'

Meanwhile any help is appreciated


regards
rajeev

---

### Post by rajeev1204 on 2007-03-31
Hi

it seems the savage version 2 e sep 3 is compiled for newer kernels. It says 2.6.17 in one of the log files ( dont remember which one)

So i guess it wont play in my dapper .

Artificial intel -- can u confirm if savage runs on dapper?




regards

rajeev

---

### Post by Perfect Storm on 2007-03-31
I can't, sorry. Only Edgy machines. (and plating with the idea to move to Feisty soon). That's why my howto only says tested edgy x86

---

### Post by rajeev1204 on 2007-03-31
hmm no problem

iam installing feisty beta . will try on it and give u feedback



regards

rajeev

---

### Post by Porta-Chaves on 2007-04-06
how do I upgrade to edgy anyway? and what are the differences?

---

### Post by Gen2ly on 2007-05-28
> **Artificial Intelligence said:**
> I'm not sure how well the intel driver is for linux, but it could be related.
Sorry I can't you :-/
Do you have other problems with 3D stuff?

I use the Intel 950 chipset and savage runs just fine considering.  I had to the the startup.cfg hack.  Sound is a little bit choppy though.

---

### Post by alinuxfan on 2007-06-07
I am running on a x86-64 system and I am getting the error
```
adam@adam-desktop:~$ ./savage
./silverback.bin: error while loading shared libraries: libcom_err.so.2: cannot open shared object file: No such file or directory
adam@adam-desktop:~$                                
```

Anyone know of a howto to install on x86-64

thanks

---

### Post by desicratn on 2007-06-13
I followed the Ubuntu Gaming website install and it works great on my Fiesty Box. 

So I decided to install it on my p3 800 Edgy box.It has a Geforce 4200ti 256 Megs or RAM, by the website specs it should run...
When I follow the install How to  when I ge t to the installer I get a GTK warning saying the destination doesnt support C Library?
After I install and run the program from the folder in terminal I get 

System_Init()
Unknown command: '/home/desi/.Games/Savage'


I dont have any issues with 3d Enemy Territory works just fine....
I am doing something wrong but.. I dont know what... Any ideas?

---

### Post by defec8ing on 2007-08-18
I have the same problem with the paintbrush mouse as earlier user- has someone  got an Idea about how to fix it?

---

### Post by psoulocybe on 2007-08-18
I have the same problem with silverback.bin with 7.04 x64.

---

### Post by sheepdogj15 on 2007-09-01
> **psoulocybe said:**
> I have the same problem with silverback.bin with 7.04 x64.

yeah. It says: 

```
./Savage: 21: ./silverback.bin: not found
```


It turns out it's due to missing libraries for going between x86_64 and i386.

Open your favorite package manager, and install ia32-libs. or:
```
sudo apt-get install ia32-libs
```


But now I'm getting the same error as this guy:

> adam@adam-desktop:~$ ./savage
./silverback.bin: error while loading shared libraries: libcom_err.so.2: cannot open shared object file: No such file or directory
adam@adam-desktop:~$

This looks like the possible solution:
[http://ubuntuforums.org/showpost.php?p=2906295&postcount=8](http://ubuntuforums.org/showpost.php?p=2906295&postcount=8)

```
cd /tmp
wget http://mirrors.kernel.org/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb
dpkg -x libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb libcom
sudo mv libcom/lib/* /lib32
```

---

### Post by sheepdogj15 on 2007-09-01
woops. i guess it isn't the same error.

---

### Post by airtonix on 2007-09-04
Just finished with world of warcraft until they make geographically located servers in australia.

so i wiped windows, installed xubuntu feisty...have my ati prop drivers cranking....and now am looking for something to play.



I remember this game....of which i had already kept a copy of said sept3 release.

installed in a folder writable by all, using my own account to do it.

ran fine.

but....updater requires libssl? but otherwise seems fine.

---

