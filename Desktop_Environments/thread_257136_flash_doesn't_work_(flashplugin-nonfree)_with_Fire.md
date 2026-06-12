---
title: "flash doesn't work (flashplugin-nonfree) with Firefox"
date: 2006-09-14
forum: Desktop Environments
---

### Post by avr on 2006-09-14
Dear Ubuntu community,

Since I used Automatix, I'm not able to see websites using Flash (like a f** d**, I asked Automatix to reinstall Flash over what I installed before).
I'm not using a 64-bit:
```
uname -a
Linux xxxx 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686 GNU/Linux
```
I'm on Dapper.

I did the following procedures:
1)
```
apt-get remove --purge flashplugin-nonfree
```
(...just to clean up my install)
reboot;
```
apt-get install flashplugin-nonfree
```
(I answered yes when it asked me to download from the internet)
```
sudo update-flashplugin
```
and then I obtain this message:
```
automatic installation failed due to network problems or upstream changes
```
I don't really understand what happenned (To me, I have no problem with my network), but flash+FF doesn't ever work... :mad: 

2) So I tried
```
apt-get remove --purge flashplugin-nonfree
```
reboot;
```
apt-get install flashplugin-nonfree
```
(This time, I answered "no" about the download)
```
wget http://download.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz
sudo update-flashplugin --local-file $PWD
```
And a new message appeared:
```
plugin changed, not trusted
```
?? I can't understand what it means... :? But it's sure flash+FF doesn't work!

3) My last chance: download from Macromedia's website the installer.tar.gz, tar xvzf (...), ./flashplayer-installer. It asked me:
```
Please ask your administrator to remove the xpti.dat from the components directory of the Mozilla or Netscape browser.
```
It don't know what this file do, but I find several xpti.dat on my computer. I removed all (I did backups ;) ).
I "rebooted" but... no more flash+FF... :cry: 

I'm feeling so alone now... ;) Seriously, I have no idea. So if anyone can help me, thanks in advance.

avr

PS: what the package 'flashplayer-mozilla' provide compared to 'flashplugin-nonfree'?
PPS: Sorry for my english (cf. "my" verb "rebooted", I don't know if it's correct). I try, I try,...

---

### Post by Rmorris84 on 2006-09-14
Have u tried EasyUbuntu, automatix foobared a friends computer, and i went back and used EasyUbuntu and it fixed his flash. Hope this helps.

---

### Post by smelly_sox on 2006-09-14
Hi Rmorris84,
You could go to the [Adobe website]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4") & download the plugin.
Follow the instructions, they're really easy.
During the install you are required to enter the directory to firefox.
With firefox, on Ubuntu 6.06 LTS it is:
*/usr/lib/firefox*
Regards

---

### Post by avr on 2006-09-14
Thanks for help.

--> To smelly_sox:
As written above, I did it. Just it never ask me to enter the dir of FF... Here are the questions:
```
Macromedia Flash Player 7 will be installed in the following directory:

Mozilla installation directory  = /home/my_log/.mozilla

Proceed with the installation? (y/n/q):
```And no other possibility than y/n/q. I typed 'y'.
```
Installation complete.


Perform another installation? (y/n): 
```I taped 'n'. Only what I get are this questions (and "please ask your adm ...."; cf. my first post).
I quit my session, connect again, and always my problem: no flash with FF.

[EDIT] I opened the script flashplayer-installer and, whereas I'm not a bash developper, I understood that I had to run the script with sudo to get the question about the installation directory of FF. I did it, answer /usr/lib/firefox, relaunch my session; but nothing more... [/EDIT]


