---
title: "How to run a script on resume in Intrepid?"
date: 2008-12-12
forum: General Help
---

### Post by FokkerCharlie on 2008-12-12
Hi!

I have a line in my 'Sessions' that remaps the media keys (actually a little touchpad) to mouse buttons 17 18 19 20.  That's fine, however after suspend/resume, this no longer works.

So, I need a script to run every time the computer resumes, but haven't been able to do it so far.  I have put this:

```
#!/bin/sh

#Set media touchpad keys to 17 18 19 20
xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```

In /etc/pm/sleep.d and /etc/acpi/resume.d but it doesn't seem to work out.  What am I doing wrong?

I am using a fully updated Intrepid install.

Cheers
Charlie

---

### Post by sdennie on 2008-12-12
See if this works in /etc/pm/sleep.d (replace your_username with your username):

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    DISPLAY=:0.0 su **your_username** -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
    ;;
esac

exit 

```

---

### Post by FokkerCharlie on 2008-12-12
Thanks for the input, vor.

Unfortunately, it didn't work!  The script is owned by root, and allowede as executable.

Any more ideas?  Shurely it can't be that hard!

Charlie

---

### Post by sdennie on 2008-12-13
I'm not sure why that wouldn't work.  One thing you could try would be to name the script something like 00-xinput.sh.  That will cause it to run as the last thing that runs when resuming the machine.  You could also suspend the machine with:

```

sudo pm-suspend

```

And see if you get any useful output.

---

### Post by FokkerCharlie on 2008-12-13
Hi again vor

Sadly still no luck with either .  There is no output in the terminal if I run sudo pm-suspend from there, nothing shows up in dmesg, so I don't know what's going on- is there any other way I can get debugging what's going on?

Cheers
Charlie

---

### Post by sdennie on 2008-12-13
Strange.  Maybe something has changed with pm-utils in 8.10.  Maybe try a less elegant:

```

#!/bin/bash

DISPLAY=:0.0 su your_username -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'

```

I use lots of things in /etc/pm in this form and they work just fine.

---

### Post by maestrobwh1 on 2008-12-13
This is a totally random shot in the dark, but often I find if I add 

sleep 1

to the **beginning** of a script that runs on resume, it works.  I think perhaps it allows other processes to catch up.

Also, perhaps this is a preference (perhaps) but in /etc/pm/sleep.d, have it call the script from where you have it stored, rather than put the commands in the /etc/pm/sleep.d/filename

so if the script you want to run is called "runthis" and you have it in /etc/

then make your /etc/pm/sleep.d/filename

> 
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    /etc/runthis
    ;;
esac

exit

If you don't have any luck, then you might have to add this somewhere in 
/usr/lib/pm-utils/sleep.d

but research further what file to edit, or perhaps create a new one there.

---

### Post by FokkerCharlie on 2008-12-13
Thanks, chaps

I have tried all of the above, to no avail.  I created a link to the script in my home folder (that runs fine when I run it from the terminal) as per maestrobwh1's post.  I have tried variations on vor's suggestions.

It surprises me that this is so tricky- it was, after all, trivial to get it working in 'Sessions'!

Any more pointers gratefully received.

Charlie

---

### Post by sdennie on 2008-12-13
As a debugging method to see if you script is even being run, try using this script:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    DISPLAY=:0.0 su **your_username** -c "gcalctool"
    ;;
esac

exit

```

If you have a calculator sitting on your desktop when you resume, you can be sure the script is working properly and it's a minor detail to get your command to run right.  If not, something else is fundamentally broken.

---

### Post by FokkerCharlie on 2008-12-13
Right- well, at least we're getting somewhere.

I made a script: /etc/pm/sleep.d/90-script-test.sh with this in it:

```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    DISPLAY=:0.0 su charlie -c "gcalctool"
    ;;
esac

exit
```

And on restart, nothing happens.

There's nothing in /var/log/messages that I can see that could be relevant.  So what's happening here?

Charlie

---

### Post by sdennie on 2008-12-13
Are you running gnome?  Also, what is the output of:

```

ps aux | grep gnome-power-manager

```

If I'm not mistaken, it's gnome-power-manager that tells pm-utils to do stuff.  If it's not running, /etc/pm things may not work.

---

### Post by FokkerCharlie on 2008-12-13
Yes, I am running Gnome.

