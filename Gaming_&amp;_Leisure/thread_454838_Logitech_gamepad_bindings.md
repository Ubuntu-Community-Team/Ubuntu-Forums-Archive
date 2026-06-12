---
title: "Logitech gamepad bindings"
date: 2007-05-25
forum: Gaming &amp; Leisure
---

### Post by ethana2 on 2007-05-25
I have a Logitech USB dual action gamepad, with four triggers, two analog thumbsticks and so on, and I was wanting to set it up like this:

First, I wanted to store different sets of key bindings.  Most games don't natively support controllers, and in Windows with my logitech software, that was never a problem with me.  I had all my games set up with certain key combinations, and my controller had profiles for them.  I'd play Halo, CoD2, tremulous, Jedi Academy, Nexuiz, use my desktop, etc.  The buttons were bound to ctrl, alt, tab, escape, delete, enter, F4, Z, X, C, V, space, the arrow keys, the mouse axes, and so forth.  The occasional game didn't know what to do with F4, but other than that, it was great.  For those that did not, I'd just use a different profile, like the one I had set for WASD.

For my desktop profile, I wanted a cursor system such that it's position would not be related to the thumb stick by vector, but by correlation of position.  When the thumbstick is pushed up, the cursor is up.  When it's pushed left, the cursor is on the left.  When it is let go, the cursor returns to the middle of the screen and becomes invisible after 2 seconds until moved again.

Summary: Is what I described a pipe dream, an intense programming project (requiring learning an entire language), a Linux utility that already exists, or just another sequence of magic bash commands I type into the console?

---

### Post by dmcdante on 2007-06-03
Ever read about joy2key? it converts joystick/joypad buttons to keys on the keyboard and sends the events to the window you select. you mean something like that?

greets, dante

---

### Post by ethana2 on 2007-06-03
Yeah, I got that and another program for the mouse...  The installation instructions were basically 
"untar, make, make install- see?  easy!"

Now, I'd be fine with that- I had to edit xorg.conf in vim to get xorg to even work, so the command line isn't all that scary anymore, but..  I got countless compiler errors on that guy's code.  If anyone else has used this successfully, I'd like to know how they did it, and in slightly more detail.

Thanks for the response...  We may be getting somewhere.

---

### Post by jw5801 on 2007-06-26
The program is in the repositories apparently!
```
jw5801@jw5801-laptop:~$ joy2key
The program 'joy2key' is currently not installed.  You can install it by typing:
sudo apt-get install joy2key
Make sure you have the 'universe' component enabled
```

I'm currently looking at buying a logitech controller, but I want to make sure it's something that works well with ubuntu. So report back and let me know how it all goes!

---

### Post by Dark Aspect on 2007-06-26
Actually not to butt in but I have the same problem with no way to program my Logitech controller.when I try to load the joy2key program I get a error complaining that I don't have joystick support in my kernel,please help.

---

### Post by ethana2 on 2007-06-26
When I find a solution to my problem, this is where it will be.
I'll take and give all the help I can.  So far, none of what I have tried has worked.

You, person with the error message- is your kernel up to date?

---

### Post by ethana2 on 2007-06-26
And don't worry about butting in.  We're all in this together.

Anyone out there- if you've gotten either of these programs to work, please, please tell us.

---

### Post by Dark Aspect on 2007-06-26
> **ethana2 said:**
> When I find a solution to my problem, this is where it will be.
I'll take and give all the help I can.  So far, none of what I have tried has worked.

You, person with the error message- is your kernel up to date?

Heres the error:

[IMG]http://i183.photobucket.com/albums/x72/Dark_Aspect/Joyerror.png[/IMG]

However I think joy2pad is just old and unusable as the readme file that is installed with it points [here]("http://atrey.karlin.mff.cuni.cz/~vojtech/joystick/").I have aready made a post for help with this [here]("http://ubuntuforums.org/showthread.php?p=2916018#post2916018").My kernel version is what installed with Ubuntu 7.04.

---

### Post by BoyOfDestiny on 2007-06-26
> **Dark Aspect said:**
> Heres the error:

[IMG]http://i183.photobucket.com/albums/x72/Dark_Aspect/Joyerror.png[/IMG]

However I think joy2pad is just old and unusable as the readme file that is installed with it points [here]("http://atrey.karlin.mff.cuni.cz/~vojtech/joystick/").I have aready made a post for help with this [here]("http://ubuntuforums.org/showthread.php?p=2916018#post2916018").My kernel version is what installed with Ubuntu 7.04.

I don't have a joystick plugged in at the moment, but it should be /dev/input/js0

I remember they changed that awhile back, and software had to be updated or you make a symlink

something like 
sudo ln -s /dev/input/js0 /dev/js0

---

### Post by Dark Aspect on 2007-06-26
whats a symlink and how can I create one?oh by the way I do have a js0 file in my input folder but you have confused me if its in a different directory then that means the program key2joy can't be used right?

---

### Post by BoyOfDestiny on 2007-06-26
> **Dark Aspect said:**
> whats a symlink and how can I create one?oh by the way I do have a js0 file in my input folder but you have confused me if its in a different directory then that means the program key2joy can't be used right?

