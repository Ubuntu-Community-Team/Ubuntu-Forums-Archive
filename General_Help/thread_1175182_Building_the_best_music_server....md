---
title: "Building the best music server...?"
date: 2009-05-31
forum: General Help
---

### Post by thecheeks on 2009-05-31
So I'm working on a file server, everything is going good but I feel like I'm missing some programs that would help automate everything music related.

I use rTorrent to download music, and depending on which watch folder I put the .torrent in, specifies where it will download (Music, Video, Misc). What I'm looking to do is to automate 'importing' Music on my Music drive. This way I send off the .torrent to the music drive, and once it is done downloading, sends it through a program that auto-corrects tags (been checking out Easytag but I'm looking for something more CLI and automated), rename the file, and put it in a folder based on Artist - Album.

Right now I have to do everything by hand which isn't too hard, however I have to do it via SSH or VNC which can be a pain (not to mention mounting network drives, when copying/moving the file has to go in/out my Mac.

Thanks!

---

### Post by DGortze380 on 2009-05-31
> **thecheeks said:**
> So I'm working on a file server, everything is going good but I feel like I'm missing some programs that would help automate everything music related.

I use rTorrent to download music, and depending on which watch folder I put the .torrent in, specifies where it will download (Music, Video, Misc). What I'm looking to do is to automate 'importing' Music on my Music drive. This way I send off the .torrent to the music drive, and once it is done downloading, sends it through a program that auto-corrects tags (been checking out Easytag but I'm looking for something more CLI and automated), rename the file, and put it in a folder based on Artist - Album.

Right now I have to do everything by hand which isn't too hard, however I have to do it via SSH or VNC which can be a pain (not to mention mounting network drives, when copying/moving the file has to go in/out my Mac.

Thanks!

Probably not the best solution, but the first thought that comes to mind is a simple script (or program) to ssh to your host from the server, check your directories, create if necessary, move the file and disconnect...

---

### Post by unutbu on 2009-05-31
Are you looking for a program that can monitor a directory, notice when a file has been created, and execute a script whenever that happens? If so, I think you might find the incron package useful. "incron" is similar to "cron", except that it runs jobs triggered by changes in the filesystem rather than being triggered by datetimes.

If this is what you are looking for then do this:
```

sudo apt-get install incron

```
Edit /etc/incron.allow

and add your username there.

Next, make a file called ~/incrontab and put this in it:
```

/path/to/watch IN_CLOSE_WRITE /path/to/script.sh $#
```

Run
```

incrontab ~/incrontab
```

This will setup incron to run /path/to/script.sh whenever a new file is written in
/path/to/watch.

All that's left for you to do is write the /path/to/script.sh script.
As a simple example to start with, you could puth this in /path/to/script.sh:
```

#!/bin/sh
echo $(date +%Y-%m-%d_%H:%M): $1 >> /tmp/watch.out
```

To test the setup, make a file in /path/to/watch:
```

cd /path/to/watch
touch hithere
```

Then check that /tmp/watch.out is created and contains something like
```

2009-05-31_22:51: hithere
```

If all that works, then all you need to do is insert the commands to 
auto-correct tags, rename the file, and move it to the right folder... (No sweat, right? :))

---

### Post by thecheeks on 2009-05-31
Hahahaha. Well, looks like I have my work cut out for me ;)

I have all summer to perfect this machine, before I move into my next apartment. Looks like I have some learning to do, my Unix knowledge is very spotty. Thanks for the response, I'll bookmark it and get to work.

---

