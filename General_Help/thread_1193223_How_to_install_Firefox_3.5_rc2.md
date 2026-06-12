---
title: "How to install Firefox 3.5 rc2?"
date: 2009-06-21
forum: General Help
---

### Post by nepenthe on 2009-06-21
Sorry for the noobish question, but how would I go about installing Firefox 3.5 rc2?

---

### Post by drs305 on 2009-06-21
Here is one way. The usual caution about using unofficial repositories...

Add this repository to Synaptic or Software Sources > Settings > Repositories > Third Party > Add:
> 
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main

Change *jaunty* to your version if different.

Add the key and update the repositories:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C713DA6
sudo apt-get update

```
If you get a different key code than above, substitute it.

Upgrade to Firefox 3.5 rc:
```

sudo apt-get update

```

---

### Post by paperplate9 on 2009-06-21
[http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html) if you *just* want to do Firefox.

---

### Post by aysiu on 2009-06-21
Here's yet another way - it keeps the Mozilla version installed as completely separate from the Ubuntu version, so you can launch either one, and they will both share the same plugins (Flash, Java, etc.):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by elamericano on 2009-06-22
*"it keeps the Mozilla version installed as completely separate from the Ubuntu version"*

There's a non-Mozilla version of Firefox??

Maybe "Mozilla version" isn't the best term, since they're all Mozilla versions.

---

### Post by Soul-Sing on 2009-06-22
> **elamericano said:**
> *"it keeps the Mozilla version installed as completely separate from the Ubuntu version"*

There's a non-Mozilla version of Firefox??

Maybe "Mozilla version" isn't the best term, since they're all Mozilla versions.

Keeps the rc version seperate from the regular version. And that linkage is great. I pefer that seperate setting...+1

---

### Post by StuM on 2009-06-22
I too didn't realise there was 'Mozilla' and 'Ubuntu' version of Firefox.

I don't really fancy running two different versions of Firefox.  What is the latest 'Ubuntu' version available? RC 1, or a 3.5 beta build perhaps?  If these are available, where can I install them from so that they overwrite my existing Firefox 3.0.11?

---

### Post by t0p on 2009-06-22
> **StuM said:**
> I too didn't realise there was 'Mozilla' and 'Ubuntu' version of Firefox.

I don't really fancy running two different versions of Firefox.  What is the latest 'Ubuntu' version available? RC 1, or a 3.5 beta build perhaps?  If these are available, where can I install them from so that they overwrite my existing Firefox 3.0.11?

The current "Ubuntu" Firefox is the one that's in Jaunty now.  They're all by Mozilla.

---

### Post by KhaaL on 2009-06-22
trying to install firefox 3.5 from that PPA errors with:

firefox-3.5:
  Depends: xulrunner-1.9.1 (>=1.9.1~rc2) but 1.9.1~hg20090620r26001+nobinonly-0ubuntu1~umd1~jaunty is to be installed

---

### Post by steveneddy on 2009-06-22
> **KhaaL said:**
> trying to install firefox 3.5 from that PPA errors with:

firefox-3.5:
  Depends: xulrunner-1.9.1 (>=1.9.1~rc2) but 1.9.1~hg20090620r26001+nobinonly-0ubuntu1~umd1~jaunty is to be installed

I'm getting that but with Hardy. I hope that they get this fixed soon.

---

### Post by Soul-Sing on 2009-06-22
There is no xulrunner "broken" or in synaptic package manager available?

---

### Post by Soul-Sing on 2009-06-22
There is no xulrunner 1.9.1 "broken" or in synaptic package manager available?

---

### Post by KhaaL on 2009-06-23
> **leoquant said:**
> There is no xulrunner 1.9.1 "broken" or in synaptic package manager available?

No. I tried investigating this further and noticed that i have two versions of xulrunner 1.9.1 from jaunty repo (1.9.1~b4~hg20090330r24021+nobinonly-0ubuntu1) and from that ppa (1.9.1~hg20090620r26001+nobinonly-0ubuntu1~umd1~jaunty).

Could this have something to do with the installation problems?

---

### Post by Soul-Sing on 2009-06-23
> **KhaaL said:**
> No. I tried investigating this further and noticed that i have two versions of xulrunner 1.9.1 from jaunty repo (1.9.1~b4~hg20090330r24021+nobinonly-0ubuntu1) and from that ppa (1.9.1~hg20090620r26001+nobinonly-0ubuntu1~umd1~jaunty).

Could this have something to do with the installation problems?

Could be...

---

### Post by lovinglinux on 2009-06-24
There is another option. You can install Swiftfox from it's [own repository](http://getswiftfox.com/deb.htm). Swiftfox uses the most recent version of Firefox and it is installed side-by-side with it. Nevertheless, it uses the same profiles as Firefox.

---

### Post by michy99 on 2009-06-24
firefox-3.5 is in the repository.

---

### Post by lovinglinux on 2009-06-24
> **michy99 said:**
> firefox-3.5 is in the repository.

The version on the repository is 3.5beta4pre

---

### Post by susanpenter on 2009-06-25
I used this method but although it says Swiftfox is 3.5 it actually opened as another version of 3.0.11!

---

### Post by lovinglinux on 2009-06-25
> **susanpenter said:**
> I used this method but although it says Swiftfox is 3.5 it actually opened as another version of 3.0.11!

Don't open it simultaneously with Firefox.

---

### Post by KhaaL on 2009-06-25
> **lovinglinux said:**
> There is another option. You can install Swiftfox from it's [own repository](http://getswiftfox.com/deb.htm). Swiftfox uses the most recent version of Firefox and it is installed side-by-side with it. Nevertheless, it uses the same profiles as Firefox.

Thanks btw, that worked well!

---

### Post by susanpenter on 2009-06-25
> **lovinglinux said:**
> Don't open it simultaneously with Firefox.

OK don't I feel daft! It works absolutely fine now, many thanks

---

### Post by Footer on 2009-06-26
> **StuM said:**
> I too didn't realise there was 'Mozilla' and 'Ubuntu' version of Firefox.

I don't really fancy running two different versions of Firefox.  What is the latest 'Ubuntu' version available? RC 1, or a 3.5 beta build perhaps?  If these are available, where can I install them from so that they overwrite my existing Firefox 3.0.11?

I didn't see that anyone answered this question yet.  I'd like to do the same thing, overwrite Firefox 3.0.11 with 3.5 RC(latest).  Is that possible?  I don't want to run two versions either.  Been there, done that.

Thanks!

---

### Post by Footer on 2009-06-26
Perhaps I've answered the question.  I just installed Firefox 3.5 from the repositories.  It's up to b4 the way it looks (Help --> About says version 3.5b4pre -- Shiretoko? -- see attached).

Anyway, it preserved the 3.0.11 version so I have both installed.  Probably as simple now as removing 3.0.11 and then I'll only have one installation?  It did take all the settings (bookmarks, compatible add-ons, etc.) from the 3.0.11 installation so it looks like my 3.5b4pre is all set, and will be updated from the repos as more RCs come out.

Only question remaining is when 3.5 goes final, will this 3.5.b4pre installation be replaced with 3.5?

Thanks!

---

### Post by lovinglinux on 2009-06-26
> **Footer said:**
> looks like my 3.5b4pre is all set, and will be updated from the repos as more RCs come out.

Only question remaining is when 3.5 goes final, will this 3.5.b4pre installation be replaced with 3.5?

Thanks!

I wouldn't count on that. I don't think they will update the b4pre version to RC or final.

---

### Post by Footer on 2009-06-26
> **lovinglinux said:**
> I wouldn't count on that. I don't think they will update the b4pre version to RC or final.

OK, now I'm confused.  Are you saying that b4pre is not an RC?

---

### Post by lovinglinux on 2009-06-26
> **Footer said:**
> OK, now I'm confused.  Are you saying that b4pre is not an RC?


b4pre = BETA 4 PRE
RC = RELEASE CANDIDATE

[http://en.wikipedia.org/wiki/Beta_version#Beta](http://en.wikipedia.org/wiki/Beta_version#Beta)
[http://en.wikipedia.org/wiki/Beta_version#Release_candidate](http://en.wikipedia.org/wiki/Beta_version#Release_candidate)

---

### Post by Footer on 2009-06-26
> **lovinglinux said:**
> b4pre = BETA 4 PRE
RC = RELEASE CANDIDATE

[http://en.wikipedia.org/wiki/Beta_version#Beta](http://en.wikipedia.org/wiki/Beta_version#Beta)
[http://en.wikipedia.org/wiki/Beta_version#Release_candidate](http://en.wikipedia.org/wiki/Beta_version#Release_candidate)

Ahh, ok, thanks for the clarification & links.  I do know the diff. between beta and release candidate, just didn't put 2 & 2 together from the help --> about.

And from your previous reply, I guess we shouldn't expect an RC in the repositories.  Oh well.

:)

---

### Post by lovinglinux on 2009-06-26
> **Footer said:**
> Ahh, ok, thanks for the clarification & links.  I do know the diff. between beta and release candidate, just didn't put 2 & 2 together from the help --> about.

And from your previous reply, I guess we shouldn't expect an RC in the repositories.  Oh well.

:)

You are welcome. Unfortunately, it seems it won't get into Jaunty repositories. I wish they update Firefox 3.0.11 to 3.5 final, but this probably ain't going to happen either.

---

### Post by Footer on 2009-06-26
> **lovinglinux said:**
> You are welcome. Unfortunately, it seems it won't get into Jaunty repositories. I wish they update Firefox 3.0.11 to 3.5 final, but this probably ain't going to happen either.

I guess it's Swiftfox or bust for RCs at this point!

Thanks.

---

### Post by l-x-l on 2009-06-26
I just installed 3.5 now & so far it's great. It handles memory a lot better. So far it's not the memory hog I remember.

I tried swiftfox but couldn't get any of the plugins to work.

---

### Post by Kirk M on 2009-06-27
> **lovinglinux said:**
> You are welcome. Unfortunately, it seems it won't get into Jaunty repositories. I wish they update Firefox 3.0.11 to 3.5 final, but this probably ain't going to happen either.

Since when hasn't Ubuntu always updated Firefox to the latest version? :P Since Firefox has been updated to the latest version all along then it stands to reason that when 3.5 final (this coming Tuesday, June 30th they say) is released then Firefox will be updated appropriately.

---

### Post by aysiu on 2009-06-27
> **Kirk M said:**
> Since when hasn't Ubuntu always updated Firefox to the latest version? Since Warty Warthog. Firefox gets updated every six months with a new release of Ubuntu. Patches are installed along the way for security issues.

---

### Post by Kirk M on 2009-06-27
> **aysiu said:**
> Since Warty Warthog. Firefox gets updated every six months with a new release of Ubuntu. Patches are installed along the way for security issues.

Well, you learn something new everyday. It'll be interesting to see what happens come next week then.

---

### Post by stinger30au on 2009-06-27
> **aysiu said:**
> Since Warty Warthog. Firefox gets updated every six months with a new release of Ubuntu. Patches are installed along the way for security issues.

very true, Ubuntu is *NOT* a rolling release distro

---

### Post by lovinglinux on 2009-06-28
> **Kirk M said:**
> Since when hasn't Ubuntu always updated Firefox to the latest version? :P 

Firefox is updated from 3.0.x to 3.0.y, not from 3.0.x to 3.w.z.

---

### Post by Alcareru on 2009-06-28
**Back to original topic... my way of "installing" this sort of things:**

P.S.
Note:
After revising this post a couple of times before and after :) posting I'm not 100% sure if all the commands work by just copy-pasting. The idea is that they should work by just copypasting what ever is in the code fields to shell and pressing enter. If you encounter any problems pm me (preferably) or write to this thread (which I might not follow that intensively).

This is the premilinary step for the installation, if you close the terminal or use another terminals (sessions) for some reason during the installation process, you need to set these variables again. Make sure the Tarball and InstallationPath have correct values.
```

