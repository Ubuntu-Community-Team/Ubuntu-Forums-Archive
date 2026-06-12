---
title: "Problem with Nicotine+ crashing"
date: 2009-05-11
forum: General Help
---

### Post by Jamesss on 2009-05-11
Since upgrading to Jaunty, I have a problem with Nicotine+ crashing. It seems to exit suddenly and randomly after a few minutes of starting up. I can search, download, chat etc but it always crashes after some minutes. Is there a log I can check somewhere? I've looked in /home/user/.nicotine/ and there's no logs directory...

---

### Post by Spektakel on 2009-05-14
I've been running Nicotine in Jaunty without problems, until yesterday. Now it keeps crashing after less then a minute. 

On another computer with different hardware but also running Jaunty, nicotine is crashing since a few days also. 

Any idea what could be causing this?

---

### Post by pmcginley on 2009-05-16
i'm having the same problem.  this newsletter:

[http://ubuntuforums.org/showthread.php?t=1123709&highlight=jaunty+nicotine+problems]("http://ubuntuforums.org/showthread.php?t=1123709&highlight=jaunty+nicotine+problems")

seems to imply that there is a jaunty specific patch for nicotine:

[https://launchpad.net/ubuntu/jaunty/+source/nicotine/1.2.9+dfsg-3ubuntu1]("https://launchpad.net/ubuntu/jaunty/+source/nicotine/1.2.9+dfsg-3ubuntu1")

this however leads to a tar.gz with nicotine source code, and i, for one, haven't the slightest idea what to do with it.  anyone have any indications for a simple user with no compiling experience?

---

### Post by pmcginley on 2009-05-16
hm, also it seems there is a newer version available, 1.2.10:

[http://www.nicotine-plus.org/]("http://www.nicotine-plus.org/")

does anyone know if this version runs cleanly on jaunty?

---

### Post by cybrsaylr on 2009-05-16
Used the 1.2.9 version last night with no problems. 
Just gave it a short test now and all seems normal on JJ.

---

### Post by pmcginley on 2009-05-16
> **cybrsaylr said:**
> Used the 1.2.9 version last night with no problems. 
Just gave it a short test now and all seems normal on JJ.

well, glad to hear it.  but as with most bugs, i imagine it doesn't affect everyone.  there's no denying that it crashes without fail on my machine, and that there is documentation of a jaunty-specific problem.

anyone tried 1.2.10?

---

### Post by pmcginley on 2009-05-19
ok, i did some searching and found an indication (don't ask me where - somewhere in a bug report on the nicotine+ site i think) that the crashing may be specifically linked to the system tray icon.  i disabled it (edit/settings/interface/icons) and nicotine+ has now been running for an hour or two without problems!  fingers crossed, this may be a reasonable solution until the bug is seen to.

hope that helps!

---

### Post by Spektakel on 2009-05-19
> **pmcginley said:**
> ok, i did some searching and found an indication (don't ask me where - somewhere in a bug report on the nicotine+ site i think) that the crashing may be specifically linked to the system tray icon.  i disabled it (edit/settings/interface/icons) and nicotine+ has now been running for an hour or two without problems!  fingers crossed, this may be a reasonable solution until the bug is seen to.

hope that helps!

Thanks, but that doesn't fix anything for my. I've tried to disable the system tray icon, but when searching for files in Nicotine, Nicotine crashes after a few seconds. 

This only happens to me when searching.

---

### Post by pmcginley on 2009-05-20
here it is, i found it again:

> i've runned nicotine with the --sync command line and then chose it without tray icon. then the error did not appear. so i chose the same in the options and when i run nicotine now, the error did'nt appear. it looks like it has something to do with the tray icon.

it's the last comment (bottom of the page) in this bug report:

[http://www.nicotine-plus.org/ticket/389]("http://www.nicotine-plus.org/ticket/389")

what you're reporting is exactly what was happening to me - if i had files lined up in my download window already it could usually stay up and running.  but as soon as i launched a search it would crash within a few minutes.  in the end it even started crashing my machine each time, rather than just itself (system-wide freeze).

sorry it doesn't help you - but just to be sure, trying doing step by step what this fellow describes, which is what i did:

from a terminal, run:

```
nicotine --sync
```

(i don't really know what this did, other that lead me to instructions for how to disable the tray icon from the terminal.  maybe you know better and can skip this step.)

then run:

```
nicotine -d
```

then be sure the system tray icon is disabled in the edit menu as previously described.  close nicotine, relaunch it the usual way, verify the tray icon is not present, and cross your fingers.

i know it's very possible that this bug is manifesting differently on your machine, but it's worth being absolutely certain this lead won't work for you...

for me, it's been running smoothly since i posted yesterday, so it's no cooincidence...

---

### Post by Soul-Sing on 2009-05-20
i have got some problems with nicotine. after closing nicotine the (a) nicotine proces is stil active, and i have to terminate it man. strang...

---

### Post by colau on 2009-05-20
Sorry for hijacking the thread.
Just installed it.
```

Nicotine-Plus version 1.2.9

```
Any problem(bug) with this version?

---

### Post by Spektakel on 2009-05-20
> **pmcginley said:**
> here it is, i found it again:



it's the last comment (bottom of the page) in this bug report:

[http://www.nicotine-plus.org/ticket/389]("http://www.nicotine-plus.org/ticket/389")

what you're reporting is exactly what was happening to me - if i had files lined up in my download window already it could usually stay up and running.  but as soon as i launched a search it would crash within a few minutes.  in the end it even started crashing my machine each time, rather than just itself (system-wide freeze).

sorry it doesn't help you - but just to be sure, trying doing step by step what this fellow describes, which is what i did:

from a terminal, run:

```
nicotine --sync
```

(i don't really know what this did, other that lead me to instructions for how to disable the tray icon from the terminal.  maybe you know better and can skip this step.)

then run:

```
nicotine -d
```

then be sure the system tray icon is disabled in the edit menu as previously described.  close nicotine, relaunch it the usual way, verify the tray icon is not present, and cross your fingers.

i know it's very possible that this bug is manifesting differently on your machine, but it's worth being absolutely certain this lead won't work for you...

for me, it's been running smoothly since i posted yesterday, so it's no cooincidence...

Thanks again, tried it this way, but still crashing when searching. However, I just installed **Nicotine 1.2.10**, the latest version, and it's **not crashing**.

So, the latest Nicotine seems to solve this problem on my computer. Here's how to download and install: [http://nicotine-plus.sourceforge.net/NicotinePlusGuide/Installation/NicotineOnAnyDistro.htm](http://nicotine-plus.sourceforge.net/NicotinePlusGuide/Installation/NicotineOnAnyDistro.htm)

I haven't tested this thoroughly, if something ugly comes up I'll post it here.

---

### Post by pmcginley on 2009-05-20
> **Spektakel said:**
> Thanks again, tried it this way, but still crashing when searching. However, I just installed **Nicotine 1.2.10**, the latest version, and it's **not crashing**.

hm, that's interesting news, thanks for letting us know.  i was wondering about that, but i couldn't be bothered to go though the hassle of installing something that's not yet in the repositories with the risk of it still not working...  ; )

my way is working ok, but it would be nice to have my tray icon back.  do let us know if a problem arises, otherwise i'll give 1.2.10 a go as well...

---

### Post by Soul-Sing on 2009-05-20
When searching with to many connections, nicotine limits (971 connections I think) the amount of connections for your one safety, nicotine+ will freeze and stop working.
Search as specific as possible. Try =U2= and nicotine+ will freeze.
Also on Nicotine 1.2.10. I have tested it.

---

