---
title: "Limewire."
date: 2005-12-16
forum: General Help
---

### Post by Helljumper on 2005-12-16
Before you say anything, Yes I read the manual and it doesn't work. Also, I already searched previously made threads and they haven't helped. I can not get limewire. I follow what everything says and when I try to access the file with any command it says that the file cannot be found and does not exist. Any help?

---

### Post by Qrk on 2005-12-17
sudo apt-get install gtk-gnutella

---

### Post by andlinux21 on 2005-12-17
have you tried automatix? it will install limewire along with a bunch of other useful apps :D

---

### Post by BLTicklemonster on 2005-12-17
[http://ubuntuforums.org/showthread.php?t=80638&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=80638&highlight=frostwire)

try this instead. It's just like limewire but no nag. (like it's divorced or something)

---

### Post by Gurgeh on 2005-12-17
Naaaah get the rpm package and alien it to a .deb package, then run the old dpkg -i to install, works for me ;-)

---

### Post by Helljumper on 2005-12-17
[QUOTE=andlinux21]have you tried automatix? it will install limewire along with a bunch of other useful apps :D[/QUOTE]

No I haven't. This method that you give seems..A lot easier :D..How do I get automatrix?

---

### Post by BLTicklemonster on 2005-12-17
trust me, 

```
sudo apt-get update

sudo apt-get install frostwire
```

and you are done.

---

### Post by cstudent on 2005-12-17
[QUOTE=BLTicklemonster]trust me, 

```
sudo apt-get update

sudo apt-get install frostwire
```

and you are done.[/QUOTE]


What repository is it on? I search Synaptic and can't come up with it.

---

### Post by BLTicklemonster on 2005-12-17
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse
## created by arniebackports


unless I'm wrong, which is usual.

google frostwire if not.

---

### Post by cstudent on 2005-12-17
Looks like the same repositories I have. I already Googled for it and downloaded the Any-OS.zip file. Right now I'm trying to figure out how to make it run if I place it in /opt. It doesn't like being there. It does run if I just unzip it in my /home and java -jar the file. Looks just Limewire without the "Upgrade to Pro" nag.

---

### Post by cstudent on 2005-12-17
Got it working now with a nice menu icon and everything:

Here's what I did:

Enter code via the terminal (Applications>>Accessories>>Terminal). This how-to assumes the use of Ubuntu with the Gnome desktop. Except for having to remove the sinqle quotes in the first example, you should be able to copy and paste each line in the terminal. 

First start by getting the zip file for FrostWire. (Remove the single quotes at each end. I had to use them to get the full path to show up.)

```


**'wget http://home.fuse.net/t3dcinc-887b/mirror/downloads/bin/FrostWire-4.9.37-0-Any-OS.zip'**


```


Next extract the zip file to the /opt directory and change permissions. You will be prompted for your password.

```


[B]sudo unzip -u FrostWire-4.9.37-0-Any-OS.zip -d /opt/
sudo chown -R root:root /opt/FrostWire/[/B]


```

Now add a little script in the /usr/bin/ directory. First open our scipt file in the text editor.

```


**sudo gedit /usr/bin/runFrostWire.sh**


```

Now enter the script code into the text editor that opened.

```


cd /opt/FrostWire/
java -jar FrostWire.jar


```

Save and close the text editor.

Now let's make it executable for everyone.

```


**sudo chmod +x /usr/bin/runFrostWire.sh**


```

Now we need to add a menu item to our applications menu. Again we are going to use the text editor to write a script.

```


**sudo gedit /usr/share/applications/FrostWire.desktop**


```

Now we enter our code in the text editor.

```


[Desktop Entry]
Name=FrostWire
GenericName=Free P2P Gnutella client
Comment=Search and share all kinds of files on the Gnutella network
Exec=/usr/bin/runFrostWire.sh
Icon=/opt/FrostWire/FrostWire.ico
Terminal=false
Type=Application
Categories=Application;Network;


```

Save and close the file.

