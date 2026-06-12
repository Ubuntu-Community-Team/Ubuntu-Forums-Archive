---
title: "frets on fire running ridiculously slow :("
date: 2007-11-07
forum: Gaming &amp; Leisure
---

### Post by Choad on 2007-11-07
i have a c2d 2.0 ghz and an nvidia 7600 go... not a graphical weakling by any stretch of the imagination, however frets on fire runs like an absolute dog to the point where it makes it almost impossible to play!

it maxes out one core, and seems to run at about 20 or so fps

running it from the command line produces no output.

the only error i can see in the logs is

```
PyAmanith not found, SVG support disabled.
```

anyone got any tips on how i can get this running better? it's such a fun game!

---

### Post by Naegling23 on 2007-11-07
disable compiz before launching

---

### Post by Choad on 2007-11-07
no difference. was the first thing i tried. 

put it this way, et:qw runs faster @1920x1200 with compiz enabled than this does @800x600 with compiz disabled! something is wrong!

---

### Post by Choad on 2007-11-07
ok i downloaded the version off of the official site and it works a charm

full 60 fps @ 1920x1200

i think the version in the repositories hasn't been compiled, which is why it runs so poorly.

bug report?

---

### Post by bsund on 2007-11-07
> **Choad said:**
> 
...
bug report?

absolutely ubuntu has problems with it's packages...

extremely big distribution but very poor packages, many apps i use i get precompiled and place in /opt because ubuntu packages are outdated and buggy..

i thought about starting to contribute into universe but i have a 3g modem with 5kb upload so it gets kinda nasty.. but worth learning to make ubuntu packages anyhow :)

to bad all docs about it is messy

---

### Post by Choad on 2007-11-07
> **bsund said:**
> absolutely ubuntu has problems with it's packages...

extremely big distribution but very poor packages, many apps i use i get precompiled and place in /opt because ubuntu packages are outdated and buggy..

i thought about starting to contribute into universe but i have a 3g modem with 5kb upload so it gets kinda nasty.. but worth learning to make ubuntu packages anyhow :)

to bad all docs about it is messy
[https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/160820](https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/160820)

submitted

---

### Post by sloggerkhan on 2007-11-07
There are a number of packages that are extremely dated or have similar problems. I have the same probl w/ frets as you. As another example, open arena is the same version as was in feisty, and inkscape's package is missing dependancies for some of the plugins.

---

### Post by QualityPancakes on 2008-01-01
FoF is running painfully slow for me too, but I got it from sourceforge and was able to run it flawlessly when I had XP. Any ideas? Also, I don't know what compiz is or how to disable it, so any help would be greatly appreciated.

---

### Post by sloggerkhan on 2008-01-01
Get the linux tar.gz from the internet. Apparently the repo version is either completely broken are missing some sort of key dependancy.

---

### Post by QualityPancakes on 2008-01-01
I did get the full version .gz from sourceforge, and other ideas? I need to rock out!

---

### Post by QualityPancakes on 2008-01-01
Also, I found this thread: 
[http://ubuntuforums.org/showthread.php?t=628857]("http://ubuntuforums.org/showthread.php?t=628857")
And when I checked the default depth it was already 24.

---

### Post by Ozor Mox on 2008-01-02
I have the same problem with both the version in the repositories and off the official site. Runs unplayably slow no matter what the options are set to. No Compiz enabled here. I wanna play :(

---

### Post by freezerburn666 on 2008-04-17
heres the deal, i have frets on fire in hardy heron. my xbox360 controller (xplorer) works flawlessly. the game works GREAT until about half way through a song, where it gets EXTREMELY sluggish. i am using the tar.gz from sourceforge, the recommended version to use with RF-Mod. this is discouraging because the game runs perfectly at first, and then gradually slows down :( any ideas?

some things i'v already tried are stopping apache and mysql because my laptop is running lamp. this didn't seem to make much of a difference. the game still ran fast at first, then terrible slow after halfway through a song.

---

### Post by daveisadork on 2008-04-28
The problem causing the slowness for everybody is that Frets on Fire uses a couple libraries called Amanith and PyAmanith. It can run without them, but it's incredibly slow. Those two libraries are next to possible to compile and install and there are no packages for them.

---

### Post by freezerburn666 on 2008-04-29
aw, well that really sucks :( maybe i should try the latest version with no mod but... ugh.. i really hate FoF without RF-Mod lol

---

### Post by jnuz on 2008-05-01
[http://www.mediafire.com/?idzmi4mo4gc](http://www.mediafire.com/?idzmi4mo4gc)

enjoy!

Ds-Alarian UC Mod Binary. just put your song folder in the data directory

---

### Post by freezerburn666 on 2008-05-02
oh.. interesting, i'm anxious to try this out when i get a chance on the weekend. i'll post back after i see how things go.

---

