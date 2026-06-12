---
title: "Auto Complete in terminal w/ up arrow"
date: 2008-12-29
forum: General Help
---

### Post by mikeman141 on 2008-12-29
Hey all,

I used to do a lot of work in MATLAB and it had one really nice feature in its command line.

Let's say I was doing some conversions in mencoder 2 days ago, and I have trouble remembering the syntax.  I could type in the terminal 

"menc" and then hit the up arrow.  It would autocomplete (like tab does now) but it would autocomplete from your history.  In other words, the last mencoder line that I typed 2 days ago would appear, and if I kept pressing up it would continue to scroll through the previous times that I typed "menc..."  

Anyway to get this in the terminal?  Or any better way to search my history besides exporting it to a temp file:

history > temp.txt

and searching throuhg it with gedit?

thanks

---

### Post by mikeman141 on 2008-12-30
no love?

---

### Post by sisco311 on 2008-12-30
Ctrl+r

---

### Post by dagnabit dang doohickey on 2008-12-30
```
!menc<enter>
```

Have a look at the history expansion section of the [bash man page]("http://linux.die.net/man/1/bash").

Edit: sisco311's reply is more likely what you want.

---

### Post by Slim Odds on 2008-12-30
As was mentioned, the GNOME terminal uses bash (as does most of linux).

bash maintains a history that can be searched (ctrl-r is reverse search, then start typing).

I highly recommend the Advanced Bash Scripting Guide. It's great as both a tutorial and a reference.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by sisco311 on 2008-12-30
> **mikeman141 said:**
> 

Anyway to get this in the terminal?  Or any better way to search my history besides exporting it to a temp file:

history > temp.txt

and searching throuhg it with gedit?

thanks

```
grep **mencoder** ~/.bash_history
```

---

### Post by heindsight on 2008-12-30
what you could also do is to edit /etc/inputrc:
```
gksudo gedit /etc/inputrc
```

somewhere around line 40 (on my Hardy install), you should find lines looking something like:
```

# alternate mappings for "page up" and "page down" to search the history
#"\e[5~": history-search-backward
#"\e[6~": history-search-forward

```

uncomment (ie remove the #s at the beginning of) the 2nd and 3d of these lines, save the file and exit gedit.

Now when you open a terminal you can the page up (and page down) button(s) to complete your current command by searching backwards (and forwards) in the command history.

---

### Post by dagnabit dang doohickey on 2008-12-30
Piping the output of history will display the history line number as well as the commands:
```
history | grep menc
```

---

### Post by Slim Odds on 2008-12-30
You're all making this harder than it has to be.

Ctrl-R is reverse search of the history (which is normally the way you want to do it).

Then.... just start typing...... bash matches against the history.

No need to pipe, edit, ......

When you find what you want, press Enter.

---

### Post by heindsight on 2008-12-30
> **Slim Odds said:**
> You're all making this harder than it has to be.

Ctrl-R is reverse search of the history (which is normally the way you want to do it).

Then.... just start typing...... bash matches against the history.

No need to pipe, edit, ......

When you find what you want, press Enter.

fair enough, though i find searching using pgup and pgdown much easier to use than Ctrl-R and uncommenting two lines in inputrc to enable it isn't all that hard...

---

### Post by Slim Odds on 2008-12-30
> **heindsight said:**
> fair enough, though i find searching using pgup and pgdown much easier to use than Ctrl-R and uncommenting two lines in inputrc to enable it isn't all that hard...

Yours was one of the simpler solutions.

I was really talking about the others.......

---

### Post by dagnabit dang doohickey on 2008-12-30
> You're all making this harder than it has to be.
As mentioned early in the thread, Ctrl-r is what the OP is looking for, but in reply to this:
> Or any better way to search my history besides exporting it to a temp file:

history > temp.txt

and searching throuhg it with gedit?

The solution is:
```
history | grep *pattern*
```

---

### Post by Slim Odds on 2008-12-30
> **dagnabit dang doohickey said:**
> As mentioned early in the thread, Ctrl-r is what the OP is looking for, but in reply to this:


The solution is:
```
history | grep *pattern*
```

I understand your "solution", but Ctrl-R in bash does a search for the "pattern" as you type. no need for grep and you get to execute the command immediately with no further fiddling.

Simple, efficient, no need for external programs.

To each his/her own.....

---

### Post by mikeman141 on 2008-12-31
Thanks folks! These are all very helpful responses.

---

### Post by dcstar on 2008-12-31
Forget it, I saw someone else say to use the "!" to use the history.

---

### Post by preki on 2009-03-05
I think the following is what the OP is looking for.  (This is taken from [http://codeinthehole.com/](http://codeinthehole.com/)).  Similar to what somebody mentioned further up the thread, if you put the following in .inputrc :

"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char

then the up arrow at the bash prompt searches command history like in Matlab.

Best wishes, S

---

### Post by ibbuntu on 2009-08-26
> **preki said:**
> I think the following is what the OP is looking for.  (This is taken from [http://codeinthehole.com/](http://codeinthehole.com/)).  Similar to what somebody mentioned further up the thread, if you put the following in .inputrc :

"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char

then the up arrow at the bash prompt searches command history like in Matlab.

Best wishes, S
I've been looking for this solution for a long time. Thanks!

---

### Post by heavystorm on 2011-01-23
> **heindsight said:**
> what you could also do is to edit /etc/inputrc:
```
gksudo gedit /etc/inputrc
```

somewhere around line 40 (on my Hardy install), you should find lines looking something like:
```

# alternate mappings for "page up" and "page down" to search the history
#"\e[5~": history-search-backward
#"\e[6~": history-search-forward

```

uncomment (ie remove the #s at the beginning of) the 2nd and 3d of these lines, save the file and exit gedit.

Now when you open a terminal you can the page up (and page down) button(s) to complete your current command by searching backwards (and forwards) in the command history.

great!!

---

### Post by heavystorm on 2011-01-23
> **preki said:**
> I think the following is what the OP is looking for.  (This is taken from [http://codeinthehole.com/](http://codeinthehole.com/)).  Similar to what somebody mentioned further up the thread, if you put the following in .inputrc :

"\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-char

then the up arrow at the bash prompt searches command history like in Matlab.

Best wishes, S

great! that's exactly what I have searched for long

---

### Post by coldraven on 2011-01-23
> "\e[A": history-search-backward
"\e[B": history-search-forward
"\e[C": forward-char
"\e[D": backward-charThat is so elegant and easy, the best thing I learned all week!
Now what was that get-iplayer command? :p

---