That should be it. Go to your Applications menu and look under Internet. You should see and entry for FrostWire. Click on it and fire it up!

Hope this is of use to some people. Thanks to Arnieboy and the old Unofficial 5.04 Guide for showing me how to do this. If any errors are found please let me know and I'll correct them.

Thanks to ykpaiha for the chmod +x suggestion.

*Edit: Corrected error in filename for chmod +x*

cstudent

---

### Post by BLTicklemonster on 2005-12-17
Oh. I just downloaded it to /home/bill/ and ran it.

---

### Post by ykpaiha on 2005-12-17
[QUOTE=cstudent]Got it working now with a nice menu icon and everything:

Here's what I did:

-----------------------------------

That should be it. Go to your Applications menu and look under Internet. You should see and entry for FrostWire. Click on it and fire it up!

Hope this is of use to some people. Thanks to Arnieboy and the old Unofficial 5.04 Guide for showing me how to do this. If any errors are found please let me know and I'll correct them.

cstudent[/QUOTE]


Great how-to!!!
It should be in the right howto section!
I was amazed ! it looked exactly like the original limewire --without the lemon of course (lol).
Just a single comment :
it can be added 
chmod +x on the /usr/bin/runFrostWire.sh
(sudo chmod +x /usr/bin/runFrostWire.sh)
thanks

---

### Post by cstudent on 2005-12-17
[QUOTE=ykpaiha]Great how-to!!!
It should be in the right howto section!
I was amazed ! it looked exactly like the original limewire --without the lemon of course (lol).
Just a single comment :
it can be added 
chmod +x on the /usr/bin/runFrostWire.sh
(sudo chmod +x /usr/bin/runFrostWire.sh)
thanks[/QUOTE]


Thanks for the suggestion to add chmod +x. I've edited my post to reflect it. I'll look into putting the how-to in the how-to section. I thought I might also look at the wiki and see what I would need to do to add it there.

---

### Post by Gurgeh on 2005-12-17
Nice one the must of took some effort that, I can never be arsed to write proper howtos, lol I do try and add the odd clue tho.

---

### Post by Helljumper on 2005-12-17
[QUOTE=cstudent]Got it working now with a nice menu icon and everything:

Now let's make it executable for everyone.

```


**sudo chmod +x /usr/bin/FrostWire.sh**


```
[/QUOTE]

There. There is stopped working. It said again. File can not be found or accessed :( 
Help?

---

### Post by cstudent on 2005-12-17
[QUOTE=Helljumper]There. There is stopped working. It said again. File can not be found or accessed :( 
Help?[/QUOTE]


I'm not 100% sure what you are asking. If you are following the how-to and get to the line "sudo chmod +x /usr/bin/FrostWire.sh" and you get an error that says the file was not found it could be:

1. You didn't save the file in the previous step.
2. You made a typo and named the file something else.

First let's try this:

Open the file browser (Nautilus) and move up to the directory /usr/bin/ by clicking on **Places** then **Home Folder**. Click the UP button twice. Double click on the **usr** folder and then double click the **bin** folder. Now look through that folder for runFrostWire.sh and see if you see it. If you do, is it spelled exactly like I typed it?

Let me know what you find.

---

### Post by Helljumper on 2005-12-17
I found it. Exactly as you typed.

---

### Post by Gurgeh on 2005-12-18
It woulda been sooo much easier just to alien the .rpm tho :P

---

### Post by GazaM on 2005-12-18
Yeah I aliened the .rpm and everything went perfectly. It's pretty much limewire - adds which I'm happy with. It could use some nicer themes/logo/artwork but for functionality it is perfect. Thanks for pointing this one out to me.

---

### Post by Gurgeh on 2005-12-18
Yep, no probs (if that was to me) it is a bit ugly tho isn't it. But it works and it works well.

---

### Post by cstudent on 2005-12-18
[QUOTE=Gurgeh]It woulda been sooo much easier just to alien the .rpm tho :P[/QUOTE]

What would be the fun in that? :)

The problem with converting rpm to deb with  alien is you never know if it's going to work or not. I also prefer to know where things are going to be installed.

---

### Post by antidrugue on 2005-12-18
[quote=Gurgeh]Naaaah get the rpm package and alien it to a .deb package, then run the old dpkg -i to install, works for me ;-)[/quote]

