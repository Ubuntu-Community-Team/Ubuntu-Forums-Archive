---
title: "Seeing man pages in Firefox"
date: 2006-08-13
forum: Desktop Environments
---

### Post by jordilin on 2006-08-13
Is there a way to see man pages by means of Firefox. In konqueror is possible by typing
```
man:/<command>
```
into the url bar
Is there sth similar in Firefox?

---

### Post by Lord Illidan on 2006-08-13
Konqueror uses the KIO slaves native to KDE to do this, I think. So I don't think it would be possible to do it in FF.

---

### Post by jordilin on 2006-08-13
I want another way to see man pages instead of doing 
```
man command
```
If not in Firefox, I would like to see it in gedit or sth similar, just to be able to search through the man page comfortably.

---

### Post by kabus on 2006-08-13
Type "/" to search in man pages and 'h' for help.

---

### Post by kaamos on 2006-08-13
Yelp shows man pages, just press F1 when on desktop..

---

### Post by jordilin on 2006-08-13
> **kaamos said:**
> Yelp shows man pages, just press F1 when on desktop..

That's very nice!! but, is there a way to only search man pages. When I look for "ls" it displays lots of entries

---

### Post by ardchoille on 2006-08-13
I'm not in gnome right now, but I remember typing man:tar into the location bar of Firefox and it opened a gnome app to browse the man page of tar. Does this not work in Ubuntu's version of Firefox?

---

### Post by jordilin on 2006-08-13
> **ardchoille said:**
> I'm not in gnome right now, but I remember typing man:tar into the location bar of Firefox and it opened a gnome app to browse the man page of tar. Does this not work in Ubuntu's version of Firefox?

Yes, that works. Typing man:command in the url bar, gnome-help pops up with the man page. It's the same as typing:
```
gnome-help man:command
```
I wanted sth like this. Now searching through a man page is by far more comfortable.

---

### Post by Tomosaur on 2006-08-13
You can use a bit of bash cheating to do this:

man synaptic > syn && firefox syn && rm syn

Very easy to turn into a shell script.

---

### Post by ardchoille on 2006-08-13
> **jordilin said:**
> Yes, that works. Typing man:command in the url bar, gnome-help pops up with the man page. It's the same as typing:
```
gnome-help man:command
```
I wanted sth like this. Now searching through a man page is by far more comfortable.

That's good to know :)

---

### Post by ardchoille on 2006-08-13
> **Tomosaur said:**
> You can use a bit of bash cheating to do this:

man synaptic > syn && firefox syn && rm syn

Very easy to turn into a shell script.

Wowsers.. thank you for that info :)

---

### Post by jordilin on 2006-08-13
> **Tomosaur said:**
> You can use a bit of bash cheating to do this:

man synaptic > syn && firefox syn && rm syn

Very easy to turn into a shell script.

What does "syn" mean?

---

### Post by jordilin on 2006-08-13
> **Tomosaur said:**
> You can use a bit of bash cheating to do this:

man synaptic > syn && firefox syn && rm syn

Very easy to turn into a shell script.

It works as well doing
```
 man synaptic > syn && firefox > rm syn 
```
anybody can explain, what's going on in this script?

---

### Post by jordilin on 2006-08-13
> **jordilin said:**
> What does "syn" mean?

Well, I have discovered it. syn is just a dummy name. It works with any other name:

```
man ls > hello && firefox hello && rm hello
```

the output of man ls is redirected to hello and then firefox displays the content of hello, then hello is erased. That's the power of Linux, Great :cool:

---

### Post by Tomosaur on 2006-08-13
Yup, you got it. You can use whatever the hell you like. Be careful where you use it though, don't want to go deleting executables and whatnot :P

---

### Post by DonS on 2006-08-15
> **Tomosaur said:**
> Yup, you got it. You can use whatever the hell you like. Be careful where you use it though, don't want to go deleting executables and whatnot :P

A complete script might look something like:
```

#!/bin/sh
man $1 > /tmp/silly-script-out && firefox /tmp/silly-script-out && rm /tmp/silly-script-out

```

Save that as (say) man-view in your path somewhere (like $HOME/bin) and change its permissions to allow it to execute.  This will stop any overwriting of important files and won't fail if you run the script from somewhere you don't have permission (outside your home directory).

You can now view man pages by pressing alt-F2 and typing man-view <man-page-name>.  I think.  I'm not at my GNOME machine at the moment, so I can't check.

Alternatively, you could just open the run dialog (alt-F2) and type "man:<man-name>" and yelp will pop up with the man page.  This also works for info pages (alt-F2, "info:<info-name>").

As for searching man pages, the command "apropos <search term>" from the terminal will print a list of relavent man pages.  Yelp might gain some more (secret) functionality in future releases to only search man and info pages, but not for Edgy[1] :(

[1] Yelp has many secret functions.  We like secrets.  Try typing "man <man-page>" in the search bar in Yelp.

---

