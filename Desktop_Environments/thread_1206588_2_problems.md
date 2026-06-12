---
title: "2 problems"
date: 2009-07-07
forum: Desktop Environments
---

### Post by Tomickescape on 2009-07-07
Hi all,

[B]First one:
[/B]
After 2 days of searching trough the net (mainly ubuntuforums) I still have the " desktop could not be enabled" 

I have this Nvidia driver: ```
05:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
```"compiz" at terminal gives me this:

```
tomickescape@tomickescape-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```at hardware drivers it says " no propietary drivers are in use on this system"  and the screen below is blank


I tried envy, which crashed.

I tried A lot of things, but none of them really worked, I hope you can help me? =)

Ow yeah, I am using Ubuntu 8.04.

[B]
Second one:

[/B]For youtube I need adobe flashplayer, I coulnd't install this one, because of the message: 
*I downloaded "install flash player plugin version 10.deb" *

```
Error: Dependency is not satisfiable:libpango 1.0-0
```So I downloaded libpango 1.0-0 and I got 

```
Error: Dependency is not satisfiable:libcairo
```Installed it...So I was still stuck there....

I choose to use another one (schockwave flash I guess?)  but this add-on is installed...just fine...but de plug-in is still blank while it tries to download any video clip.

So I hope you can tell me how to uninstall that version that doesn't work and install adobe flashplayer.



I really hope you could help me, because I really don't know what to do anymore...

And if you didn't noticed...I am a newb =P

Greetz

Mick

---

### Post by masux594 on 2009-07-07
I've the answer for the second problem.. Try with this command..```
sudo apt-get install flashplugin-installer flashplugin-nonfree 
```

Sysc, A..

P.s. I'm an ATI owner.. no experience about nvidia =|, sorry!

---

### Post by Tomickescape on 2009-07-07
> **masux594 said:**
> I've the answer for the second problem.. Try with this command..```
sudo apt-get install flashplugin-installer flashplugin-nonfree 
```Sysc, A..

P.s. I'm an ATI owner.. no experience about nvidia =|, sorry!

Yes thank you, but this happened

```
E: Couldn't find package flashplugin-installer
```

---

### Post by masux594 on 2009-07-07
Sorry, i miss the part when u say "Ubuntu 8.04".. Oki, well, try to install only the second with ```
sudo apt-get install flashplugin-nonfree
``` ..

Sysc, A

---

### Post by Tomickescape on 2009-07-08
I'll try that as soon as I get at my moms place....thursday or friday =)

---

### Post by Tomickescape on 2009-07-08
I have done this:
```

tomickescape@tomickescape-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for tomickescape: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
flashplugin-nonfree is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
```
I would love to copy paste it in english, but I don't know how to change the language of the terminal...

Anyway it says that I already have the latest version, and that there is nothing update or installed.

---

### Post by masux594 on 2009-07-08
Hmm.. Well, i've fount an article in italian.. i will translate quickly in steps:

[LIST=1]
[*]Close FF
[*]```
sudo apt-get remove flashplugin-nonfree
```
[*]```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb
```
[*]```
sudo dpkg -i install_flash_player_10_linux.deb
```
[/LIST]

Hope that this guide will help u!

Sysc, A

---

### Post by Tomickescape on 2009-07-08
```
[LEFT]tomickescape@tomickescape-desktop:~$ sudo apt-get remove flashplugin-nonfree [/LEFT]
 [LEFT][sudo] password for tomickescape:  [/LEFT]
 [LEFT]Pakketlijsten worden ingelezen... Klaar [/LEFT]
 [LEFT]Boom van vereisten wordt opgebouwd        [/LEFT]
 [LEFT]Reading state information... Klaar [/LEFT]
 [LEFT]De volgende pakketten zullen VERWIJDERD worden: [/LEFT]
 [LEFT]  flashplugin-nonfree [/LEFT]
 [LEFT]0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 1 te verwijderen en 0 niet opgewaardeerd. [/LEFT]
 [LEFT]After this operation, 168kB disk space will be freed. [/LEFT]
 [LEFT]Wilt u doorgaan [J/n]? j [/LEFT]
 [LEFT](Database inlezen ... 137282 bestanden en mappen geïnstalleerd.) [/LEFT]
 [LEFT]flashplugin-nonfree wordt verwijderd ... [/LEFT]
 [LEFT]tomickescape@tomickescape-desktop:~$ wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb [/LEFT]
 [LEFT]--22:16:32--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb [/LEFT]
 [LEFT]           => `install_flash_player_10_linux.deb' [/LEFT]
 [LEFT]Resolving fpdownload.macromedia.com... 92.123.2.70 [/LEFT]
 [LEFT]Connecting to fpdownload.macromedia.com|92.123.2.70|:80... connected. [/LEFT]
 [LEFT]HTTP request sent, awaiting response... 200 OK [/LEFT]
 [LEFT]Length: 3,963,520 (3.8M) [application/x-debian-package] [/LEFT]
  [LEFT]100%[====================================>] 3,963,520    255.41K/s    ETA 00:00 [/LEFT]
  [LEFT]22:16:48 (254.68 KB/s) - `install_flash_player_10_linux.deb' saved [3963520/3963520] [/LEFT]
  [LEFT]tomickescape@tomickescape-desktop:~$ sudo dpkg -i install_flash_player_10_linux.deb [/LEFT]
 [LEFT]Selecteren van voorheen niet geselecteerd pakket adobe-flashplugin. [/LEFT]
 [LEFT](Database inlezen ... 137276 bestanden en mappen geïnstalleerd.) [/LEFT]
 [LEFT]Uitpakken van adobe-flashplugin (uit install_flash_player_10_linux.deb) ... [/LEFT]
 [LEFT]**dpkg: vereistenproblemen verhinderen de configuratie van adobe-flashplugin: **[/LEFT]
 [LEFT]** adobe-flashplugin is afhankelijk van libpango1.0-0 (>= 1.20.5); maar: **[/LEFT]
 [LEFT]**  Versie van libpango1.0-0 op dit systeem is 1.20.1-1. **[/LEFT]
 [LEFT]dpkg: fout bij afhandelen van adobe-flashplugin (--install): [/LEFT]
 [LEFT] vereistenproblemen - blijft ongeconfigureerd [/LEFT]
 [LEFT]Fouten gevonden tijdens behandelen van: [/LEFT]
 [LEFT] adobe-flashplugin [/LEFT]
 [LEFT]tomickescape@tomickescape-desktop:~$  [/LEFT]