Certainly the best way to do it.

Build the package with alien and fakeroot:
```

sudo apt-get install alien fakeroot
fakeroot alien -d LimeWireLinux.rpm

```

Install the resulting .deb package:
```

sudo dpkg -i limewire-free_4.9.37-1_i386.deb

```

Automatix? I wouldn't dare running that on my system...

---

### Post by BLTicklemonster on 2005-12-18
[QUOTE=antidrugue]

Automatix? I wouldn't dare running that on my system...[/QUOTE]

Reason?

---

### Post by antidrugue on 2005-12-18
[quote=BLTicklemonster]Reason?[/quote]

Because I'm just too conservative. ;)

And, I had no choice but to learn how to install [them all]("http://ubuntuforums.org/showthread.php?t=105343&highlight=automatix") on Debian.

That being said, automatix does look very nice, great initiative.

I just think it is essential to be able to install those manualy. But, then again, it may be way to much trouble for most people.

---

### Post by BLTicklemonster on 2005-12-18
Yeah, old school, huh? Love that avatar by the way.

---

### Post by mztriz on 2005-12-18
just get aMule, much better not to mention you can connect to limewire with it ;)

---

### Post by BLTicklemonster on 2005-12-18
I have used emule and amule many times, and to this day, I have yet to actually get a file downloaded. They just sit there and say waiting for more resources. I even tried ones that showed tons of people sharing them.

Oh, and you all do know that if you have a file that is like 815 or 817 kb, that it's more than likely a virus, so delete it so that it's not available for upload, right?

---

### Post by Gurgeh on 2005-12-19
antidrugue, a man (or woman) after my own heart.

---

