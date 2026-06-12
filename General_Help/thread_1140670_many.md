---
title: "many"
date: 2009-04-27
forum: General Help
---

### Post by Part Of What on 2009-04-27
hi  -ive installed nexuis but its slow in the menus -ive ran janitor and after reboot the panels changed. how can you change that back? -the sound that coming out of the speakers is low, how can that be fixed? -when email link pressed the evolution start to run, though thunderbird configured on mine -the pidgin when running has a menu instead the interface when pressed -when windows radio files are being try to run the system dont find it a plugin though it did in the past -how can you be able to make shot system passwords? -how to kill programs with linux?..  sy

---

### Post by codeseer on 2009-04-27
> **Part Of What said:**
> hi  -ive installed nexuis but its slow in the menus -ive ran janitor and after reboot the panels changed. how can you change that back? -**the sound that coming out of the speakers is low, how can that be fixed? -when email link pressed the evolution start to run, though thunderbird configured on mine** -the pidgin when running has a menu instead the interface when pressed -**when windows radio files are being try to run the system dont find it a plugin though it did in the past** -how can you be able to make shot system passwords? -**how to kill programs with linux?..**  sy

I'll address a few that I understand clearly.

The mail issue; in Firefox, click the Edit menu and click Preferences, then go to the Applications tab and find the mailto: entry and change it to Thunderbird.

Sound; double-click the speaker icon in the upper right corner of your screen and adjust the volumes.

For Windows media playback, you need to install the ubuntu-restricted-extras package.

Killing programs; in the terminal, see the 'killall --help' and 'ps --help' commands. However, it may be easiest for you to enable the 'Force Quit' icon on the toolbar by right clicking the bar at the top and clicking 'Add to panel'. This will allow you to simply click it and then click on the application to kill.

Edit:

I don't know much about pidgin. I don't know what nexuis is. The janitor issue sounds like a bug; I'll see if I can find something on it.

Could you restate the part about passwords, please? Do you mean 'short' passwords?

---

### Post by Part Of What on 2009-04-27
> **codeseer said:**
> I'll address a few that I understand clearly.

The mail issue; in Firefox, click the Edit menu and click Preferences, then go to the Applications tab and find the mailto: entry and change it to Thunderbird.

Sound; double-click the speaker icon in the upper right corner of your screen and adjust the volumes.

For Windows media playback, you need to install the ubuntu-restricted-extras package.

Killing programs; in the terminal, see the 'killall --help' and 'ps --help' commands. However, it may be easiest for you to enable the 'Force Quit' icon on the toolbar by right clicking the bar at the top and clicking 'Add to panel'. This will allow you to simply click it and then click on the application to kill.

Edit:

I don't know much about pidgin. I don't know what nexuis is. The janitor issue sounds like a bug; I'll see if I can find something on it.

Could you restate the part about passwords, please? Do you mean 'short' passwords?

 how can it be changed to thunderbird? where is the file located?  the sound got higher somewhat, still low  how to install the restrikted package?  dont know how to place buttons to default  question was on how to make short password, the system asked for long  see you

---

### Post by codeseer on 2009-04-27
> **Part Of What said:**
> how can it be changed to thunderbird? where is the file located?  the sound got higher somewhat, still low  how to install the restrikted package?  dont know how to place buttons to default  question was on how to make short password, the system asked for long  see you

[LIST=1]
[*]Try typing 'which thunderbird' in the terminal to find thunderbird.
[*]Sound: try using 'alsamixer' in the terminal.
[*]Restricted Extras: Click System, Administration, Synaptic Package Manager. When it comes up, click the 'Search' button and type 'ubuntu-restricted-extras', then hit Enter.
[*]To place the buttons on the panel, right click a blank area in the panel and click Add to Panel, then find the one you want to add (for instance Force Quit) and just drag it from the window to the panel and drop it with the mouse.
[*]The password to your system is what a lot of your security hinges on, you probably want it to be long so the system stays secure. I know the password can be practically disabled, but I'm not sure if you can make it any shorter than the requirements say.
[/LIST]

---

### Post by Part Of What on 2009-04-28
> **codeseer said:**
> 
[LIST=1]
[*]Try typing 'which thunderbird' in the terminal to find thunderbird.
[*]Sound: try using 'alsamixer' in the terminal.
[*]Restricted Extras: Click System, Administration, Synaptic Package Manager. When it comes up, click the 'Search' button and type 'ubuntu-restricted-extras', then hit Enter.
[*]To place the buttons on the panel, right click a blank area in the panel and click Add to Panel, then find the one you want to add (for instance Force Quit) and just drag it from the window to the panel and drop it with the mouse.
[*]The password to your system is what a lot of your security hinges on, you probably want it to be long so the system stays secure. I know the password can be practically disabled, but I'm not sure if you can make it any shorter than the requirements say.
[/LIST]


 got that