Tarball="firefox-3.5rc3.tar.bz2"
InstallPath="/where/ever/you/want/to/install/"
Version=${Tarball/firefox-/} Version=${Version/.tar.bz2/}

```
First download the tarball if you haven't already and extract it, also make sure the aforementiond variables are set and _have correct values_:
```

mkdir -p ${InstallPath} &&\
tar -jxvf ${Tarball} -C ${InstallPath}

```
It seems to be a common convention that you also remove the tarballs after extraction. To do that run:
```

rm ${Tarball}

```
Now you probably want to ease launching the application a bit so make a symbolik link or a small shell script that launches the right firefox on destkop or some apropriate system folder (/usr/bin for instance?) Something like this:

```

sudo ln -s ${InstallPath}/firefox/firefox /usr/bin/firefox${Version} &&\
echo -e "[Desktop Entry]\n\
Encoding=UTF-8\n\
Type=Application\n\
Exec=firefox${Version}\n\
Terminal=false\n\
Name=Firefox${Version}\n" > ~/Desktop/Firefox${Version}.desktop &&\
chmod u+x ~/Desktop/Firefox${Version}.desktop

```
(The last line could also be:
Name_[en_GB]_=Firefox${Version}\n" > ~/Desktop/Firefox${Version}.desktop &&\
but then if your using some other language the launcher would appear as unnamed.)


Uninstall (omit -v if you don't want the commands to print what they are doing):
```

