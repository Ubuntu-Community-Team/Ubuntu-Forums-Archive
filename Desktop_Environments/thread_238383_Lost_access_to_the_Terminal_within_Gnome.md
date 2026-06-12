---
title: "Lost access to the Terminal within Gnome"
date: 2006-08-17
forum: Desktop Environments
---

### Post by MikeMLP on 2006-08-17
Clicking applications > accessories > Terminal makes the "starting terminal" box appear in the window list, however after several seconds, the box disappears and the gnome terminal window fails to show up.  

I have a feeling that this could be due to some updates I recently installed.  Is there a way to review recently installed/updated packages and revert back to old ones?  

If this doesn't solve the issue, is there a way I can launch the gnome terminal window from one of my virtual terminals, which might give me some error output?  I would appreciate any help that you could provide.

---

### Post by jive_turkey on 2006-08-17
Can you create a launcher on the desktop to see if the actual terminal app is corrupted? Also if you need a quick fix you could nstall a different terminal app, I suggest Eterm.

---

### Post by peabody on 2006-08-17
This is a problem related to the quinn compiz repositories.  Keep trying apt-get update, apt-get dist-upgrade from the terminal.

---

### Post by mssever on 2006-08-17
I also had the same problem. I don't know if it's a bug in the current version, or if our systems are broken somehow. You can switch to a console by typing Ctrl+Alt+F1. From there, do this:
```
sudo apt-get install gnome-terminal=2.14.2-0ubuntu1 gnome-terminal-data=2.14.2-0ubuntu1
```

This will downgrade gnome-terminal to the pre-upgrade version. I just had to do this myself.

---

### Post by MikeMLP on 2006-08-17
yep, as you have correctly guessed, I am using Quinn's repos.  Additionally, I have noticed three packages that don't seem to exist on the server, even though synaptic tells me they've been updated.  See my post here: [http://www.compiz.net/topic-3154-missing-packages]("http://www.compiz.net/topic-3154-missing-packages")

@ mssever, I'm going to try that right now, and I'll get right back to all of you to say if it worked or not.  

Thanks for the help!

---

### Post by MikeMLP on 2006-08-17
I get this:
```
E: Version '2.14.2-0ubuntu1' for 'gnome-terminal' was not found
```

although it could be a typographical error, since copy-paste doesn't work between screen 0 (ctrl+alt+F7) and virtual terminal 1 (ctrl+alt+F1).  I'll try installing an alternate gui terminal as was previously suggested to eliminate the possibility of any such error.

---

### Post by peabody on 2006-08-17
> **MikeMLP said:**
> yep, as you have correctly guessed, I am using Quinn's repos.  Additionally, I have noticed three packages that don't seem to exist on the server, even though synaptic tells me they've been updated.  See my post here: [http://www.compiz.net/topic-3154-missing-packages]("http://www.compiz.net/topic-3154-missing-packages")

@ mssever, I'm going to try that right now, and I'll get right back to all of you to say if it worked or not.  

Thanks for the help!

The font problems some people have been experiencing are also related to this.  I think the quinn repos are in the middle of updating their repository.

---

### Post by MikeMLP on 2006-08-17
again, @ msserver, I got Eterm running, and did a straight copy-paste, same error, so I guess something is missing right now.  With respect to the fonts... I may have gotten those packages, because my fonts are looking quite nice right now, as good as windows cleartype, if not better, so that was a godsend :)

---

### Post by mssever on 2006-08-17
> **MikeMLP said:**
> again, @ mssever, I got Eterm running, and did a straight copy-paste, same error, so I guess something is missing right now.

Hmmm...I copied and pasted the command from the one that I used successfully.

After reading your post on the Compiz forum, I think the error is related to compiz. If you run gnome-terminal from another terminal program, I think you'll see some relevant error messages.

---

### Post by compwiz18 on 2006-08-17
Hi all,

We just solved this problem over in a different thread: [http://ubuntuforums.org/showthread.php?t=238226](http://ubuntuforums.org/showthread.php?t=238226)

Hope that's helpful...

---

### Post by MikeMLP on 2006-08-17
Yes, that definitely proves it is related to the compiz packages:

```
mike@Ubuntu:~$ gnome-terminal
gnome-terminal: symbol lookup error: gnome-terminal: undefined symbol: vte_terminal_set_opacity

```

---

### Post by MikeMLP on 2006-08-17
...And I just saw your post, thanks for the cross-topic post, this just proves the power of the forums... Still have to try the fix, but I'm sure it will work. Again, thanks to all who replied.

---

### Post by Uncle Spellbinder on 2006-08-17
Perhaps I never had a Synaptic or Terminal problem because I probably overdid my Compiz repo: :mrgreen: 

```
## Compiz
deb http://www.beerorkid.com/compiz dapper main aiglx
deb-src http://www.beerorkid.com/compiz dapper main aiglx
deb http://xgl.compiz.info/ dapper main aiglx
deb-src http://xgl.compiz.info/ dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
deb-src http://ubuntu.compiz.net/ dapper main aiglx
```

---