```


Translation bold part:
"dpkg: requirementsproblems prevents the configuration of adobe-flashplugin:
adobe-flashplugin is depending of libpango 1..0-0 >= 1.20.5) ; but; version of libpango 1.0-0 at this system is 1.20.1-1" 

Basically it is the same problem as my first post told you =S

I hope you have any more options =)

---

### Post by masux594 on 2009-07-08
And, what about [this post]("http://ubuntuforums.org/showpost.php?p=4822974&postcount=1")? Or [this]("http://dev-logger.blogspot.com/2008/06/flash-plugin-in-firefox-30-on-ubuntu.html")?

Sysc, A

P.s. I never give up =P !

---

### Post by Tomickescape on 2009-07-08
None of the sites worked....tried different scrips =/

Damn, you still think you can get it to work? =(

---

### Post by masux594 on 2009-07-09
Never give up! Don't worry..I'll search for new articles!

Sysc, A

---

### Post by Tomickescape on 2009-07-09
> **masux594 said:**
> Never give up! Don't worry..I'll search for new articles!

Sysc, A

So you are doing the same thing I did for over 2 days :p

Well try searching on the issue "Error: Dependency is not satisfiable: libpango 1.0-0" 

I think that's the issue, but how to solve it? =S

---

### Post by Tomickescape on 2009-07-09
I know have  Gnash blablabla

It works...
But not perfectly =P

---

### Post by zolero on 2009-07-11
> **Tomickescape said:**
> ```
[LEFT]tomickescape@tomickescape-desktop:~$ sudo apt-get remove flashplugin-nonfree [/LEFT]
[...][LEFT]**dpkg: vereistenproblemen verhinderen de configuratie van adobe-flashplugin: **[/LEFT]
 [LEFT]** adobe-flashplugin is afhankelijk van libpango1.0-0 (>= 1.20.5); maar: **[/LEFT]
 [LEFT]**  Versie van libpango1.0-0 op dit systeem is 1.20.1-1. **[/LEFT]
 [LEFT]dpkg: fout bij afhandelen van adobe-flashplugin (--install): [/LEFT]
 [LEFT] vereistenproblemen - blijft ongeconfigureerd [/LEFT]
 [LEFT]Fouten gevonden tijdens behandelen van: [/LEFT]
 [LEFT] adobe-flashplugin [/LEFT]
 [LEFT]tomickescape@tomickescape-desktop:~$  [/LEFT]

```
[...]
I hope you have any more options =)

Wanneer u wilt klaar maaken dit vereistenproblem, u moet te maaken de volgende...  Maar dit is een wenig "unofficiel". Komt in engels nu (mijn slechte netherlands ;) ):

1.) In Nautilus as root (ALT+F2 -> gksudo nautilus) right-click on DEB package, and select "Unpack here". You'll get a directory with package's name (without deb extension).

2.) Go in that dir. There are 3 files: control and data tarballs, and a debian-binary version sticker file.

3.) Unpack the tarballs. The **control** one gives you a control dir. Rename it to **DEBIAN** (with UPPERCASE please...). Do the same with the **data** tarball. If it results in a **data** dir, go inside, cut out everything there, and paste in one level up, in the initial directory, near the DEBIAN one. Then remove the tarballs, the debian-binary and the data directory (Only if applies... If not, let the **usr**, **etc**, or **var** dirs there. They contain your package's files.) Now comes the tricky thing...

4.) Go inside the **DEBIAN** directory and open up the **control** file in an editor (gedit?). This file contains the package dependencies list (in the row beginning with **"Depends:"**). Now open up **Synaptic Package Manager**, and check out every dependency version. If you found one that doesn't match, correct its version to the one which you have installed (or installable via repositories). It doesn't matter if some aren't installed yet. The important thing is to match the requirements in the **control** file. Later this will be crucial. Save the edited control file and remove the backup from directory.

5.) Go up two levels (out of package directory) open a termnial there (or navigate to it), and issue this command at prompt:

```
dpkg --build <prepared_package_dirctory_full_name>
```

then hit ENTER. You'll get your desired application's rebuilt DEB package that met the dependency requirements to install. ;)  That's all.

As I've stated before in dutch, this is _**the very dirty, and irregular way**_ to satisfy package dependencies. Therefore I do not encourage to use this, unless he/she's in really pressed situation. Instead I suggest everyone to try building stuffs from sources. That's not so painful, but a clean, orthodox way to get things working.

---

