---
title: "Screen goes blank after ~10 minutes"
date: 2006-07-16
forum: Desktop Environments
---

### Post by sceptre0 on 2006-07-16
I am running Ubuntu 6.06 with XGL.  I set the screen saver to start after 40 minutes and the monitor to go to sleep after an hour.  I don't think it is either of those things.  The screen goes blank after about 10 minutes, which is very annoying when watching a movie.  Is it a problem with XGL?  Any input would be appreciated.

---

### Post by adam.tropics on 2006-07-16
I believe it is a problem with xgl yes, and I am not sure there is a fix yet. Very annoying! That said, using xgl, you might get better peroformance watching movies by logging out of xgl and into a normal gnome session anyway. In which case this will not happen.

---

### Post by tigrez on 2006-07-16
I've the same problem, but I've not installed Xgl. 

It seem a gnome-power-manager problem. I've completly remove from session startup, and now it seem to be solved.

---

### Post by citizenr on 2006-07-16
add
        Option "BlankTime" "0" #This blanks screen
        Option "StandbyTime" "0" #This is DPMS
        Option "SuspendTime" "0" #DPMS
        Option "OffTime" "0" #DPMS

to xorg.conf

---

### Post by adam.tropics on 2006-07-16
> **citizenr said:**
> add
        Option "BlankTime" "0" #This blanks screen
        Option "StandbyTime" "0" #This is DPMS
        Option "SuspendTime" "0" #DPMS
        Option "OffTime" "0" #DPMS

to xorg.conf

except I can comment out DPMS completely, which should prevent it, and it still happens!

Will have a look at gnome power manager in startup. but not too keen on that one really.

---

### Post by sceptre0 on 2006-07-16
I have tried both adding those lines to xorg.conf and removing the power manager from startup and neither of those solutions worked.  I should also point out this only happens on my desktop computer.  My laptop computer with Ubuntu 6.06 does not blank the screen.  My laptop does not have Xgl installed.  It must be a bug with Xgl.  Thanks for replying so quickly.

---

### Post by targaman on 2006-07-17
I'm a new user, but I have a few more data points for this problem. My systems don't run XGL and are essentially default installs from downloaded ISOs.

I installed Kubuntu 6.06 on my laptop and had the screen blacking out problem both when running the Live CD and during installation. It continued after the full install and was so annoying that I decided to blow the installation away and try Ubuntu 6.06 which is running happily on a desktop.

The Ubuntu installation ran flawlessly with no screen blanking out, and all was fine after the installation completed. Then I made the fatal mistake of allowing the system to update itself. After the update, the screen blanking problem appeared just as with Kubuntu, although perhaps not quite as often. I also noticed that, after a system restart not long after the problem started again, the fonts in the login screens (where you enter user name and password) had changed from the nice proportional fonts to what looked like monospace fonts.

I hope this extra information will help with diagnosis of the problem.

In the meantime, how do I roll back to the working pre-update configuration?

---

### Post by domino on 2006-07-25
You know, this is so goddamn pathetic. Why is this stupid option even in Linux if no one can disable it and no documentation on disabling the stupid 10min blank screen worthless POS. I have searched for the solution the past 3 week. Turned of APM, ACPI*, even tinkered with the damn BIOS. Why the f* is this feature even in Linux?

Someone give me a damn explanation so I can stop bitching about it and finally watch my TV shows without moving the damn mouse every damn 10 min. We manage to install xgl/compiz but can't manage to turn off this simple f*ing feature.

---

### Post by easyease on 2006-07-25
i reccomend using Kaffeine player to watch movies as it does "fake" keypresses to stop the screen saver etc kicking in.

---

### Post by domino on 2006-07-25
Well it aint that easy, easy. i have my TV tuner working like a champ and this worthless "bug" keeps kicking in every 10min. So far this is what I have done:

- commented out all instances of DPMS in xorg.conf
- pasted all on this page's Post #4 comment to xorg.conf
- disable acpi-support using sysv-rc-conf
- disable acpid using sysv-rc-conf 
- disable apmd using sysv-rc-conf
- removed those last 3 I disabled from reboot and restart script
- Changed my BIOS APM config and tested changes