### Post by Des33 on 2005-12-19
[QUOTE=Helljumper]There. There is stopped working. It said again. File can not be found or accessed :( 
Help?[/QUOTE]

yeah i had the same problem.. should it be :

```

sudo chmod +x /usr/bin/runFrostWire.sh

```

and not
```

sudo chmod +x /usr/bin/FrostWire.sh

```

nice howto dude.. but alas not working for me...

---

### Post by cstudent on 2005-12-19
[QUOTE=Des33]yeah i had the same problem.. should it be :

```

sudo chmod +x /usr/bin/runFrostWire.sh

```

and not
```

sudo chmod +x /usr/bin/FrostWire.sh

```

nice howto dude.. but alas not working for me...[/QUOTE]

Thanks for catching that. I've edited my post to reflect the correction. I'll also correct the wiki page, since the same mistake was pasted to it.

If it still does not run, what version of Java are you using? The FrostWire site suggest Sun's version.

---

### Post by Des33 on 2005-12-19
[QUOTE=cstudent]
If it still does not run, what version of Java are you using? The FrostWire site suggest Sun's version.[/QUOTE]

yeah its down to my java... i have 1.4.2 and 1.5 installed on my machine... i'm gonna sort that out now ... your howto is spot on.. my java locations are not.. lol

---

### Post by cstudent on 2005-12-19
Don't know if you know this command or not. Just in case:

```

sudo update-alternatives --config java

```

---

### Post by Des33 on 2005-12-19
```
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy

```

error from terminal... but i do have java there...

---

### Post by cstudent on 2005-12-19
What do you get if you enter:

```


java -version


```

---

### Post by Des33 on 2005-12-19
```

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

not the sun version is appears... i just realised i only have the SDKs installed.. downloading the runtime enviroment now.. that should solve the problem..

---

### Post by cstudent on 2005-12-19
Are you doing it by the Sun instructions? If you want an easy way to install it in 32bit Breezy try Automatix. It can simplify things. See my sig for a link to the thread for it.

---

### Post by Des33 on 2005-12-19
umm yeah.. ive done it correctly.. still no go..

heres a screenie of my usr/java folder..

---

### Post by Des33 on 2005-12-19
oops nevermind.. got it working :) thanks :D

---

### Post by cstudent on 2005-12-19
Excellent.

---

### Post by shadow07 on 2005-12-19
Nice find with the FrostWire.  I was always wanting to find a good alternative to  LImeWire. Now, only if FrostWire would support eDonkey/Overnet.

---

### Post by Gurgeh on 2005-12-20
As if, whats wrong with limewire?

---

### Post by antidrugue on 2005-12-20
[quote=shadow07]Nice find with the FrostWire.  I was always wanting to find a good alternative to  LImeWire. Now, only if FrostWire would support eDonkey/Overnet.[/quote]

FrostWire a good alternative to LimeWire?

If it doesn't support eDonkey/Overnet, how is it an alternative?

For myself anyway I just use torrents. I like Azureus, the well known memory-eater.

---

### Post by Gurgeh on 2005-12-22
Memory eater and a bleedin half. The things so baaad i've set up a VMware machine on a pc in the garage just for it to eat and Terminal service in when I need to get stuff lol, Such a cool application tho, the stats it gives are ace.

Plus, whats wrong with limewire? That GNUtella is just overkill, I like my options but with that app there so many it left my harddrive almost as soon as I put it on. It like sooo un-user friendly, I think the guy who made it wrote it for himself...

---

### Post by shadow07 on 2005-12-22
Because there have been issues with finding certain items on the Limewire P2P network, that are on Overnet P2P.  There's more content on the Overnet network period.

---

### Post by alynx on 2005-12-22
[QUOTE=Qrk]sudo apt-get install gtk-gnutella[/QUOTE]

hi 

what do i have to add in my sourceslist to get this ?

---

### Post by Gurgeh on 2005-12-23
Is there really? Well i'll have to look into that. Like the 'period' bit by the way shadow07, quite the haughty type aren't ya :P

---

### Post by alynx on 2006-01-05
im so glad i installed Amule , no hazzle at all.  But it's kinda hard to get down some files there IMO

---

### Post by alynx on 2006-01-09
finally got Limewire to work , so much easier to get to the files :) weee:rolleyes:

---

### Post by mattbarlow on 2006-01-12
Really Great 
I believe that it is as good as Limewire pro not the regular limewire am i right?

---

### Post by goathunter on 2006-01-17
[QUOTE=antidrugue]Certainly the best way to do it.

Build the package with alien and fakeroot:
```

sudo apt-get install alien fakeroot
fakeroot alien -d LimeWireLinux.rpm

```

Install the resulting .deb package:
```

sudo dpkg -i limewire-free_4.9.37-1_i386.deb

```

Automatix? I wouldn't dare running that on my system...[/QUOTE]

Hello.
I did as you said when installing limewire, and got as far as making the .deb file, but it won't install. Its says its unpacking etc but nothing shows up in the apps menu and it won't run from the commmand line either.


"marcus@marcus:~$ sudo dpkg -i limewire-free_4.10.3-1_i386.deb
Password:
(Reading database ... 59089 files and directories currently installed.)
Preparing to replace limewire-free 4.10.3-1 (using limewire-free_4.10.3-1_i386.deb) ...
Unpacking replacement limewire-free ...
Setting up limewire-free (4.10.3-1) ...
marcus@marcus:~$"

"marcus@marcus:~$ limewire
sh: runLime.sh: No such file or directory
marcus@marcus:~$ LimeWire
bash: LimeWire: command not found
marcus@marcus:~$ LimeWireLinux
bash: LimeWireLinux: command not found
marcus@marcus:~$
'

Everthing else seemed to work as expected until I got to this point. BTW I do have JRE installed and also have got frostwire to work as well using the alien method on this thread. However I also wanted to give limewire a go for comparison.
Could someone please help me with this?
Thanks for your time.

---

