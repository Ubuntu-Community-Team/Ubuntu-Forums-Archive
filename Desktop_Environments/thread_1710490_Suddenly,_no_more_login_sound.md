---
title: "Suddenly, no more login sound"
date: 2011-03-19
forum: Desktop Environments
---

### Post by kerke on 2011-03-19
[SIZE=2]Suddenly, when I login to my Ubuntu 10.10 user account, I no-longer hear the login sound (desktop-login). What's interesting is that if I login using any other user account, the login sound plays OK. All setting (*System > Preferences > Startup Applications* and *System > Preferences > Sound*) are exactly the same for my user account and the other user accounts.

Where could I find the login sound configuration settings in my home directory? Something tells me that a configuration setting in my own home directory must be messed up, then again I may be wrong.

Does anybody know what may be happening here?

Thank you in advance,

Kerke

[/SIZE]

---

### Post by nickleboyblue on 2011-03-20
In System->Preferences->Sound you can select a sound theme.  If the sound theme that you have selected is "No Sound," you will not get a login sound.

This, for me, is the preferred behavior.  I have a laptop, and it's annoying when I have to start it in one of my classes and it announces the fact to the world.

If that's not your problem, I've no idea what is.

---

### Post by kerke on 2011-03-20
> **nickleboyblue said:**
> In System->Preferences->Sound you can select a sound theme.  If the sound theme that you have selected is "No Sound," you will not get a login sound.

This, for me, is the preferred behavior.  I have a laptop, and it's annoying when I have to start it in one of my classes and it announces the fact to the world.

If that's not your problem, I've no idea what is.

My  *System > Preferences > Sound > Sound Theme* is Ubuntu.

---

### Post by Krytarik on 2011-03-20
Ok, you did say that all settings in "Preferences -> Sound" are exactly the same in both user accounts. But just to make sure, the "Alert volume" is set to a reasonable level and "Mute" is not ticked, right?

And check the command for "Startup Applications -> GNOME Login Sound", it should be like this:
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```Also, do you have a file named ".asoundrc" or similar in your home directory?
Although this post is bit older: [http://ubuntuforums.org/showthread.php?t=421482](http://ubuntuforums.org/showthread.php?t=421482)

---

### Post by kerke on 2011-03-20
> **Krytarik said:**
> Ok, you did say that all settings in "Preferences -> Sound" are exactly the same in both user accounts. But just to make sure, the "Alert volume" is set to a reasonable level and "Mute" is not ticked, right?

And check the command for "Startup Applications -> GNOME Login Sound", it should be like this:
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```Also, do you have a file named ".asoundrc" or similar in your home directory?
Although this post is bit older: [http://ubuntuforums.org/showthread.php?t=421482](http://ubuntuforums.org/showthread.php?t=421482)

Krytarik, here are the settings:

All my settings in "Preferences > Sound" are exactly the same on all other user accounts.

The "Alert Volume" is not "Mute" and the slider is set all the way to the left (would that be zero?). However, all other user accounts also have the "Preferences > Sound > Alert Volume" slider set all the way to the left -- their login sounds work OK, but not with my user account. In fact, it looks like the "Alert Volume" slider is set all the way to the left by default but that doesn't prevent the login sound to work, except for my user account :mad:

My "Startup Applications > GNOME Login Sound" is exactly like yours:
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```.

I don't have a file named ".asoundrc" or similar in my home directory.

To find out where are the "Preferences > Sound" configuration settings saved, I opened the "Preferences > Sound" and changed the Sounds from "Ubuntu" to "No Sounds" and back to "Ubuntu". Then, from the GNOME Terminal I typed "find -mmin .5" to find files modified in the last 30 seconds. It looks like  the "Preferences > Sound" configuration settings are saved in this XML file: ```
.gconf/desktop/gnome/sound/%gconf.xml
```. Here's the content of my ```
.gconf/desktop/gnome/sound/%gconf.xml
``` file:

```

<?xml version="1.0"?>
<gconf>
    <entry name="input_feedback_sounds" mtime="1300570402" type="bool" value="false"/>
    <entry name="theme_name" mtime="1300630529" type="string">
        <stringvalue>ubuntu</stringvalue>
    </entry>
    <entry name="event_sounds" mtime="1300630529" type="bool" value="true"/>
</gconf>

```

And here's the content of the other user accounts' ```
.gconf/desktop/gnome/sound/%gconf.xml
``` file:

```

<?xml version="1.0"?>
<gconf>
    <entry name="theme_name" mtime="1300587493" type="string">
        <stringvalue>ubuntu</stringvalue>
    </entry>
    <entry name="event_sounds" mtime="1300587493" type="bool" value="true"/>
</gconf>

```

I tried deleting my ```
.gconf/desktop/gnome/sound/%gconf.xml
``` file, it didn't make a difference. I tried replacing my ```
.gconf/desktop/gnome/sound/%gconf.xml
``` file content with the one from another user, no difference :mad:

I realize this is by no means a huge problem, but I'd like to know if this issue is caused by a bug or is it something I did? Regardless of the cause, this is bothering me and I'd really like to find the culprit.

Krytarik, by the way, I followed your advice from yesterday and changed my forum user name ;-)

Thank you in advance,

---

### Post by Krytarik on 2011-03-20
> **kerke said:**
> 
The "Alert Volume" is not "Mute" and the slider is set all the way to the left (would that be zero?).
Yeah, that means "zero". Just try sliding it to the middle.
If you want to manually reset "gconf" settings, you can run a command like this:
```
gconftool --recursive-unset /desktop/gnome/sound
```But I don't believe that it helps in this case, thus I didn't mention it.
> **kerke said:**
> 
Krytarik, by the way, I followed your advice from yesterday and changed my forum user nameCool, that was you! :)

---

### Post by kerke on 2011-03-20
> **Krytarik said:**
> Yeah, that means zero. Just try sliding it to the middle.
If you want to manually reset "gconf" settings, you can run a command like this:
```
gconftool --recursive-unset /desktop/gnome/sound
```But I don't believe that it helps in this case, thus I didn't mention it.
Cool, that was you! :)

 Krytarik, I moved the Alert Volume slider to the middle and the login sound came back, loud and clear. All is well now :D

Thank you!!!!

---

### Post by Krytarik on 2011-03-20
> **kerke said:**
> Krytarik, I moved the Alert Volume slider to the middle and the login sound came back, loud and clear. All is well now :D

Thank you!!!!
You're welcome!

But what is indeed curious, is that the same setting apparently works in the other user accounts!

---

