---
title: "conky + tablet rotation"
date: 2010-05-29
forum: Desktop Environments
---

### Post by SnickerSnack on 2010-05-29
I'm having some trouble getting conky to play nice with tablet screen rotation.

Here is the background info (the question will come at the end).

The first problem I had was conky had the wrong background (solid black) after switching from landscape to portrait.  I figured out that this was because conky was grabbing its background from a region that is off-screen and is therefore black (my default solid color background).

So, I added a line in some scripts to restart conky when rotating, and a new problem arose.  First an over view of my scripts.

I have four scripts that actually perform the rotation commands: rotatenormal, rotateinverted, rotateleft, and rotateright.  Here is rotatenormal which sets the rotation mode to normal:

```
xrandr -o normal
xsetwacom set stylus Rotate none
sudo setkeycodes  0x71 103 0x6f 108 0x6e 105 0x6d 106
```

Then I have two scripts which call the appropriate rotateXYZ script based on the current rotation state: rotatebuttonl and rotatebuttonp (l for landscape, p for portrait).  Here is rotatebuttonl which calls rotateinverted if the screen is currently in normal mode, calls rotateinverted otherwise, and records the change in the file rotationmode:

```
mode=`cat /usr/bin/rotationmode`

if test 0 = $mode
then
echo 1 > /usr/bin/rotationmode
rotateinverted
fi

if test 1 = $mode
then
echo 0 > /usr/bin/rotationmode
rotatenormal
fi

if test 2 = $mode
then
echo 0 > /usr/bin/rotationmode
rotatenormal
fi

if test 3 = $mode
then
echo 0 > /usr/bin/rotationmode
rotatenormal
fi

killall conky
wait
conky
```

Originally, conky was not affected by the scripts, but after the first problem (conky had black background), I added the lines

```
killall conky
conky
```

to the end of the four rotateXYZ scripts.  This fixed that problem, but then had the result that sometimes conky failed to start again after being killed.  So, I removed those lines and added

```
killall conky
wait
conky
```

to the ends of the rotatebuttonXYZ scripts.  It did not fix the problem.

So, question: How can I change my bash scripts so that conky always restarts? Or: Is there a better way to make sure that conky always has the right background image?

Thanks

---

### Post by bra|10n on 2010-05-29
Wow I didn't know that you could rotate conky! Can it be done at a set interval?

Don't know I can help much here but a couple of points;
conky has a pause variable inbuilt.
Most use a bash script to start conky, the advantage of leaving such lines outside of your conkyrc.
Some people even use a bash script with a shortcut icon to toggle conky on and off.

ConkyHardcore! has some info that might help...

