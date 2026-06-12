---
title: "Disabling system beep trouble"
date: 2009-05-04
forum: General Help
---

### Post by brandoncolorado on 2009-05-04
I am running Jaunty NBR.  After each reboot, the pc speaker volume control is unmuted.  This means that with each shutdown I get the LOUDEST beeping noise ever.  After searching the forums, I tried these things:

- ran $ sudo modprobe -r pcspkr

- added "blacklist pcspkr" to the file /etc/modprobe.d/blacklist.conf

I still cannot disable this thing!  

What else could I do?

---

### Post by brandoncolorado on 2009-05-05
bump

---

### Post by marmuta on 2009-05-05
Try that old thread
[http://ubuntuforums.org/showthread.php?t=1041329](http://ubuntuforums.org/showthread.php?t=1041329)

---

### Post by ikacer on 2009-05-05
If you want to completely remove the system beep you can try:

```
sudo rmmod pcspkr
```

Edit: guess im a bit slow in posting...

---

### Post by brandoncolorado on 2009-05-05
> **marmuta said:**
> Try that old thread
[http://ubuntuforums.org/showthread.php?t=1041329](http://ubuntuforums.org/showthread.php?t=1041329)

Thanks for that link.  I have pcspkr and the other one blacklisted as well.  Neither works.  I read through that posting and I don't understand the part about .profile.

Should I also append this to my profile?
sh -c "xset b off && xset b 0 0 0"

---

### Post by wpshooter on 2009-05-05
Isn't there a check box under the sound section of Ubuntu which allows you to disable the PC speaker ?

---

### Post by brandoncolorado on 2009-05-05
> **wpshooter said:**
> Isn't there a check box under the sound section of Ubuntu which allows you to disable the PC speaker ?

No, but there is a "pc speaker" option in volume controls.  I can mute it there and that works, but it loses that option after each restart.

---

### Post by marmuta on 2009-05-05
If I remember correctly he just added the line to System->Preferences->Startup Applications. I guess ~/.profile (gedit ~/.profile) would work too though. 
wpshooter could be right with the checkbox. It may have been added since then, but I couldn't tell where to find it.

---

### Post by baseface on 2009-05-05
open your case and unplug it.

---

### Post by StuartN on 2009-05-05
> **wpshooter said:**
> Isn't there a check box under the sound section of Ubuntu which allows you to disable the PC speaker ?

Yes, under System->Preferences->Sound, under the Sounds tab, uncheck the "Play Alert Sound". It disables all beeps without disabling any other sound on my system.

Incidentally, there is also a "Terminal Bell" option in the Profile Preferences of terminal, so you can disable shell beeps without disabling system beeps.

---

### Post by brandoncolorado on 2009-05-05
> **crackdealer said:**
> open your case and unplug it.

Using a netbook.

---

### Post by brandoncolorado on 2009-05-05
> **StuartN said:**
> Yes, under System->Preferences->Sound, under the Sounds tab, uncheck the "Play Alert Sound". It disables all beeps without disabling any other sound on my system.

Incidentally, there is also a "Terminal Bell" option in the Profile Preferences of terminal, so you can disable shell beeps without disabling system beeps.

That is unchecked on my system and the beep still plays.

---

### Post by brandoncolorado on 2009-05-06
Still no luck everyone.

Does anyone know where I can make sure that my volume settings are kept after reboot?  Manually turning off the beep in volume control, and well as manually turning on main volume works, but they are lost with each reboot.

---

### Post by brandoncolorado on 2009-05-08
bump

---

### Post by marmuta on 2009-05-08
brandon, this could be worth a try. The alsa mixer settings like volume levels and switches are stored in /var/lib/alsa/asound.state. For whatever reason this filed may be invalid or not saved/restored at all. Try to rename the old file
```
sudo mv /var/lib/alsa/asound.state /var/lib/alsa/asound.state.old

```
Adjust the volume levels/mute switches in volume control ( or from the terminal with "alsamixer") like you want them.
Then save the settings with
```
sudo /etc/init.d/alsa-utils stop
```
This will create a fresh /var/lib/alsa/asound.state, but mute everything.
To unmute sound and restore the new settings run
```
sudo /etc/init.d/alsa-utils start
```

This should be preserved across boots. If you see any errors please post the output of these commands.


If you still get beeps try running 
```
xset b off
xset b 0 0 0

```
manually in a terminal. If that silences it we can figure out to make it survive reboots.

When do the beeps happen anyway? Boot, shutdown, while working with what?
Edit: just saw it was on shutdown

---

### Post by marmuta on 2009-05-09
Well, I've found I could do without that shutdown beep too. And true, xset or the checkbox in sound properties cannot disable this specific beep, because the "shutdown" command actually asks every single virtual console to beep. In the end this worked for me:

Edit the file /etc/rc.local ```
gksu gedit /etc/rc.local
```and make it look like
```
#!/bin/sh -e
# ...
for console in /dev/tty[1-7]; do setterm -term linux -blength 0 >$console; done
exit 0

```
If the file didn't exist before you may have to make it executable with
```
sudo chmod +x /etc/rc.local

```

Then after rebooting once the shutdown beep should be gone. Well, at least it is for me :). Hope that helps.

---

### Post by brandoncolorado on 2009-05-09
Marmuta,

Thanks for taking the time to write the very helpful response.  I tried everything you mentioned, and I still have the same problem.  This is the case after several shutdowns/reboots.  The xset commands did not silence the problem.

The only way I can get the beep to turn off prior to shutdown is to manually mute the pc beep in the GUI for volume control.

I did find this:  [https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/331589](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux/+bug/331589)

but I am not sure if it applies to me, or what I can do to fix it on my machine.

---

### Post by brandoncolorado on 2009-05-09
> **marmuta said:**
> Well, I've found I could do without that shutdown beep too. And true, xset or the checkbox in sound properties cannot disable this specific beep, because the "shutdown" command actually asks every single virtual console to beep. In the end this worked for me:

Edit the file /etc/rc.local ```
gksu gedit /etc/rc.local
```and make it look like
```
#!/bin/sh -e
# ...
for console in /dev/tty[1-7]; do setterm -term linux -blength 0 >$console; done
exit 0

```
If the file didn't exist before you may have to make it executable with
```
sudo chmod +x /etc/rc.local

```

Then after rebooting once the shutdown beep should be gone. Well, at least it is for me :). Hope that helps.

