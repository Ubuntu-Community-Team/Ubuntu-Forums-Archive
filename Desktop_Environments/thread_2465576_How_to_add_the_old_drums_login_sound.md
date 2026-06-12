---
title: "How to add the old drums login sound?"
date: 2021-08-05
forum: Desktop Environments
---

### Post by alro7779 on 2021-08-05
Hi, guys!

I remember the days using Ubuntu 11.09 (I think that was the version) and being prompted to type my login password with that simple but nice drums-sound, and I wonder how can I have that login sound back on my Xubuntu 20.04? Is there someone who'd know how to do that? I'd appreciate it so much.

-Alex.

---

### Post by deadflowr on 2021-08-05
You need the gnome-session-canberra package installed, if not already.
Not sure if it's included in Xubuntu or not.

Then you need to allow it to display in Startup Applications like
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /usr/share/gnome/autostart/libcanberra-login-sound.desktop

```
The option should then show up in Startup Applications, maybe.

Whoops, I forgot, the file is set to only show in GNOME and Unity
You might try setting it to show for all.
In the file */usr/share/gnome/autostart/libcanberra-login-sound.desktop* is a single line shown as
```
OnlyShowIn=GNOME;Unity;
```
you can try commenting that out, which should allow it to show in any desktop, including Xubuntu.

For that you can try a simple sed command again like
```
sudo sed -i 's/Only/#Only/g' /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```

See if that works

> Ubuntu 11.09 (I think that was the version)
11.04 maybe, Since there was no such version as 11.09.
There was also a version 11.10.
So could be either 11.04 or 11.10.

---

### Post by alro7779 on 2021-08-05
Thanks for your answer!
I don't have that */usr/share/gnome/autostart/libcanberra-login-sound.desktop* file, that *autostart* folder only has a **GNOME Login Sound** file which content is:

> [Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
#OnlyShowIn=GNOME;Unity;
AutostartCondition=GSettings org.gnome.desktop.sound event-sounds
X-GNOME-Autostart-Phase=Application
X-GNOME-Provides=login-sound
X-GNOME-Autostart-enabled=false
NoDisplay=false

The 'OnlyShowIn' line I've already commented out, as you can see... and no login sound available at startup yet.

EDIT: I added */usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" *to Session and Startup as a new application, but still the same.

---

### Post by deadflowr on 2021-08-05
Do you have the ubuntu-sounds package installed?
That's the package which contains the actual sound files.

By the way Gnome Login Sound is the same file as the /usr/share/gnome/autostart/libcanberra-login-sound.desktop file.
it just shows as Gnome Login Sound because .desktop files do that.

---

### Post by alro7779 on 2021-08-05
Yes, I have ubuntu-sounds package installed.

---

### Post by deadflowr on 2021-08-06
Yep.
This seems more painful than it should be.
I found this thread: [https://forum.xfce.org/viewtopic.php?id=12609]("https://forum.xfce.org/viewtopic.php?id=12609")
And it's relatively recent, so the suggestions on what to do should still work.

---

### Post by alro7779 on 2021-08-06
I did the steps mentioned on this [link]("https://askubuntu.com/questions/1156774/how-to-enable-event-sounds-on-xubuntu") from 1 to 8, and nothing. I added the code posted to my profile:

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi

GTK_MODULES="$GTK_MODULES:canberra-gtk-module" 
export GTK_MODULES
```

However, if I go to my ubuntu sounds folder, and open up a Terminal there and play whatever sound using the **canberra-gtk-play -f **command, it does work! So, there must be something else.

Here are my outputs from the commands mentioned on this [link]("https://forum.xfce.org/viewtopic.php?id=11952"):

```
~$ xfconf-query -c xsettings -lv | grep -i sound
/Net/EnableEventSounds          true
/Net/EnableInputFeedbackSounds  true
/Net/SoundThemeName             default
```

```
~$ env | grep GTK_MODULE
GTK_MODULES=:canberra-gtk-module
```

```
~$ ls /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)/stereo
ls: cannot access '/usr/share/sounds/default/stereo': No such file or directory
```

```
~$ which canberra-gtk-play
/usr/bin/canberra-gtk-play
```

---

### Post by alro7779 on 2021-08-08
Any other clue, guys?

---

### Post by monkeybrain20122 on 2021-08-09
```
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```

