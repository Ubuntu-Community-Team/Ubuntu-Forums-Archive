---
title: "Are these rsync commands correct?"
date: 2009-04-15
forum: General Help
---

### Post by Rytron on 2009-04-15
Hi.
I saw these rsync commands on a YouTube video. It was difficult to read the text on the video. I think these are correct:

```
# copy files from Cd to local directory
cp -R /media/CDROM/* .
```

```
#copy after interuption
rsync -Pav /media/CDROM/* .
```

Please could some verify if the above commands are correct.
Thanks.

---

### Post by jowilkin on 2009-04-15
If you don't say what you want the command to do then how can we tell you if it's correct?

Check out the rsync man page to see what that command does.

-P is to show progress during the transfer
-v is verbose mode
-a is archive mode

So your command copies everything under /media/CDROM to the current directory.

---

### Post by Rytron on 2009-04-15
> **jowilkin said:**
> If you don't say what you want the command to do then how can we tell you if it's correct?

Check out the rsync man page to see what that command does.

-P is to show progress during the transfer
-v is verbose mode
-a is archive mode

So your command copies everything under /media/CDROM to the current directory.

I put the commands purpose after the # symbols.

```
**# copy files from Cd to local directory**
cp -R /media/CDROM/* .
```

```
**# copy after interuption**
rsync -Pav /media/CDROM/* .
```

---

### Post by tobydeemer on 2009-04-15
Those look good for copying the data off the CD. (That obviously doesn't make an .iso however.)

But using the -r option to recurse into directories tended to work better for me rather than using /* wildcards (though technically both should be correct).

The nicer thing about rsync is that its compression algorithm is much better than CP, e.g I just used rsync to move a 2.6 GB file from my HD to an external USB drive in less than two minutes over USB 2.0. Drag-and-drop or using cp would take much longer to move that file.

Hope that's at least a little useful...

---

### Post by maheshasolkar on 2009-04-15
Same command in a more readable form (although a pain to type frequently):

```
  rsync --verbose --progress --archive /media/CDROM/* .

```

I always prefer rsync to cp when it comes to copying large chunks of data - especially from/to an external media or network. If there is an interruption, rsync picks from where it left - copy does it all over again. Unless you know exactly what is left to be copied.

I am sure everyone already knows that, but felt like reiterating :)

---