```
~$ ps aux | grep gnome-power-manager
charlie   6823  0.0  0.7  87148 16308 ?        Ssl  14:55   0:01 gnome-power-manager
```

Hope that means more to you than it does to me!

Charlie

---

### Post by sdennie on 2008-12-13
Strange.  Make a script called 00-testing in your home directory and try this:

```

#!/bin/bash

cat /proc/acpi/battery/*/state > /tmp/state

```

To install it:

```

sudo install 00-testing /etc/pm/sleep.d/

```

Suspend the machine on AC power, unplug it and then resume on battery power and post the contents of /tmp/state.

---

### Post by FokkerCharlie on 2008-12-13
```
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            3656 mA
remaining capacity:      1635 mAh
present voltage:         11289 mV
```

---

### Post by sdennie on 2008-12-13
> **FokkerCharlie said:**
> ```
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            3656 mA
remaining capacity:      1635 mAh
present voltage:         11289 mV
```

That's excellent news!  It means that things are working as expected.  You aren't running XGL or the X server on a non-standard display are you?  What is the output of:

```

echo $DISPLAY

```

---

### Post by FokkerCharlie on 2008-12-13
```
~$ echo $DISPLAY
:0.0

```

Looks OK to me.

Thanks for your continued assistance with this!

Charlie

---

### Post by sdennie on 2008-12-13
I really don't understand.  I tried the "gcalctool" script on my machine just to verify it worked and it did.  The last thing to try would be to hit Ctrl-Alt-F1, login and try:

```

DISPLAY=:0.0 gcalctool & sleep 30 && pkill gcalctool

```

Then hit Ctrl-Alt-F7 and you should see the calculator on your desktop.  It should vanish after 30 seconds.

---

### Post by FokkerCharlie on 2008-12-13
OK, something interesting happened there.  I did ctrl+alt+f1, and typed in you command.  This was the output:

```
[1] 6919
No protocol specified
(gcalctool:6919): Gtk-WARNING **: CANNOT OPEN DISPLAY: :0.0
```

No calculator running after going back into the graphical display!

Charlie

---

### Post by sdennie on 2008-12-13
Interesting.  Have you locked down your X server in any way?  Try running that Ctrl-Alt-F1 thing but, before typing it try:

```

DISPLAY=:0.0 xhost +

```

---

### Post by FokkerCharlie on 2008-12-13
Ah ha!

That gave me:```


access control disabled, clients can connect from any host
```

And after ctrl+alt+f7, a calculator window appeared for 30 secs.  Well, I think that it was the calculator (AWN gave me a clue), but it was a blank white window with no decoration!  (Did I mention I was using compiz?)

So that's progress, I guess...

Charlie

---

### Post by sdennie on 2008-12-13
> **FokkerCharlie said:**
> Ah ha!

That gave me:```


access control disabled, clients can connect from any host
```

And after ctrl+alt+f7, a calculator window appeared for 30 secs.  Well, I think that it was the calculator (AWN gave me a clue), but it was a blank white window with no decoration!  (Did I mention I was using compiz?)

So that's progress, I guess...

Charlie

That may be progress.  Try the original script I posted but modified like this:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    DISPLAY=:0.0 su your_username xhost +
    DISPLAY=:0.0 su your_username -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
    DISPLAY=:0.0 su your_username xhost -
    ;;
esac

exit

```

---

### Post by FokkerCharlie on 2008-12-14
Sadly, no joy there.

I tried that as 00-remap-media-keys.sh, 99-remap-media-keys.sh, even added the 'gcalctool' line in for good measure, but nothing happens.

:(

Just a thought- are the scripts in /etc/pm/sleep.d run before or after login?

Charlie

---

### Post by darkbluede on 2008-12-16
Hi Everyone,

I just followed this thread because I had a very similar problem. I stumbled over the solution when I copied the script mentioned early in this thread:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
    DISPLAY=:0.0 su your_username xhost +
    DISPLAY=:0.0 su your_username -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
    DISPLAY=:0.0 su your_username xhost -
    ;;
esac

exit

```

If you do it like me and copy&paste the script to a file then you might experience the same problem I had. The part

```

. /usr/lib/pm-utils/functions

```

has an error - because of the whitespace between . and / - correctly it should look like this:

