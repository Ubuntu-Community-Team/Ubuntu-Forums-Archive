---
title: "using multimedia keys for rhytmbox"
date: 2012-03-07
forum: Desktop Environments
---

### Post by Xanza on 2012-03-07
This works on my ubuntu machine but not on my xubuntu machine.. How do I set my multimedia keys to work with Rhythmbox?

---

### Post by LewisTM on 2012-03-07
Take a look at [rhythmbox-client]("http://manpages.ubuntu.com/manpages/hardy/man1/rhythmbox-client.1.html") commands then bind the appropriate ones to multimedia keys in the Keyboard/Application Shortcuts settings.

Cheers!

---

### Post by Xanza on 2012-03-07
How do I go about getting rhythmbox-client? Can't find it in software center

---

### Post by LewisTM on 2012-03-07
It's packaged with rhythmbox.
Just run [FONT="Courier New"]man rhythmbox-client[/FONT] in the Terminal to verify.

---

### Post by Toz on 2012-03-07
@OP, In the event that rhtyhmbox-client doesn't work (I couldn't get it to work on my 12.10 beta install), you could also control rhythmbox through dbus. 
See this gentoo link ([http://en.gentoo-wiki.com/wiki/Multimedia_Keys#Rhythmbox]("http://en.gentoo-wiki.com/wiki/Multimedia_Keys#Rhythmbox")) for information about the commands to use.

---

### Post by LewisTM on 2012-03-07
Toz, do you come from the future?
12.10 ????
;) hehe

I don't use Rhythmbox myself so couldn't report on how well it works in archaic 11.10. 
Turns out the client is [missing]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/875064") from the Oneiric (and Precise) rhythmbox package
{Face palm}

Sorry

---

### Post by Toz on 2012-03-07
> **LewisTM said:**
> Toz, do you come from the future?
12.10 ????
;) hehe

I don't use Rhythmbox myself so couldn't report on how well it works in archaic 11.10. 
Turns out the client is [missing]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/875064") from the Oneiric (and Precise) rhythmbox package
{Face palm}

Sorry

Damn that time machine...always going wonky.
Sorry, I meant 12.04.

---

### Post by DoritosBR on 2012-04-28
I was a little disappointed today.
I just installed Xubuntu 12.04, and no application works with the multimedia keys.

They only work when setting the shortcut. I can set the key both in clementine and on xfce keyboard settings, and they recognize the key.

But when I press the key to pause the music, or to increase or decrease the volume, nothing happens.

Any help?

---

### Post by Toz on 2012-04-28
> **DoritosBR said:**
> I was a little disappointed today.
I just installed Xubuntu 12.04, and no application works with the multimedia keys.

They only work when setting the shortcut. I can set the key both in clementine and on xfce keyboard settings, and they recognize the key.

But when I press the key to pause the music, or to increase or decrease the volume, nothing happens.

Any help?
According to:
```
man clementine
```
...or [http://manpages.ubuntu.com/manpages/precise/man1/clementine.1.html](http://manpages.ubuntu.com/manpages/precise/man1/clementine.1.html)

You can execute the clementine command with parameters:

To play/pause:
```
clementine -t
```

To increase volume by 4%:
```
clementine --volume-up
```

To decrease volume by 4%:
```
clementine --volume-down
```

Try adding those to the keyboard shortcuts.

---

### Post by DoritosBR on 2012-04-28
I could swear that even the shortcuts set in the XFCE Keyboard Settings did not work, well, they worked.
I set all the shortcuts for stop, play, volume down and up.

But the mute volume doesn't toggle mute, it just mutes and doesnt unmute.

I used the command "amixer set Master toggle"

---

### Post by Toz on 2012-04-29
There appears to be an issue unmuting using amixer because it mute seems to mute both the Master & PCM channels, but unmute only unmutes the Master channel. Use this script to take care of this situation:
```
#!/bin/bash
    if amixer -c 0 get Master | grep -q off
then
    amixer set Master unmute
    amixer set PCM unmute

else
    amixer set Master mute
fi

```

---

