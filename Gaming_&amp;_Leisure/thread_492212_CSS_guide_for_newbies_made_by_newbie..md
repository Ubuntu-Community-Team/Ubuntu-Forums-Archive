---
title: "CSS guide for newbies made by newbie."
date: 2007-07-04
forum: Gaming &amp; Leisure
---

### Post by Haz13r on 2007-07-04
Haha, i am a newbie at this but although i am a newbie, i was able to figure out how to get Counter Strike Source working.

The most effective way i did it was install it straight from steam which i had gotten from this website:  [http://halflife2.filefront.com/file/Steam_installer;27442](http://halflife2.filefront.com/file/Steam_installer;27442)

Then open it up with Wine.

When installing it, you cant see anything it says am i correct? Well i got the Tahoma Font from this website:  [http://fonts.appliedlanguage.com/tahoma_font.shtml](http://fonts.appliedlanguage.com/tahoma_font.shtml)

Now what i did next was drag the Tahoma Font into home/<username>/.wine/drive_c/windows/fonts.

For those who do not know how to view hidden folders, on the top there is a TAB called View.  Click it and scroll down to Show Hidden Files.  Or just press CTRL+H.

Now you will be able to see everything.  Now install Counter Strike.

Although if you have the CDs, which i do as well, i wanted to do this because its less complicated.  And im just lazy.

---

### Post by threeonethree on 2007-07-04
what about the microsoft visual c++ library error that i get? . ihave wine 9.40

---

### Post by Haz13r on 2007-07-04
I dunno about that, Im still new at this.  I didnt get any errors during this process.  sorry, but try and send a new thread.

---

### Post by ubu-for on 2007-07-04
> **threeonethree said:**
> what about the microsoft visual c++ library error that i get? . ihave wine 9.40

How do you launch CSS?

1. Step
```
cd ~/.wine/drive_c/Programs/Steam
```

2. Step
```
WINEDEBUG=-all wine steam -applaunch 240 -fullscreen -heapsize 524288
```

Look at [this](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games#cli) HOWTO.

---

### Post by threeonethree on 2007-07-25
steam?? actually my game is a pirated download from the internet :-s what steam?


runs fine on my pirated windows

---

### Post by eiskalt on 2007-07-25
This tutorial is better.

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

---

### Post by frodon on 2007-07-26
Don't forget that the first guide to look at and surely the most up to date is on the appDB, each wine user should read the coresponding appDB entry before installing any windows apps, you will gain a lot of time and surely get the best possible performances for your apps :
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

@eiskalt, you will see that the guide you linked is also linked in the CS:S appDB entry ;)

---

