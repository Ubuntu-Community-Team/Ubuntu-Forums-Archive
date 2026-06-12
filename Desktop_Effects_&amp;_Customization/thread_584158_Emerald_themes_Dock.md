---
title: "Emerald themes? Dock?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by spyker3292 on 2007-10-20
So I finally got compiz-fusion running and I would like to know how to install emerald themes and a mac OSXish dock of some sort.

Thanks!

---

### Post by divague on 2007-10-20
i use avant window navigator that looks like the mac os x dock, this is the how-to i followed
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by Tachyon1000 on 2007-10-20
Install emerald via Synaptic.  Go into the Emerald Manager in the system menu and follow instructions for getting non-GPL themes or go here to get themes ( [http://themes.beryl-project.org/](http://themes.beryl-project.org/) ).

---

### Post by overlord.gaurav on 2007-10-20
If you have already installed Emerald then go to System>>Preference>>Emerald Theme Manager.
Else, do this:
```
sudo apt-get install emerald emerald-themes
```

For the OSX like dock you can use [Avant-Window-Manager]("http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+manager") OR you can try [gDesklets]("http://ubuntuforums.org/showthread.php?t=203093")

---

### Post by spyker3292 on 2007-10-20
How do you select a theme once I have one in the emerald theme manager?

---

### Post by Bert_2 on 2007-10-21
Well, I know how emerald works, I used it all the time on feisty, but now that I have upgraded to gutsy it seems like I can't get the themes to appear in the emerald theme manager. Also, the package emerald-themes isn't in the repository yet :S :?

---

### Post by OysteinAndersen on 2007-10-21
It seems that emerald themes not installed by default. I did this to go solve the problem
[LIST]
[*]Install svn "sudo apt-get install subversion"
[*]Get the themes "svn export https://svn.generation.no/emerald-themes"
[*]Import them in emerald , make sure you have choose one theme before you close.
[*]Change compiz to use emerald "<ALT>+<F2> and then print **compiz --replace emerald**"
[/LIST]

Its working, and enjoy this super cool feature!

---

### Post by vector9 on 2007-10-21
i tried this but i have no title bars now
what did i do wrong
i did exactly as you said

---

### Post by ReloadedFusion on 2007-10-21
Hi vector9

Check out my post on this thread:

[http://ubuntuforums.org/showthread.php?t=583919](http://ubuntuforums.org/showthread.php?t=583919)

It should help with your no borders problem

Hope it helps

---

### Post by vector9 on 2007-10-21
thank you it works now

---

