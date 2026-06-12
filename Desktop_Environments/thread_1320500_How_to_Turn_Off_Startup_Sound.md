---
title: "How to Turn Off Startup Sound"
date: 2009-11-09
forum: Desktop Environments
---

### Post by Cerin on 2009-11-09
This has been asked before, but since Gnome has once again gone through some major UI changes, it bears re-asking.

How do you turn off the Ubuntu startup sound? It used to be System->Preferences->Sound, then scroll to the "startup" sound and disable. But in 9.10, this interface is gone and instead replaced with a "Sound Effect", "Hardware", "Input", "Output", and "Applications" tab. There's no list of the individual sounds played. I tried selecting "No sounds" for the "Sound theme" dropdown, but that annoying dumming sound still plays when the login screen comes up. How do you disable that?

---

### Post by TetonsGulf on 2009-11-09
Try this:

System> Preferences> Start Up Applications

Deselect the Gnome Login Sound and you won't hear it again!

---

### Post by Cerin on 2009-11-09
Beautiful. Thanks!

---

### Post by Cerin on 2009-11-10
Turns out, the sound's still playing, even with "Gnome Login Sound" disabled. Note, I'm talking about the sound that plays when the "Login Screen" comes up, not when a user logs in.

I think the "Login Screen Settings" dialog might have had an option to turn that sound off, but it too seems to have gone through a redesign, and no longer has that option. Any other ideas?

---

### Post by asmythee on 2009-11-11
I found a well hidden fix via google finally.  Run this in a shell:

  [FONT=Calibri]sudo -u gdm gconftool-2[/FONT] [FONT=Calibri]&#8211;[/FONT][FONT=Calibri]-set /desktop/gnome/sound/event_sounds[/FONT] [FONT=Calibri]&#8211;[/FONT][FONT=Calibri]-type bool false[/FONT]


[FONT=Calibri]
[/FONT]

---

### Post by Dullstar on 2009-11-11
<sigh> Everything is more complicated in 9.10.  Dual booting, for one thing, or the Software Center, Add/Remove, and Synaptic error that pulled a Windows (reboot time). ;)  If Lucid Lynx doesn't fix the issues, I may have to use a different distro. :-(

---

### Post by Cerin on 2009-11-12
Yeah, thanks for the fix. It seems to work. It's just frustrating that Gnome keeps losing functionality...

I wish I can say this only happened on Ubuntu, but having come from Fedora, I can say it's a common problem on most distros.

---

### Post by klaatu on 2009-12-05
Well, all I can say guys is, "welcome to Linux".
The final soultion given is a demonstration of how it should be done.
The GUI does nothing but create lazy users. Thats why the average Windows user is useless when things hickup.

You have learned a valuable lesson here, and are richer for it, :)

---

### Post by OliverN on 2009-12-17
> **TetonsGulf said:**
> Try this:

System> Preferences> Start Up Applications

Deselect the Gnome Login Sound and you won't hear it again!

Thank you!

> **klaatu said:**
> Well, all I can say guys is, "welcome to Linux".
The final soultion given is a demonstration of how it should be done.
The GUI does nothing but create lazy users. Thats why the average Windows user is useless when things hickup.

You have learned a valuable lesson here, and are richer for it, :)

While I agree with your main point I personally find that a text-based interface is simply another way of creating "lazy users". *Real* linux-users simply manipulate the transistors of their processors manually using microscopic magnets.
It may well have taken me years to learn how to respond to your post, but once I had the method it was a matter of seconds.

---

### Post by Cerin on 2009-12-17
> **OliverN said:**
> Thank you!



While I agree with your main point I personally find that a text-based interface is simply another way of creating "lazy users". *Real* linux-users simply manipulate the transistors of their processors manually using microscopic magnets.
It may well have taken me years to learn how to respond to your post, but once I had the method it was a matter of seconds.

Cute retort. I too have found the parent's viewpoint deterimental to Linux, and downright annoying. People wonder why the rest of the world doesn't take Linux seriously as a desktop, when you have people like this who expect causal users to fix trivial problems by having 10+ years experience in Linux shell programming.

