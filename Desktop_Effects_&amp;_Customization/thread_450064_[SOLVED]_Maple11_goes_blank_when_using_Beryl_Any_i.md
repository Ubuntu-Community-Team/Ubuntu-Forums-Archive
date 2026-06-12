---
title: "[SOLVED] Maple11 goes blank when using Beryl Any ideas?"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by laptoplinux on 2007-05-20
I just recently installed Maple 11 for Linux, and I noticed that if I try to start xmaple with beryl running, the application starts up but with a completely blank window.  The maple splash comes up and the startup window pops up ok, but the main window shows up completely blank.  If I switch to Metacity and run xmaple, everything goes fine, and if I switch back to beryl after xmaple has successfully started, xmaple continues to run ok.  

Although I can always just temporarily switch beryl off when starting xmaple, any ideas on what the problem might be and how I can fix it so I can keep beryl on all the time?

Thanks in advance.

---

### Post by terdon on 2007-05-21
Try ```
export AWT_TOOLKIT=MToolkit && xmaple
```

---

### Post by laptoplinux on 2007-05-21
That worked perfectly!  Thanks so much!

(I also added that export to my .bashrc for future sessions).

---

### Post by AllanJP on 2007-09-10
Hey Thanks, it works like a charm..

---

### Post by apex` on 2007-10-20
> **terdon said:**
> Try ```
export AWT_TOOLKIT=MToolkit && xmaple
```how to make shotcut on my desktop

---

### Post by terdon on 2007-10-21
Well just create a shortcut the way you normally do and then right click on the shortcut icon and edit the "command" so that it reads 
```
 export AWT_TOOLKIT=MToolkit && xmaple 
```

---

### Post by apex` on 2007-10-22
> **terdon said:**
> Well just create a shortcut the way you normally do and then right click on the shortcut icon and edit the "command" so that it reads 
```
 export AWT_TOOLKIT=MToolkit && xmaple 
```it doesnt work :( [http://img218.imageshack.us/img218/4994/screenshotow2.png](http://img218.imageshack.us/img218/4994/screenshotow2.png)

---

### Post by terdon on 2007-10-22
OK, in that case try adding an alias for xmaple to your .bashrc file:

```
gedit $HOME/.bashrc
```

add this line to the end of the file:

```
alias xmaple='export AWT_TOOLKIT=MToolkit && xmaple'
```

What this does is tell your system that whenever you type "xmaple" you actually mean "export AWT_TOOLKIT=MToolkit && xmaple".

Then create your shortcut to xmaple normaly. You probably need to log out and log back in again to make sure that .bashrc has been read.

Let me know if that didn't work.

---

### Post by terdon on 2007-10-22
By the way, are you using breezy??? If that is the case you should definately upgrade...

---

### Post by arjenzwerver on 2007-10-24
This worked really nice for me also.

Thnx!

---

### Post by apex` on 2007-10-24
I add alias, but it wont work. Im using gutsy

---

### Post by terdon on 2007-10-24
Ok, then just check if it works when run from the terminal. Open a terminal window (eg Applications => Accessories => Terminal) and type ```
xmaple
```

Does it work ok? If it does then just log out and log back in again and the shortcut should be fine.
If not, the please post the output of ```
which -a xmaple
```

PS. Make sure that your desktop shortcut is for "xmaple" and NOT "export AWT_TOOLKIT=MToolkit && xmaple"

---

### Post by apex` on 2007-10-25
> **terdon said:**
> Ok, then just check if it works when run from the terminal. Open a terminal window (eg Applications => Accessories => Terminal) and type ```
xmaple
```

Does it work ok? If it does then just log out and log back in again and the shortcut should be fine.
If not, the please post the output of ```
which -a xmaple
```

PS. Make sure that your desktop shortcut is for "xmaple" and NOT "export AWT_TOOLKIT=MToolkit && xmaple"Yes, from terminal it works, but from launcher (shortcut) not.
```
arw@arw-desktop:~$ which -a xmaple
/usr/local/bin/xmaple
```

---

### Post by terdon on 2007-10-25
OK, then try this:

1) delete the alias from your .bashrc file

2) add this line to your .bashrc file

```
 export AWT_TOOLKIT=MToolkit;
```

3) make sure your desktop shortcut command field is set to "xmaple" ONLY

4) log out then log back in and try again

---

### Post by apex` on 2007-10-25
> **terdon said:**
> OK, then try this:

1) delete the alias from your .bashrc file

2) add this line to your .bashrc file

```
 export AWT_TOOLKIT=MToolkit;
```

3) make sure your desktop shortcut command field is set to "xmaple" ONLY

4) log out then log back in and try againNope, things not get better :(

---

### Post by terdon on 2007-10-25
What error message do you get when you double click the shortcut?

---

### Post by apex` on 2007-10-25
> **terdon said:**
> What error message do you get when you double click the shortcut?

Maple runs, but window is blank (no error).

---

### Post by terdon on 2007-10-25
OK, it sounds like the export is not working. Try this:

1) run maple (from the shortcut)
2) open a terminal and type```
  echo $AWT_TOOLKIT
```
and post the output here.

Also please post the output of ```
grep export $HOME/.bashrc
```

---

### Post by apex` on 2007-10-25
```
arw@arw-desktop:~$ echo $AWT_TOOLKIT
MToolkit
arw@arw-desktop:~$ grep export $HOME/.bashrc
export HISTCONTROL=ignoredups
export HISTCONTROL=ignoreboth
export AWT_TOOLKIT=MToolkit;

```

---

### Post by terdon on 2007-10-25
Well everything seems fine... Sorry I have no idea why it won't work... :(

---

### Post by u-slayer on 2007-11-02
Thank guys! I had downloaded maple from the pirate bay and it worked great on feisty but it was giving me trouble until I found this thread. I love the terminal one liners!:)

---

### Post by apex` on 2007-11-12
i have another problem in maple i cant type bracket, equal symbol and all top digit keys dosn work

---

### Post by schlort on 2007-12-31
To get Maple to work from a launcher, do the following:

Edit (or create) a ~/.gnomerc file and add to it:

AWT_TOOLKIT=MToolkit
export AWT_TOOLKIT


Restart Gnome.
Enjoy!

---

### Post by olavjunior on 2008-02-16
> **schlort said:**
> To get Maple to work from a launcher, do the following:

Edit (or create) a ~/.gnomerc file and add to it:

AWT_TOOLKIT=MToolkit
export AWT_TOOLKIT


Restart Gnome.
Enjoy!

I got a little confused about the first suggestions, as when to restart gnome to get it to work, and cause my apple command is /home/me/.maple11/bin/xmaple. But your suggestion worked great! Thanks

---

### Post by dontcopymusic on 2008-02-18
works great! thanks!
I added export AWT_TOOLKIT=MToolkit to my .profile
login, logout, xmaple runs nice :)

---

### Post by orluar on 2008-03-21
Hi there,

but can you tell me where do I type the "export ..." command?

I typed it in the home directory but it says** "bash: xmaple: command not found"**

Sorry but I'm really new to this...

---

