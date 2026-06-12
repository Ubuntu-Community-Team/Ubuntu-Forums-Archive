---
title: "Thunderbird: how to run program on attachment?"
date: 2005-10-29
forum: Desktop Environments
---

### Post by greyhound4334 on 2005-10-29
Hi all,

Running latest mozilla thunderbird.

I get voicemails mailed to me as attachments.  They're in .wav format, that I can play from the command line with "bplay -d /dev/dsp1 filename.wav".

I'd like to be able to associate a default action with opening the attachment such that double clicking on it automatically launches bplay with the right parameters, and plays the file.

Can't seem to figure out how to make this happen.

Hoping someone can offer some clues!

Thanks,
john

---

### Post by HermanAB on 2005-10-29
Click Tools, Options, Attachments, File Types, but goodness knows what to put in there.  You'll have to do some Googling.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by greyhound4334 on 2005-10-29
Thanks, but I kinda got that far :)  That's the easy part.

What goes there is the actual question! ;)

---

### Post by aysiu on 2005-10-29
I found my solution to associating Thunderbird and Firefox here:
[http://ubuntuforums.org/showthread.php?t=60427](http://ubuntuforums.org/showthread.php?t=60427)

Maybe there's an equivalent you could put in for sound files...

---

### Post by greyhound4334 on 2005-10-29
Thanks.

For anyone who cares about this, I ended up writing a short shell script to invoke mplayer with the right parameters, then pointing at my shell script in the thunderbird edit->preferences->attachments dialog.

The shell script just takes the name of the attachment file as its (only) input parameter, and invokes mplayer as needed.

---

### Post by greatshape on 2005-10-29
[QUOTE=greyhound4334]Thanks.

For anyone who cares about this, I ended up writing a short shell script to invoke mplayer with the right parameters, then pointing at my shell script in the thunderbird edit->preferences->attachments dialog.

The shell script just takes the name of the attachment file as its (only) input parameter, and invokes mplayer as needed.[/QUOTE]

Nice workaround, but maybe you can post your script here? It can be usefull to others in the future. ;-) 

Regards, steve

---

### Post by greyhound4334 on 2005-10-29
Sure, it's trivially simple.

```
#!/bin/sh
mplayer -ao arts $1
```

BTW, I'm not sure why bplayer didn't work the same way, but it might have been pilot error on my part back when I first started trying to figure this out.  I see no reason why you couldn't run any valid program that's able to accept a single input file using this technique.

---