I love using the command line, but (news flash) the vast majority of people don't. Especially for mind-numbingly trivial things like turning off sound.

---

### Post by VCoolio on 2009-12-18
I think ubuntu is doing pretty ok. I don't like to upgrade every six months and notice nothing has changed. A new version comes with new features. And especially karmic has new stuff that is not yet 100 % evolved, like the new gdm and empathy and the software center. But if you checked before installing you could have known. I like new stuff and features and don't mind googling and messing around to tweak stuff. If you do, stick to lts releases; you'll still have an upgrade each two years.

---

### Post by Baneblade on 2010-02-02
This still isn't working for me. I have tried to remove the sounds from the GUI, I check the startup apps and couldn't find anything relating to sound in there other than the volume manager. The code that was pasted earlier seemed to be accepted fine, but upon reboot the little drum sound still played. I now HATE that little drum.. grrr. lol.

The only solution I have found so far is having the sound muted when I shutdown the machine. This seems to leave the sound muted upon restarting. Not elegant but it stops the whole lecture theatre looking round at me :p

Is there anything I can do to remove this sound permanently? I'm not opposed to removing all the sounds if that is the only solution, I don't use them anyway.

---

### Post by Baneblade on 2010-02-02
Never mind. I seem to have finally found a way to disable it.
The first [solution on here]("http://tacticalvim.wordpress.com/2009/11/27/disable-gdm-ready-sound-in-ubuntu-9-10-karmic/") didnt work for me, however renaming the file to break the simlink seemed to work just fine.

Hope that helps someone :)

---

### Post by Garth Smith on 2010-02-23
> **Baneblade said:**
> ... however renaming the file to break the simlink seemed to work just fine.
Hello!

Is this really the only way to disable the "drums" sound? I need to have a silent boot up, but I'm flabbergasted that this is my only option.

Thanks!
- Garth

---

### Post by VCoolio on 2010-02-24
You can use [gdm2setup]("https://launchpad.net/gdm2setup") to configure gdm and apparently also disable sound. I already disabled all kinds of system sounds and beeps, but the theme and background configuration works fine with this.

---

### Post by clausfse on 2010-04-13
The method proposed by oliverN is easy and works fine for me in Ubuntu 9.10.
Just want to add, that you can even adjust the volume in this way:

As described by oliverN go to 
System->Preferences->Startup Applications
scroll to Gnome Login Sound

a) to mute just uncheck 
b) to change the volume click on "Edit" on the right of the window
and change the entry in the command line
from
/usr/bin/canberra-gtk-play  --id="desktop-login" --description="GNOME Login"
to
/usr/bin/canberra-gtk-play -V -40.0 --id="desktop-login" --description="GNOME Login"

Note, the -V parameter describes the volume in decibel (neg logarithm), so 0 corresponds to full volume and -50 can barely be heard.

Hope that helped.

Claus

---

### Post by fanqi1234 on 2010-04-16
> **Baneblade said:**
> Never mind. I seem to have finally found a way to disable it.
The first [solution on here]("http://tacticalvim.wordpress.com/2009/11/27/disable-gdm-ready-sound-in-ubuntu-9-10-karmic/") didnt work for me, however renaming the file to break the simlink seemed to work just fine.

Hope that helps someone :)

:popcorn:

THANKS A LLOOTTT



Just to celebrate I finally found this solution.
-- I was ready to wipe out all sound files on /

---

### Post by nuchdog on 2010-04-16
try this

1st: alt+F2 and run gconf-editor to open the editor
2nd: untick the active key in order to disable the login ready drums sound in /apps/gdm/simple-greeter/settings-manager-plugins/sound/
3rd: must reboot

This is courtesy of nanonils in another thread

---

### Post by VCoolio on 2010-04-17
> **nuchdog said:**
> try this

1st: alt+F2 and run gconf-editor to open the editor
2nd: untick the active key in order to disable the login ready drums sound in /apps/gdm/simple-greeter/settings-manager-plugins/sound/
3rd: must reboot

