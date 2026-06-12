---
title: "Funny problem: Don't play start music after boot."
date: 2015-03-21
forum: Desktop Environments
---

### Post by Dmitry_Fry on 2015-03-21
It's normal for 14.04?

---

### Post by deadflowr on 2015-03-22
Do you mean the crickets and drumbeat sound at login?
Your description is lacking.
So it is unclear what you mean.

---

### Post by Dmitry_Fry on 2015-03-22
> **deadflowr said:**
> Do you mean the crickets and drumbeat sound at login?
Your description is lacking.
So it is unclear what you mean.
Yes, a mean [COLOR=#000000]the crickets and drumbeat sound at login. My english poor sorry for this. i have a problem with startup after install ubuntu 14.04 LTS but i solve it
```
[/COLOR][COLOR=#000000][FONT=dejavu sans mono]sudo chown fry:fry ~/.config/autostart[/FONT][/COLOR][COLOR=#000000]
```
maybe [/COLOR]maybe it due this.

---

### Post by buzzingrobot on 2015-03-22
Some speakers, like mine, sleep when they are inactive.  Mine don't wake up until after Ubuntu finishes booting, so I never hear the startup sounds.

---

### Post by Keith_Helms on 2015-03-23
I thought I read somewhere that the sound setting on the login screen was separate from the sound setting once you're logged in and running.  I muted the sound on my login screen to get rid of that annoying drumbeat, but the sound on my desktop comes up unmuted.

---

### Post by Dmitry_Fry on 2015-03-23
> **Keith_Helms said:**
> I thought I read somewhere that the sound setting on the login screen was separate from the sound setting once you're logged in and running.  I muted the sound on my login screen to get rid of that annoying drumbeat, but the sound on my desktop comes up unmuted.
and there is i can fing the sound setting on the login screen?

---

### Post by Dmitry_Fry on 2015-03-23
i think , i need [COLOR=#777777][FONT=arial]choose [/FONT][/COLOR]Correctly soundcard on the login screen

---

### Post by deadflowr on 2015-03-23
The sound card used during login should be which ever soundcard you select during a session.
As this has been my experience, when setting a second soundcard as my default.

As far as the login sound being playable or not, that depends upon whether or not the login sound file is set to autostart.
The login sound startup settings can be found in the file 
> /usr/share/gnome/autostart/libcanberra-login-sound.desktop
the file is a basic .desktop file which looks like
```
[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=GNOME;Unity;
AutostartCondition=GSettings org.gnome.desktop.sound event-sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound
X-GNOME-Autostart-enabled=false
NoDisplay=true

```
if you change the setting from false to true in the X-GNOME-Autostart-enabled line, it'll toggle it on or off; which ever you choose.
You can also make the entry show up in you startup applications file by changing the NoDisplay line to false. Preferred since adding it to the startup applications listing will allow you to toggle, whenever you want, as opposed to need to constantly edit the file.

Note this would need to be done with root rights (sudo/gksu/kdesudo), so not really ideal, IMO.

Also note, you can avoid the file altogether and use your own login sound, if you wish (I do!!!)
You can do so easily by opening the Startup Applications program and clicking on the add option then give whatever name, and in the command line use
```
 canberra-gtk-play --file=filename-goes-here
```
replace filename-goes-here, with the path to the file you want to use; ie, /home/you/Music/some-song.ogg, I do not remember if it plays mp3's well or not, as I set ogg's.

Note that this method is done entirely as you, so no need to run any of it with root rights. Easier, IMO.

If you wish to use the user startup appiications method, but still want to use the Ubuntu login sound, the login sound file can be found in the folder
> /usr/share/sounds/ubuntu/stereo/
The file name is for it is self-explanatory --desktop-login.ogg.

Hope this helps, or makes sense.

---

### Post by Dmitry_Fry on 2015-03-23
Only now do I realize that I do not hear any system sounds, nor about logout or when you shut down. No any.

---