--> To Rmorris84:
Oh! i forgot this tool... So I installed [easy**K**ubuntu]("http://smarter.free.fr/EasyKubuntu.tar.bz2") (sorry, I didn't specify I have KDE), ran it with "sudo python EasyKubuntu.py" and... It became worse that it never be. :( 

First, it tried to get PLF repositories for Breezy (!!), so It crashed before the end of all the install's. Then I was not able to reload my source.list. I'm not a geek, but It seems it was a conflict between versions of openoffice.org (why????).

After many experiment (mix of new and old source.list, reinstall of openoffice.org-core with -f option (beurk!),...), it's now quite OK for my packages.
[EDIT2](but I'm subject to some changes. E.g. my /usr/bin/firefox was a link to /opt/firefox/firefox which doesn't exist now. I have now /usr/bin/firefox.ubuntu (?). I created a link firefox -> firefox.ubuntu but I don't want use automatic scripts anymore. They make me mad ](*,) )[/EDIT2]

And now, some fonts are ugly (e.g. fonts on FF tabs,...) and I don't know why.


And I still miss flash...
:evil:

---

### Post by gotgenes on 2006-09-15
You should have followed smelly_sox's post completely. The correct answer for "Mozilla installation directory" is "/usr/lib/firefox", as smelly_sox stated.

---

### Post by cviorel on 2006-09-15
This is my solution. I can confirm that it works.
So, here we are:

1. In synaptic package manager, completely remove libflash-mozplugin. Make SURE you use the "completely remove" option, that gets rid of the gstreamer-ugly and couple other packages.
2. Download the latest flash plugin from [www.adobe.com](www.adobe.com) ([http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz))
3. Unzip it to a folder on your desktop.
4. In terminal cd to that dir and sudo ./flashplayer-installer
5. follow the prompts, and make sure the path to your plugins is right (for most Ubuntu Dapper users it's going to be /usr/lib/firefox)

Then see if flash works in a browser - it should work just fine now on all the sites. You won't be able to use flash 9 content (yet), but you should be able to view most things with no problem.
I hope this helps some people.

---

### Post by tomBorgia on 2006-09-15
> **cviorel said:**
> This is my solution. I can confirm that it works.
So, here we are:

1. In synaptic package manager, completely remove libflash-mozplugin. Make SURE you use the "completely remove" option, that gets rid of the gstreamer-ugly and couple other packages.
2. Download the latest flash plugin from [www.adobe.com](www.adobe.com) ([http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz))
3. Unzip it to a folder on your desktop.
4. In terminal cd to that dir and sudo ./flashplayer-installer
5. follow the prompts, and make sure the path to your plugins is right (for most Ubuntu Dapper users it's going to be /usr/lib/firefox)

Then see if flash works in a browser - it should work just fine now on all the sites. You won't be able to use flash 9 content (yet), but you should be able to view most things with no problem.
I hope this helps some people.

If the automated installer doesn't work (it didn't for me...) you can copy the 2 files from the /flashplayer-installer dir manually into your firefox plugin directory... the 2 files you need are flashplayer.xpt and libflashplayer.so and the directory is /usr/lib/firefox/plugins/ or /usr/lib/mozilla/plugins/ :)

---

### Post by hellfried on 2006-09-15
> **tomBorgia said:**
> If the automated installer doesn't work (it didn't for me...) you can copy the 2 files from the /flashplayer-installer dir manually into your firefox plugin directory... the 2 files you need are flashplayer.xpt and libflashplayer.so and the directory is /usr/lib/firefox/plugins/ or /usr/lib/mozilla/plugins/ :)

flash does not work for me in both firefox 1.5 and firefox 2.0b2. i downloaded the flash installer from the the macromedia website and did exactly what the earlier post said. i even checked in the plugin folder of my firefox 2.0b2 folder. both the .xpt and .so files are in there but still no flash!

---

### Post by artisan on 2006-09-15
Well I for one have started to migrate back to Windows. At least I can use Flash player in Windows.

I installed, no I tried to install Flash player using EasyUbuntu. To put it simply it did not work.
It seemed to install. I closed my browser (firefox) and reopened it. No Flashplayer.
EasyUbuntu now loads it gives a screen saying:
“Previously installed components have been detected. Note that EasyUbuntu CANNOT uninstall them; therefore, their checkboxes are disabled (grayed out).”
 EasyUbuntu now has the Flashplayer “greyed out”

As for the suggestion:
You could go to the Adobe website & download the plugin.
Follow the instructions, they're really easy.
During the install you are required to enter the directory to firefox.
With firefox, on Ubuntu 6.06 LTS it is:
/usr/lib/firefox   etc etc

This does not work for me as I get
sudo: ./flashplayer-installer: command not found

