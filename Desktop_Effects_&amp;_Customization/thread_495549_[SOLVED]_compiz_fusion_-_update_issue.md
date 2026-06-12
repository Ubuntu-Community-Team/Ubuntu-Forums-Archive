---
title: "[SOLVED] compiz fusion - update issue"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by rax_m on 2007-07-08
Hi, 

Some automatic updates came through for compiz fusion recently and since then whenever I start it I lose my window borders and title bars. Running from the terminal I get the following:

```

rmistry@rmistry-laptop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

```


Anyone know how this could be fixed? I already have AddARGBGLXVisuals in my xorg.conf file. 

Thanks
Rax

---

### Post by koshari on 2007-07-08
i think you have a dependency hickup, i just installed compiz fusion and got a message to run apt fix or something of the like and it did the trick, gimme a minute and i will togle through the commends i issued in terminal and find it.

sorry cant find it. i think it was something like sudo apt fix -f  but it was a couple of hours ago and i cant relly remember what it was, 

hopefully someone a bit more fluent in apt can enlighten you.

---

### Post by firmwire on 2007-07-08
> **rax_m said:**
> Hi, 

Some automatic updates came through for compiz fusion recently and since then whenever I start it I lose my window borders and title bars. Running from the terminal I get the following:

```

rmistry@rmistry-laptop:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

```


Anyone know how this could be fixed? I already have AddARGBGLXVisuals in my xorg.conf file. 

Thanks
Rax

You and several of us are having the same problem. I don't think it is an ATI or nVidia or even an AMD 64 or i386 issue. It just doesn't work. I have even tried formatting and reinstaling again and tried everything I can find.
This is definitely something I want to get working again, before I starting installing other things in the system. 

Thanks everyone all over the forum for your great info. I'm sure this will be able to be fixed. Just have to somehow get all the information in place.

---

### Post by asi594 on 2007-07-08
Also have the same problem and currently stumped

---

### Post by rax_m on 2007-07-08
Thanks for the feedback guys.. 
I did some browsing and still can't find anything. 

BTW I also have this package libcompizconfig0 that can't be updated for some reason.. not sure if that's contributing to the issue.

---

### Post by firmwire on 2007-07-08
I am not home, but I am having your issue too.

Have you tried this:

> **hyperair said:**
> Go to CompizConfig Settings Manager. In the search box, type decoration. Make sure that plugin is enabled. Also, for the command, put "emerald --replace" without quotes.

or

> **hyperair said:**
> The command to start Compiz.. Instead of using ```
compiz --replace
``` use ```
compiz --replace --use-copy
```. If you use the code that starts emerald with it, ```
compiz --replace -c emerald
``` use this instead: ```
compiz --replace --use=copy -c emerald
```.

---

### Post by asi594 on 2007-07-08
I've tried a lot of things.
I think this library might be a reason

libcompizconfig

it was recently updated, how do I go back one version with apt-get ?
force version in the package manager is disabled for it.

---

### Post by asi594 on 2007-07-08
after removing the library, and its dependency's I can run compiz with 
```

compiz --replace --use-copy

```

by removing the library I also removed compizconfig-settings-manager, wich is a bit of a bummer

---

### Post by hyperair on 2007-07-08
I reckon you're now running Compiz as opposed to Compiz Fusion, but I could be mistaken.

---

### Post by firmwire on 2007-07-08
Found this in a similiar topic:

> **blackdevil said:**
> Talked to Trevinho, and the problem is that the deb isnt updated in  the script. He is apparently working on it now and the fix should be out soon hopefully.

---

### Post by asi594 on 2007-07-08
Thanks for the info Firmwire, I hope it's about the same problem.
I found the thread, and will keep an eye on it for updates,

---

### Post by hyperair on 2007-07-08
Actually when was the post made? The update could have been over by now. I mean I never experienced such a problem and I practically update everyday.

---

### Post by firmwire on 2007-07-08
> **hyperair said:**
> Actually when was the post made? The update could have been over by now. I mean I never experienced such a problem and I practically update everyday.


It was made this morning, not too long ago.

[http://ubuntuforums.org/showthread.php?t=481615&page=25](http://ubuntuforums.org/showthread.php?t=481615&page=25)

---

### Post by asi594 on 2007-07-08
I am hoping it's the problem that blackdevil posted about.    But I still think my packages are some how screwed up, we'll see.   compiz  0.5  is working fine now, just no configuration manager for it. If i install the configmanager and that library i mentioned, then I get the error .

---

### Post by asi594 on 2007-07-08
I see compiz fusion packages have an update now,  does this solve ur problems.  I havn't tried yet, gotta do some other stuff 1st

---

### Post by hyperair on 2007-07-08
Well I've been updating rather regularly and have never faced any problems.... so..? ><

---

### Post by rax_m on 2007-07-08
hmm... I haven't received any updates yet today.. :/

---

### Post by asi594 on 2007-07-08
HI

ok as mentioned before I had this issue

```

Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706

```

I saw some updates available to the packages I was using about 2 hrs ago, I updated them now, and my problem has gone away. **yeay.** So Firmwire, I think the packages have been fixed now.

just for the record, I have the following setup in my 3rd party sources. hope it fixes ur problem.

```

http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64 (Source Code)

```

---

### Post by rax_m on 2007-07-08
i just managed to fix the issue!! 
Every time I've opened update manager recently I've been prompted to a partial upgrade which I have NOT been doing.. I decided to just try it out now, and that upgrades the libcompizconfig package and allows me to run compiz fusion with "compiz --replace"

---

### Post by firmwire on 2007-07-08
Awesome! I can't wait to get home and try it out! Thanks for the information!

---

### Post by Alex&amp;Linux on 2007-07-08
Yep, working fine now ^_^

---

### Post by hyperair on 2007-07-09
Good to hear. I wonder why it didn't have any problems on my system though.

---

### Post by BoucherieSanzot on 2007-08-27
Hello,

I just resolved the same problem, this way:

- In the **synaptic** package manager, search for *compiz*
- Find all packages installed on your system, and look in the *Versions* tab, if you have multiple versions.
- If you have multiple versions, choose which one you want to use: either the version form tuxfamily  (labeled with *3v1*) or the *ppa* versions. Choose it with *Package / Force version* (Ctrl+E shortcut).   Be sure to be consistent.
- Apply  the modifications, and just relaunch Compiz.

Voilà !

---

### Post by unca.paka on 2007-08-28
I was having a problem with Emerald not taking over decorating(no border, toolbars, etc) Went through every How-To, guide, and forum I could Google. Then I decided to install Beryl, don't ask me why, and *poof* everything worked. 

Compiz-fusion is running smoothly now, with no problem. But if I try to launch Beryl Manager, X freezes. Go figure. Could Compiz/Beryl be conflicting? Thats my guess at least.

---

