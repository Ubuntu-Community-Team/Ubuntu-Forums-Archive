---
title: "KDE - Konsole Transparency"
date: 2006-07-10
forum: Desktop Environments
---

### Post by chris_pmf on 2006-07-10
Hello,

since my upgrade to Dapper, KDE's Konsole won't save changes and display transparency only in the first Konsole tab.

How can I fix this? :(

Thanks

---

### Post by ElijahLofgren on 2006-07-10
> **chris_pmf said:**
> 
since my upgrade to Dapper, KDE's Konsole won't save changes and display transparency only in the first Konsole tab.

How can I fix this? :(

This works for me:
[LIST=1]
[*]In the menu click "**Settings -> Schema -> Transparent Konsole**"
[*]In the menu click "**Settings -> Save as Default**"
[/LIST]

Hope this helps. ;)

---

### Post by chris_pmf on 2006-07-10
Thats the problem ... this only works for the first **tab** in konsole but not in new tabs.

---

### Post by ElijahLofgren on 2006-07-10
> **chris_pmf said:**
> Thats the problem ... this only works for the first **tab** in konsole but not in new tabs.

Hmm.. Maybe you could try deleting the Konsole config file and then re-trying the steps above:
```

rm ~/.kde/share/config/konsolerc

```

Or it could be that was fixed in KDE 3.5.3. I'm running KDE 3.5.3
Info about upgrading to it is here:
[http://kubuntu.org/announcements/kde-353.php](http://kubuntu.org/announcements/kde-353.php)

---

### Post by chris_pmf on 2006-07-10
won't work too :(

The funny part about this is, even if I delete the file and then reopen Konsole to select an schema nothing happens (except that the colors changes).
The transparency isn't visible bevore I restart Konsole :confused:

PS: sry I forgot to mention I already use KDE 3.5.3 with all other updates installed

---

### Post by ElijahLofgren on 2006-07-10
> **chris_pmf said:**
> won't work too :(

The funny part about this is, even if I delete the file and then reopen Konsole to select an schema nothing happens (except that the colors changes).
The transparency isn't visible bevore I restart Konsole :confused:

PS: sry I forgot to mention I already use KDE 3.5.3 with all other updates installed

Sorry, I'm out of ideas. :| 

Maybe someone else has some?

---

### Post by chris_pmf on 2006-07-11
please anybody :confused:

---

### Post by peibol on 2006-09-01
I'm having this exact problem :confused:. I can confirm it extends to yakuake (i've compiled it from kde-look)
Any idea would be greatly appreciated.

Regards

---

### Post by chris_pmf on 2006-09-01
Oh, sorry I forgot about this thread...

I just removed the package **scim-qtimm**, as you can read in an reply to my [bug-report]("https://launchpad.net/bugs/52999") in launchpad.

---

### Post by peibol on 2006-09-01
:DThanks a lot:D, i wonder how did you get to find out...

---

### Post by chris_pmf on 2006-09-01
Wasn't really me, as you can see in the bug-report.

---