---

### Post by Part Of What on 2009-04-28
why the windows panel not draging to the top? can you tell of progrsm to wipe files with an interface? who can help with the mentioned game? when ive hitet join{game} it quit how can i remove the ubuntu logo from the applications button? how does the disk can be partitioned if encrypted?

---

### Post by Part Of What on 2009-04-28
how can i change the letters of the language bar? how to fix a problem which after a short time a stream of radio would stop? how does tor is installed?

---

### Post by codeseer on 2009-04-28
> **Part Of What said:**
> how can i change the letters of the language bar? how to fix a problem which after a short time a stream of radio would stop? **how does tor is installed?**

You'll need to add the tor repositories from the official site to your sources list. This is because there was a disagreement with updating tor for Ubuntu repositories; therefore, in order to stay up to date and, as a result, secure you will need to use the ones from the tor website.

You can do this by clicking System->Administration->Software Sources and click on the Third Party tab. You will need to add the source as follows:

```
deb http://mirror.noreply.org/pub/tor intrepid main
```

Then run the following in the command line, throwing sudo in front of it where needed:

```

gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg --fingerprint 94C09C7F

gpg --export 94C09C7F | sudo apt-key add -

apt-get update
apt-get install tor

```

Source: [https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian")

---

### Post by codeseer on 2009-04-28
> **Part Of What said:**
> **why the windows panel not draging to the top? can you tell of progrsm to wipe files with an interface?** who can help with the mentioned game? when ive hitet join{game} it quit how can i remove the ubuntu logo from the applications button? **how does the disk can be partitioned if encrypted?**

As far as the panel goes, try right-clicking it and making sure that it isn't locked into position. If you need another panel, click the 'New Panel' menu selection from the right-click menu; this may be easier than moving panels.

If you're using Ext3 or some other journaled file system it is going to be very difficult to fully wipe files from the drive. I do not know of any interfaces for this either. Your install comes with shred, which can be looked at further (including the journaled file system warning) by typing 'shred --help'. Alternatively, you can get 'secure-delete' and 'wipe' from the repositories, but I don't think they are really able to handle journaled file systems well either. I have not compared or used all of these tools yet, but it's on my todo list. The recommended alternative to wiping files on Linux with journaled file systems is to encrypt your files. I recommend using TrueCrypt, which can be found here: [http://www.truecrypt.org/]("http://www.truecrypt.org/")

If you have an encrypted disk that you want to partition, then you will need to probably first unencrypt it, then partition it and then reencrypt the partitions separately depending on how you have it set up. If you have entire disk encryption, like may be provided by the hardware itself, then you can probably just partition like you would normally; as the drive should be unencrypted when in operation.

---

### Post by codeseer on 2009-04-28
For those new to the post and to serve as a reference, these are the questions that have not yet been answered:

[LIST=1]
[*]hi -ive installed nexuis but its slow in the menus. who can help with the mentioned game? when ive hitet join{game}
[*]ive ran janitor and after reboot the panels changed. how can you change that back?
[*]the pidgin when running has a menu instead the interface when pressed.
[*]how can i remove the ubuntu logo from the applications button?
[*]how can i change the letters of the language bar?
[*]how to fix a problem which after a short time a stream of radio would stop?
[/LIST]

---

### Post by codeseer on 2009-04-28
Number 4, the logo on applications menu. I have been looking into that for you and there used to be a way to do it using gconf-editor. However, when I try on the modern Ubuntu installs, it doesn't work. You'd think that icon is somewhere on the drive though and could be replaced at least.

Perhaps someone will come by that knows.

---

### Post by Part Of What on 2009-04-29
suddenly ask.com got in the list of search websites  also, can you tell how to install a graphic card driver that will make better performance?  when screen is locked the english isnt chosen for typing a password most of the time  can you tell about a way to alternate the first login screen with the graphic objects with 3d and the shininess effects?

---

### Post by cariboo on 2009-04-29
@Part Of What

I know English is not your native language, but could you at least put a **?** at the end of each question, and use the enter key to seperate each question. I find I have to read your questions at least three time to understand what you are asking.

If you make your questions easier to read you may get more people trying to answer them.

---

### Post by Part Of What on 2009-04-29
how can you make subject of thunderbird disappear and also at when you get little windows on the side of the screen?

---

### Post by codeseer on 2009-04-29
Up to date questions:

[LIST=1]
[*]hi -ive installed nexuis but its slow in the menus. who can help with the mentioned game? when ive hitet join{game}
[*]ive ran janitor and after reboot the panels changed. how can you change that back?
[*]the pidgin when running has a menu instead the interface when pressed.
[*]how can i remove the ubuntu logo from the applications button?
[*]how can i change the letters of the language bar?
[*]how to fix a problem which after a short time a stream of radio would stop?
[*]how can you make subject of thunderbird disappear
[*]...and also at when you get little windows on the side of the screen?
[*]can you tell how to install a graphic card driver that will make better performance?
[*]when screen is locked the english isnt chosen for typing a password most of the time can you tell about a way to alternate the first login screen with the graphic objects with 3d and the shininess effects?
[/LIST]

---

### Post by codeseer on 2009-04-29
In response to #9, type the following in a terminal window and post the output:

```
lspci | grep VGA
```

```
lsb_release -a
```

```
uname -a
```

---

### Post by Part Of What on 2009-04-30
there is text to speech like realspeak to linux?

---

### Post by codeseer on 2009-04-30
> **Part Of What said:**
> there is text to speech like realspeak to linux?

[http://espeak.sourceforge.net/download.html](http://espeak.sourceforge.net/download.html)
[http://espeak.sourceforge.net/mbrola.html](http://espeak.sourceforge.net/mbrola.html)

```
espeak -v mb-en1 -f textfile | mbrola -e /usr/share/mbrola/en1 - test.wav
```

---

### Post by Part Of What on 2009-04-30
can you tell about rss programs? does some allow to view many rss or feeds in one page?

---

### Post by codeseer on 2009-04-30
> **Part Of What said:**
> can you tell about rss programs? does some allow to view many rss or feeds in one page?

I've tried a lot of them out myself. I personally like RSSOwl. In it, you can add all your feeds into a folder structure. Then all you have to do is right click on a folder and click 'aggregate news' and it will show all the feeds on one screen.

---

### Post by Part Of What on 2009-05-01
not all the time when typing a beginning of text to the dress bar it give suggestions of things in the history with firefox, if restarted it does  how can you change the letter indicating a language at the upper panel?  ill look at your replies later

---

### Post by Part Of What on 2009-05-01
what would you suggest if keepassx says file is damaged?  what if the system slow?

---

### Post by codeseer on 2009-05-01
> **Part Of What said:**
> what would you suggest if keepassx says file is damaged?  what if the system slow?

I've never had keepassx tell me that. But, it's probably right. Did you have a backup? I add my keepassx file to my rsync bash script as a daily backup.

---

### Post by codeseer on 2009-05-01
> **Part Of What said:**
> what if the system slow?

Slow in what way? Are you running Intrepid or Jaunty?

---

### Post by Part Of What on 2009-05-02
just half of the time the page down button works in firefox when it does half of time scrolling is very slow  and swf in full screen stuck every sec

---

### Post by codeseer on 2009-05-03
> **Part Of What said:**
> just half of the time the page down button works in firefox when it does half of time scrolling is very slow  and swf in full screen stuck every sec

Are you on jaunty or intrepid?

---

### Post by Part Of What on 2009-05-10
is this thing works with linnux? [http://www.fxsound.com/dfxadapter/index.php?vendor=0&subvendor=0&plus=0&refer=0](http://www.fxsound.com/dfxadapter/index.php?vendor=0&subvendor=0&plus=0&refer=0)  when there is a wait curser it have non smooth appearance, wai??

---

### Post by Part Of What on 2009-05-11
hhi  how can you remove icons them entirely? like in menus

---

### Post by Part Of What on 2009-05-12
do you know why this one appears fora couple of times already?

---

### Post by Part Of What on 2009-05-17
> **Part Of What said:**
> do you know why this one appears fora couple of times already?

 what you do when such a thing comes again  and again and again and again?

---

### Post by Part Of What on 2009-05-20
hi  how can you change what behind tto a defferent color??  see you

---

### Post by Part Of What on 2009-05-20
hhow can you switch panel positions??

---

### Post by Part Of What on 2009-05-26
how can uoo make letters be blue?

---

### Post by Part Of What on 2009-05-26
how can u change users namesss??/

---

