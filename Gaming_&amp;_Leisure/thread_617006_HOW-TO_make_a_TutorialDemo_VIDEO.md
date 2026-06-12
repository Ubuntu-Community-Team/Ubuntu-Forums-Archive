---
title: "HOW-TO make a Tutorial/Demo VIDEO"
date: 2007-11-18
forum: Gaming &amp; Leisure
---

### Post by jorgerosa on 2007-11-18
Ok, sometimes is really usefful to have a Tutorial or Demo video for a program or game and post it in youtube (for example).
The right way is really easy, the right and powerfull tools for Linux/Ubuntu are here, all in open-source glory, but took me lots of time to find out what works better, was more complicated since i was used to windows software names, so here goes: (Im trying to get it as simple as it can be, all with GUIs, etc.)
[COLOR=Blue][COLOR=Black]--------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-----------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----------------------------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-----------------------------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]---------------------------------------------------------------------------------------------------------------[/COLOR][B]

Recording all desktop action[/B][/COLOR] (Can record compiz-fusion, effects, movies, audio, mouse, etc, etc.)

* 1 - RECORDING*
**Install application: (Type in terminal) **sudo apt-get install gtk-recordmydesktop
**Running:** go to menu: "Applications" ---> "Sound & Video" ---> "gtk-recordMyDesktop"  *(You can read more about it, here: [LINK]("http://recordmydesktop.sourceforge.net/about.php") )*
**Stop Recording: **Click in the small grey square icon (next to time and date bar)
**Movies are saved at:** /home/[COLOR=Blue]yourname[/COLOR]/out.ogg

*2 - CONVERTING TO OTHER VIDEO FORMATS*
**Convert OGG video to AVI format: **[WinFF for GTK]("http://winff.org/html_new/")  (ffmpeg Gnome based GUI)  **OR  **Check brennydoogles, next posts!

[I]3 - EDITING THE SAVED VIDEOS
[/I]**Install application: (Type in terminal) **sudo apt-get install kino
**Running:** go to menu: "Applications" ---> "Sound & Video" ---> "Kino"
[Added in Jan 2010] OR **[COLOR=YellowGreen]OpenShot[/COLOR]** - New open source video editor here: [http://www.openshotvideo.com/](http://www.openshotvideo.com/) (I haven´t tried it yet)


*4 - SHARE IT* 
**Final Video Example:** brennydoogles turotial video about "AIM In Virtualbox" [here]("http://www.youtube.com/watch?v=G1ESxHTkvhA")
**My Videos:** [here]("http://www.youtube.com/user/jorgeerosa")


[COLOR=Blue][COLOR=Black]-----------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-----------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----------------------------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]---[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]------------------------------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]---------------------------------------------------------------------------------------------------------------[/COLOR][/COLOR]
OTHER IDEAS, FROM POSTS:

[COLOR=Red]**retro89:**[/COLOR] "I recommend Open Shot Video editor [http://www.openshotvideo.com/](http://www.openshotvideo.com/). It imports and exports many different file types. First you will need to install the dependencies which are on the website then install Open Shot.The files are .deb files which makes installation a breeze. "


[COLOR=Blue][COLOR=Black]-----------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]-----------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]----------------------------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]---[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]------------------------------------[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]---------------------------------------------------------------------------------------------------------------[/COLOR][/COLOR]
That's all, hope this helps, so lets make some tutorial videos, and share... or... Game video demos! ;)
Tested under Gutsy Gibbon - Ubuntu 7.10

---

### Post by brennydoogles on 2007-11-18
> **jorgerosa said:**
> Ok, sometimes is really usefful to have a Tutorial or Demo video for a program or game and post it in youtube (for example).
The right way is really easy, the right and powerfull tools for Linux/Ubuntu are here, all in open-source glory, but took me lots of time to find what works better, was more complicated since i was used to windows software names, so here goes:
[COLOR=Blue][B]
Recording all desktop action[/B][/COLOR] (compiz, movies, and mouse included, etc. If you want to):