[http://conky.linux-hardcore.com/](http://conky.linux-hardcore.com/)

cheers

---

### Post by SnickerSnack on 2010-05-29
Actually, I'n rotating the whole screen, not conky itself.

See:
[http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateP.png](http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateP.png)
[http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateL.png](http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateL.png)

Thanks anyway.

---

### Post by bra|10n on 2010-05-29
Oops :oops:

Ok that makes a solution somewhat clearer / easier then doesn't it?
Something along the the lines of an $if_  statement in your conky_restart.sh linked to your rotation scripts?

---

### Post by SnickerSnack on 2010-05-29
I figured out one solution.  I added

```
killall conky
wait
sleep 0.1
conky
```

to the end of the script.

Edit: Even that doesn't work 100% of the time.  Conky fails to restart less often though.

> **bra|10n said:**
> Something along the the lines of an $if_  statement in your conky_restart.sh linked to your rotation scripts?

Maybe that would work, but sleeping for a tenth of a second did the trick.  Thanks.

---

### Post by SnickerSnack on 2010-05-29
Is there a way to get conky to grab its background image from the desktop background based on some condition (if statement?)?

I'm checking the site you linked for that right now.

EDIT: I'm making no progress with if_exists in .conkyrc

---

### Post by SnickerSnack on 2010-05-29
Yeah, ${if_exists} works fine as a variable in the text area, but not in the config area.  Basically, I need to make an if statement in the config area of .conkyrc.

I'd also appreciate it if anyone could tell me about a way to see *why* conky is failing to restart.

---

### Post by bra|10n on 2010-05-29
> **SnickerSnack said:**
> Yeah, ${if_exists} works fine as a variable in the text area, but not in the config area.  Basically, I need to make an if statement in the config area of .conkyrc.

I'd also appreciate it if anyone could tell me about a way to see *why* conky is failing to restart.

If you start conky via the terminal it will list problems encountered...

Conky takes a 'snapshot of the desktop' prior to loading to give the impression of transparent background, though I know you are aware of this...
So as a consequence, and regarding the $If_exists statement, I was thinking more along the lines of $If_exists 'rotation', then 'reload conky' via another ${exec } ? call to an external start_stop.sh script, which should take care of the background issue? Hang on, shouldn't update_interval 1 ensure the correct background is loaded?

Just some thoughts, this is stretching my scripting knowledge :(

---

### Post by SnickerSnack on 2010-05-30
> **bra|10n said:**
> If you start conky via the terminal it will list problems encountered...

I tried that.  It turns out that commands such as

```
killall -SIGUSR1 conky
killall conky ; conky
killall conky && conky
```

sometimes cause conky to segfault.  It seems (from googling) that there is no way to have conky restart and do it correctly every time.

> **bra|10n said:**
> Conky takes a 'snapshot of the desktop' prior to loading to give the impression of transparent background, though I know you are aware of this...  So as a consequence, and regarding the $If_exists statement, I was thinking more along the lines of $If_exists 'rotation', then 'reload conky' via another ${exec } ? call to an external start_stop.sh script, which should take care of the background issue?

If I had a reliable start/stop method, I could just put it in my rotate script.  That's what I've been working on.  Maybe I could write a script that handles the segfaults...hmmmm.

> **bra|10n said:**
> Hang on, shouldn't update_interval 1 ensure the correct background is loaded?

I don't know, but I'll try it.  I had it at 4.

I've also considered including a 'run conky' button in the panel, but I *really* want to avoid that.  It shouldn't be necessary.



If I can get this working well, I may write an AWN applet to handle rotation. :twisted:


BRAINSTORM: Maybe having something like "touch ~/.conkyrc" in the rotate script would work.

Edit: No, that doesn't work.  conky is grabbing a new background for itself, but remember the problem is that it's not grabbing the right image.  I suspect that it is grabbing from off-screen and getting only black.  See:

[http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateWrong.png](http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateWrong.png)

as compared to

[http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateP.png](http://i306.photobucket.com/albums/nn276/zacherysharon/desktops%20backgrounds/conkyRotateP.png)

The problem with the second picture is that the setup that gets that occasionally causes conky to crash.

---

### Post by SnickerSnack on 2010-05-30
This really does not want to work.  I finally got the background to update so that it looks right by adding

```
sed -i -e '1c \#lacrosse' /home/zsharon/.conkyrc
```

so the landscape script and

```
sed -i -e '1c \#periwinkle' /home/zsharon/.conkyrc
```

to the portrait script, which forces conky to reload since .conkyrc changed.  But, it crashes half the time!  The error:

```
Conky: X Error: type 0 Display 88a7820 XID 58720257 serial 493 error_code 16 request_code 10 minor_code 0 other Display: 88a7820
```

Here's the output of running rotatebuttonp (with a panel button) a few times:

```
conky
Conky: forked to background, pid is 13234
zsharon@Weierstrass:~$ 
Conky: desktop window (22000a9) is subwindow of root window (109)
Conky: window type - normal
Conky: drawing to created window (0x2600001)
Conky: drawing to double buffer
Conky: '/home/zsharon/.conkyrc' modified, reloading...
Conky: forked to background, pid is 13243

Conky: desktop window (22000a9) is subwindow of root window (109)
Conky: window type - normal
Conky: drawing to created window (0x5a00001)
Conky: drawing to double buffer
Conky: '/home/zsharon/.conkyrc' modified, reloading...
Conky: forked to background, pid is 13275

Conky: desktop window (22000a9) is subwindow of root window (109)
Conky: window type - normal
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Conky: X Error: type 0 Display 88a7820 XID 58720257 serial 493 error_code 16 request_code 10 minor_code 0 other Display: 88a7820
```

Is there a way around this X error?

Edit: It turns out that that's the same error caused by trying to restart conky by killing it first.  Now, I just need to find out how to avoid or fix

```
Conky: X Error: type 0 Display 88a7820 XID 58720257 serial 493 error_code 16 request_code 10 minor_code 0 other Display: 88a7820
```

---

### Post by bra|10n on 2010-05-30
In the main conky configure thread;

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

I think [ddnev45]("http://ubuntuforums.org/member.php?u=393581") is working on something similar. You'll get more support and dare say common sense there also ;)

---

### Post by SnickerSnack on 2010-05-30
> **bra|10n said:**
> In the main conky configure thread;

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

I think [ddnev45]("http://ubuntuforums.org/member.php?u=393581") is working on something similar. You'll get more support and dare say common sense there also ;)

I was looking for that thread, but couldn't find it for some reason.  Thanks!

Edit: I was able to get my main task done with the help I got in the conky thread that bra|10n linked to, but I still don't know why "killall -SIGUSR1 conky" wouldn't work well.

---

