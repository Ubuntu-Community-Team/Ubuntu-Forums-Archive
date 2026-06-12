---
title: "[SOLVED] installed Feisty Fawn and . . . no sound"
date: 2008-08-22
forum: Desktop Environments
---

### Post by gusteman on 2008-08-22
Hi there,
after having resolved a few not so minor problems with the help of the forum members I finally succeeded in installing Feisty Fawn on a repartitioned HD I mounted in a DELL Optiplex GX1 (I know, this machine is getting a quite respectable age but until now it worked fine for me and my needs). Only problem I am now encountered with: I can't seem to get the sound working. For example when I go to Applications/Audio+Video and open the sound level adapter I get a window which tells me that no devices for GStream can be found.
What am I doing wrong, what did I miss or just looked over.
If anyone has a solution I'd be much obliged. BTW as I'm still a rookie and learning day by day, pls try to explain step by step. Like an old Chinese saying goes: [COLOR="Blue"]the journey of a thousand miles begins with one step[/COLOR].
Greets, Gusteman

---

### Post by ugm6hr on 2008-08-22
The following command will tell you what driver you use for audio:
```
lshw -class multimedia
```

This will open alsamixer:
```
alsamixer
```

PS: It is easier to get help if you install Hardy (8.04).

---

### Post by maniheer on 2008-08-22
Have you got alsa-utilities installed, if yes can you run

```

sudo alsaconf

```

If yes again follow the instructions that come on the terminal. When its finished open your favorite mixer and put all the bars up. (Then pray it works)

If you can't run alsaconf then tell me and i'll tell you a different (less recommended) way. :popcorn:

---

### Post by gusteman on 2008-08-23
Hi there maniheer,
i haven't yet tried out what you proposed but had already tried out this:
opened terminal en entered quote sudo gedit unquote
In Gedit i did not find the File System in the left window so I wasn't able to get to /etc/modules this way. Then I went to the Desktop, opened Locations/Computer/File systems/Etc and found no folder named Modules. As far as I now it's in this folder that I should make the adjustments.

I must say that on the second hard drive in my PC I also have Feisty and there I have no problems whatsoever with sound or media. Unfortunally that drive has only 3,6 GB of space which is the main reason I mounted a 80 GB HD. This proves that the problem lies within Ubuntu (maybe something went wrong installing Feisty?) so maybe I'd better re-format the disk and start allover again. Greetings, Gusteman

---