The command ln can make it, it's like a "shortcut" one location points to another.

So if you do 
sudo ln -s /dev/input/js0 /dev/js0

That (should I think) make a link so when joy2key looks for /dev/js0, it will find it, and will use /dev/input/js0.

---

### Post by Dark Aspect on 2007-06-26
> **BoyOfDestiny said:**
> The command ln can make it, it's like a "shortcut" one location points to another.

So if you do 
sudo ln -s /dev/input/js0 /dev/js0

That (should I think) make a link so when joy2key looks for /dev/js0, it will find it, and will use /dev/input/js0.
It worked!!!!!!Now I have a new error but I think its a normal one:

[IMG]http://i183.photobucket.com/albums/x72/Dark_Aspect/NoTarget.png[/IMG]

Now I have to figure out what target its talking about,is it revering to js0?Of course now that it worked in the terminal I could actually try the executable.I may need to restart my system.

---

### Post by ethana2 on 2007-06-26
There is a kernel module you have to have to use your joystick, and that's whatever driver it requires.

I forget what the one I needed was called, but if you have a logitech usb dual action, yours will be the same.
Somewhere on this forum, there was a list of all of those- I started this thread because that covered passing controller input to programs that use it, not binding it to keys.  As most games and stuff, in my experience, don't support controller input anyway, key and mouse binding is essential.

Still, to do any of this, you have to find that thread- I couldn't... and if you find that, reposting a link here would be helpful.  This thread is here to cover key and mouse binding after those instructions have been followed.

I think my driver was "adi"

---

### Post by Dark Aspect on 2007-06-29
> **ethana2 said:**
> There is a kernel module you have to have to use your joystick, and that's whatever driver it requires.

I forget what the one I needed was called, but if you have a logitech usb dual action, yours will be the same.
Somewhere on this forum, there was a list of all of those- I started this thread because that covered passing controller input to programs that use it, not binding it to keys.  As most games and stuff, in my experience, don't support controller input anyway, key and mouse binding is essential.

Still, to do any of this, you have to find that thread- I couldn't... and if you find that, reposting a link here would be helpful.  This thread is here to cover key and mouse binding after those instructions have been followed.

I think my driver was "adi"
Ok I am going to look for the driver btw I have a [Rumblepad 2]("http://www.logitech.com/index.cfm/gaming/pc_gaming/gamepads/devices/264&cl=us,en") does this mean I have a different driver then you?

---

### Post by ethana2 on 2007-06-29
Hey, that thing looks nice ;)

You might have a different driver....  I don't know.  That thread I was talking about is hiding somewhere on this forum, and it has a huge list of gamepads and their drivers...  ...and I still can't find it.  I'd google your gamepad's name with the words Linux and driver and see what it gives you.

It would be nice if it was a bit easier to set gamepads up- if the drivers are there, I don't see why this process should be so complicated.

Is there somewhere to put feature requests for ubuntu?  I'd like a unified gamepad manager that takes care of drivers, profiles, and key/mouse binding.

---

### Post by acoustibop on 2007-06-29
FWIW I have a Rumblepad 2 (wired) and it's worked in Feisty from the start - it didn't need any sort of installation.  However, I probably had it plugged in when I installed Feisty, and the installation may have picked it up and installed the driver anyway.

---

### Post by ethana2 on 2007-06-29
Oh, man.  That makes sense.

I guess when Gutsy comes out I'll try to make note of that for my install.
You know, people reinstall Linux a lot more than they do windows, but it's funny-
the difference between keeping up with the most awesome thing out there and jumping between junkers like a frog jumps between lily pads ;)
What's worse is that people pay money for those things.  Poor people.

...Anyway- I'm going to look for the feature request thingy, to ask for:

an ubuntu sponsored xwinwrap plugin for compiz fusion
colemak keyboard layout installed by default in ubuntu
easy to use gamepad bindings and driver manager.

Anyone want me to add anything?

---

### Post by ethana2 on 2007-09-02
Okay.  I'm resurrecting this thread.  I'm trying to get rid of my windows partition soon, and getting this gamepad working in Linux is the last thing stopping me.

I ran a sudo apt-get install joy2key.
I ran a sudo ln -s /dev/input/js0 /dev/js0 (I may have that backwards here, but I typed it into the console correctly.

Now when I run joy2key, it tells me "Must specify a target!"
And when I run js2mouse, it says "Error when opening mouse fifo for writing : Permission denied"
So I type sudo js2mouse, and get "Number of  axes : 6
Number of  buttons : 12
Driver version : 131328
Joystick name : Logitech Logitech Dual Action" --and then it doesn't do anything.

Anyone out there that could point me to a solution?

---

### Post by ethana2 on 2007-09-22
I have found something I think may work.  I promised to post what I found here for you guys, to not leave you in the dark if you had subscribed to this thread.

Forget joy2key and those.  Google QJoyPad.  Hopefully it works as needed.  I'm going to try it out now.

---

### Post by JohnL2009 on 2008-12-15
Ok, I've read the above - but can someone tell me how to just get the pad installed on Ubuntu 8.10?  None of the above makes any sense to me - maybe it will if and when I can get it installed.  Thanks.

---

