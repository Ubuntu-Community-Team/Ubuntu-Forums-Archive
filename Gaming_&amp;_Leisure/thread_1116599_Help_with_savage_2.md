---
title: "Help with savage 2"
date: 2009-04-05
forum: Gaming &amp; Leisure
---

### Post by Legenderay on 2009-04-05
I'm new to linux and looking for a few games and people have been telling me how good savage 2 is. So I downloaded it, but when I try to open it it says : There is no application installed for this file type.
Can anyone tell me what application I need to open it?

---

### Post by vandorjw on 2009-04-05
did you download a something.bin file?
if so try this.

1. open the terminal and go to the directory where you downloaded the file to. For example, if you downloaded it to the desktop you type.

```

cd ~/Desktop

```

ps: the terminal is found in Applications --> Accessories --> terminal

2. When you type LS (in lower capitals) it should display the names of the files in that directory. (so something .bin should be printed out on your screen)
```

ls

```

3. If you did not see something.bin in step 2, this will not work.
but if you did, type this
```

chmod a+x something.bin

```

4. This makes the .bin file executable. Now you can run it by typing.
```

./something.bin

```

(I pretty sure the game will install when you follow these steps)

Cheers - CC7

---

### Post by Legenderay on 2009-04-05
Whoa, thanks so much it worked.

---

### Post by Legenderay on 2009-04-05
Sorry guys but i've got another problem: I have the whole zip file of savage 2 and it is installed but I don't know how to run it.

Here is the terminal bit if it helps:

me@ubuntu:~$ cd ~/Savage2
me@ubuntu:~/Savage2$ ls
change_log.txt       game         modelviewer     savage2_update.bin
dedicated_server.sh  libk2.so     modelviewer.sh  uninstall-Savage2.sh
editor               libs         s2icon.png      updater_x11.so
editor.sh            license.txt  savage2.bin     vid_gl2.so

---

### Post by Naiki Muliaina on 2009-04-05
Is it not hiding in your games menu? Pretty sure when savage 2 installs it appears in the games menu.

---

### Post by Legenderay on 2009-04-05
Ah yes it does but the bad thing is that when I click it the whole screen goes black and logs me off for some reason.

---

### Post by Legenderay on 2009-04-05
Im getting annoyed (*,) is this game really worth all the hassle?

---

### Post by Naiki Muliaina on 2009-04-05
Yes it is :)

Could you tell us whats in your machine aswell by the way, graphics card etc. Also if you have installed the most recent graphics drivers (System -> Administration -> Hardware Drivers).

---

### Post by Legenderay on 2009-04-05
Okay wait a few minutes i'm going to find out.

---

### Post by Legenderay on 2009-04-05
Intel(R) 82945G Express Chipset Controller 0 (Microsoft Corporation - WDDM) - if that helps.

And when I went on to hardware drivers (Or whatever) it says : No proprietary drivers are in use on this system.

Oh btw I have a duel boot between Windows vista and Ubuntu.

---

### Post by Naiki Muliaina on 2009-04-05
Does it list any drivers for you to use?

---

### Post by Legenderay on 2009-04-05
No, there is just nothing there.

---

### Post by Legenderay on 2009-04-05
Im going to log off, ill check this thread tomorrow

---

### Post by Naiki Muliaina on 2009-04-05
Ok, this is going to go beyond what i know technically (sorry, i only have a basic technical knowledge of Linux). A quick forum search turned up the following threads :

[http://ubuntuforums.org/showthread.php?t=1100761&highlight=Intel(R)+82945G](http://ubuntuforums.org/showthread.php?t=1100761&highlight=Intel(R)+82945G)
[http://ubuntuforums.org/showthread.php?t=1091148&highlight=Intel(R)+82945G](http://ubuntuforums.org/showthread.php?t=1091148&highlight=Intel(R)+82945G)

If neither are of any help, i recomend asking in one of the main support forums for help with your graphics. Intel are known for having rubbish drivers for Linux.

When you do, give as much information as possible for best chance of a reply. Include in your post the output from the terminal command : *glxinfo | grep rendering*. Also have a look at your Xorg.conf file and copy paste the contents into your post. Find it by entering the following into terminal. [I]sudo gedit /etc/X11/xorg.conf
[/I]

---

### Post by meborc on 2009-04-05
are you sure your intel graphics card is powerful enough for this game... read this - [http://ubuntuforums.org/showthread.php?t=1116311](http://ubuntuforums.org/showthread.php?t=1116311)

savage2 is my favourite game right now, and my nvidia 8600m gt has to work overtime to get it running :)

---

### Post by Perfect Storm on 2009-04-05
nevermind

---

### Post by wolfyking2 on 2009-04-05
yea, intel cards don't cut it.  Some of them have opengl 2.0, though.  My intel card sure can't play savage 2 >.<

---

### Post by Vadi on 2009-04-05
Intel cards won't work, sorry. The game is rather effects-intensive:

[http://www.savage2.com/en/media.php?t=ss](http://www.savage2.com/en/media.php?t=ss)

---

### Post by Legenderay on 2009-04-06
Oh, okay:frown:I'm sure ill find some other games to play.

---

### Post by binbash on 2009-04-06
that game does not work on intel cards

---

