---
title: "Firefox Broke..."
date: 2005-12-24
forum: Desktop Environments
---

### Post by UltraSonicSite on 2005-12-24
edit

---

### Post by NewbieNik on 2005-12-24
[QUOTE=UltraSonicSite]

So eh, I kinda screwed up didnt I?[/QUOTE]

In a word, Yes.....


I would try using the terminal and run a:-

sudo apt-get -f install

to try and fix it. If it still doesn't work then add and remove by:-

sudo apt-get remove firefox

answer "yes" to the 6 packages to be removed then reverse the command and re-install it:-

sudo at-get install firefox

And keep your fingers crossed!!!!

---

### Post by Fearan on 2005-12-24
> sudo at-get install firefox
don't you mean 
```
sudo apt-get install firefox
```? just a thought.

---

### Post by NewbieNik on 2005-12-24
[QUOTE=Fearan]don't you mean 
```
sudo apt-get install firefox
```? just a thought.[/QUOTE]


Yes, but my dodgy Packard-Bell Laptop has a dodgy Packard-Bell Keyboard and sometimes doent typ the kys I ht!!!

Ars, its bggerd up agin

---

### Post by UltraSonicSite on 2005-12-25
Didn't work. Same thing pops up, right now I'm download Ubuntu-Desktop (again) Kubuntu, and Edubuntu.

Hopefully installing these three wont do anything wierd, but if it does, you have about 8 minutes to tell me before it starts configuring..

---

### Post by towsonu2003 on 2005-12-25
on terminal ```
firefox --safe-mode
```

---

### Post by briancurtin on 2005-12-25
what do you want edubuntu for? are you 6 years old?

---

### Post by UltraSonicSite on 2005-12-25
I see, well, Maybe I can let my sister use it? I dunno =P

Although it seems obvious your being sarcastic, it would be kind of wierd to have a 6 year old complaining about how his configuration disallowed him to use firefox, knowing that it came built into ubuntu. Unless i'm some sort of non-american smart child or something. =P

That would be neat, i'm gonna try the safe mode thing

---

### Post by UltraSonicSite on 2005-12-25
Lol nope, same screen...this is starting to displease me.

I'm gonna go try these new desktops, if you dont hear from me within 3 minutes, then my computer died.

---

### Post by towsonu2003 on 2005-12-25
//edit// sorry - see next post [http://www.mozilla.org/support/firefox/profile](http://www.mozilla.org/support/firefox/profile)

---

### Post by towsonu2003 on 2005-12-25
lol

try this one ```
mv .mozilla .mozilla_backupnew
firefox --safe-mode
```

-> any luck?

---

### Post by UltraSonicSite on 2005-12-25
Alright, my computer didnt die, but now it says edubuntu at login =P

Let me try the 2 suggestions you guys did.

---

### Post by UltraSonicSite on 2005-12-25
Alright guys I fixed it, I made a new profile =P

and now I got 1.5

Thanks for your support, I'll put the fix on the first post.

---

### Post by UltraSonicSite on 2005-12-25
Oh one last thing, (sorry for triple) How do I make it load that profile every time =P

cause now If i load it through the shortcut, I still get the error, but if I run it with the profile manager then it works just fine.

---

### Post by UltraSonicSite on 2005-12-26
Still need some help =P

---

### Post by towsonu2003 on 2005-12-27
Note that if you did what I described in post#11, this should not happen. Because we moved the profile althoghether using ```
mv .mozilla .mozilla_backupnew
```

Anyway, I'm looking at here while writing this: [http://www.mozilla.org/support/firefox/profile#new](http://www.mozilla.org/support/firefox/profile#new)

Preparation:
```
cp ~/.mozilla/fiirefox/profile.ini ~/.mozilla/fiirefox/profileini.backup
ls ~/.mozilla/firefox/
```
two folders that look weird in the output (<too many numbers and letters>.default) are profiles. one was your old profile, one is the new one... 

1 Open up profiles.ini in a text editor. The file is located in the application data folder for Firefox:

    * On Linux, the path is ~/.mozilla/firefox/

In there, you'll see something like > [General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=**503guxm5.default**
Default=1

[Profile1]
Name=oldprofile
IsRelative=1
Path=**ct586uq1.default**


In this example, change the places of these two: 503guxm5.default ct586uq1.default --note that names will be different in your case... find them from your ls output. 

2 Save profiles.ini and restart Firefox.

I'm pretty sure there is an easier way, but I just went with the one I used :) good luck.

---

### Post by UltraSonicSite on 2005-12-27
lol I only have ONE.
```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=e86ev359.default

```

---

### Post by towsonu2003 on 2005-12-27
ehueh

I would just do this and it should fix the problems at once: ```
mv ~/.mozilla ~/.mozilla_back2
firefox
```

Please make sure ```
mv ~/.mozilla ~/.mozilla_back2
``` does not give any errors. 

This has to fix it because, once you launch it, firefox will recreate everything from scratch (including profiles). After this, you can import your bookmarks from /home/<username>/.mozilla_back2/firefox/e86ev359.default/bookmarks.html using the 'Manage Bookmarks' feature in firefox (import file). 

hope this helps.

PS. <username> is your username for that machine.

---