```

./usr/lib/pm-utils/functions

```

That solved the problem for me - I hope it helped ;)


cu

Darkblue

---

### Post by FokkerCharlie on 2008-12-16
Hmmmm.

This is still causing a problem for me.  Darkbluede, would you be able to post your script in its entirety, and also its location?

This is very curious.

Cheers
Charlie

---

### Post by darkbluede on 2008-12-18
Hi Charlie,

I have it in

```
/etc/pm/sleep.d
```

and named it 00-testing (I know the name is not perfect ;) ) ... I use it to restart the wii-remote-controlling software wminput after resume. Here is the exact content of the file:

```

#!/bin/sh

#cat /proc/acpi/battery/*/state > /tmp/state
#DISPLAY=:0.0 su mythtv -c "gcalctool"

./usr/lib/pm-utils/functions

#echo "$1" > /tmp/state

case "$1" in
    thaw|resume)
#    DISPLAY=:0.0 su mythtv -c "gcalctool"
        wminput -d &
    ;;
esac

exit

```

As you can see I have tested around a lot. I think it's safe to assume, that you can remove the commented out lines (beginning with #) - but you never know in this indeterministic world of ours ...

I should also add that I have not simply copied the file to this location but rather installed it properly by the command some of my predecessor in this thread mentioned earlier:

```
install 00-testing /etc/pm/sleep.d/
```

I hope it will work for you this time. But I also shoud warn you that it tends to be a bit unreliable - infrequently it won't be executed for some reason I have not figured out yet. But most of the time it works.

Good Luck!


cu

Darkblue

---

### Post by FokkerCharlie on 2008-12-19
Thanks very much to you both.

Unfortunately, this still isn't working for me.  Perhaps it will just be something that I can't do!  For info, I tried all this in my script in the end, in the hope that SOMETHING would work!

```
#!/bin/sh

./usr/lib/pm-utils/functions

DISPLAY=:0.0 su charlie xhost +
DISPLAY=:0.0 su charlie -c "gcalctool"
su charlie -c "gcalctool"
	gcalctool
	xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
DISPLAY=:0.0 su charlie xhost -

case "$1" in
    thaw|resume)
#    DISPLAY=:0.0 su charlie xhost +
#    DISPLAY=:0.0 su charlie -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
#    DISPLAY=:0.0 su charlie -c 'xinput set-button-map "7" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
#    DISPLAY=:0.0 su charlie -c 'xinput set-button-map "8" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
#    DISPLAY=:0.0 su charlie -c "gcalctool"
#    DISPLAY=:0.0 su charlie xhost -
DISPLAY=:0.0 su charlie xhost +
DISPLAY=:0.0 su charlie -c "gcalctool"
su charlie -c "gcalctool"
	gcalctool
	xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
DISPLAY=:0.0 su charlie xhost -
    ;;
esac

exit
```

Not to worry, going to crack open a beer.

Cheerio!
Charlie

---

### Post by darkbluede on 2008-12-19
Have you tried something like this:

```

#!/bin/sh

./usr/lib/pm-utils/functions

echo "OK:" > /tmp/state
echo "$1" >> /tmp/state

exit

```

When successful there should be a file in */tmp* called *state* containing something similar to

```

OK:
resume

```

And have you checked if *./usr/lib/pm-utils/functions* truly exists and can be executed?

Good night
Darkblue

---

### Post by FokkerCharlie on 2008-12-20
Hi darkblue

Thanks for your patience!

The script you describe generates a 'state' file with the contents you describe, so that's working OK.  I also put those two lines into my other script, and that worked again, so that means that the script itself is being executed.  The problem seems to be with the gcalctool or xinput commands.  Here's the current state of my script:

```
#!/bin/sh

./usr/lib/pm-utils/functions

DISPLAY=:0.0 su charlie xhost +
DISPLAY=:0.0 su charlie -c "gcalctool"
su charlie -c "gcalctool"
	gcalctool
	xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
DISPLAY=:0.0 su charlie xhost -

case "$1" in
    thaw|resume)
echo "OK:" > /tmp/state
echo "$1" >> /tmp/state
#    DISPLAY=:0.0 su charlie xhost +
#    DISPLAY=:0.0 su charlie -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
#    DISPLAY=:0.0 su charlie -c 'xinput set-button-map "7" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
#    DISPLAY=:0.0 su charlie -c 'xinput set-button-map "8" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
#    DISPLAY=:0.0 su charlie -c "gcalctool"
#    DISPLAY=:0.0 su charlie xhost -
DISPLAY=:0.0 su charlie xhost +
DISPLAY=:0.0 su charlie -c "gcalctool"
su charlie -c "gcalctool"
	gcalctool
	xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
DISPLAY=:0.0 su charlie xhost -
    ;;
esac

exit
```

