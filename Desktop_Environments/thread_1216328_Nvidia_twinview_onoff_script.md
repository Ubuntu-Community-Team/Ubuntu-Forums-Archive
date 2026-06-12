---
title: "Nvidia twinview on/off script"
date: 2009-07-18
forum: Desktop Environments
---

### Post by Altreus on 2009-07-18
Hi

Couldn't decide between this forum and multimedia, so if I got it wrong please move.

I am working on a laptop with an Nvidia in it. I can plug my monitor into it when I get back to my desk and then I have to go through exactly the same set of steps every single time:


[LIST]
[*]Open Nvidia settings
[*]Go to display settings
[*]Click autodetect displays
[*]Select new display
[*]Click Configure
[*]Set to Twinview
[*]Click OK
[*]Click Apply
[*]Click Yes
[/LIST]
And then before I leave I have to undo it by basically doing it all backwards:


[LIST]
[*]Select new display
[*]Click Configure
[*]Select Disabled
[*]OK
[*]Apply
[*]Yes
[/LIST]
I am trying to figure out a way of scripting this:

./twinview-on
./twinview-off

which would be doubly helpful as I don't have to keep the monitor plugged in to do it.

Can anyone give me any insight as to where I might start looking for what this GUI does in the background? Or indeed just tell me outright, if anyone knows!

Many thanks
Al

---

### Post by Altreus on 2009-07-20
I found this:

[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

It has an Ubuntu repository. Simply add that, apt-get install disper, and then

```
disper -d auto -e
```

Add ```
-t top
``` in there somewhere if your second display is above you - see manpage for the details.

Genius!

---

