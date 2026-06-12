---
title: "Missing bar - File Edit Veiw etc"
date: 2009-03-31
forum: Desktop Environments
---

### Post by zami on 2009-03-31
Somehow, I've lost one of the "bars" that should be at the top of most programs.

Not the title bar - I have that, and I have the bar with "New Open Save" and so forth.  I'm missing the bar that goes between, that usually has "File Edit View Tools Help" etc.

It's missing from Gedit, Evolution, and any folder - or you could say it's missing from Nautilus I guess.  It's there in Firefox, and OpenOffice...  I honestly don't remember if it's usually there in other programs.  (It seems it's missing from gnome-native applications only?)

So! Any clue how I can get it back?

Even just knowing the name of that bar would be very helpful!  It's hard to search for how to fix it when I don't know what "it" is.

Thanks for any help!

-zami

Edit:
Forgot some important points!  I'm using Gnome, and some vanilla Gnome theme and options etc (Clearlooks I think).

---

### Post by zami on 2009-04-02
Shameless bump. 

Still missing said bar.  Any ideas?

Thanks!

-zami

---

### Post by kanikilu on 2009-04-02
I don't know of any way to disable the menu bar without installing something like the "globalmenu", but that doesn't sound like the case here.

When you are in gedit, for example, does anything happen if you press F10? By default that's the key to open the menu.

// Edit - Oh, and I think it's referred to as menubar or gtkmenubar (the former is used in gconf-editor > /desktop/gnome/interface)

// Edit2 - Also, try starting gedit from a terminal and watch for output, any errors should show up there and might help point you in the right direction...

---

### Post by zami on 2009-04-02
Kanikilu, it WAS the global menu applet!!

I'd completely forgotten I'd installed it (as it crashed twice and then I never used it and forgot about it).

```

sudo apt-get remove gnome-globalmenu

```

fixed me right up.

THANK YOU for the memory jog!!

I love when when a fix is simple, and takes nothing more than a coconut hitting me in the head.  :)

Thank!

-zami

---

### Post by kanikilu on 2009-04-02
Heh, no problem ;) I was thinking about trying that out on my netbook to save some screen real estate, but I might hold off until it's more stable...

---

### Post by DaniFilth on 2009-04-03
Man, i had this problem and you saved me from reinstalling everything again, thanx for solving this issue.

---

### Post by Glendon on 2009-04-28
I had this problem as well.

I setup Gnome to look like MacOSX last month and today decided I didn't like it. 

This was the last step I couldn't figure out. 

Thanks.

---

