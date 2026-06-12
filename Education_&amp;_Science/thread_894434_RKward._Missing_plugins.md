---
title: "RKward. Missing plugins"
date: 2008-08-19
forum: Education &amp; Science
---

### Post by orduek on 2008-08-19
after installing RKward on ubuntu 8.10 i wasn't able to load it properly.
every time I load it it says NO (valid) plugins found. pluings are needed: you may manage these through "Settings-->configure-->RKward"
then it says page doesn't exist.

in the terminal:
XML-parsing '/home/ord/rkward/all.pluginmap' : Could not open file for reading
XML-parsing '/home/ord/rkward/all.pluginmap' : Error parsing XML-file. Error-message was: 'unexpected end of file' in line '1', column '1'. Expect further errors to be reported below


whats wrong?
thank you.

---

### Post by earlycj5 on 2008-08-20
Mine shows "/usr/share/apps/rkward//all.pluginmap" for the .pluginmap files.

You might try symlinking or copying "/home/ord/rkward/all.pluginmap" to that file if it exists?

I'm still using 08.04 though.

---

### Post by orduek on 2008-08-22
I don't have any file like it in my home folder.
I do have this file in my usr..... folder.

any ideas?

---

### Post by earlycj5 on 2008-08-22
> **earlycj5 said:**
> Mine shows "/usr/share/apps/rkward//all.pluginmap" for the .pluginmap files.

You might try simlinking or copying "/home/ord/rkward/all.pluginmap" to that file if it exists?

I'm still using 08.04 though.

> **orduek said:**
> I don't have any file like it in my home folder.
I do have this file in my usr..... folder.

any ideas?

Perhaps I wasn't clear enough?  I'd either correct the setting in RKward and point it to "/usr/share/apps/rkward//all.pluginmap" or I would simlink to that file from "/home/ord/rkward/all.pluginmap".

---

### Post by sethlatimer on 2008-08-28
> **earlycj5 said:**
>  point it to "/usr/share/apps/rkward//all.pluginmap" or I would simlink to that file from "/home/ord/rkward/all.pluginmap".

Pardon my ignorance...How is this done? Something like:

sudo ln home/ord/rkward/all.pluginmap /usr/share/apps/rkward/all.pluginmap

I am really new to this but ***really*** want to use the newest rkward.
Seth

---

### Post by earlycj5 on 2008-08-29
> **sethlatimer said:**
> Pardon my ignorance...How is this done? Something like:

sudo ln home/ord/rkward/all.pluginmap /usr/share/apps/rkward/all.pluginmap

I am really new to this but ***really*** want to use the newest rkward.
Seth

Seth,
If your simlinking from anywhere within your /home directory you don't need to use sudo.

I'd just change the path within RKWard myself to keep it simple.

Settings -> Configure RKWard -> Plugins -> Remove (the erroneous file path)

Settings -> Configure RKWard -> Plugins -> Add (point it to the correct /usr/share/apps/rkward/all.pluginmap file)

---

### Post by fsando on 2008-09-09
> **sethlatimer said:**
> Pardon my ignorance...How is this done? Something like:

sudo ln home/ord/rkward/all.pluginmap /usr/share/apps/rkward/all.pluginmap

I am really new to this but ***really*** want to use the newest rkward.
Seth

Hi
Have you found a solution yet?


I use 8.10 only because my new laptop is not really supported under 8.04 otherwise you should stick with 8.04 it is great and rkward runs like a dream if you compile it from the latest sources.

If you don't know how to compile it just ask - it is really easy :)

@earlycj5
The rkward Settings menu is incomplete in 8.10 and doesn't contain a 'Configure' entry. 

I'll be looking into where rkward reads its settings from at startup.

---

### Post by cjawcrusher512 on 2008-09-09
[[size=2][color=#006699]How to buy a ball mill with quality at reasonable price in China  ?[/color][/size]](http://answers.yahoo.com/question/index?qid=20080826203448AAVEOrl)

---

### Post by earlycj5 on 2008-09-09
> **fsando said:**
> 
@earlycj5
The rkward Settings menu is incomplete in 8.10 and doesn't contain a 'Configure' entry. 

I'll be looking into where rkward reads its settings from at startup.

Hmmm, really?  Mine did using the install from the repositories because I had to deal with this issue myself.

Though now I'm using 0.5 which I compiled myself.

---

### Post by fsando on 2008-09-09
> **earlycj5 said:**
> Hmmm, really?  Mine did using the install from the repositories because I had to deal with this issue myself.

Though now I'm using 0.5 which I compiled myself.
That's exactly what I do under 8.04.

I think either rkward or R (or both) might be broken in 8.10 at the moment

But I sort of solved it:
I installed 8.04, installed R, compiled rkward etc. and then did an upgrade to 8.10 instead of a clean install. This turned out to be the right path. So now I have a functional computer with a functional statistical environment :)

---

### Post by earlycj5 on 2008-09-11
> **fsando said:**
> That's exactly what I do under 8.04.

I think either rkward or R (or both) might be broken in 8.10 at the moment

But I sort of solved it:
I installed 8.04, installed R, compiled rkward etc. and then did an upgrade to 8.10 instead of a clean install. This turned out to be the right path. So now I have a functional computer with a functional statistical environment :)

Ah, oh, sorry, I missed the 8.10 part.  Next time I'll pay more attention in class.

I just know I've had the same error message that I dealt with and neglected to think about which version of Ubuntu you were using.

---

### Post by tsphere on 2008-11-01
Can anyone tell me where do I download the 0.5 and how to compile it myself?
I have intrepid and I get the same issues.

---

