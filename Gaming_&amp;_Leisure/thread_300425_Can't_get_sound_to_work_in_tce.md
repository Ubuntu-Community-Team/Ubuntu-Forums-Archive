---
title: "Can't get sound to work in tc:e"
date: 2006-11-15
forum: Gaming &amp; Leisure
---

### Post by thecynicality on 2006-11-15
My sound works fine for the most part, it works on the desktop and for the internet and in some games, but when i try to play tc:e i have no sound in the game. I've tried a few things that people suggested like:

```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```

and just:
```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

```

```

sudo killall artsd 
sudo killall esd
```

```
/etc/init.d/alsasound restart
```

I also tried reinstalling alsa but no improvement.

Does anybody have any idea as to what i should do?

---

### Post by fatsheep on 2006-11-15
Try running these commands before running:

**NOTE: Remember to replace user:user with your own username! For me this is fatsheep:fatsheep.**

> sudo killall esd
chown user:user /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 

Or you can make a startup script (just a text file with executable permissions):

> #!/bin/bash
sudo killall esd
chown user:user /proc/asound/card0/pcm0p/oss
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
et 

When you run the script, it automatically automatically starts Enemy Territory with sound.

---

### Post by LuisGMarine on 2007-05-18
**Sorry to bring up such an old post, its almost ancient.**

But I just got done installing a fresh install of Ubuntu Feisty AMD64, got through the process of installing Enemy-Territory ( ET ) after a few hours of playing around with a bunch of different commands.  Then I launched the game, keep in mind I was really excited, and then to find out there is no sound.

I've been looking for solutions to fix my sound problem in ET for the past four hours, and this - so far - , have been the only post that has worked. 

Although I changed a bit of commands, this is what I put in.  I hope that this can stand as a howto for some of the new users that are having trouble.  

First I ran the command to kill esd:
```
sudo killall esd
```

Then I changed the permissions in */proc/asound/card0/pcm0p/oss*:
```
sudo chown user:user /proc/asound/card0/pcm0p/oss
```

Then ran this command:
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

After this I ran Enemy-Territory (ET) with the regular '*et*' from the command line and I got sound working!

I was worried that these commands somehow might mess up the rest of my systems sound, but it didn't.  I ran youtube ( swiftweasel ) and I got sound working from YouTube, ontop of that I'm listsening to music through Rhythmbox right now.  The reason I mention this is because from all the posts that I have read today, some people say that the commands above mess up their whole system.

From scripting a littlebit, I know that the script below is legit and should work.  

Once again sorry to the rest of the community for bringing such an old thread, but after four hours of fustrating search and no avail, I thought I'd comment on the **ONE** thread that made the difference for me. 

Thanks!

---

