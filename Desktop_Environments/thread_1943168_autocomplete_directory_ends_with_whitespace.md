---
title: "autocomplete directory ends with whitespace"
date: 2012-03-19
forum: Desktop Environments
---

### Post by ronaldv on 2012-03-19
Hi,

on the commandline when I use autocomplete to enter a directory name a whitespace is added at the end of the directory name. This is annoying because in most cases you want to continue into another directory. If I remember correct this used to be different some months/years ago.

(Why )has this changed?
How can I return to the old-fashioned autocomplete?

---

### Post by texpat on 2012-03-19
I've come across this problem as well (in Xubuntu 11.10). 

But it doesn't always do it. I haven't had the time to work out in which situations it does this, but I'll make a point of posting any findings here.

---

### Post by ajgreeny on 2012-03-19
Surely the whitespace is only added when you get to the end of a pathway.  If there are subfolders and/or files in the folder you enter with autocomplete, or it is an empty folder, there is no whitespace.  As far as I can make out the whitespace only appears when you start the name of a file, never a folder.

That is certainly the case in my installation of 10.04.

So autocomplete will add a forward slash with no whitespace to a folder name that is autocompleted, but will always add a space after an autocompleted filename so you can add further files if you want.

---

### Post by texpat on 2012-03-20
I tried out a few commands:

Commands that produce a blank at the end of the autocomplete and no slash when directory:

```

cp
mv
ls
less
diff
rm

```

Commands that work as expected (no blank and end in slash if in a directory):

```

cd
more
chmod

```

---

### Post by texpat on 2012-03-23
OK, so no-one else has seen this? This is really quite a hassle, so any input at all would be appreciated.

Thanks for reading

---

### Post by Paddy Landau on 2012-03-23
@texpat:

I get the same as ajgreeny: white space after files, slash after directories. (I have tested this on gnome-terminal on 11.04 and 12.04, and on the TTY console on 11.04.)

This is normal and expected behaviour. Your behaviour is unexpected, i.e. being different between commands. Which terminal emulator are you using, on which system?

---

### Post by texpat on 2012-03-23
I'm on Xubuntu 11.10. Selecting 'About' in the terminal's 'Help' menu gives me:

Terminal 0.4.8
Xfce Terminal Emulator

As far as 'shell' is concerned, it runs in bash. Calling Xterm from the bash shell gives me a separate window that runs Xterm. The auto-complete behavior, however, is the same as described above.

---

### Post by Paddy Landau on 2012-03-24
Well, that's interesting.

For me, both xterm and xfce4-terminal give the expected behaviour.

I have tested xfce4-terminal versions 0.4.7 (Natty) and 0.4.8 (Precise). Puzzling indeed!

---

### Post by texpat on 2012-03-24
> **Paddy Landau said:**
> Well, **that's interesting**.

snip..

**Puzzling indeed!**

Oh dear, now I'm really worried ;)

---

### Post by shioyama on 2012-04-14
I'm getting the same problem as texpat, anybody have a fix for this?

---

### Post by shioyama on 2012-04-14
The solution [here]("https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/769866/comments/10") fixed it for me:

> I believe there is a bug on line 1587 of /etc/bash_completion, the "-o default" on that line should be changed to "-o filenames".


---

### Post by texpat on 2012-04-15
> **shioyama said:**
> The solution [here]("https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/769866/comments/10") fixed it for me:

Excellent! Thanks a ton! This was driving me nuts.

---

### Post by wilson47 on 2012-10-13
shioyama's solution worked for me too. Thanks!

---