And as for this suggestion:
1.In synaptic package manager, completely remove libflash-mozplugin. Make SURE you use the "completely remove" option, that gets rid of the gstreamer-ugly and couple other packages.
2. Download the latest flash plugin from [www.adobe.com](www.adobe.com) ([http://fpdownload.macromedia.com/get...7_linux.tar.gz](http://fpdownload.macromedia.com/get...7_linux.tar.gz))
3. Unzip it to a folder on your desktop.
4. In terminal cd to that dir and sudo ./flashplayer-installer
5. follow the prompts, and make sure the path to your plugins is right (for most Ubuntu Dapper users it's going to be /usr/lib/firefox)

libflash-mozplugin does not exist in  synaptic package manager.

I am getting tired of Ubuntu. Not the people who run the forums. You guys do a great job. Unfortunately Ubuntu doesn't. 
It is still more buggy than Windows and you have to be a programmer to do the slightest thing. Like add Flash.
I am sad to say, after a month of trying Ubuntu, I have put my Windows hard drive back in.
If any body has any suggestions about the Flash thing. I am willing to listen.

---

### Post by hellfried on 2006-09-15
i just read about the recent security vulnerabilities the flashplayer and the advice by macromedia to upgrade to version 7.0.68.0 which is what i got when i downloaded the package from their website. perhaps there is something wrong with this version that makes it impossible to run in ubuntu.

the reason for this 'conspiracy theory' is because flash was running very well on ubuntu day before yesterday for me. i accidentally wiped out my ubuntu partition yesterday and i had to do a clean reinstall. i spent the whole day installing all my favourite multimedia programs and compiz. everything else is working except for flash.

is there any possibility of getting hold of the previous version and installing that? the funny thing is that even the flashplugin-nonfree package in the repositories does not work.

---

### Post by artinla on 2006-09-15
Flash 9.0 sites are an issue right now.  It is not an ubuntu thing, it is a problem for the whole linux community.  Adobe needs to get off their a$$es and finish the linux version.

Until then, do what I did and install Firefox for Windows with wine and then install the Flash plugin for windows as well.  There is a howto somewhere on this forum.  It works great for me, but I only use it for youtube, metacafe etc. that use flash 9.

When Vista comes out at the end of the year, trust me.. many will come running to Linux.  If you think Ubuntu is frustrating, try Vista for a week... it is horrible.

---

### Post by hellfried on 2006-09-15
> **artinla said:**
> Flash 9.0 sites are an issue right now.  It is not an ubuntu thing, it is a problem for the whole linux community.  Adobe needs to get off their a$$es and finish the linux version.

Until then, do what I did and install Firefox for Windows with wine and then install the Flash plugin for windows as well.  There is a howto somewhere on this forum.  It works great for me, but I only use it for youtube, metacafe etc. that use flash 9.

When Vista comes out at the end of the year, trust me.. many will come running to Linux.  If you think Ubuntu is frustrating, try Vista for a week... it is horrible.

i am aware of the flash 9 issues but right now i can't get any flash going. not even youtube which used to work fine for me.

---

### Post by spur on 2006-09-16
They both dont go in plugins. If you read the directions from the download site you will see one goes in plugins and one goes in componants. I fixed this on my system this am by copying them in to the firefox plugins and componnents directory
/usr/lib/firefox/components  gets a copy of flashplayer.xpt
/usr/lib/firefox/plugins   gets a copy of libflashplayer.so
if you put both in plugins it will not work.

---

### Post by tim-e on 2006-09-16
> **artisan said:**
> Well I for one have started to migrate back to Windows. At least I can use Flash player in Windows.That's like selling your car because the alternator's on the blink.

---

### Post by Zieher on 2006-09-16
I am having the same problem here.

Selling the car due to a faulty alternator? I've talked to people that dumped their cars for less.

I am annoyed with computers, Windows and Linux have issues, and all I want to do is to get my programs to work. Flash might be an alternator to some (to stay in the "car"-theme, but to others it might be the engine.
With Linux there is at least a community, that has access to the code and can thus at least tell you noob user (me) what you are doing wrong.

I'm frustrated, but still too scared of Windows' strange user and service management and Redmond-back-doors (I can't close) to shoot the duck.

I might just as well go to bed again.

---

### Post by hellfried on 2006-09-16
> **spur said:**
> They both dont go in plugins. If you read the directions from the download site you will see one goes in plugins and one goes in componants. I fixed this on my system this am by copying them in to the firefox plugins and componnents directory
/usr/lib/firefox/components  gets a copy of flashplayer.xpt
/usr/lib/firefox/plugins   gets a copy of libflashplayer.so
if you put both in plugins it will not work.

the strangest thing happened just now but this story has a happy ending. i have a 'firefox' folder and a 'firefox-old' folder in my /usr/lib directory. i guess the 'old' folder was created automatically when i installed firefox 2.0b2. i shifted flashplayer.xpt to the 'components' folder but still could not get flash to run.
i deleted the firefox folder which contains ff2.0 and renamed the old folder to 'firefox'. when i clicked on the icon in my top panel, ff opens up and i can confirm that it is version 1.5.0.5 which was the default version that came with installing ubuntu. still no flash.
i went into synaptic and completely removed firefox. i also made sure that flashplugin-nonfree was not installed. i then reinstalled firefox only and voila, i now have flash! i really do not know what i did but there you go! =D> 
anyways some of you might want to try reinstalling firefox to see what happens but please not blame me if things go wrong. :biggrin:

---

### Post by BadDolphin on 2006-09-16
$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

Durn :(

The 64-bit processor was a huge and serious mistake I sure won't repeat.

---

### Post by spur on 2006-09-16
This is not just linux though as windows 64bit is without falsh as well. If you have 64 bit processor you can run 32 bit os on it. My 32bit installation of kubuntu runs faster than xp did and faster than suse as well.
If you want to run 64 bit I found that any linux distro will be better for compatability then windows 64bit.
Just something to throw around in your head. I expect flash to be available for 64bit soon but add to the pressure by requesting it on their site. I did but I forget how.

---

### Post by jtbl on 2006-09-16
There is a bug in the package in the Ubuntu repos. This bug was caused by Adobe releasing version 7.0.68 a few days ago. This bug did get fixed in the Flash Plugin option in Automatix 6.5-3.

---

### Post by hellfried on 2006-09-16
> **jtbl said:**
> There is a bug in the package in the Ubuntu repos. This bug was caused by Adobe releasing version 7.0.68 a few days ago. This bug did get fixed in the Flash Plugin option in Automatix 6.5-3.

thank you for confirming my suspicion.

---

### Post by avr on 2006-09-20
Dear all,

It's now OK for me. I noticed that I had /usr/lib/firefox, /usr/lib/mozilla/firefox, /usr/lib/mozilla-firefox,...
So I completly removed (with --purge) firefox and all mozilla components. As I still had ~/.mozilla/firefox/,... directories (why? I used --purge :confused: ), I removed them (I did backups for my bookmarks and my extensions). I had to removed also thunderbird (it belong to Moz' suite) but I saved ~/.mozilla-thunderbird/xxx.defaults/Mail/ .
[Edit]I also searched all occurrences of FF in /usr/ and removed approxymately all I estimated important (e.g. not icons or doc)[/Edit]

Then I (re)installed FF and Thunderbird, cp my bookmoarks.html.bak to my new ~/.mozilla/firefox/xxx.defaults and my Mail.bak/ to the new ~/.mozilla-thunderbird/xxx.defaults/.

I downloaded the Macromedia'installer (.tar.gz), untar it. But I didn't use the install script (you *must* use sudo --or be root-- but they don't explain it on their page) because now I'm traumatized with automatic install scripts I don't understand (cf. my previous posts and my adventures with Automatix and EasyKubuntu).

So I only copy (with sudo) flashplayer.xpt and libflashplayer.so to /usr/lib/mozilla/plugins/. Then, just for symmetry with other plugins (like mplayer), I did 'sudo ln -s ../../mozilla/plugins/[lib]flashplayer.[xpt|so]' in /usr/lib/firefox/plugins.
And now, all is fine. I can see google video, youtube, some blogs,... sites (not  metacafe but I don't care).

Ouf. :cool: 

Just 2 questions:
1) Why 2 directories /usr/lib/firefox/(plugins/) and /usr/lib/mozilla/(plugins/)? Isn't it redundant?
2) Why, with 'apt-get remove --purge' command (or with Synaptic->Completly remove), are "home" directories (like ~/.firefox, ~/.mozilla,...) still present?

---

