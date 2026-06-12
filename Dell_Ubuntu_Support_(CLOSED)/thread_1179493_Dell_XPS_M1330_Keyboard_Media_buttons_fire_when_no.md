---
title: "Dell XPS M1330 Keyboard Media buttons fire when not touched"
date: 2009-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gsal17 on 2009-06-05
I cannot even figure out what makes this happen.  The touch media control buttons on the top of the keyboard (by the power switch with eject, prev., stop, etc.) turn on and off without being touched.  This has become a very annoying problem that has happened since I bought this computer preinstalled with ubuntu. Even if the solution would be to make them not work at all I would be happy since when they do fire, the eject button actually makes the cd drive try to eject a non existent cd. 

Note: I have disabled all the keyboard sound shortcuts in the System->Preferences-> Keyboard shortcuts

---

### Post by coffeeaddict22 on 2009-06-06
Sounds like someone/ thing has monkeyed with your keyboard assignments.  What version of Linux?  What sort of keyboard have you told the system it's got on it(System/Preferences/Keyboard)?  
Be warned, Linux has moved in the last few months from using xorg.conf for input control to HAL.  The documentation, it's fair to say, hasn't completely caught up.  Have a look [at this Debian page]("http://wiki.debian.org/XStrikeForce/InputHotplugGuide") and [on the Ubuntu wiki]("https://wiki.ubuntu.com/X/Config#hal") for a bit more info.

---

### Post by gsal17 on 2009-06-07
Right now it is set to Generic 105-key (Intl) PC
Do you think that changing this to a dell specific keyboard layout will help with these buttons just doing what they want?

---

### Post by coffeeaddict22 on 2009-06-07
It'll help, almost certainly, but there's a few other things you can try if it doesn't fix it all. 
Have a look at [this, ]("http://ubuntuforums.org/showthread.php?p=6527653#poststop") but only if you aren't paranoid.  Essentially, you should be able to get most of them working, the DSDT seems to be more about the non-standard hardware keys so might be off-topic for you.  There's also been a few BIOS upgrades from Dell lately that have helped- have a look [here for them.]("http://linux.dell.com/projects.shtml")

---

### Post by gsal17 on 2009-06-09
Sorry I am rather new to this whole experience so you will have to bare with me.  I can get them to work (meaning I can have them set to control the media (eject, prev. stop, etc.)) The problem comes when they just start engaging (the blue square around them lights up and if they are set up to actually control anything, they do that action) This is annoying because I am not controlling when they fire.  The buttons are temperature triggered and if I run my finger over them they all work (meaning light up) and if programmed they do their desired task. The problem is when I don't touch them, they still fire and if programmed, do the task (meaning they change my song or eject a cd without me touching them.)

I don't know if it is hardware based and it has been wrong the whole time or if there is a way to change the temperature at which the activate (it seems to happen more often when the computer is hotter and it seems like this may be the desired solution)

---

### Post by coffeeaddict22 on 2009-06-09
Are you dual booting?  If you are, does it happen in another OS?
As a long shot, it might be worth looking at motherboard operating temp.  System gremlins aren't a lot of fun tracking down; however, it's probably worth starting with the sytem temp.  Linux and system cooling have had a bit of a strange and unique relationship.
Get a computer temp monitor applet (there's one in the Add/ Remove Applications panel, and another couple in Synaptic Package manager- System/Admin/Synaptic); keep an eye on your system temp and see if things are getting too hot.

---

### Post by t2a on 2009-06-17
I acknowledge this issue. Having the same problem in Jaunty as in Hardy. I also have chosen the same keyboard. 

Somewhere I read that this problem could relate to pulseaudio. So I did an un-install apt-get remove pulseaudio --purge

Just did that today, so let's see what happens. I get back!

Cheers,
Raymond.

---

