---
title: "Change the function of the extra mouse buttons into volume up and down."
date: 2010-11-24
forum: Desktop Environments
---

### Post by The Stinger on 2010-11-24
So I'm new to Ubuntu and I really like the how fast it is compared to Windows 7(which I'm dual booting with).

Though I've run in to one problem which makes me go back to Windows 7, and that's not 
being able to change my extra mouse buttons to function as volume up and down.
I watch a lot of movies and series on my PC, and I use my wireless mouse to control volume and to pause and play. The last 2 are no problem, but I can't seem to find an option to change the function of the extra mouse buttons.

I've looked all over the net, and read various forums, they don't have a clear answer or even an idea how to accomplish this. So I turned to this forum, which I should have done
in the first place. ;)

So please someone help me stop switching back to Windows 7 just to watch videos.

---

### Post by shakma on 2010-11-29
Howdy, Stinger.  Welcome to the forums!  This place has been an invaluable resource for me, so I hope I can begin to steer you in the right direction today.

For starters, what do you use to watch videos?  If you want easy mouse control of volume, I highly recommend VLC.  It's both a linux and windows program, and I use it under both.  The great thing is, if you simply put your mouse cursor over the volume meter in the lower right corner, then scroll the wheel, the volume will go up and down!  No configuration necessary!

If you're set on having two mouse buttons ALWAYS do volume up and down, let me get you started on that, too:
1. Depending on exactly what mouse you have, you need to find out what Ubuntu sees as the "number" assigned to that button.  This can vary greatly with different mice.  You'll either need to search the forums for your mouse model (Microsoft and Logitech mice are well represented), or you'll need to fire up the terminal and run the command "xev".  A little white box with a black square in it will open up.  Put your mouse cursor in the square and start clicking buttons.  Messages will be FLYING by in the terminal, but don't worry.  Just steady the cursor in the black square, then click and release the button you care to use.  Watch the message that comes up as you RELEASE this button, and look carefully for the entry that begins "ButtonRelease event" and ends with mention of a "button #" (then usually followed by "same_screen YES").  I'm attaching a screen shot of me having just released my regular left mouse button ("button 1").

2. Once you figure out the button numbers of the two buttons you want to use, you'll need to do some configuring of a package called "imwheel".
  
[http://ubuntuforums.org/showthread.php?p=3987048#post3987048](http://ubuntuforums.org/showthread.php?p=3987048#post3987048)

This is a good thread to get you started, and Nion's post (#32 in that thread) is a great explanation of how to get imwheel installed.  Step three in his post about the .imwheelrc config file is where you're gonna need to really pay attention.  This thread is about making extra mouse buttons perform forward and back functions in web browsers and file managers.  But you can adapt that last part to to anything.  I don't know the keyboard commands for volume up and down off the top of my head, but I can find out for you if you need them.

I'll watch this thread.  Reply if anything I've said is helpful... or confusing.  I'm no expert, but I've learned nearly everything I know from this forum over the last 4 years or so.  We were all new at this at the beginning.  Keep asking questions!

---

### Post by The Stinger on 2010-11-30
Hey shackma, thanks for replying. :)

Tried various players, but I stuck with mplayer and the Smplayer gui.
I really like the way you can configure the mouse in the options menu of Smplayer.

About my problem, I already fixed it. I should have posted a reply or something. :oops:

Anyway heres what I did:
1 installed imwheel and added this to etc/X11/xorg.conf:
[PHP]Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection[/PHP]
2 installed btnx and pressed detect mouse and buttons.
Setup the side button to use volume up and down.
left button is KEY_VOLUMEDOWN and the right button KEY_VOLUMEUP
3 changed IMWHEEL_START=0 in IMWHEEL_START=1 etc/X11/imwheel/startup.conf

And that did the trick. :D

But I've got a small problem with the volume though, when the system volume level is around 10% it just mutes. I doesn't show a mute icon, the sound just cuts out and theres no sound, even if I put the speakers at 100%.

---

