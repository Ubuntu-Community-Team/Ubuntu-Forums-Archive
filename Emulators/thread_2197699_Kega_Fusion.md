---
title: "Kega Fusion"
date: 2014-01-05
forum: Emulators
---

### Post by BostonLinux99 on 2014-01-05
Hello, 

I saw some other threads on this but I'm a noob so wasnt' sure I could re-activate an old thread.
But bottom line, I've had great luck getting a ton of stuff working in lubuntu 13.10 but can't get Kega Fusion running.

I click on it, or run it from the terminal and it basically says - no such command
It complains initially about the file not be marked executable, though I tell it to run anyway, though it won't.  I have also have marked it executable and no improvement.

Oddly enough, on another Xubuntu 13.10 machine, it just runs 100% out of the box no problem.
So, I know I'm not doing anything different and it's fine there.

Two thoughts are - 1) maybe some kind of  openGL issue on this machine, since it has integrated Intel i915 video and the other has nvidia, or 2) gzip isn't unzipping the file properly?

These are both guesses.

I just can't figure out why I can't run an executable that's right there.. though it seems it's not really an executable like I know it's supposed to be.


Basically I can see it right there, and it just won't run - interminal or not.

---

### Post by BigSilly on 2014-01-05
What command are you using to run it in the terminal? The correct command is -

```
./Fusion
```

But first you must cd (change directory) into the directory (or folder) you have downloaded and extracted. For example my command on my desktop is -

```
cd /home/bigsilly/Emulators/Fusion
```

then

```
./Fusion
```

To execute it. You should see any errors in the output you get. Obviously change your ***/path/to/directory*** to suit how you have done it. Let us know.

---

### Post by BostonLinux99 on 2014-01-05
Thank you v. much.

i cd to the directory and run ./Fusion and get

"Segmentation fault (core dumped)"

At least that's an error vs. the nothing I was seeing.
Thank you v. much for helping.

I spent a bunch of time trying to figure out if it was an openGL support issue but in terms of problem solving, it makes more sense to pursue an actual error vs. a guess.

---

### Post by BostonLinux99 on 2014-01-05
"[COLOR=#333333][FONT=UbuntuRegular]attempts to access a part of memory that cannot be accessed, or which the program is prohibited from accessing"

Do you think it could be a permissions/prohibition issue?
This is the ls -l of the folder contents

[/FONT][/COLOR]-rwxr-xr-x 1 jay jay 713776 Oct  7  2009 Fusion
-rwxr-xr-x 1 jay jay  40424 Oct  7  2009 History.txt
-rwxr-xr-x 1 jay jay  28031 Sep 27  2009 Readme.txt

---

### Post by BigSilly on 2014-01-05
> **BostonLinux99 said:**
> Thank you v. much.

i cd to the directory and run ./Fusion and get

"Segmentation fault (core dumped)"

At least that's an error vs. the nothing I was seeing.
Thank you v. much for helping.

I spent a bunch of time trying to figure out if it was an openGL support issue but in terms of problem solving, it makes more sense to pursue an actual error vs. a guess.

That's unusual. Is that the only error message you're getting? I'm really sorry but I haven't any experience of using Lubuntu.

---

### Post by BostonLinux99 on 2014-01-05
Sure, no problem.  I runs other things fine, but I'll just skip it for now, it's ok.
Thanks for looking into it.

---

### Post by BigSilly on 2014-01-06
Are you running 64 or 32 bit Lubuntu? Usually problems arise with Kega Fusion when running on 64 bit machines because it requires 32 bit libraries to run. Another idea is perhaps you are using a config file from a previous install. You could try deleting the fusion.ini and retrying.

Have you read [this post]("http://ubuntuforums.org/showthread.php?t=2189763&p=12859349#post12859349") I made a while ago in another thread?

---

