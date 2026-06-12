---
title: "Rhythymbox won't open mp3s"
date: 2006-05-06
forum: Desktop Environments
---

### Post by GuitarHero on 2006-05-06
I put some of my cds on my computer and tried to play them with rhythym box but it says "This file is not an audio stream" but they are mp3s

What is wrong?

---

### Post by jazzmuzik on 2006-05-06
Legal gobbledeegook is the reason mp3 codecs are not included by default. But nearly everybody enables mp3 at some point anyway. See this page to do it:

Restricted Formats:
        [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by GuitarHero on 2006-05-06
Well I ran sudo apt-get install  gstreamer0.8-mad and now it will open them but ubuntu is just silent on my machine.  I dont know why it wont make sound.  I have the volume up on my speakers, in the program, and in the 3d control sound thing but it is still as if something was muting it.  The soundcard is detected and selected in the sound administration.  What do I do now?

EDIT: I tried burning with serpentine and it worked fine, still couldnt play the cd on my computer but it works on my walkman.

---

### Post by vr04 on 2006-05-06
GuitarHero,

Have you messed around with your sound preferences by any chance? This has happened to me before. Just to make sure, go to System > Preferences > Sound. On the "General" tab, see if "Enable sound server startup" is checked. If not, check it and click Close.

That's the only thing I can think of at the moment...

---

### Post by GuitarHero on 2006-05-06
No i didnt mess with it, the box was checked.

---

### Post by jazzmuzik on 2006-05-06
Besides the volume, see if any devices are muted.

Like vr04 says, it takes a bit of playing around with settings to get it working. I can't remember anything specific that I did to get it working at the moment. Sorry. I did install all the codecs mentioned though. The win32codec package is good to have.

Sometimes programs are trying to use a particular sound engine (esd) when the default sound system is set to something else (alsa). You might look into that.

---

### Post by GuitarHero on 2006-05-06
How do I check if my soundcard is muted?

Also I tried burning a cd with k3b to test it out and it doesn't recognize my mp3s as compatible files even though rhythym box does now.  Do I have toi install something to burn mp3s also?

---

### Post by jazzmuzik on 2006-05-06
[QUOTE=GuitarHero]How do I check if my soundcard is muted?[/quote]

Double click on the speaker icon on the toolbar. If you see a red "X" over the little speaker image on the Master volume, click it and the X will disappear. Do the same thing with PCM and others as needed.

> Also I tried burning a cd with k3b to test it out and it doesn't recognize my mp3s as compatible files even though rhythym box does now.  Do I have toi install something to burn mp3s also?

You need to install more codec packages. K3b uses the libmad library. Install that. In the K3b "plugins" section, I show "K3b MAD" decoder and I *think* (can't remember, sorry) that if you install the libmad package you will be good. I believe this is all discussed in the restricted formats link I mentioned above.

Oops. I just noticed I have a k3b-mp3 package loaded. Here's what I show:

```
$ dpkg -l "*mp3*"
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  k3b-mp3                       0.12.7-1ubuntu1~breezy1       The KDE cd burning application library - MP3 decoder
ii  libmp3-info-perl              1.13-1                        Perl MP3::Info - Manipulate / fetch info from MP3 audio files.
un  libmpeg-mp3info-perl          <none>                        (no description available)
un  mp3-decoder                   <none>          
```

I also see this:

```
$ dpkg -l "*mad*"
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  gstreamer0.8-mad              0.8.11-0ubuntu5               MAD MPEG audio decoder plugin for GStreamer
ii  libmad0                       0.15.1b-2.1                   MPEG audio decoder library
ii  libmad0-dev                   0.15.1b-2.1                   MPEG audio decoder development library
un  vlc-mad                       <none>                        (no description available)
un  vlc-plugin-mad                <none>                        (no description available)
ii  xmms-mad                      0.8-1                         mp3 input plugin for xmms based on libmad
pn  xmms2-decoder-mad             <none>                        (no description available)
```

It's one of them. ;)

---

### Post by GuitarHero on 2006-05-06
Well what is the code to install them, I am very new to this and don't know the command line code yet

---

### Post by jazzmuzik on 2006-05-06
You could try 

sudo apt-get install k3b-mp3

but I'm not sure what repository that came from...


Read the linked document again about restricted formats. You can also use Synaptic to install programs once you figure out what they are.

---

### Post by GuitarHero on 2006-05-07
Well K3B now accepts mp3s, but when i open it it says
Unable to find cdrdao executable
K3b uses cdrdao to actually write CDs.
Solution: Install the cdrdao package.

Also the origional problem of no sound output still isnt resolved.

---

### Post by GuitarHero on 2006-05-07
Well I removed my soundcard and it works now, guess i have to use onboard sound.  It recognized the card in sound admin but i guess it didnt have the drivers or something, its an old card i salvaged from a friends unused computer.  Don't really need it i guess.

---

### Post by vr04 on 2006-05-07
[QUOTE=GuitarHero]Well K3B now accepts mp3s, but when i open it it says
Unable to find cdrdao executable
K3b uses cdrdao to actually write CDs.
Solution: Install the cdrdao package.

Also the origional problem of no sound output still isnt resolved.[/QUOTE]

To solve the "cdrdao" problem, type this in the terminal:```
sudo apt-get install cdrdao
```

---