sudo rm -v /usr/bin/firefox${Version} &&\
rm -v ~/Desktop/Firefox${Version}.desktop &&\
rm -rfv ${InstallPath}/firefox &&\
rmdir ${InstallPath} #This will fail if the dir is not empty so don't worry about it.

```

If you only use the new firefox by launching it from desktop (not from terminal or from scripts, or anything) you could do it like this:
```

echo -e "[Desktop Entry]\n\
Encoding=UTF-8\n\
Type=Application\n\
Exec=${InstallPath}/firefox/firefox${Version}
Terminal=false\n\
Name=Firefox${Version}\n" > ~/Desktop/Firefox${Version}.desktop &&\
chmod u+x ~/Desktop/Firefox${Version}.desktop

```

Now the good thing about this is that you don't touch any of you system folders, so uninstalling is as easy as removing one launcher from desktop and deleting the application files.
Uninstall:
```

rm -v ~/Desktop/Firefox${Version}.desktop &&\
rm -rfv ${InstallPath}/firefox &&\
rmdir ${InstallPath} #This will fail if the dir is not empty so don't worry about it.

```

If you don't feel like using those launchers, just make a trivila script that calls the app:
```

echo -e '#!/bin/sh'"\n\
${InstallPath}/firefox/firefox\n\
exit "'$?\n' > ~/Desktop/Firefox${Version}.sh &&\
chmod u+x ~/Desktop/Firefox${Version}.sh

