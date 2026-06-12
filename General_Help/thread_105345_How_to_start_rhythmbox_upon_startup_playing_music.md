---
title: "How to start rhythmbox upon startup playing music?"
date: 2005-12-18
forum: General Help
---

### Post by sup on 2005-12-18
Hello, I would like to make rhythmbox play music when started without manually starting the music. I compiled 0.9.2 version for myself in order to get ID3tag editing, but it should not be the problem, I hope. I put it to system>preferences>sessions and it starts when I boot up the computer, but I do not know how to make it play. 
```
rhythmbox --play
``` suggest it could be it, but whenever I try it from command line, it gives this:```
(rhythmbox:10134): Rhythmbox-WARNING **: error: Failed to register the shell: (null)
This probably means that you installed Rhythmbox in a different prefix than bonobo-activation; this warning is harmless, but IPC will not work.

``` I tried to install about every non-ddevelopment bonobo package founded via synaptic, but it does not help either. There are some options mentioning bonobo when I issue 
```
rhythmbox --help
``` but I have no idea what they mean and which values I should put in. I did not really google anything besides I maybe (it was not concerning Rhythmbox but just bonobo) should set some enviroments variables for bonobo ([http://thomas.apestaart.org/log/index.php?cat=1]("http://thomas.apestaart.org/log/index.php?cat=1")),not that I really know what it means, where and how to do it:-(. Any ideas?

---

### Post by Sutekh on 2005-12-20
Okay I only have Rhythmbox 0.9.1, but if I use
```
rhythmbox --play-pause
```
It starts playing music straight away.

Does this work in 0.9.2?

---

### Post by sup on 2005-12-21
well, I downgraded to 0.9 (desided I do not need ID3tah editing that much) and it started working (both --play and --play-pause work). But i think it is not an issue of a version but a version of directory, where it is installed. I compiled 0.9.2 myself so it installed in /usr/local share and not to /usr/share/ like now, when I installed it with synaptic. And in /usr/share/ it seems to find bonobo without problems.

Is there a way to install something I compiled myself to /usr/share/?

---

### Post by sup on 2005-12-21
Alright, sometimes RTFM is a very nice advice:-). From [http://sourceforge.net/forum/forum.php?forum_id=665]("http://sourceforge.net/forum/forum.php?forum_id=665"):> When I start Rhythmbox, I get this "failed to activate the shell: (null)" dialog box. What can I do about this? 

This issue is caused when Rhythmbox is not installed in the same prefix as GNOME (bonobo-activation, specifically). The easy workaround for this is to pass --no-registration to Rhythmbox. You may also link the GNOME_Rhythmbox.server file into your prefix/lib/bonobo/servers directory.
which pretty much solves the problem. --no-registration silences log but does not solve the problem, I recommend linking (or rather copying since the file is located only in the source you may want to delete) GNOME_Rhythmbox.server to - in ubuntu - /usr/lib/bonobo/servers/

---

