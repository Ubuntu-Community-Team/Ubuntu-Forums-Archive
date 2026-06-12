---
title: "Installing Nexuiz on Feisty"
date: 2007-05-31
forum: Gaming &amp; Leisure
---

### Post by Grazfather on 2007-05-31
Hey guys, I installed feisty probably a month ago, worked ok, but I used my laptop more.  I'm trying to install Nexuiz on this bad boy so I can have some fun, but my computer is older.
It's got 512megs of RAM, a geforce 4 card, and it's a 1ghz AMD.
I tried running it by running /usr/games/Nexuiz/nexuiz-linux-glx.sh but it froze on the first screen and had some weird stuff going on, i couldn't do anything so i had to switch to a console and kill it, but that Xsession was then messed so I only saw about a quarter of the screen.  I tried updating my graphics card driver from the nvidia website but that didn't work (No kernel template or something like that) but I'm thinking that's not it as this distro should come with new drivers.

Am I running the right command?
Is there another thing i need to do to install this?
is my computer too crappy?
do I need to update anything?

Thanks alot.

---

### Post by izizzle on 2007-05-31
How did you install nexuiz? From the add/remove tool or did you download it from their site?

---

### Post by Grazfather on 2007-06-01
> **izizzle said:**
> How did you install nexuiz? From the add/remove tool or did you download it from their site?

Just untarred the file into a directory... it said just run the script so i guess it's a binary.

---

### Post by Grazfather on 2007-06-01
Bump? :(

---

### Post by dez_cole on 2007-06-01
i think you should uninstall the one you installed and install through add/remove programs..

---

### Post by Grazfather on 2007-06-03
Add/Remove programs? ubuntu has that? i actually use kubuntu so i use the adept manager.. would that show up in the repositories? I'll check it out though, thanks

---

### Post by Grazfather on 2007-06-03
wow, i was trying to hard, i didn't even check the Adept Manager, I'm installing it now I'll let you guys know how it works, but thanks so far.

---

### Post by Grazfather on 2007-06-03
Hate to triple post, got it installed, frotn screen was extremely laggy, i also tried tuxkart and supertux, and they are both too slow to run, So I'm thinking this computer is a piece :)
I did play CS 1.6 on it on windows be fore.. but even that was at most 30fps on low settings.

---

### Post by timzak on 2007-06-03
Grazfather,

Which Geforce4 card do you have?  An MX is very slow but a Ti4xxx is not half bad for most Linux games (Nexuiz is an exception).  Which AMD processor do you have?  Athlon?  Duron?

---

### Post by hikaricore on 2007-06-03
Just fyi ubuntu packages of Nexuiz 2.3 are up on getdeb:

[http://www.getdeb.net/app.php?name=Nexuiz](http://www.getdeb.net/app.php?name=Nexuiz)

GetDeb.net is free and offers recently updated packages for Feisty of popular software.
Please consider donating to them to help with bandwidth/hosting costs if you find their service useful.
If you can't offer them anything else, just shoot them a message via the contact us link and let them know you appreciate thier work.  ^_^

I'm not in any way affiliated with GetDeb.net, just throwing out some suggestions.

---

### Post by Stu284 on 2007-06-04
Hi, 

newbie question.....installed nexuiz using the add/remove programs, but now i am wondering how i install the new version?

thanks

---

### Post by Sockerdrickan on 2007-06-04
Your answer is 1 post above you lol

---

### Post by Stu284 on 2007-06-04
sorry i am total newbie, did not even realise i could just click on the files, then i was getting a dependency error before i realised i had to download all the files  ](*,)

---

### Post by Sockerdrickan on 2007-06-04
lol :popcorn:

---

### Post by pappapump on 2007-06-04
Go get the NEw nexius and just unzip it and click this command,  -> nexuiz-linux-686-glx <-
then you can play it right where you unzipped it.
No install hassles with the new one, and dont forget to get the new map pack, its friggin loaded.

---

### Post by Grazfather on 2007-06-04
Thanks for the GetDeb link, I'll check it out.
it's an Athlon, and i dunno about the graphics card though... don't know where to get that info w/out taking this apart.

---

### Post by timzak on 2007-06-11
Question on the GetDeb link:  there are three files there, nexuiz, nexuiz-data, and nexuiz-music.  Do I download all three?  How do I install?  Do all three just unpack into the same folder?

Earlier I tried downloading from the Nexuiz site and it was a .zip file that I couldn't figure out how to install (maybe that was a Windows-only version?  There was only one download option--I didn't see separate OS installs on the Nexuiz site).

If you must poke fun at my expense, I'm okay with that, as long as you help me get it running.  :p

I'm still not real good with manually installing things in Linux, but at least I got the hang of Add/Remove and Synaptic. ;)

Thanks!

---

### Post by Sockerdrickan on 2007-06-11
The official zip is a zip you unzip and exec the sh file
it's win mac linux zip

the three from getdeb is installed like this: data music nexuiz

---

### Post by timzak on 2007-06-11
Thanks.  I wish this info was included in a readme file or on the Nexuiz website somewhere.  At least I couldn't find it anywhere.  Thanks again, I'll try it out when I get home.  I was trying to execute by double-clicking the .exe file :p  I didn't realize I had to run the sh file.  That's what happens when you install everything by Add/Remove or Synaptic and just click the icon under Applications to execute.

---

### Post by Sockerdrickan on 2007-06-12
A tip, .exe = windows only, files with no ending = linux, .sh executes them with preferences!

---

### Post by timzak on 2007-06-12
> **Tux0r said:**
> A tip, .exe = windows only, files with no ending = linux, .sh executes them with preferences!

Thanks.  Now what's the difference between the glx file and the other one (I think it's sdl?)  There are two sh files.  Not sure which is the correct one to launch.

I'm going to make a new post on a performance problem with Nexuiz.  Take a peak at it if you can.

Thanks.

---

### Post by Sockerdrickan on 2007-06-12
Try SDL, if it works you don't need to try GLX :P

---

### Post by timzak on 2007-06-15
New problem:  :(

When I try to download from the GetDeb page, I get the following error when I click on any of the download links:

> Warning: array_key_exists() [function.array-key-exists]: The second argument should be either an array or an object in /home/www/ta0014/public_html/download.php on line 48

Warning: Cannot modify header information - headers already sent by (output started at /home/www/ta0014/public_html/download.php:48) in /home/www/ta0014/public_html/download.php on line 159

What's the difference between the .zip file and the .deb files?  Should I just use the .zip version?

---