```
Uninstall:
```

rm -v ~/Desktop/Firefox${Version}.sh &&\
rm -rfv ${InstallPath}/firefox &&\
rmdir ${InstallPath} #This will fail if the dir is not empty so don't worry about it.

```

or symbolic link:
```

ln -s ${InstallPath}/firefox ~/Desktop/Firefox${Version}

```
Uninstall:
```

rm -v ~/Desktop/Firefox${Version} &&\
rm -rfv ${InstallPath}/firefox &&\
rmdir ${InstallPath} #This will fail if the dir is not empty so don't worry about it.

```

 or use full path from terminal :)

**Additional notes:**
You may want to backup your old settings by executing:
```

cp -rv ~/.mozilla ~/.mozilla.backup

```
or equivalent..
and if something goes wrong with your settings, then just:
```

cp -rfv ~/.mozilla.backup ~/.mozilla

```
(this leaves any files added after making the backup inplace, but if it's one of them that's broken or they are incompatible with files from mozilla.backup then of course this won't help much)

or to make it absolutely sure there's nothing fishy at ~/.mozilla
```

rm -rfv ~/Desktop/Firefox${Version} &&\
cp -rv ~/.mozilla.backup ~/.mozilla

```
(first clear all current settings and then copy the backups, sholud work always, but you might lose unnecessarily all changes to your settings after backup)

Also note that if your browsing the web with firefox 3.0 or what ever and you try to start a new firefox instance of firefox 3.5, you'll end up having just another firefox 3.0 browser window opened. So before running firefox 3.5 you must close all older firefox browser windows.

---

### Post by aysiu on 2009-06-28
Alcareru, what's the difference between that approach and the one in my link?
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by Alcareru on 2009-06-29
> **aysiu said:**
> Alcareru, what's the difference between that approach and the one in my link?
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
Well, it depends. There's quite a few ways to do it in my post. None of them does this:
```

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

```
The core idea was that /usr/bin/firefox is not to be touched. Sure, it's not that difficult to modify the tutorial you provided and end up with something like these, but now I've done the job for everybody so even the most recent linux noob will be able to install it this way.

Bottom line: So if you do it my way after installation running from terminal, firefox will start firefox 3.0 (or which ever version you had previously installed), but running firefox3.5rc3 (if you took the first route) will start the new version.

---

### Post by aysiu on 2009-06-29
> **Alcareru said:**
> Well, it depends. There's quite a few ways to do it in my post. None of them does this:
```

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