This won't work, if you run the command in the terminal

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Failed to play sound: File or data not found

```

You can check that 'desktop-login' is missing here
```
cd /usr/share/sounds/freedesktop/stereo/
$ ls
alarm-clock-elapsed.oga         dialog-warning.oga
audio-channel-front-center.oga  message-new-instant.oga
audio-channel-front-left.oga    message.oga
audio-channel-front-right.oga   network-connectivity-established.oga
audio-channel-mono.oga          network-connectivity-lost.oga
audio-channel-rear-center.oga   onboard-key-feedback.oga
audio-channel-rear-left.oga     phone-incoming-call.oga
audio-channel-rear-right.oga    phone-outgoing-busy.oga
audio-channel-side-left.oga     phone-outgoing-calling.oga
audio-channel-side-right.oga    power-plug.oga
audio-test-signal.oga           power-unplug.oga
audio-volume-change.oga         screen-capture.oga
bell.oga                        service-login.oga
camera-shutter.oga              service-logout.oga
complete.oga                    suspend-error.oga
device-added.oga                trash-empty.oga
device-removed.oga              window-attention.oga
dialog-error.oga                window-question.oga
dialog-information.oga

```

gnome has removed login sound upstream. 

But it doesn't matter.

Basically you need a command that plays a sound and make it autostart. So there are two pieces, a media player and a sound file. You can choose any player and any sound for that matter and the process is the same, there is nothing special about canberra-gtk-play, you can use vlc if you like and nothing special about gnome's login sound, you can choose any sound file you like. I enabled login sound with 
```

paplay /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
```

You can run this in the terminal and see if you like it

I don't know if the file /usr/share/sounds/ubuntu/stereo/desktop-login.ogg is there by default in xubuntu, if not you can just  install ubuntu-sounds
```
sudo apt install ubuntu-sounds
```

If you don't like the sound you can choose other sound themes e.g oxygen-sounds for kde, or whatever custom sound file that suites your fancy ("happy_birthday_to_you.mp3"?)

so now to make this autostart, just make a .desktop file like your post #3 but replace the 
Exec= 
line with something else (e.g Exec=paplay /usr/share/sounds/ubuntu/stereo/desktop-login.ogg )

Place it in either ~/.config/autostart in your home or in /etc/xdg/autostart for system wide (requires sudo)

---

### Post by Dennis N on 2021-08-10
There were actually two different startup sounds in the old Ubuntus - 8.04, for example. The drums sound played when you reached the login screen. Then, there was a fanfare when you reached the desktop. Using autostart to play a sound file would play after login when you reach the desktop. But that may be good enough.

---

### Post by deadflowr on 2021-08-10
You should only need to change the SoundThemeName from default to ubuntu.

Try this
Open Setting Editor and go down to xsettings in the left side pane.
In the right side (main window area), scroll down to The Net section and look for the SoundThemeName listing.
click on the word *default*, then delete it and enter in *ubuntu* in it's place.
Then close the Setting Editor.
 
Then try testing the command
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```
If it works then try enabling it in the startup program.

To add open Session and Startup in the main menu.
Then go to the Application Autostart and if the Gnome Login Sound option isn't in the listed startup programs then go down and click on the Add button to add the command manually.
Give it some name, any name and the description doesn't usually matter.
And then copy the command into the Command field.
Save and close and exit.
Then logout and see if it works.

Hope that makes sense, or works.

---

### Post by alro7779 on 2021-08-12
I tested that command in the Terminal and it worked!!! So I added it to *Start and Session*, then I logged out and logged in again... and voila! Now I have desktop-login sound!!! However, I did the same with desktop-logout sound, and it doesn't work! 

This is what my desktop-login and desktop-logout files have located in the *autostart* folder:

> [Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Login Sound
Comment=
Exec=/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
OnlyShowIn=XFCE;
RunHook=0
StartupNotify=false
Terminal=false
Hidden=false


> [Desktop Entry]Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Logout Sound
Comment=
Exec=/usr/bin/canberra-gtk-play --id="desktop-logout" --description="GNOME Logout"
OnlyShowIn=XFCE;
RunHook=1
StartupNotify=false
Terminal=false
Hidden=false

The only difference I notice between those two files is the **RunHook** value... I wonder what does that mean. However, I can see the light at the end of the tunnel now.

---

