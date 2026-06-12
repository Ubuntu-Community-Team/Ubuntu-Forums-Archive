---
title: "some possibly dumb new user qns"
date: 2004-12-19
forum: Desktop Environments
---

### Post by liquid boy on 2004-12-19
i just got given a copy of ubuntu 4.10 ... it installed nicely enough (even automatically configured my network settings perfectly...:) )
i've had (a little) experience with linux, but mostly windows and beos *drool*, so i'm not really used to this
what directory are apps installed into, by default. it's kind of confusing for me cos in windows/beos you just install to any folder. where as (it seems to me anyway) in linux there's a specific place you have to install stuff too...

i was trying to install flash player7, and i extracted the archive, and *tried* to go to the directory which was created in a terminal, but it told me the folder didn't exist... :| and i was just going to manually put the necessary files in the plugins folder, but since i don't know where the firefox folder is, and i can't find it using a search... (my next question)

i tried searching for stuff, but nothing comes up, i searched in the folder "/" (instead of /boot/matthew - which is the default)

how do you make it so that when using nautalus (spelling?) you can see the directory path?

also, when i drag windows around, there's 'lag' (if that makes sence) it's almost like computer is very slow (but its a 1.3mhz 256mb ram, which isn't that slow)

how do i get it so that (in gnome) when i drag windows around, it doesn't show the content? and is there a way of getting rid of the minimize window animation?


ok, i think that's about it (for now :P) thanks.

---

### Post by jodef on 2004-12-19
> i was trying to install flash player7, and i extracted the archive, and *tried* to go to the directory which was created in a terminal, but it told me the folder didn't exist... :| and i was just going to manually put the necessary files in the plugins folder, but since i don't know where the firefox folder is, and i can't find it using a search... (my next question)

i tried searching for stuff, but nothing comes up, i searched in the folder "/" (instead of /boot/matthew - which is the default)

how do you make it so that when using nautalus (spelling?) you can see the directory path?



First you may want to check out the 
[Unofficial Ubuntu Starter Guide](http://ubuntuguide.org/index.html) 
Under the section add on applications you will see the easy way to install flash in Ubuntu.

To see the path in Nautilus :
Computer -> Desktop Preferences -> File Management -> Select Behaviour Tab and select always open in browser window.

---

### Post by liquid boy on 2004-12-19
ah, yes, the starter guide......  *cough* thanks. :P

---

### Post by LongTooth on 2004-12-19
liquid boy  *cough*. I like your response. Lol. Go to the HowTo section. One of the best is Ubuntu-geek's "Tweaking Ubuntu after your first installation". That one will really get your system fine tuned. Also, Disposible's "Ubuntu Multimedia" will get your video need going. This one has grown to some 15 pages. Some folks have problem but there are solutions to them. Read it completely to the end. Oh, but wait, there more! You'll really appreciate Zenwhen's "Make your fonts smooth enough to drool over". Less I forget, don't pass up the "Intellimouse/Mouseman extra buttons config" howto from Panickedthumb if you have a thumb button on you mouse. I've got my working. Amazing how usefull it is. And last but certainly not least is this one I did just yesterday - Jconnell's "Bluecurve on Ubuntu". Coming from Fedora Core 2, it brings on a warm and fuzzy feeling. 

By the way, Jodef's tip on the " Unofficial Ubuntu Starter Guide" is right on. It chock full of good information. Check it out. 

There is more but those will help in making your Ubuntu experence much more enjoyable.

---

### Post by liquid boy on 2004-12-20
hmm i think that i need something more basic than even the starter guide... i want to to explain *why* and *what* not just how..

> 3. Enable Universe in Synaptic.
Quote:
From your desktop select Computer > System Configuration > Synaptic Package Manager you will be asked to enter your password. Goto Settings > Repositories you will see (2) grayed out boxes click both of them, then click the Reload button.

um i'm assuming that "universe" means enabling it to se repositories on the internet? i followed the instructions. i clicked both (one after another) im not sure what it's supposed to do, since there's no reload button in the repositores window, i'm assumign tis talking about the one in the main window. so i click both , close the window and click "reload" - now there's 3 things greyed out... um, this is rather confusing.

also, how do i change the colour depth (to 32bit) the wall paper looks like its in 16bit mode...


> First open a terminal window and enter:
sudo nano /etc/apt/sources.list

Look for the following lines:
Quote:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted


Change them to look like:
Quote:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe

Save the file and then run:
sudo apt-get update

This will update your repository and include all the files available in the universe. if i open it in a terminal, i can change it, but i can't save it. if i open it in a text editor, i can't change it. it wontc let me write... this is *alot* of effort to go to just to be able to install software...

---

### Post by LongTooth on 2004-12-20
liquid boy, when I first started working with Linux, GUIs gave me trouble. Don't know why but they did. CLIs did too. Some instructions are given in such a way that leaves newbies scratching their heads. I started playing with PC late in life and maybe that's why it was hard for me to pick it up. But for young bucks like you it may come easier.  Lets take it slow and easy. And if I may suggest, don't go too deep. In time all of this will start to make sense. Don't worry about the why and what right now. Just strive for success. A little bit of that will go a long way to bolstering your ego and keep you working in Linux. It not really hard. Like brain surgery, once you've got the basics down, the rest is easy!


"...um i'm assuming that "universe" means enabling it to se repositories on the internet? i followed the instructions. i clicked both (one after another) im not sure what it's supposed to do, since there's no reload button in the repositores window, i'm assumign tis talking about the one in the main window..."


This step will add more repositories to you source.list. Once you've done that, on the main window click "reload". To add other repositories you will have to add them at the bottom of that window. Just click on the ones that come with Ubuntu to see the parttern and what informatin is need. Stop. Slow down. Take it easy. Back out if needed.  


"....deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted..."


This is an easy step if you use the GUI (Synaptic). They are there. Just click the boxes and 'reload' (main Synaptic window) when done. 

When adding other not already on the list click on the box of those already there and see below to see what information goes where. Again hit 'reload'. on the main Synaptic window.


"...sudo nano /etc/apt/sources.list..."


Stay from editors like nano, vim, joe for the time being and use 'gedit'. It's a GUI based editor and very easy to use. Your input should look like this:

sudo gedit /etc/apt/sources.list

The GUI gedit will open and you make the changes needed. When done, look for the 'floppy' on top to save. If you open a file with gedit and you get a message that says - you don't have this file do you want to save it -  you have not opened the correct file and gedit is asking you if you want to make a file and save. Click no.Of course if you want to make a file say yes. But save that for later. Slow and easy, remember?  

But you don't have to us an editor for this particular job. Stick with Synaptic. One other thing, you will have to use an editor and gedit is the one I recommend. Matter of fact it's the only one I use. Even after all of the years, I feel its the easy and best for my needs. Why drive a stick shift car when you can use an automatic? Eh?

If you feel more comfortable using a GUI by all means do. For 90% of you work in Linux a GUI is avalible. Still, don't forget the CLI. Can't do without it. 

Writ back for more information and help. We will be here.

---

### Post by Rancoras on 2004-12-20
[QUOTE=liquid boy]um i'm assuming that "universe" means enabling it to se repositories on the internet?[/QUOTE]

"universe" is a repository that contains software that is not supported by the developers.  That means they don't do security updates on the packages.

[QUOTE=liquid boy]if i open it in a terminal, i can change it, but i can't save it. if i open it in a text editor, i can't change it. it wontc let me write...[/QUOTE]

If you open in the terminal, make sure you are typing

```
sudo nano /etc/apt/sources.list
```

If you prefer and GUI editor, you can also type in the terminal

```
sudo gedit /etc/apt/sources.list
```

When is asks you for the password, you enter the password for the account you created during the install process.

---

### Post by liquid boy on 2004-12-20
well, i'm writing this from xfce, so i guess i (or some mysterius force) sorted synaptic out... yep gedit is alot easier... i think that things are *starting* to make sence to me...    thanks for the patient replies :)


oh btw, i tried to install flash by doing this 
```
$ sudo apt-get install flashplayer-mozilla
```
it said it couldn't find it, but then i did it in synaptic and it worked fine... go figure :P

---

### Post by jdong on 2004-12-20
[http://ubuntuforums.org/showthread.php?t=8486](http://ubuntuforums.org/showthread.php?t=8486)

If you'd like newer XFCE packages (4.2 RC2 at the moment), try Ubuntu Backports!

You only need to add the Stable Backports section.

---

### Post by jodef on 2004-12-20
What are the packages req'd for basic XFCE install I am on dial up. So I could always add later on.

---

### Post by jdong on 2004-12-20
[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/)

Hard to say. It's a desktop environment, lots of packages interdepend.


Best way: Go to a broadband system, download the packages from the link that start with 'xf'. Transfer them to /var/cache/apt/archives.

---

### Post by LongTooth on 2004-12-20
Liquidboy, the easest way I found to install flash is 'sudo apt-get install flashplugin-nonfree'. Of course remember, with sudo the system will ask you for your 'user password'. Or you can use Sysnaptic>search> flashplugin-nonfree. Apply. That's all there is to that! Bye the way, have you added to your source.list by either CLI or via Synaptic? Do so before anything else.

---

### Post by liquid boy on 2004-12-22
um, i added those repositories. a few of them failed when i hit 'reload', and when i start it up it gives me this error:
> Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) warty-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ub...se_binary-i386_dists_warty-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)

when i do a search for firefox,it only give s me the 0.99 version. no the 1.0 version, adn xfce -  4.0.5-2 is the newest version i can get.

---

### Post by Rancoras on 2004-12-22
Try reloading again, maybe the repo was unavailable for a bit.  If that doesn't work, post your sources.list here. (make sure to use code tags, it makes it much easier to read)

---

### Post by LongTooth on 2004-12-22
LiquidBoy, stay away from the 'backport' repository for the time being. Jdong is doing a great job working on it but you are too new to take that on. You can get most if not all of what you need by adding Universal. Its are already listed in Synaptic. Also manually add  multiverse and marillat will get you more packages.  

Binary (deb)
URL: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Distribution: warty
Section (s): multiverse  

Binary (deb)
URL: [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
Distribution: testing
Section (s): main  

Your Synaptic should have the resources it came with plus the one listed and checked by you (Universal). and the two added by hand (marillat and multiverse). Tlhat's more that enough for anyone. Here you are just learning Linux and you want to add a backport listing? Get real! You're bitting off more then you can chew. One has to learn to crawl before one can walk. Slow and easy, remember?

---

### Post by liquid boy on 2004-12-23
here's my sources.list:
```
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  


deb http://archive.ubuntu.com/ubuntu/ warty main restricted universe  
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted universe 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe 

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted 

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe 




deb http://ubuntu-bp.sourceforge.net/ub...se/binary-i386/ warty-backports universe 



deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports-staging main universe 

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-extras contrib universe 

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-extras-staging contrib universe 

deb http://www.getsweaaa.com/~tseng/ubuntu/debs ./

```

---

### Post by Rancoras on 2004-12-23
It's having trouble with this line:

deb [http://ubuntu-bp.sourceforge.net/ub...se/binary-i386/](http://ubuntu-bp.sourceforge.net/ub...se/binary-i386/) warty-backports universe 

I don't think that one is necessary, do you recall why you added it?

---

### Post by liquid boy on 2004-12-24
um actually, i dont recall :P probably doesn't need to be there huh?

appart from that, can you see what might be causing problems?

---

### Post by Rancoras on 2004-12-25
I would just remove that line.  The rest of the file looks fine.

---

### Post by liquid boy on 2004-12-25
so it should all start working fine once i remove that line?

---

### Post by Rancoras on 2004-12-25
If you're unsure, just comment the line out, and then you can re-enable it if it doesn't work right.

---

### Post by liquid boy on 2004-12-25
[QUOTE=LongTooth]LiquidBoy, stay away from the 'backport' repository for the time being. Jdong is doing a great job working on it but you are too new to take that on. You can get most if not all of what you need by adding Universal. Its are already listed in Synaptic. Also manually add  multiverse and marillat will get you more packages.  

Binary (deb)
URL: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Distribution: warty
Section (s): multiverse  

Binary (deb)
URL: [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
Distribution: testing
Section (s): main  
[/QUOTE]

hmm, i added the two lines manually. i saved the file. when i opened synaptic, it gave me these 3 errors:
> Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
> Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
> Couldn't stat source package list [http://www.getsweaaa.com](http://www.getsweaaa.com) ./ Packages (/var/lib/apt/lists/www.getsweaaa.com_%7etseng_ubuntu_debs_._Packages) - stat (2 No such file or directory)

this is my sources.list now: (its not much different to before):
```
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  


deb http://archive.ubuntu.com/ubuntu/ warty main restricted universe  
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted universe 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe 

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted 

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe 

deb http://archive.ubuntu.com/ubuntu/ warty multiverse

deb ftp://ftp.nerim.net/debian-marillat/ testing main




##deb http://ubuntu-bp.sourceforge.net/ub...se/binary-i386/ warty-backports universe 



deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports-staging main universe 

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-extras contrib universe 

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-extras-staging contrib universe 

deb http://www.getsweaaa.com/~tseng/ubuntu/debs ./
```

---

### Post by LongTooth on 2004-12-25
LiquidBoy, let me tell you a story about my experience with Fedora Core 2. Everytime I saw a post about a new repository, I would add it to my Yum source.list. And why not? The more the merrier, right? Wrong. Have you ever heard about what too many cooks do to the broth? They spoil it. Too many sources means conflicts. Keep your source list to the ones that it came with plus Universe, multiverse and marillat. And that is all for now. As you grow you'll learn which sources to add and which to comment out. Now keep it simple and move on to other challenges.

As for the error messages, try later. Sometimes the repositories are down or busy or something. As long as you've input them correctly.

---

### Post by liquid boy on 2004-12-26
ok, sweet, i'll do that.  i'll cut out all the backports for now...

thanks for the advice.

---

### Post by nigrima4977 on 2007-05-15
> **liquid boy said:**
> hmm i think that i need something more basic than even the starter guide... i want to to explain *why* and *what* not just how..



um i'm assuming that &quot;universe&quot; means enabling it to se repositories on the internet? i followed the instructions. i clicked both (one after another) im not sure what it's supposed to do, since there's no reload button in the repositores window, i'm assumign tis talking about the one in the main window. so i click both , close the window and click &quot;reload&quot; - now there's 3 things greyed out... um, this is rather confusing.

also, how do i change the colour depth (to 32bit) the wall paper looks like its in 16bit mode...


 if i open it in a terminal, i can change it, but i can't save it. if i open it in a text editor, i can't change it. it wontc let me write... this is *alot* of effort to go to just to be able to install software...


[memory food science Bankruptcy Girls Bankruptcy](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

### Post by haker20057544 on 2007-05-15
> **LongTooth said:**
> liquid boy, when I first started working with Linux, GUIs gave me trouble. Don't know why but they did. CLIs did too. Some instructions are given in such a way that leaves newbies scratching their heads. I started playing with PC late in life and maybe that's why it was hard for me to pick it up. But for young bucks like you it may come easier.  Lets take it slow and easy. And if I may suggest, don't go too deep. In time all of this will start to make sense. Don't worry about the why and what right now. Just strive for success. A little bit of that will go a long way to bolstering your ego and keep you working in Linux. It not really hard. Like brain surgery, once you've got the basics down, the rest is easy!


&quot;...um i'm assuming that &quot;universe&quot; means enabling it to se repositories on the internet? i followed the instructions. i clicked both (one after another) im not sure what it's supposed to do, since there's no reload button in the repositores window, i'm assumign tis talking about the one in the main window...&quot;


This step will add more repositories to you source.list. Once you've done that, on the main window click &quot;reload&quot;. To add other repositories you will have to add them at the bottom of that window. Just click on the ones that come with Ubuntu to see the parttern and what informatin is need. Stop. Slow down. Take it easy. Back out if needed.  


&quot;....deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted...&quot;


This is an easy step if you use the GUI (Synaptic). They are there. Just click the boxes and 'reload' (main Synaptic window) when done. 

When adding other not already on the list click on the box of those already there and see below to see what information goes where. Again hit 'reload'. on the main Synaptic window.


&quot;...sudo nano /etc/apt/sources.list...&quot;


Stay from editors like nano, vim, joe for the time being and use 'gedit'. It's a GUI based editor and very easy to use. Your input should look like this:

sudo gedit /etc/apt/sources.list

The GUI gedit will open and you make the changes needed. When done, look for the 'floppy' on top to save. If you open a file with gedit and you get a message that says - you don't have this file do you want to save it -  you have not opened the correct file and gedit is asking you if you want to make a file and save. Click no.Of course if you want to make a file say yes. But save that for later. Slow and easy, remember?  

But you don't have to us an editor for this particular job. Stick with Synaptic. One other thing, you will have to use an editor and gedit is the one I recommend. Matter of fact it's the only one I use. Even after all of the years, I feel its the easy and best for my needs. Why drive a stick shift car when you can use an automatic? Eh?

If you feel more comfortable using a GUI by all means do. For 90% of you work in Linux a GUI is avalible. Still, don't forget the CLI. Can't do without it. 

Writ back for more information and help. We will be here.


[Mortgages Britney Spears blood pressure weather Mortgages](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