Thanks, I'll give that a go and report back.

---

### Post by brandoncolorado on 2009-05-09
It worked!  Thanks a million.  That was a major annoyance.  Hopefully others will find this useful too.  As a less-than-advanced Linux user, I have no idea what that command means, but it worked.

---

### Post by marmuta on 2009-05-10
> **brandoncolorado said:**
> It worked!  Thanks a million.  That was a major annoyance.  Hopefully others will find this useful too.  As a less-than-advanced Linux user, I have no idea what that command means, but it worked.

Great! I wonder why the volume/mute settings don't get restored though, that shouldn't happen. You may still want to open a bug for that on launchpad. 

Here is a better readable version of /etc/rc.local. "-term linux" was only necessary for testing from gnome-terminal, so I've removed it here.
```
#!/bin/sh -e
# ...
for console in /dev/tty[1-7]; do 
    setterm -blength 0 >$console
done
exit 0
```
What it does, is to loop through all 6+1 virtual terminals (the ones you can switch to with ctrl+alt+F1-F7) that jaunty has by default and set the beep length (-blength) for each of them to 0ms. Since "shutdown" sends the bell character to every single tty, the beep would slip through if only a single terminal left them enabled, hence the loop. The neat thing about setterm is that it doesn't actually set anything. It just generates invisible control codes that can be easily redirected to the virtual terminals devices /dev/tty1..7. "man setterm" has more.

---

### Post by Ramita de Avellano on 2009-05-22
It worked for me: Dell Inspiron 700m (Jaunty)

Thanks marmuta!!

---

### Post by Cavemann on 2009-06-02
Hi All

Thanks for the above post - I posted this same question problem on my Dell Inspiron 8600 somewhere else just today.

After what others have said it must work.

Maybe I will now not get caught out with closing down late at night and waking everyone including the dog who goes mad barking at the beep sound.

Thanks again

---

### Post by Cavemann on 2009-06-02
Hi All

Thanks a million it worked

Thanks

---

### Post by troyer81 on 2009-06-03
Marmuta, thanks a million.  Both of our machines are now blissfully quiet.  Thanks for the explanation, too.

---

### Post by James Keating on 2009-06-06
This was driving me crazy too. Turning off system sounds in  System > Preferences > Sound doesn't actually turn off the system sounds -- most annoying. An old thread suggested changing the preferences in the Volume Control applet. The applet seems to be set up differently now, but this approach brought me success. Since the Volume Control applet ranks below the Sound preferences, you have to disable beeps in the applet first, then in the system preferences:

1. Click on Volume Control applet.
2. Click on Volume Control ...
3. In the Sound Theme tab, choose "No sounds" for Sound Theme. Close the applet.
4. Go to System > Preferences > Sound
5. Check "Play alerts and sound effects" so you can turn off the options below
6. Uncheck "Play sound effects when buttons are clicked"
7. Uncheck "Play alert sound"
8. Uncheck "Play alerts and sound effects" and close 

If all else fails, a straightforward way to disable Ubuntu system sounds is to remove the executable permission for the directory that contains all system sounds:
     sudo chmod 664  /usr/share/sounds

As a side effect, this will "gray out" the system sound control areas in the volume applet and system sound preferences. If you want to change those again, you have to restore the original permissions with 
      sudo chmod 775   /usr/share/sounds

---