What the hell else is a person suppose to do to get rid of this busted stepchild? I mean, who the hell cares if the screen turns black but the backlight is still on? What f*ing use is that?

---

### Post by fberbert on 2006-08-08
Hi all,

I had the same problem and google sends me to this page. As I saw that is no solution, I tried by myself and I think I found a solution.

Try:

Xgl --help

There is the following option:

-s #                   screen-saver timeout (minutes)

Hmmmm, very interesting. I just changed my Xgl start command line adding, for example, "-s 300". Now I can watch movies without shake my mouse for 300 minutes :)

Well, I don't know if it works yet, but I post this here because after restart my X, I probaly will not come back here. hehehe

Good luck!!!

Fabio Berbert de Paula

---

### Post by hexion on 2006-08-09
Same here.

2 weeks with the problem...

- Deactivated gnome-power-manager with session manager.
- Tried to quit DPMS from xorg.conf
- Added lines to xorg.conf like [Option "BlankTime" "0"] and so.
- Added option -s 9999 at Xgl script (startxgl.sh)
- Played with command xset (view [http://www.shallowsky.com/linux/x-screen-blanking.html]("http://www.shallowsky.com/linux/x-screen-blanking.html"))


NOTHING WORKS :(

I'll check this thread for if someone finds the solution.

Best regards.

---

### Post by domino on 2006-08-10
This one worked for me, thanks to a member at compiz.net for taking 5 minutes of his time to post it.

[quote=WiLLiE]Perhaps use something like this in your xorg.conf?

```
Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection
```[/quote]

---

### Post by hexion on 2006-08-10
IT WORKED!!!!!!!!!!!!!!!!!!!!

FINALLY!!!!!!!!!!!!!


Thank you! :)

---

### Post by sceptre0 on 2006-08-14
Hats off to you, domino.  It worked.  Thanks for passing along the info.

---

### Post by bahrain on 2007-03-01
this problem still in edgy.

i'll try what domino wrote.

---

### Post by macabro22 on 2007-12-16
> Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

Sweet. Thanks for the info.

---

### Post by d_fiant_1 on 2007-12-19
This one worked for me, thanks to a member at compiz.net for taking 5 minutes of his time to post it.

Quote:
Originally Posted by WiLLiE
Perhaps use something like this in your xorg.conf?

Code:

Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

FANTASTIC...it works for me...editted xorg.conf 24 hours ago, left on over night and started this morning with NO black screen...thank you

---

### Post by jhorner on 2007-12-19
Added this to my Xorg and it killed my GUI.  Thankful for the backups...

Any other suggestions?  I am not running XGL, just basic KDE 7.10 on a T23 laptop.

---

### Post by Vinno on 2007-12-19
Hope this doesnt sound stupid, sure it isnt just the screensaver that go's on? mine is set to blank screensaver by default i think.

---

### Post by stingx on 2007-12-20
This isn't screensaver. I've messed with this problem for a long time. As I could see this problem is not ACPI or whatever hardware blanking. Screen is still exists, but X just draw a black frame to all screen. It is stupid default option for X server, that need to be changed in future releases.

---

### Post by jhorner on 2007-12-20
Not a stupid question.  

No it's not the SS.  First the screen saver is different than a blank screen, second the screen tends to go blank >10 mins and the SS is set to 15 min.

---

### Post by cartisdm on 2007-12-20
So....what's the solution? I have this same problem whenever I try to watch movies.

---

### Post by cartisdm on 2007-12-20
With a little searching around I found this.  I don't know yet if it works but it's worth a shot.

> I think I finally resolved the problem. I used the Configuration Editor (gconf-editor from the command prompt) and it lets you tweak a lot of settings. Check the settings under:

/apps/gnome-screensaver/idle_delay

Set this value to zero, or set it to a very high value.

---

### Post by cartisdm on 2007-12-22
don't know if this is quite the same problem you were having but take a look at this thread

[http://ubuntuforums.org/showthread.php?p=3997204#post3997204]("http://ubuntuforums.org/showthread.php?p=3997204#post3997204")

---