This is courtesy of nanonils in another thread

Did you try this? It won't work because you're configuring this as user, while your user isn't active (yet) when the login screen appears. It does so as 'gdm' so you'll have to run a gconftool2 command with 'sudo -u gdm' to use this setting.

---

### Post by jonny163 on 2010-04-28
I am wondering if there is a way to change the login sound, and I think there must be. The login sound is executed in Lucid by:
```
/usr/bin/canberra-gtk-play
```and can be found as mentioned above by going to System > Preferences > Startup Applications > GNOME login sound
Can anyone help meh? >.<

EDIT: I managed to figure out where the login sound is found, /usr/share/sounds/ubuntu/stereo and can hopefully pull it off from here
Sorry to have gone on a tangent :S

---

### Post by VCoolio on 2010-04-28
You could edit the file here to specify what file to play or to do something fancy: /usr/share/gdm/autostart/LoginWindow/libcanberra-ready-sound.desktop

---

### Post by jonny163 on 2010-04-29
I think I'll stick to simple, thanks :P

---

### Post by AlexanderDGreat on 2010-07-19
There have been 2-3 fixes to disable the drums in the Login Screen and it's driving me crazy!

As a group & community, what do you guys think is the Final Simple, Most Basic Answer to our problem?

Please help! Thanks. :)

---

### Post by AlexanderDGreat on 2010-07-19
sudo gconf-editor, unchecking the apps/gdm/simple-greeter/settings-manager-plugins/sound/ ACTIVE - and making it DEFAULT

**Doesn't work in Lucid Lynx!**

---

### Post by roboz on 2010-08-04
> **Cerin said:**
> Turns out, the sound's still playing, even with &quot;Gnome Login Sound&quot; disabled. Note, I'm talking about the sound that plays when the &quot;Login Screen&quot; comes up, not when a user logs in.

I think the &quot;Login Screen Settings&quot; dialog might have had an option to turn that sound off, but it too seems to have gone through a redesign, and no longer has that option. Any other ideas?

 Well after some investigation and trying some of the suggestions in the forum I found that this "bongos" sound in the login screen can be turn of by going to: System -> Administration -> Login Screen . This brings a box with the " Login Screen Settings", and what do you know?... at the top of the list is the option "Play Login Sound". You may need to unlock the settings via the [Unlock] button and provide you password. Then simply "un-check" the option and close the box. All done, no more bongos at the login. I hope this helps.

---

### Post by roboz on 2010-08-04
oops. did mean to repeat the reply.

---

### Post by DigDesignEng on 2010-09-03
Thank you, [AlexanderDGreat]("http://ubuntuforums.org/member.php?u=873200").  This was the not-so-obvious answer that I needed.  Perhaps someone should clarify, but there are two different sounds.  One is the login sound which plays just before you log in, and the other is the gnome startup sound (the annoying one) which plays after the desktop has started. :D

---

### Post by deepakjoy on 2010-12-07
An update for 10.04 (lucid lynx) users. 
To turn off the pre-login sound, go to

system -> administration -> login screen

there you will find a checkbox for disabling sound (and also one for automatic logging in).

check out this link for screenshots [http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/]("http://www.liberiangeek.net/2010/07/disableturnoff-startup-booting-sound-ubuntu-10-04-lucid-lynx/")

---

### Post by yrohinkumar on 2012-01-21
> **AlexanderDGreat said:**
> There have been 2-3 fixes to disable the drums in the Login Screen and it's driving me crazy!

As a group & community, what do you guys think is the Final Simple, Most Basic Answer to our problem?

Please help! Thanks. :)

The most basic way of doing this and a lot of other things is to install "Ubuntu Tweak"... It gets disabling sound very easily...

Just go to "Login Settings" in Ubuntu tweak and uncheck "Play Sound at login"...ta da...:D

Regards,
Rohin!

---

### Post by oldos2er on 2012-01-21
Closed, necromancy.

---