(I know it's a mess, this is computing by brute force and determination!)

All that happens is the state file gets created.

EDIT:  Running the script manually, after the system is resumed, works fine.  gcalc appears a couple of times, and the media keys are remapped.  So it looks like the problem is something about passing the command to X.  I think.

Any more ideas?

Thanks again
Charlie

---

### Post by darkbluede on 2008-12-24
Hi Charlie,

so now we know the script gets executed for sure. That's a start. Maybe you don't see the calculator because it takes longer for x to restart your desktop then it takes for the command to be executed. Try to put a 

```
sleep 10
```

directly after

```
    thaw|resume)
```

The next resume 10secs should be enaugh to rewake the desktop and probably the calculator gets started. And you should't place any code **outside** of

```

case "$1" in
    thaw|resume)

...

    ;;

```

because as I understand it that code gets also executed when the computer **enters** sleep mode.

Good luck and merry X-mas.
darkblue

---

### Post by FokkerCharlie on 2008-12-24
Thanks, darkbluede.

Making those changes did not fix the problem. The current contents of my script:

```
#!/bin/sh

./usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)

sleep 10

DISPLAY=:0.0 su charlie -c "gcalctool"
su charlie -c "gcalctool"
	gcalctool
DISPLAY=:0.0 su charlie xhost +
DISPLAY=:0.0 su charlie -c "gcalctool"
su charlie -c "gcalctool"
	gcalctool
	xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
DISPLAY=:0.0 su charlie xhost -
    ;;
esac

exit
```

And no calculator appears!  No buttons re-mapped, either.  I really think that I am missing something here, but just can't see what...

Thanks again for your input, happy christmas to you, too.

Charlie

---

### Post by 3poD on 2008-12-24
dont forget that you need to wait a few seconds and then remap buttons... BUT, you need to do this in background, because it seem that other processes like X itself won't start because the current script hasn't finished..

so for me, this one works (change your_username):

```

#!/bin/sh

set_media_keys() {
sleep 15
DISPLAY=:0.0 su your_username -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
}

case "$1" in
	thaw|resume)
		set_media_keys **&**
		;;
	*)
		;;
esac

```

**&** symbol means it will start on background

---

### Post by FokkerCharlie on 2009-01-01
Hi 3poD

Sorry, but I just can't get this working.  It seems that I cannot pass any command to X.  I can write to files and things (see previous pages), but the x bit isn't working out.  No idea why.  Thanks for you help, anyhoo.  For the record, I have all this in a script, just to try to get SOMETHING working- to no good effect!

```
#!/bin/sh

./usr/lib/pm-utils/functions

gcalctool

DISPLAY=:0.0 xhost +
DISPLAY=:0.0 su charlie -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
DISPLAY=:0.0 su charlie -c gcalctool
DISPLAY=:0.0 charlie -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
DISPLAY=:0.0 charlie -c gcalctool
DISPLAY=:0.0 xhost -
DISPLAY=:0.0 su charlie -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
DISPLAY=:0.0 su charlie -c gcalctool

set_media_keys() {
sleep 15
DISPLAY=:0.0 xhost +
DISPLAY=:0.0 su charlie -c 'xinput set-button-map "4" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16'
DISPLAY=:0.0 su charlie -c gcalctool
DISPLAY=:0.0 xhost -
}

case "$1" in
	thaw|resume)
		set_media_keys &
		;;
	*)
		;;
esac
```

Cheers
Charlie

---

### Post by NTolerance on 2009-02-09
Just spent a while on a similar resume script which requires a valid XWindows display.  Here's mine:

```
#!/bin/sh
#DISPLAY=:0.0 su username -c 'gsynaptics-init --sm-disable'

case "$1" in
    thaw|resume)
	sleep 5
        DISPLAY=:0.0 su username -c 'gsynaptics-init --sm-disable'  
    ;;
esac

exit 0
```

I kept getting errors in my virtual terminals and the display would fail to switch to my GUI after resume.  The big key for me was the "exit 0" at the end.  I think this causes the script to always report a successful exit status regardless of what actually happens.  I think that the Ubuntu power management system expects all resume scripts to end successfully without any warnings or anything, otherwise bad things happen.  Give that a try.

---

### Post by FokkerCharlie on 2009-02-12
Thanks for posting your solution, NT, but it still ain't working for me.

I am not sure I will ever know why.  When Jaunty comes out, I will go for a clean installation, perhaps that will get rid of whatever gremlin is causing this to happen for me.

Cheerio
Charlie

---

### Post by colden46 on 2009-02-20
Hi Charlie,

One problem is the line:
*DISPLAY=:0.0 xhost +*

'xhost' is used to grant permission to connect to an X server. The above line is basically saying "hey, connect to the X server, and give me permission to connect to the X server". Unless you already have permission to connect, this isn't going to work. In other words, 'xhost' must be run from your current X session, not from this script.

So, login to X, open a terminal, run 'xhost +', and then try your script. If this works, you can add the xhost invocation to your System->Preferences->Sessions configuration to run automatically when you log in.

(Note that using 'xhost' like this is pretty insecure. If you have other users on this machine, they could show whatever windows they wanted on your desktop, including installing keyloggers. It's probably fine for most single-user home systems though)

Hope this helps!

---

### Post by FokkerCharlie on 2009-02-23
Hi Colden

xhost + seems to cause an additional problem.  Here is my current script:

```
#!/bin/sh
#DISPLAY=:0.0 su username -c 'gsynaptics-init --sm-disable'

case "$1" in
    thaw|resume)
	sleep 5
        DISPLAY=:0.0 su charlie -c 'gsynaptics-init --sm-disable'
	DISPLAY=:0.0 su charlie -c 'gcalctool'  
    ;;
esac

exit 0
```

xhost + works fine in the terminal.  Unfortunately, my computer doesn't wake up properly after suspend.  I just get a blank screen with the flashing cursor in the top left corner.  If I suspend/resume without xhost + (but with the script in place) all is well.  Of course, the script does still not work!

I do seem to have found myself in a situation that noone else can reproduce!

Cheers
Charlie

---

### Post by colden46 on 2009-04-01
> **FokkerCharlie said:**
> xhost + works fine in the terminal.  Unfortunately, my computer doesn't wake up properly after suspend.  I just get a blank screen with the flashing cursor in the top left corner.  If I suspend/resume without xhost + (but with the script in place) all is well.  Of course, the script does still not work!

Interesting that it would cause the system to not wake up... I've got something else you can try. From the terminal, type 'echo $XAUTHORITY'. On my system, it prints /home/[me]/.Xauthority. Try putting that value in your script, so the line would look something like this:

XAUTHORITY=/home/charlie/.Xauthority DISPLAY=:0.0 su charlie -c 'gcalctool'

No guarantees, but it may be worth a shot.

You can also try redirecting the output to a file, so you can see what's going on. Put '> /tmp/blah 2>&1' at the end of the line in your script where you're trying to run the command.

Good luck!

---

### Post by jis on 2009-04-13
> **darkbluede said:**
> 
If you do it like me and copy&paste the script to a file then you might experience the same problem I had. The part

```

. /usr/lib/pm-utils/functions

```

has an error - because of the whitespace between . and / - correctly it should look like this:

```

./usr/lib/pm-utils/functions

```

That solved the problem for me - I hope it helped ;)


cu

Darkblue

I think the whitespace belongs in between "." and "/usr/lib/pm-utils/functions". The "." is actually a command, but I don't know what it is supposed to do. (Try to run it as such in terminal.) However, the whole line may be unnecessary in the script. Mine worked without it, at least.

---

### Post by FokkerCharlie on 2009-05-04
Hello!

Well, I still can't get a script working on resume, I've tried all the above to no avail...

However, the behaviour that I originally wanted to restore (xinput ButtonMapping) now persists after resume anyway, so the original problem's solved anyway.

VMT to everyone who contributed, I appreciate it.  I guess that I must just be missing something daft...

Cheers
Charlie

---