```
The core idea was that /usr/bin/firefox is not to be touched. Sure, it's not that difficult to modify the tutorial you provided and end up with something like these, but now I've done the job for everybody so even the most recent linux noob will be able to install it this way.

Bottom line: So if you do it my way after installation running from terminal, firefox will start firefox 3.0 (or which ever version you had previously installed), but running firefox3.5rc3 (if you took the first route) will start the new version.
But those are just details.

It's essentially the same approach. You're "installing" the Mozilla Firefox to its own location with its own launcher and keeping the Ubuntu Firefox installed with its own launcher.

With the commands I linked to, *firefox* will launch the newer Firefox (the one from Mozilla's website) and *firefox.ubuntu* will launch the older Firefox (the one from the Ubuntu repositories).

I'm not trying to say one approach is better than the other. In fact, I kind of see them as essentially the same for a new user (copy and paste these commands, you have two separate launchers for the two Firefoxes installed). So I guess I'm wondering why a new user would want to copy and paste more commands instead of copying and pasting fewer commands.

---

### Post by Alcareru on 2009-07-01
> **aysiu said:**
> But those are just details.

It's essentially the same approach. You're "installing" the Mozilla Firefox to its own location with its own launcher and keeping the Ubuntu Firefox installed with its own launcher.

With the commands I linked to, *firefox* will launch the newer Firefox (the one from Mozilla's website) and *firefox.ubuntu* will launch the older Firefox (the one from the Ubuntu repositories).

I'm not trying to say one approach is better than the other. In fact, I kind of see them as essentially the same for a new user (copy and paste these commands, you have two separate launchers for the two Firefoxes installed). So I guess I'm wondering why a new user would want to copy and paste more commands instead of copying and pasting fewer commands.
Well, yes it is very alike. It was my exploration to the topic of how could this thing be achieved. Is it just details? Maybe so, but that's the point. To give a bit of a choice for the details so even a noob has choices. And detail or not, the spirit is different. In your tutorial the idea is to update to new firefox, but leave the old one installed in case one wants to explicitly use it. In mine the idea is to install some unstable version temporarily (for untill it becomes stable release) so that it's easily accessible, but changes as little as possible in the system.

And as you say why would someone want to execute more commands, well. How many more commands there really is? 1 if you count setting 3 variables as a command, 2 if I add this line
```

sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins

```
to my version, then I have the command for making symlin, applauncher, script on the desktop. Also I have chainged all commands on any code section so that you can copy paste them all in an single operation to the terminal and press enter be done with it. In your version you have to copypaste and press enter separately for 7 commands. On mine you do:
1. set variables
2. untar
(optionally remove the tar)
3. install
= 3 or 4 copypastes and enters. Sounds like a less of hassel for a newb, right?

But anyways, as I said it's just my way and if someone else finds it usefull, that's just super, if not, well I don't mind. In any case, I hope I have given good enough reasons to justifying writing that tutorial. It will be unlikely that I'd be giving any more of those... :)

---

### Post by aysiu on 2009-07-01
Actually, the commands in the link I gave can all be copied and pasted as one set. They do not need to be copied and pasted individually.

So really it's just one copy and paste if you want.

There's really no harm in having other methods, I suppose. I just don't want people getting confused, and your instructions confused me, frankly.

---

### Post by Alcareru on 2009-07-04
> **aysiu said:**
> Actually, the commands in the link I gave can all be copied and pasted as one set. They do not need to be copied and pasted individually.

So really it's just one copy and paste if you want.

Oh, yes. Hmm.. now how the hell I had came up with the idea that they couldn't, I wonder..? Anyways I think chaining is better for most part because then if one command fails the rest went be executed.

> 
There's really no harm in having other methods, I suppose. I just don't want people getting confused, and your instructions confused me, frankly.

Well it's a good thing their on the page 4 then isn't it? :D Noon will ever find it..

---

### Post by adam_ski on 2009-07-21
> **aysiu said:**
> Here's yet another way - it keeps the Mozilla version installed as completely separate from the Ubuntu version, so you can launch either one, and they will both share the same plugins (Flash, Java, etc.):
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Worked a treat for me. Many thanks.

---

