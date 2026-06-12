---
title: "Get rid off the ugly indicator"
date: 2011-10-31
forum: Desktop Environments
---

### Post by crazy bird on 2011-10-31
Hi,

Somewhere on this forum i found a command which enable users to get rid off that ugly indicator on the right top side of the screen. I really hate that and with that command i could get rid of it. But now i can't find that command anymore.

Someone out there helping me out here? Many thanks in advance!

---

### Post by gsmanners on 2011-10-31
Hi. Here's how you can remove things. To remove an indicator, use this command in terminal:

```
sudo apt-get remove indicator-something
```

Where something is the indicator you want gone. To get it back:

```
sudo apt-get install indicator-something
```

Here's a list of some indicators:

indicator-session (session, status and user stuff)
indicator-messages (IM and email stuff)
indicator-power (power state)
indicator-network (network manager)
indicator-sound (sound)
indicator-datetime (a simple clock)

There's probably a bunch more.

---

### Post by crazy bird on 2011-11-01
> **gsmanners said:**
> Hi. Here's how you can remove things. To remove an indicator, use this command in terminal:
 
```
sudo apt-get remove indicator-something
```
 
Where something is the indicator you want gone. To get it back:
 
```
sudo apt-get install indicator-something
```
 
Here's a list of some indicators:
 
indicator-session (session, status and user stuff)
indicator-messages (IM and email stuff)
indicator-power (power state)
indicator-network (network manager)
indicator-sound (sound)
indicator-datetime (a simple clock)
 
There's probably a bunch more.
 
Thanks for your input, but that's not what i'm looking for. It's a command which moves a whole directory or parts of a directory to my home folder.
 
something like: *sudo mv /***/*** ~/*

---

### Post by crazy bird on 2011-11-01
Found it! Did a good search on this forum and found what i'm looking for:
 
> sudo mv /usr/lib/notify-osd .
 
This does the tric!
 
Link to the post: [http://ubuntuforums.org/showthread.php?t=1765210&highlight=notify-osd](http://ubuntuforums.org/showthread.php?t=1765210&highlight=notify-osd)

---

