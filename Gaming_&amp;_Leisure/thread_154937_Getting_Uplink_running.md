---
title: "Getting Uplink running"
date: 2006-04-04
forum: Gaming &amp; Leisure
---

### Post by glotz on 2006-04-04
Hi there. Searched [Ubuntu Wiki](https://wiki.ubuntu.com/Games) but no entry there on [Uplink](http://www.uplink.co.uk/).  Trying to run Uplink I get ```
./uplink: symbol lookup error: ./uplink: undefined symbol: __glutRoot
```

I found [this thread](http://forums.introversion.co.uk/uplink/viewtopic.php?t=35531) in Uplink forums addressing the issue but how do I apply those patches? Got the full game. I'm a Linux newbie, so if you help, keep it really simple! :D

Trust maybe a weakness, but I trust you to help me!

[[IMG]http://img105.imageshack.us/img105/5579/uplinkbackgroundaf8.th.png[/IMG]](http://img105.imageshack.us/my.php?image=uplinkbackgroundaf8.png)

---

### Post by Thorin on 2006-04-04
Since you already have the game installed, my suggestion would be to use the loki updater found [here.]("http://www.uplink.co.uk/cgi-bin/countdownmemset.cgi?uplink-full-1.31.sh") Not at my home box, so I can't tell ya how it works, but loki has yet to fail me.

---

### Post by glotz on 2006-04-04
Uhm, am I to open the file with something or save it and then what? Did I mention I'm pretty green... Firefox suggests to open it with gedit which says that it can't open it and tried saving the file and running it thru terminal and file browser but it couldn't make it work... I feel slightly daft here. Maybe I should go back using windows 3.1...

---

### Post by Thorin on 2006-04-04
Woah, let's not do anything rash here...Give me a few minutes to drag out my uplink disc, will edit my post with further instructions.

EDIT: it appears I left the CD at a friend's house, will have to wait until morning, but here is my suggestion, have you tried running the downloaded file?

```
Applications -> Accessories -> Terminal
```

You will then be looking at the Ubuntu equivalent of a command prompt. Assuming you saved the file to your Desktop, you would then type in: 

```
cd Desktop

sudo sh uplink-full-1.31.sh
```

See if that won't get you running.

---

### Post by glotz on 2006-04-10
Thanks Thorin. A nice GUI'd installed popped up and all went smoothly until half way install it demanded to "mount the CD". Which was in the CD drive! Then I went to install without the CD data files, which worked, more or less.

But it wouldn't run but threw me some error I can't remember now. (It was a long and bloody battle...) After this I did something and got it running. Have downloaded the both patches and fooled around with them like crazy. At one point I copied all files to the install folder/lib. as I was presented with an error messages that some .dat files weren't found in the ./lib folder. Ugliest possible install procedure resulting in tons of duplicate unneeded files, but hey, it works!

(I guess this post isn't exactly wiki stuff for people who have difficulties installing the game, but at least they'll know it's doable.

I might later try to figure out the exact procedure I used. Reply here if you'd like to see it.)

---

### Post by Thorin on 2006-04-10
Well, this is embarassing, but when I pulled out my cd, it gave me the same errors you were getting, so I'm all for seeing the method you used. I think i'm going to play with it a bit more tonight, will see what I can come up with. Congrats on getting it working though!

---

### Post by sharperguy on 2006-04-11
any GPL games like this (cr/hacking sims)?

Just wondering.

---

### Post by vozik on 2006-04-11
Allright, I think I've just found out, what's going on here.
I followed the steps mentioned before and got stuck, cause it
threw me a message, that i have some .dat files missing.
The file that was missing is "patch.dat".
Seems like in introversion they have just ommited that one in
the loki patch...
I found the file rather by an accident. I told my bash to locate patch.dat 
for me, and it pointed me to my old windows installation of uplink. 
I copied it from there. 
So I suggest U guys to DL the loki-patch (.sh file), run it, 
select the non CD instalation. After that, DL the another patch(alternative
mirror), and copy the patch.dat to the /lib folder, in your uplink folder. Easy 
and working.

Hope that helps. 
GL HF ;)

---

### Post by glotz on 2006-04-18
If somebody can confirm this procedure, let's write a Wiki article!

---

### Post by Ob1 on 2006-04-19
is Uplink Open source?

---

### Post by Thorin on 2006-04-19
No it's not, it's from a company called introversion. [www.introversion.co.uk](www.introversion.co.uk)

---

### Post by glotz on 2006-04-19
[QUOTE=Ob1]is Uplink Open source?[/QUOTE]

Nope, proprietary. (love your sig. btw)

---

### Post by sparehead1 on 2006-07-18
I can confirm this method, I'm using xubuntu so i had to:

sudo apt-get install gtklib1.2

although that step sort of explains itself cause when you try to run the .sh updater it complains that gtklib1.2.lib or something like that, isn't there.

So for me I poped in the cd, unzipped the file in the linux directory on the cd to my home/my_home/uplink dir and tryed to chmod the uplink file (no idea what i did wrong there, just wouldn't execute even though ls -l said it was read and execute by all. Prolly something basic I dont know about BASH but punching in uplink while in the dir i extracted everything too did jack)  then grabbed uplink-full-1.31.sh and from /home/my_home/uplink ran:

sh uplink-full-1.31.sh

and did the no cd data option, then did:

cp *.dat /usr/local/games/uplink/lib/

then I grabbed linuxpatch1.31.tar.gz and used xarchiver to extract patch.dat into home/my_home/uplink and then did:

cp patch.dat /usr/local/games/uplink/lib/

This was needed to resolve this error message:

/usr/local/games/uplink
/usr/local/bin/uplink: Fatal error: missing data files (*.dat) in /usr/local/games/uplink/lib
If you have just installed the patch to the full version of the game
you will need to copy *.dat from your existing uplink installation

hope this is helpful to any others who have had problems :)

---

### Post by sparehead1 on 2006-07-19
ok dont do what I did!

I dun broke xfce4 and im rebuilding now ](*,) 

I'm going to try and get it going using the original files from the cd and the files from the alternate patch (not the .sh installer)

wish me luck! Cause I have no idea how I'm going to get it to work or even where or if there will be error logs :???:

---

### Post by contarc on 2006-07-30
Copying all the *.dat files from the tarball patch after running the loki patch worked for me too.  Method works.

---

### Post by hygraed on 2006-07-30
> **sharperguy said:**
> any GPL games like this (cr/hacking sims)?

Just wondering.

Well, there's [Endgame: Singularity](http://emhsoft.net/singularity/index.html), which is a game where the player is an AI trying to stay alive by building a worldwide computer network. There's also [Hackz 2](http://home.nedlinux.nl/~florian/), which isn't playable yet, but looks pretty badass.

---

### Post by ericsp on 2006-09-02
I am using Ubuntu 6.06 and I keep getting the following error: ./uplink: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

any suggestion?
Eric

---

### Post by Beggar Su on 2006-09-04
> **ericsp said:**
> I am using Ubuntu 6.06 and I keep getting the following error: ./uplink: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

any suggestion?
Eric

What I did to get it working (using ubuntu dapper drake 6.06) was to

+ Unzip uplink.zip from cd to i.e /home/usr       ~home folder
+ Download both loki and tar patches from uplink website
+ Run the loki sh script (edit the install path of uplink if you put it somewhere else. Also to uncheck 'CD Data Files')
+ Patch created a lib folder in uplink folder. Copy the .dat files in the uplink folder to the lib folder.
+ Untar the tar patch and copy the patch.dat to the lib folder and 'uplink'
 script to main uplink folder.
+ Terminal, change directory to uplink folder. Run ./uplink

Hope that helps

---

### Post by glotz on 2006-09-04
> **ericsp said:**
> I am using Ubuntu 6.06 and I keep getting the following error: ./uplink: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

any suggestion?
Eric

Can you find libstdc++-libc6.2-2.so then? (**sudo locate -u** followed by **sudo locate libstdc++-libc6.2-2.so**) If you do have it, you might want to try copying it to same location where it is to the filename you're 'missing'. Sounds crazy all right, but just might work... :biggrin:

---

### Post by Jonahhubunutu on 2006-11-26
He'll have em, that seems like the best step by step process i've seen about this thing, Beggar Su...
I'm gonna try it myself been waiting for this for a while, had the same prob as this guy numerous directions and couple of threads later i find this, 
i'll get back to ya if it doesn't work,
job...

---

### Post by Jonahhubunutu on 2006-11-26
> **Beggar Su said:**
> What I did to get it working (using ubuntu dapper drake 6.06) was to

+ Unzip uplink.zip from cd to i.e /home/usr       ~home folder
+ Download both loki and tar patches from uplink website
+ Run the loki sh script (edit the install path of uplink if you put it somewhere else. Also to uncheck 'CD Data Files')
+ Patch created a lib folder in uplink folder. Copy the .dat files in the uplink folder to the lib folder.
+ Untar the tar patch and copy the patch.dat to the lib folder and 'uplink'
 script to main uplink folder.
+ Terminal, change directory to uplink folder. Run ./uplink

Hope that helps
Yeah it works, i had trouble running the x-app in a shell script way so i just overwrote the uplink file with the demo shell script i downloaded from introversion, thanks a bunch kid,
luck of the irish be with ya!

---

### Post by glotz on 2007-09-03
Looks like there's another patch. Here's how I got it working this time. Extract the zip in the Linux folder on the CD. Download Patch 1.54 for Linux from [http://www.uplink.co.uk/otherfiles.html](http://www.uplink.co.uk/otherfiles.html) and run it. Then copy *.dat from the folder you extracted the stuff to it's subfolder lib. Then just run ./uplink.

---

### Post by StooJ on 2007-09-20
Thanks Glotz, I got it working with your instructions.
However, I am a linux beginner, so it took me a while to get everything together.
Here's my beginners guide to getting Uplink working with Ubuntu (I'm using Feisty)

First of all, Uplink requires libgtk1 for the installation wizard to work. Install it using:

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install libgtk1.2
```

*(If someone knows how to do the following steps with the terminal I'd be grateful for their help)*

I used the CD to install uplink. Put the CD in and open up the terminal.
Navigate to your CD using
```
cd /media/cdrom
```
Now open up the linux folder located on the cd using
```
cd linux
```

Before we copy the linux files from the CD to your computer, lets make a temporary folder to keep the files.

```
mkdir ~/Uplink
```

Now copy the file (which is a single zip file by the way) into your new folder

```
cp uplink.zip ~/Uplink
```

Now head over to your new Uplink folder

```
cd ~/Uplink
```

Unzip the files in this directory by typing

```
unzip uplink.zip
```

Now you need to download the latest linux patch from the[ Uplink website]("http://uplink.co.uk/otherfiles.html") (version 1.54 at time of writing). Save the file to your desktop (usually this is the default for Firefox)

Once it is downloaded run the patch using:
```
cd ~/Desktop
sudo sh uplink-patch-1.54.sh
```

It's probably best to leave the settings as they are. I will assume you have done so.
The installation wizard is very straightforward, follow the onscreen instructions and don't change the options.

Now we just need to copy the files you took off the CD into the Uplink game folder. The latest uplink patch includes a new sound.dat, so I wouldn't copy this one. The easiest way to do this (I've found) is touse the -u switch with the cp command. This Updates your files (ie only overwrites files if the source is newer than the target. Since the new patched sound.dat is newer than the old sound.dat we obtained off the CD, when we copy the files it won't overwrite the latest sound.dat. Geddit?

Anyway, to do this:

```
sudo cp -u ~/Uplink/*.dat /usr/local/games/uplink/lib
```

That's it! It sounds a lot more complicated than it actually is.

There is one slight problem I've found with my installation though. Uplink (And Darwinia for that matter) add a shortcut to your applications menu, but it seems to go into the wrong place.
It's easy to move it to your games folder
**System** -> **Preferences** -> **Main Menu**
Using the main menu preferences you can easily move the shortcut to your **games** folder (it's in the **Other** folder by default, by the way). Just drag the shortcuts into the **Games** folder

To run the game, click on the shortcut you've just moved, or (because it's Uplink and it's that bit more immersive) type Uplink into the terminal.

Enjoy this awesome game.

By the way, it's safe to delete the Uplink folder in your home folder now.

---

### Post by glotz on 2007-09-20
Glad to be of any use. Great writeup mate! I missed that new sounds file completely! It would be cool if somebody included this in the wiki, say at [https://wiki.ubuntu.com/Games/Uplink](https://wiki.ubuntu.com/Games/Uplink) I was too lazy to do it myself... :oops:

---

### Post by StooJ on 2007-09-20
Thanks Glotz.

Write on the wiki? That'd be my "coming of age" in Ubuntu - I'd love it!

However, I'd like to get the guide streamlined a bit more first. If I knew the command to extract the zipped file to the home folder or something I'd be well up for publishing it.

In the meantime, I'm going to post it on the [Ubuntu Gamers Arena]("http://gaming.gwos.org/doku.php/start") tonight.

---

### Post by glotz on 2007-09-20
Great! :D

To cd into the cdrom do cd /media/cdrom
Then cd into the linux folder
To make a folder you mkdir. e.g. mkdir ~/games/uplink
To copy the zippie do cp uplink.zip ~/games/uplink
Then cd into ~/games/uplink
To extract the zip you unzip. e.g. unzip uplink.zip

I hope I didn't include too many logic errors there... Don't worry about getting the wiki page perfect. The point of a wiki is that everybody can contribute and fix any errors that there might be. I think writing this kind of 'meta documentation' is a good way for newbies (like myself) to give back something to the community. From newbies to newbies! :)

---

### Post by stomponthis on 2007-10-25
Great guide, thanks

---

### Post by jack handy on 2007-12-06
anyone know how to get mods working in linux?  like custom gateways and stuff?

edit: nevermind, found my answer:  extract to /uplink/lib instead of just to /uplink

---

### Post by nefrin on 2008-05-20
Hi all

I am trying to install Uplink as well from the CD that I did get from introversion.co.uk. The issue that I am facing is that everyone keeps telling me to unzip the uplink.zip file that is located on the CDROM, but I don't have an uplink.zip file. the only file located in the Linux folder is uplink-complete-1.31.sh

when I run that, all I get is:

Verifying archive integrity... All good.
Uncompressing Uplink complete 1.31............................................................................

Then nothing happens, and I'm not seeing any files located anywhere on my system.

Am I missing a file on the CD (as in did I get a bad copy?) or am I missing a step here?

---

### Post by glotz on 2008-05-20
I think you've either got a defective CD or maybe they've changed the contents. They have a forum, try asking there if nobody here comes up with a solution. And the future generations will appreciate you posting the solution here once you figure it out. :)

---

### Post by nefrin on 2008-05-20
Ok, trying to bypass the CD issue by downloading the linux version direct from introversion (1.54).

when trying to sh the .sh file, I get this issue:

/home/usr/.setup8136: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I do have libgtk1.2 installed, and as far as I know I am not running any other apps that would interfere with this (such as Adept or Package Manager).

I have also searched/asked for help on the Uplink forums. There is one posting that is kinda similar, but since the OP is/was using the unoffical HE version produced in the states, his CDROM was all together different from mine, thus making his steps to completetion not very good for me (I have tried).

---

### Post by glotz on 2008-05-20
Try [http://ubuntuforums.org/showpost.php?p=1460629&postcount=19](http://ubuntuforums.org/showpost.php?p=1460629&postcount=19)

---

### Post by nefrin on 2008-05-20
I did search my system for the libgtk-1.2 files, and found them in the /usr/lib folder.

tried to copy them to my home folder, and the Uplink folder, but still getting the same error 

(/home/(user name)/.setup10699: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory) 

I would copy them to the .setup folder, but it doesn't exist on the system after trying to install.

Can you suggest where I need to copy these files to?

---

### Post by glotz on 2008-05-20
Do a sudo cp /usr/lib/libgtk-1.2.so /usr/lib/libgtk-1.2.so.0

This might be a bad idea, dunno. It worked for me once.

---

### Post by nefrin on 2008-05-20
cp: cannot stat `/usr/lib/libgtk-1.2.so': No such file or directory

above error when I try the copy command.

looking through my /usr/lib, I have both libgtk.so and libgtk-1.2.so.0, and according to the system they are the same file.

---

### Post by nefrin on 2008-05-20
Woot, I finally got uplink to install in Ubuntu. 

As it turns out, Uplink is a 32 bit program, and I am running a 64 bit OS, which was causing the problems. Synpatic was *only* installing the 64 bit versions of the libgtk-1.2.so.0 files, which where the conflicts were coming from.

Here is the fix, for anyone else. Also may work for other problems encountering the same area:

[http://whynotwiki.com/GNU/Linux_/_Running_32-bit_applications_on_64-bit_Linux](http://whynotwiki.com/GNU/Linux_/_Running_32-bit_applications_on_64-bit_Linux)

Followed this wiki to the letter (except I didn't have to run through the steps a third time like the writer) and finally the install kicked in with I ran "sh setup.sh"

Basically, you have to go hunt for for the 32 bit files that you don't have, and manually copy them over to your ~/lib32 directory so that you can use 32 bit programs.

---

### Post by MoridinBG on 2008-06-01
I got it running ont 8.04 Kubuntu, but the text is invisible?! I can't see any text, only the buttons and images.

---

### Post by Cebonet on 2008-06-17
I get this error and I did install libgtk1.2: 


Verifying archive integrity... All good.
Uncompressing Uplink patch 1.54......................................................................................
/home/cebrail/.setup10374: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

i don't understand.

---