### Post by sethlatimer on 2008-11-01
I am not too hip on compiling stuff. So I made a directory called rkward in my home and then copied all of the contents of /usr/share/apps/rkward/ into the new directory.... now I have plugins for most of the things that I had in the previous version (I think 4.9.x on hardy). Although I do miss the run buttons. I hope this helps someone as I haven't been able to get it to work with other's recommendations.
seth

---

### Post by vinylasphalt on 2008-11-02
found an easy fix after bashing my head into the wall. earlycj5 had a correct method save for the actually getting to the configuration menu. heres a different way of getting to that menu and doing the fix.

1) Find your all.pluginmap file 
   (should be located at /usr/share/apps/rkward)
2) load Rkward (errors and all)
3) On the left hand side click on workspace
4) right click any of the packages listed
5) click configure defaults
6) on the left menu go to the Plugins tab
7) remove the faulty all.pluginmap location and add the one you found (/usr/share/apps/rkward)

Restart rkward and everything should be ok.

i still get the 
QFSFileEngine::open: No file name specified
error, so if anyone finds a fix for that (if its important) post it.

---

### Post by vinylasphalt on 2008-11-03
still further error with common.php. the only workaround i have found is renaming your .rkward file in home directory (hidden) to rkward which is kinda annoying. anyone know how to point rkward at .rkward for the common.php file?

---

### Post by earlycj5 on 2008-11-03
> **vinylasphalt said:**
> still further error with common.php. the only workaround i have found is renaming your .rkward file in home directory (hidden) to rkward which is kinda annoying. anyone know how to point rkward at .rkward for the common.php file?

```

ln -s .rkward rkward

```

Creates a symlink, I think that's what you're asking?

---

### Post by earlycj5 on 2008-11-03
> **vinylasphalt said:**
> found an easy fix after bashing my head into the wall. earlycj5 had a correct method save for the actually getting to the configuration menu. heres a different way of getting to that menu and doing the fix.

1) Find your all.pluginmap file 
   (should be located at /usr/share/apps/rkward)
2) load Rkward (errors and all)
3) On the left hand side click on workspace
4) right click any of the packages listed
5) click configure defaults
6) on the left menu go to the Plugins tab
7) remove the faulty all.pluginmap location and add the one you found (/usr/share/apps/rkward)

Restart rkward and everything should be ok.

i still get the 
QFSFileEngine::open: No file name specified
error, so if anyone finds a fix for that (if its important) post it.

Now that I've upgraded to Intrepid I fully understand the issues with the missing menu item.  However, I didn't have any issues loading it since it was already pointing to the correct all.pluginmap.

I don't get any QFSFileEngine::open error though.  I just did a dist-upgrade on Friday.  Haven't been using Intrepid that long here at work.

---

### Post by mfox on 2008-11-16
Thanks for the instructions earlycj5; that got rkward going.  However, it still doesn't load the introduction page.  Any idea how I get that back?

---

### Post by earlycj5 on 2008-12-01
Looks like the svn version has finally caught up to the official release of R.

I don't know when, I just compiled it now, these directions will help.
[http://sourceforge.net/forum/message.php?msg_id=5508112](http://sourceforge.net/forum/message.php?msg_id=5508112)

I've got full functionality again (I think).  My icons are complete at the top and my menu-bar is full.

mfox, sorry, I didn't see your question until just now.  I think you want "Settings -> Configure RKWard -> General and check the "Show RKWard help on startup" box.

---

### Post by asdir on 2008-12-16
> **earlycj5 said:**
> ```

ln -s .rkward rkward

```

Creates a symlink, I think that's what you're asking?

I am afraid the link has to be different. In my case (after a standard installation) it had to look like this:

```

:~$   ln -s /usr/share/apps/rkward/phpfiles rkward

```

(":~$" means you should use the command while being in your home folder).


By the way: Are these two problems with locations (at least I would view them as 2 different probs) registered as bugs at launchpad yet? I had a look but could not understand the technical gibberish there. :-(

---

### Post by earlycj5 on 2008-12-16
> **asdir said:**
> I am afraid the link has to be different. In my case (after a standard installation) it had to look like this:

```

:~$   ln -s /usr/share/apps/rkward/phpfiles rkward

```

(":~$" means you should use the command while being in your home folder).


Thanks for making that more clear.

---

### Post by miguelastico on 2009-02-05
am I stupid or what?
I didn't have the menu, so I opened, went into the workspace, right click, edit defaults, and entered the correct folder
I don't want to add a rkward directory in my home, I don't see why; if any software required that it would be a mess
So I put it in the settings
Now I have half of the menu, the "settings" still doesn't show "configure rkward"
compared to my friend installation (on fedora) mine sucks
I am under ubuntu 8.10 and kde desktop

---

### Post by lbthrice on 2009-03-08
hello all,

I have submitted some information pertinent to this bug to the tracker for this project at sourceforge.

[https://sourceforge.net/tracker/index.php?func=detail&aid=2537674&group_id=50231&atid=459007]("https://sourceforge.net/tracker/index.php?func=detail&aid=2537674&group_id=50231&atid=459007")

and I referenced this thread.

The maintainers suggest compiling the current svn version to obtain a working rkward install.
> The version in the repos is possible a corrupted version with all the KDE
4.0 -> 4.1 -> 4.2 changes, R's 2.8 change, ... You may want to compile from
SVN, recently there has been some patch updates. See here:
[http://rkward.sourceforge.net/wiki/index.php?title=RKWard_SVN](http://rkward.sourceforge.net/wiki/index.php?title=RKWard_SVN)

For help pages, r-base-html is needed.



Thank you

---

