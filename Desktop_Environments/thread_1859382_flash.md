---
title: "flash"
date: 2011-10-13
forum: Desktop Environments
---

### Post by boblizar on 2011-10-13
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

to find what flash version you have visit here.
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

unfortunately flash is used by many websites and does not come with an apt repo for ubuntu 11.04

nab the tar.gz for "other" linux from in 64 or 32 what ever you run.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

once downloaded

alt + f2

gnome-terminal

run

```

cd $HOME/Downloads
tar -xf install_flash_player*.tar.gz && rm install_flash_player*.tar.gz
mv libflashplayer.so $HOME/.mozilla/plugins
rm $HOME/Downloads/readme.txt
rm -rf $HOME/Downloads/usr

```

and thats it....  restart your browser

---

### Post by beew on 2011-10-13
I think the flash-aid addon for Firefox would install 64-bit flash.

---

### Post by ezramorris on 2011-10-14
The easier way to do this is to open the software centre, search for flash, and install "Adobe Flash plug-in". This will automatically download and install it for you.

---

### Post by holdinbanks on 2012-02-24
> **ezramorris said:**
> The easier way to do this is to open the software centre, search for flash, and install "Adobe Flash plug-in". This will automatically download and install it for you.

I'm a total Newbie and I just got **BT5-GNOME 64** today, I think everyone has the same problem with flash, but today I found the solution. It doesn't involve opening the terminal for commands, the solution for me was very simple, and I hope it works for you too. 
Step by Step here is what I did: **1st: **_g__o to youtube and click a video, it wont play, it will ask you to get the plug-in, but that's not available._** 2nd: Go to add-ons and Download *Flash-Aid***, then** google *Adobe Flash and *****Download *Adobe Flash.tar.gz, ***click on adobe in the download list, nothing happens. **3rd: Disable: *No-Script and Tamper Data. ***[I]

Wait a few seconds and see if you hear the youtube video play. I know it sounds too simple, but KISS, also I downloaded [/I]**FireBug and Fire-Cookies**, I doubt it had anything to do with solving the problem, but you never know.

Hope this works for all of you, if not most of you, let me know if this solved the problem for you guys.
Also there are some videos that wont play, "HTML 5"  i will try and figure out why, and solve that too.

---

