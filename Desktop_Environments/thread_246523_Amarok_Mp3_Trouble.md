---
title: "Amarok Mp3 Trouble"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Techman010 on 2006-08-29
I have been working of this for a while but can't seem to get it figured it out...

I just downloaded and installed amarok 1.4.2 using these instructions:
[http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/](http://www.imbrandon.com/2006/08/23/get-it-hot-amarok-142-released/)
However I can't seem to get mp3's working (they work fine in other programs, xmms, rhythmbox).

When I try to play them it says that they are not installed.  I click install, but then nothing happens and it gives me this message in the terminal:

/usr/lib/amarok/install-mp3: line 23: kdesu: command not found
/usr/lib/amarok/install-mp3: line 6: kdialog: command not found

I am using Ubuntu 6.06. Any suggestions? Thanks in advanced.

---

### Post by gunksta on 2006-08-30
I don't have 1.4.2 installed, I just use the default Dapper stuff, but I had a problem where I had to delete my .xine folder in my home directory. First, quit Amarok. Delete ~/.xine and restart Amarok to see if this helps.

--andy

---

### Post by Techman010 on 2006-08-30
Thanks for the reply gunksta, but I still get the same message.
Any other suggestions?

Edit: I normally also keep to the default stuff, but mp3's weren't working in that version of Amarak either (that's why I upgraded).

---

### Post by gunksta on 2006-08-31
So much for my shot in the dark. Linux being the silly thing that it is, mp3 playback in Rhythmbox does not imply mp3 playback in Amarok! How about that?!?!?

Rhythmbox, and most of the GNOME music apps are using gstreamer for mp3 playback. Amarok uses xine or arts (yuck) for playback. But, most video players continue to use Xine if you want them to not suck. So here goes. First, let's isolate the problem.

Do you have xine-ui, kaffeine OR totem-xine (not totem-gstreamer)? If you do, try making these programs play an mp3 file. If all is right with the world, this should fail to work. ](*,) 

If xine-ui plays the mp3.....I will be very confused. Otherwise, make sure you have xine-extracodecs installed and the w32codecs package. I can send you a working w32codecs package if you don't have one....as long as you are on x86.

--andy

---

### Post by orb9220 on 2006-08-31
I got 1.4.2 by doing thiws in terminal

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

sudo -s

apt-key add kubuntu-packages-jriddell-key.gpg

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

---

### Post by ravpaul on 2006-08-31
Hi I am also having a problem with my amarok (version 1.3.9) not playing MP3 files. However it does not give an error when trying to play mp3 files, it just starts to go through them. For example if I have a playlist with 3 songs and double-click the 1st song the title appears but no music plays and the focus shifts to the next song again no music plays and the focus shifts to the 3rd song and so forth. It just stays on each song for approx one second.

When opening xine have a message on its top toolbar saying:

xine: there is no mrl

When trying to play a mp3 in xine gives the following error:

the stream 'location of file.mp3' use an unsupported codec:

audio codec:mpeg 1 layer 3 CBR (0x0)

Start playback anyway.

When selecting yes. Nothing happens.

Please help.. my friend told me amarok is the best media player and that I can also synch my ipod using it. Closest thing to Winamp in Linux!!!

---

### Post by mitch.c on 2006-08-31
Try:
```
sudo apt-get install libxine-extracodecs
```
Amarok is the *best*!

---

### Post by gunksta on 2006-08-31
Or, try the automatix way.....

[http://www.getautomatix.com/](http://www.getautomatix.com/)

I agree, you need the libxine-extracodecs package. Automatix will get it for you and you can also find it through Adept, the package management tool.

--andy

---

### Post by ravpaul on 2006-09-01
```
sudo apt-get install libxine-extracodecs
```

U DA MAN!!! Gonna learn the ipod bit now

---

### Post by Techman010 on 2006-09-04
Thanks Mitch.C it worked.  Thanks to all for helping out.

Edit:  Okay Just got two more (less important) problems.

1. Can't edit Tags, once I do it says that sorry and that it can't edit it.
2. Can't delete files with the manage files option after right clicking on a song.

(Could these problems because I am using the Gnome desktop and not KDE..., just a sugestion) Thanks again.

O and Amarok *IS* very sweet.

---