INSTALL
**Application: **sudo apt-get install recordmydesktop
**GUI: **sudo apt-get install gtk-recordmydesktop
SAVED VIDEOS
**Movies are saved in:** /home/[COLOR=Blue]yourname[/COLOR]/out.ogg
EDIT VIDEOS
**Application with GUI: **sudo apt-get install kino
SAHRE IT
**Site: **[http://www.youtube.com](http://www.youtube.com)

That's all, so lets make some tutorial videos, and share 
Or... Game video demos, eheh ;)

```
sudo apt-get install gtk-recordmydesktop
```
will install both the program and GUI, so the first command is redundant, and by using the attached script you can automatically convert your videos to avi format (which is able to be uploaded to youtube... while the ogg cannot), which will then be moved to a folder called ~/screencasts. Hope this helps!!

---

### Post by jorgerosa on 2007-11-18
First post edited. Big thanks to [B]brennydoogles ;)
[/B]

---

### Post by brennydoogles on 2007-11-18
> **jorgerosa said:**
> 
**Run it:** go to menu: "Applications" ---> "Sound & Video" ---> "gtk-recordMyDesktop"
**Stop Recording: **Click in the small grey square icon (next to time and date bar)


Also if you want, you can run the following command in Terminal ```
 gtk-recordMyDesktop && ogg2avi.sh && exit

```
(assuming that your ogg2avi.sh is in either your home folder, /usr/bin/ , or anywhere else in your $PATH) which will launch the GUI version of recordmydesktop, followed immediately by my script in the same terminal window (you have to click quit on the recordmydesktop window before it will launch), and then the window will close when the conversion is complete.



> **jorgerosa said:**
> First post edited. Big thanks to [B]brennydoogles ;)
[/B]

Thanks!! I created [this video]("http://www.youtube.com/watch?v=G1ESxHTkvhA") using the above method. I love it!!

---

### Post by ashmew2 on 2008-01-29
Thanks for the wonderful HOWTO , But i have been having this problem regarding my sound card. whenever i run it , it says :

Recording is finished.
recordMyDesktop has exited with status: 768
Description: Could not open/configure sound card.

Thanks.

---

### Post by jorgerosa on 2008-02-02
ashmew2, i tryed several times here, but that error (audio related) never happened with me (even when i tried to simulate it)... Can anyone give an hand here? Thx.

---

### Post by AlexFoster on 2008-04-10
I've just had the same error message. The most annoying bit is that it recorded sound and video fine the first time round. I then tried to record something else without changing any settings and have received the same error since.

---

### Post by SendDerek on 2008-06-07
Just add the --no-sound option in the advanced tab if you don't need sound.

---

### Post by manolomanolo on 2010-01-01
I get this error:

```
"record mydesktop has exited with status: 768"
```

and I would always be able to record sound. Any suggestion? Thanks.

---

### Post by jorgerosa on 2010-01-01
Because [SIZE=3]**sound issues**[/SIZE], I´ve found this:
[http://recordmydesktop.sourceforge.net/faq.php#I_have_no_sound!]("http://recordmydesktop.sourceforge.net/faq.php#I_have_no_sound%21")
and found these results in google:
[http://www.google.pt/q=recordmydesktop+sound+problem]("http://www.google.pt/#hl=en-UK&q=recordmydesktop+sound+problem&meta=&aq=0&oq=recordMyDesktop+sound&fp=1&cad=b")


[SIZE=3]**WinFF**[/SIZE], its not in author page anymore, now it has its own .org website:
[http://winff.org/html_new/](http://winff.org/html_new/)


There are also [SIZE=3]**2 more frontends**[/SIZE] for recordMyDesktop available in its project homepage:
[http://recordmydesktop.sourceforge.net/about.php](http://recordmydesktop.sourceforge.net/about.php)

---

### Post by retro89 on 2010-01-01
I recommend Open Shot Video editor [http://www.openshotvideo.com/](http://www.openshotvideo.com/). It imports and exports many different file types. First you will need to install the dependencies which are on the website then install Open Shot.The files are .deb files which makes installation a breeze.

---

### Post by jorgerosa on 2010-01-01
> **retro89 said:**
> I recommend Open Shot Video editor [http://www.openshotvideo.com/](http://www.openshotvideo.com/). It imports and exports many different file types. First you will need to install the dependencies which are on the website then install Open Shot.The files are .deb files which makes installation a breeze. Thanks. I dont know about that one. Just added in main Thread.

---

