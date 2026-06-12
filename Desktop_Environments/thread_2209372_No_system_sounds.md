---
title: "No system sounds"
date: 2014-03-05
forum: Desktop Environments
---

### Post by Marvel0169 on 2014-03-05
Hello everyone, I am  a newbie of Linux world and I approached it via Ubuntu 13.10. I am happy to be with you. I hope you have patience with a newbie like me.:)

  
Eventually, after obvious hardware problems, I have an old pc, with celeron 2GHz, 1Gb ram, hdd 150 Gb, I gave up and switched from ubuntu 13.10 to xubuntu 12.04LTS and everything has improved. 

  First of all the performance videos are now normal and smooth, then the audio now works for "almost" everything. I can hear the music CDs, movies, youtube, audio files but I still can not hear xubuntu system sounds, like the sounds of windows so to speak. 
I tried to follow these guidelines (in italian language), 
  [http://www.xfce-italia.it/index.php?topic=1726.0](http://www.xfce-italia.it/index.php?topic=1726.0), and, finally, I managed to create two files in the folder Xsession.d, but I had to give the command 
  sudo leafpad / etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules, otherwise  the file was created in the X11 folder and not in Xsession.d folder, however I was wrong because now I have the two files in X11 folder and in Xsession.d folder ...
     I checked again these steps (translating by Italian, I hope readable in English): 
1) "then go into dconf editor / org / gnome / desktop / enable sound event sounds and sound feedback and theme ubuntu". 

2) "in settings-editor settings xsetting / net / soundthemename ubuntu". 

3) retried the command "play / usr / share / sounds / ubuntu / stereo / desktop-login.ogg" and confirm that the sound you hear. 

4) controlled canberra that were installed with the command sudo apt-get install canberra and the result was that everything was already in place and there was nothing to install. 

However, the system sounds still do not feel ... 
Any idea, please? 

Many thanks! Ciao! 

Marco

---

### Post by Toz on 2014-03-05
Hello and welcome to the forums.

[This link]("http://ubuntuforums.org/showthread.php?t=2156763&p=12702910&viewfull=1#post12702910") still works for me. Can you confirm that you have all items completed? Also make sure that the System sounds are turned up in pavucontrol.

---

### Post by Marvel0169 on 2014-03-05
Hi Toz, thanks for your reply! I completed the items listed in my post, but in your link there are more that I have not completed. This afternoon I will try soon to follow all your suggestions!! 

Many thanks, ciao!

Marco

---

### Post by Marvel0169 on 2014-03-06
Hi Toz, well, yesterday I tried to follow the instructions of the link you suggested.

Step 1) ok, done.

Step2) points 1 and 2 ok.[INDENT]point 3: - xsettings/net/SoundThemeName = (a name of a sound theme - they are located in /usr/share/sounds)
I am confused: when I go in the line as above, right click on the right side of the highlighted line it open a windows with a path. I must write just "Ubuntu" or I must to coplete the line as: /net/SoundThemeName/ubuntu or /net/SoundThemeName/ubuntu/stereo (the sounds are in a folder called "stereo" inside the ubuntu folder)?
[/INDENT]
Step 3) ok, done. 
gksu mousepad /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-module

I wrote "sudo leafpad....." I think is the same for the final results...
Step 4) Create a login sound event by command line:
leafpad ~/.xprofile

Then I add the line: "canberra-gtk-play -V 0.1 -f </path/to/login/sound/file> &". I wrote this path: /usr/share/sounds/ubuntu/stereo/*namefile*.ogg. It is right?

*"Then make that file executable"*: I must to give the command: "chmod +x ~/.xprofile" by the command line again?

Step 5) ok, done, but not sounds....:(...

Many thanks for all your help and be patience please, I am a beginner in Xubuntu environment and the command line is practically unknown coming from a Windows environment. 
I hope that what I have written above is understandable. 

Ciao!

Marco

---

### Post by Toz on 2014-03-06
> **Marvel0169 said:**
> 
point 3: - xsettings/net/SoundThemeName = (a name of a sound theme - they are located in /usr/share/sounds)
I am confused: when I go in the line as above, right click on the right side of the highlighted line it open a windows with a path. I must write just "Ubuntu" or I must to coplete the line as: /net/SoundThemeName/ubuntu or /net/SoundThemeName/ubuntu/stereo (the sounds are in a folder called "stereo" inside the ubuntu folder)?
Just the one word of the theme name. So in your case, "Ubuntu" (no quotes)

> Then I add the line: "canberra-gtk-play -V 0.1 -f </path/to/login/sound/file> &". I wrote this path: /usr/share/sounds/ubuntu/stereo/*namefile*.ogg. It is right?Yes, looks right.

> Step 5) ok, done, but not sounds....:(...

Can you post back the results of the following commands:
```
xfconf-query -c xsettings -p /Net/EnableEventSounds
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
xfconf-query -c xsettings -p /Net/SoundThemeName
ls -l /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)
cat /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
cat /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
cat ~/.xprofile
ls -l ~/.xprofile

```

Have you adjusted your "System Sounds" volume?
Have you rebooted?

---

### Post by Marvel0169 on 2014-03-07
Hi Toz, thanks for you reply! I will do as you suggest soonest.

> Have you adjusted your "System Sounds" volume?

Yes, I checked by pulseaudio. When I move the left/right slides in the output devices tag I hear sounds, as "click-clock", but they are the only sounds I heard...:(

> Have you rebooted?

Yes....but no positive results....

I will report you the results of your directions. :)

Many thanks!! Ciao!

Marco

---

### Post by Toz on 2014-03-07
> **Marvel0169 said:**
> Yes, I checked by pulseaudio. When I move the left/right slides in the output devices tag I hear sounds, as "click-clock", but they are the only sounds I heard...:(
Then it works. 

The issue that you are going to run into is that there really aren't any good Xfce sound themes. According to the [canberra implementation]("https://gitorious.org/libcanberra/mainline/source/ac5ac9e486aa33f7be0cd9ddd315c03780676795:src/canberra-gtk-module.c#L3"), only the following sound effects are supported:
> /*
We generate these sounds:
dialog-error
dialog-warning
dialog-information
dialog-question
window-new
window-close
window-minimized
window-unminimized
window-maximized
window-unmaximized
notebook-tab-changed
dialog-ok
dialog-cancel
item-selected
link-pressed
link-released
button-pressed
button-released
menu-click
button-toggle-on
button-toggle-off
menu-popup
menu-popdown
menu-replace
tooltip-popup
tooltip-popdown
...meaning that you need to have those files in your /usr/share/sounds/SOUND_THEME/stereo folder.

Try using [this]("https://www.dropbox.com/s/bfyk05r4y8qog2c/usr_share_sounds_borealis.tar.gz") sound theme instead. Its one that I've been working on that's based on the [original Borealis theme]("http://gnome-look.org/content/show.php?content=12584") that complies better with [freedesktop sound spec]("http://0pointer.de/public/sound-naming-spec.html") and the canberra implementation of it. Its not perfect, but it has many more sound effects.

---

### Post by Marvel0169 on 2014-03-07
Hi Toz, okay, I will try all you suggested and I will report the results.

Many thanks for all your help!! Ciao!):P

Marco

---

### Post by Marvel0169 on 2014-03-07
Hi Toz, these the results of commands:

> xfconf-query -c xsettings -p /Net/EnableEventSounds
TRUE

> xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
TRUE

> xfconf-query -c xsettings -p /Net/SoundThemeName
DEFAULT

> ls -l /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)
ls: impossibile accedere a /usr/share/sounds/default: File o directory non esistente

> cat /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
if [ -z "$GTK_MODULES" ] ; then
    GTK_MODULES="canberra-gtk-module"
else
    GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi
export GTK_MODULESmarco@marco-desktop:~$ 

> cat /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
if [ -z "$GTK_MODULES" ] ; then
    GTK_MODULES="canberra-gtk-module"
else
    GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi
export GTK_MODULESmarco@marco-desktop:~$ 

> cat ~/.xprofile
canberra-gtk-play -V 0.1 -f /usr/share/sounds/freedesktop/stereo/service-login.ogg &marco@marco-desktop:~$ 

> ls -l ~/.xprofile
-rwxrwxr-x 1 marco marco 84 mar  5 18:30 /home/marco/.xprofile


What do you think about?
Many Thanks!

Ciao.

Marco

---

### Post by Toz on 2014-03-07
> [QUOTE]xfconf-query -c xsettings -p /Net/SoundThemeName
DEFAULT
[/QUOTE]
This one is incorrect. Change it to the name of the theme that you want. For example, if you are using the freedesktop sound theme, change it to read **freedesktop**. To make the change, use the Settings Editor in the Settings Manager.

---

### Post by Marvel0169 on 2014-03-10
Hi Toz, thanks for your reply! Ok, I will set as you suggest. I downloaded Borealis sound theme also, but I could not to istall it in 
/usr/share/sounds/. I unpackaged Borealis in docoments and after I tried to move it to /usr/share/sounds/ but it doesn't work.... 
Which is the command by command line to set Borealis in the right place, please?

Many thanks! Ciao!

Marco

---

### Post by Toz on 2014-03-10
/usr/share/sounds is a restricted area on your hard drive - you need root access to copy the files there. Try this command:
```
sudo cp -r Borealis /usr/share/sounds
```
...from the directory where Borealis was uncompressed.

---

### Post by Marvel0169 on 2014-03-10
Thanks a lot Toz, I will try soonest :) !

Ciao!

Marco

---

### Post by Marvel0169 on 2014-03-10
> **Toz said:**
> /usr/share/sounds is a restricted area on your hard drive - you need root access to copy the files there. Try this command:
```
sudo cp -r Borealis /usr/share/sounds
```
...from the directory where Borealis was uncompressed.

Hi Toz, well, surely I could be wrong this time also! Now the situation of Borealis is as follow:
File system/usr/share/sounds/Borealis/usr/share/sounds/Borealis/stereo...etc...

Now how can I delete Borealis folder and install it correctly? I have the uncompressed Borealis in "home". Follow the path: marco/documents/Borealis/usr/share/sounds/Borealis/stereo...etc...

Many thanks for your help and patience. Ciao!

Marco

---

### Post by Toz on 2014-03-10
Try:
```
sudo cp -r /usr/share/sounds/Borealis/usr/share/sounds/Borealis/stereo /usr/share/sounds/Borealis
sudo mv /usr/share/sounds/Borealis/usr /tmp
```
...and on next reboot, /tmp will be cleared.

---

### Post by Marvel0169 on 2014-03-13
Hi Toz, well, I done, now Borealis is in the right place...:).

I checked whith command xfconf-query -c xsettings -p /Net/SoundThemeName and the results is always "default".

I check also setting editor xsettings/net/soundthemename...etc and I tried to set borealis. When I click on soundthemename a windows opened and i tried several times to set as follow, /net/soundthemename/borealis/stereo or net/soundthemename/borealis or only borealis (not permitted this last test) but no sounds however.
Now I have two "SoundThemeName": one as soundthemename/borealis/stereo (stereo has "true" in his  right side);
another as soundthemename/borealis/stereo whit Soundthemename has "default" in the his right side.

Sincerely I am really confused....

Any ideas...?

Many thanks! Ciao!

Marco

---

### Post by Toz on 2014-03-13
> **Marvel0169 said:**
> Hi Toz, well, I done, now Borealis is in the right place...:).

I checked whith command xfconf-query -c xsettings -p /Net/SoundThemeName and the results is always "default".

I check also setting editor xsettings/net/soundthemename...etc and I tried to set borealis. When I click on soundthemename a windows opened and i tried several times to set as follow, /net/soundthemename/borealis/stereo or net/soundthemename/borealis or only borealis (not permitted this last test) but no sounds however.
Now I have two "SoundThemeName": one as soundthemename/borealis/stereo (stereo has "true" in his  right side);
another as soundthemename/borealis/stereo whit Soundthemename has "default" in the his right side.

Sincerely I am really confused....

Any ideas...?

Many thanks! Ciao!

Marco

First, run this command to set Borealis as the sound theme:
```
xfconf-query -c xsettings -p /Net/SoundThemeName -s Borealis
```

Secondly, can you post back the results of this command:
```
ls /usr/share/sounds/Borealis/*
```

---

### Post by Marvel0169 on 2014-03-14
Hi Toz, thanks for your help. 
Results of "xfconf-query -c xsettings -p /Net/SoundThemeName -s Borealis": none, no results or system message.

Results of "ls /usr/share/sounds/Borealis/*"
```
button-pressed.ogg        dialog-warning.ogg       Startup1_1.ogg
button-toggle-off.ogg     Exit1_2.ogg              Startup1_2.ogg
button-toggle-on.ogg      install.sh               Startup1_3.ogg
desktop-login.ogg         K3b_success.ogg          system-ready.ogg
desktop-logout.ogg        Knock.ogg                trash-empty.ogg
desktop-switch-left.ogg   Kopete_status.ogg        uninstall.sh
desktop-switch-right.ogg  message-new-instant.ogg  window-close.ogg
device-added.ogg          phone-incoming-call.ogg  window-maximized.ogg
device-removed.ogg        phone-outgoing-busy.ogg  window-minimized.ogg
dialog-error.ogg          README                   window-unmaximized.ogg
dialog-information.ogg    service-login.ogg        window-unminimized.ogg
dialog-question.ogg       service-logout.ogg

```

Next step? 

Thanks a lot! Ciao!

Marco

---

### Post by Toz on 2014-03-14
> **Marvel0169 said:**
> Hi Toz, thanks for your help. 
Results of "xfconf-query -c xsettings -p /Net/SoundThemeName -s Borealis": none, no results or system message.
What does the following now return:
```
xfconf-query -c xsettings -p /Net/SoundThemeName
```

> Results of "ls /usr/share/sounds/Borealis/*"
```
button-pressed.ogg        dialog-warning.ogg       Startup1_1.ogg
button-toggle-off.ogg     Exit1_2.ogg              Startup1_2.ogg
button-toggle-on.ogg      install.sh               Startup1_3.ogg
desktop-login.ogg         K3b_success.ogg          system-ready.ogg
desktop-logout.ogg        Knock.ogg                trash-empty.ogg
desktop-switch-left.ogg   Kopete_status.ogg        uninstall.sh
desktop-switch-right.ogg  message-new-instant.ogg  window-close.ogg
device-added.ogg          phone-incoming-call.ogg  window-maximized.ogg
device-removed.ogg        phone-outgoing-busy.ogg  window-minimized.ogg
dialog-error.ogg          README                   window-unmaximized.ogg
dialog-information.ogg    service-login.ogg        window-unminimized.ogg
dialog-question.ogg       service-logout.ogg

```
Please run these commands:
```
sudo mkdir /usr/share/sounds/Borealis/stereo
sudo mv /usr/share/sounds/Borealis/*.ogg /usr/share/sounds/Borealis/stereo
```

---

### Post by frank18 on 2014-03-14
> **Marvel0169 said:**
> Hello everyone, I am  a newbie of Linux world and I approached it via Ubuntu 13.10. I am happy to be with you. I hope you have patience with a newbie like me.:)

  
Eventually, after obvious hardware problems, I have an old pc, with celeron 2GHz, 1Gb ram, hdd 150 Gb, I gave up and switched from ubuntu 13.10 to xubuntu 12.04LTS and everything has improved. 

  First of all the performance videos are now normal and smooth, then the audio now works for "almost" everything. I can hear the music CDs, movies, youtube, audio files but I still can not hear xubuntu system sounds, like the sounds of windows so to speak. 
I tried to follow these guidelines (in italian language), 
  [http://www.xfce-italia.it/index.php?topic=1726.0](http://www.xfce-italia.it/index.php?topic=1726.0), and, finally, I managed to create two files in the folder Xsession.d, but I had to give the command 
  sudo leafpad / etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules, otherwise  the file was created in the X11 folder and not in Xsession.d folder, however I was wrong because now I have the two files in X11 folder and in Xsession.d folder ...
     I checked again these steps (translating by Italian, I hope readable in English): 
1) "then go into dconf editor / org / gnome / desktop / enable sound event sounds and sound feedback and theme ubuntu". 

2) "in settings-editor settings xsetting / net / soundthemename ubuntu". 

3) retried the command "play / usr / share / sounds / ubuntu / stereo / desktop-login.ogg" and confirm that the sound you hear. 

4) controlled canberra that were installed with the command sudo apt-get install canberra and the result was that everything was already in place and there was nothing to install. 

However, the system sounds still do not feel ... 
Any idea, please? 

Many thanks! Ciao! 

Marco

Funny i did the other way around, i have also an old Dell P4 2.0 ghz cpu 1ghz ram,  I had Xubuntu  12.04lts  and updated to Xubuntu 13.10 Beta and i notice difference for better.

---

### Post by Marvel0169 on 2014-03-15
Hi Toz, here the results for the command you suggested:

```
xfconf-query -c xsettings -p /Net/SoundThemeName
```
Borealis

```
sudo mkdir /usr/share/sounds/Borealis/stereo
```
mkdir: impossibile creare la directory "/usr/share/sounds/Borealis/stereo": File già esistente
*(mkdir: impossible to create directory "/usr/share/sounds/Borealis/stereo": File already exists)*

```
sudo mv /usr/share/sounds/Borealis/*.ogg /usr/share/sounds/Borealis/stereo
```
mv: impossibile eseguire stat di "/usr/share/sounds/Borealis/*.ogg": File o directory non esistente
*(mv: impossible to perform stat of "/usr/share/sounds/Borealis/*.ogg": File or directory does not exist)*

Many many thanks for your help! I waiting for next steps...

@frank18: > Funny i did the other way around, i have also an old Dell P4 2.0 ghz cpu  1ghz ram,  I had Xubuntu  12.04lts  and updated to Xubuntu 13.10 Beta  and i notice difference for better.

I do not know whether it is better to go for me to update to Xubuntu 13.10, I think my pc is quite old....or not...?

What kind of improvement did you notice from Xubu 12.04 to xubu 13.10, please?

Ciao!

Marco

---

### Post by Toz on 2014-03-15
> **Marvel0169 said:**
> Hi Toz, here the results for the command you suggested:

```
xfconf-query -c xsettings -p /Net/SoundThemeName
```
Borealis
Good.

> ```
sudo mkdir /usr/share/sounds/Borealis/stereo
```
mkdir: impossibile creare la directory "/usr/share/sounds/Borealis/stereo": File già esistente
*(mkdir: impossible to create directory "/usr/share/sounds/Borealis/stereo": File already exists)*

```
sudo mv /usr/share/sounds/Borealis/*.ogg /usr/share/sounds/Borealis/stereo
```
mv: impossibile eseguire stat di "/usr/share/sounds/Borealis/*.ogg": File o directory non esistente
*(mv: impossible to perform stat of "/usr/share/sounds/Borealis/*.ogg": File or directory does not exist)*

This doesn't make sense based on your last reply. What does the following return:
```
ls /usr/share/sounds/Borealis/stereo
```

And finally, what does this return:
```
env | grep GTK
```

---

### Post by Marvel0169 on 2014-03-15
Et voilà:
> marco@marco-desktop:~$ ls /usr/share/sounds/Borealis/stereo

[COLOR=#0000ff]button-pressed.ogg        dialog-warning.ogg       Startup1_1.ogg
button-toggle-off.ogg     Exit1_2.ogg              Startup1_2.ogg
button-toggle-on.ogg      install.sh               Startup1_3.ogg
desktop-login.ogg         K3b_success.ogg          system-ready.ogg
desktop-logout.ogg        Knock.ogg                trash-empty.ogg
desktop-switch-left.ogg   Kopete_status.ogg        uninstall.sh
desktop-switch-right.ogg  message-new-instant.ogg  window-close.ogg
device-added.ogg          phone-incoming-call.ogg  window-maximized.ogg
device-removed.ogg        phone-outgoing-busy.ogg  window-minimized.ogg
dialog-error.ogg          README                   window-unmaximized.ogg
dialog-information.ogg    service-login.ogg        window-unminimized.ogg
dialog-question.ogg       service-logout.ogg[/COLOR][COLOR=#008000]
[/COLOR]
marco@marco-desktop:~$ env | grep GTK
[COLOR=#0000ff]GTK_MODULES=canberra-gtk-module:canberra-gtk-module[/COLOR]
marco@marco-desktop:~$ 


Returns in blue. Usually I copy and paste as for your commands. 
In standby for new commands, captain!;)

Many thanks!

Marco

---

### Post by Toz on 2014-03-15
Everything looks fine now. Do you have sounds? If you click on the Xfce menu you should hear a click sound (or try minimizing and maximizing a window). If not, check the volume level of "System Sounds" from your sound indicator (or by running "pavucontrol" in a terminal window).

---

### Post by Marvel0169 on 2014-03-15
Hi toz, unfortunately I have no sounds.:( I hear sounds like "click-clock" when I move slides control outputs device in pulseaudio controls; I hear a sound when I do a forbidden action, so a windows open and I hear the "action denied" sound.
I heard only this two sounds....

 Sounds system in pulseaudio control panel is at 153%, at maximum level, but I don't hear sounds when I move slide control volume.

No sounds when minimize or maximixe windows. 

Maybe some codec or driver lost or to reinstall...?

Many thanks!!

Marco

---

### Post by Toz on 2014-03-15
> **Marvel0169 said:**
> Hi toz, unfortunately I have no sounds.:( I hear sounds like "click-clock" when I move slides control outputs device in pulseaudio controls; I hear a sound when I do a forbidden action, so a windows open and I hear the "action denied" sound.
I heard only this two sounds....
So you do hear sounds and it works.

> Sounds system in pulseaudio control panel is at 153%, at maximum level, but I don't hear sounds when I move slide control volume.Slide controls don't have associated sound events. Recall from [post #7]("http://ubuntuforums.org/showthread.php?t=2209372&p=12949521&viewfull=1#post12949521") of this thread that only certain events are supported by sound as per the canberra implementation.

> No sounds when minimize or maximixe windows. 
This is odd. You should hear a brief sound when it does. Do either of the following commands play a sound that you can hear?
```
canberra-gtk-play -f window-minimized.ogg
canberra-gtk-play -f window-unminimized.ogg
```
...the sound is very brief. Also try this one for comparison's sake:
```
canberra-gtk-play -f desktop-login.ogg
```
...it is much longer.

---

### Post by Marvel0169 on 2014-03-17
Hello Toz, I understand (finally...;)) > Sounds  system in pulseaudio control panel is at 153%, at maximum level, but I  don't hear sounds when I move slide control volume.
[QUOTE]Slide controls don't have associated sound events. Recall from [post #7]("http://ubuntuforums.org/showthread.php?t=2209372&p=12949521&viewfull=1#post12949521") of this thread that only certain events are supported by sound as per the canberra implementation.[/QUOTE]

I give commands as you suggest...Unfortunately I confirm no sounds, these the results of commands:

> marco@marco-desktop:~$ canberra-gtk-play -f window-minimized.ogg
Failed to play sound: File or data not found
marco@marco-desktop:~$ canberra-gtk-play -f window-unminimized.ogg
Failed to play sound: File or data not found
marco@marco-desktop:~$ canberra-gtk-play -f desktop-login.ogg
Failed to play sound: File or data not found
marco@marco-desktop:~$ 


Next steps captain?

Many thanks! Ciao!

Marco

---

### Post by Toz on 2014-03-17
Sorry, forgot the full path. Try these:
```

canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/window-minimized.ogg
canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/window-unminimized.ogg
canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/desktop-login.ogg

```

---

### Post by Marvel0169 on 2014-03-17
Wow!! In this way they works right!! 

What is the problem in this case?

Thanks, ciao!

Marco

---

### Post by Toz on 2014-03-17
> **Marvel0169 said:**
> Wow!! In this way they works right!! 

What is the problem in this case?

Thanks, ciao!

Marco

When you minimize a window by clicking on the minimize button in the title bar, do you hear the /usr/share/sounds/Borealis/stereo/window-minimized.ogg sound?

And the same for the maximize sound?

What is the Volume level of "System Sounds" in pavucontrol? Is it unmuted?



To get the desktop login sound to work, change your ~/.xprofile file to read:
```
canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/desktop-login.ogg &
```
...and on login, does the sound play?

---

### Post by Marvel0169 on 2014-03-17
This is really odd. As I said before no sound when I minimize or maximize windows. I heard sounds by command line, follow commands you told me.

Even now I heard login sound when I give canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/desktop-login.ogg & command. But then no other sound...

In pavucontrol, reproduction tag, the system sound volume is at 153%, 11dB....but no sounds when I move the sound slide;
instead, even in pavucontrol output tag, when I move the two volume slides I hear a "click-clock" sound....
In "configuration" tag, I selected "digital stereo (IEC958) output". Is it right?

> To get the desktop login sound to work, change your ~/.xprofile file to read:

...ehmm...You should to give to me a step by step instructions to change ~/.xprofile... Sorry, my ability is very low whit xubuntu environment....

Many thanks! Ciao!

Marco

---

### Post by Toz on 2014-03-17
> **Marvel0169 said:**
> In pavucontrol, reproduction tag, the system sound volume is at 153%, 11dB....but no sounds when I move the sound slide;
instead, even in pavucontrol output tag, when I move the two volume slides I hear a "click-clock" sound....
In "configuration" tag, I selected "digital stereo (IEC958) output". Is it right?
What other options do you have there? Can you play music or get sound from youtube videos on your system?

> ...ehmm...You should to give to me a step by step instructions to change ~/.xprofile... Sorry, my ability is very low whit xubuntu environment....
First:
```
leafpad ~/.xprofile
```
Then change the command and save the file.
Finally, log out and back in again.

Note: if you get an error when trying the leafpad command, try instead:
```
mousepad ~/.xprofile
```

---

### Post by Marvel0169 on 2014-03-17
Hurrà!! Now login sound works! I modified the ~/.xprofile file as you suggested. But no other system sounds.


> What other options do you have there? Can you play music or get sound from youtube videos on your system?

Yes, this is the oddness. I can play music from cd or usb key or from youtube videos but no system sounds...


Maybe are we take a good way to solve this trouble? 

Many thanks Toz! Ciao!

Marco

---

### Post by Toz on 2014-03-17
As a sanity check, can you post back one more time:
```
xfconf-query -c xsettings -p /Net/EnableEventSounds
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
xfconf-query -c xsettings -p /Net/SoundThemeName
ls -l /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)/stereo
env | grep GTK
```

---

### Post by Marvel0169 on 2014-03-18
Ok Toz, this afternoon I will try commands you suggest, then I'll let you know.
Many thanks!

Marco

---

### Post by Marvel0169 on 2014-03-18
hi Toz, below the results of the commands:

> marco@marco-desktop:~$ xfconf-query -c xsettings -p /Net/EnableEventSounds
true
marco@marco-desktop:~$ xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
true
marco@marco-desktop:~$ xfconf-query -c xsettings -p /Net/SoundThemeName
Borealis
marco@marco-desktop:~$ ls -l /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)/stereo
totale 2960
-rw-r--r-- 1 root root   8357 mar 11 18:39 button-pressed.ogg
-rw-r--r-- 1 root root  10284 mar 11 18:39 button-toggle-off.ogg
-rw-r--r-- 1 root root  10120 mar 11 18:39 button-toggle-on.ogg
-rw-r--r-- 1 root root 447104 mar 11 18:39 desktop-login.ogg
-rw-r--r-- 1 root root 227654 mar 11 18:39 desktop-logout.ogg
-rw-r--r-- 1 root root  10120 mar 11 18:39 desktop-switch-left.ogg
-rw-r--r-- 1 root root  10284 mar 11 18:39 desktop-switch-right.ogg
-rw-r--r-- 1 root root  10120 mar 11 18:39 device-added.ogg
-rw-r--r-- 1 root root  10284 mar 11 18:39 device-removed.ogg
-rw-r--r-- 1 root root  40703 mar 11 18:39 dialog-error.ogg
-rw-r--r-- 1 root root  11652 mar 11 18:39 dialog-information.ogg
-rw-r--r-- 1 root root  52026 mar 11 18:39 dialog-question.ogg
-rw-r--r-- 1 root root  16193 mar 11 18:39 dialog-warning.ogg
-rw-r--r-- 1 root root 225536 mar 11 18:39 Exit1_2.ogg
-rw-r--r-- 1 root root   4630 mar 11 18:39 install.sh
-rw-r--r-- 1 root root 278722 mar 11 18:39 K3b_success.ogg
-rw-r--r-- 1 root root  24192 mar 11 18:39 Knock.ogg
-rw-r--r-- 1 root root  29711 mar 11 18:39 Kopete_status.ogg
-rw-r--r-- 1 root root  30409 mar 11 18:39 message-new-instant.ogg
-rw-r--r-- 1 root root  84820 mar 11 18:39 phone-incoming-call.ogg
-rw-r--r-- 1 root root  48009 mar 11 18:39 phone-outgoing-busy.ogg
-rw-r--r-- 1 root root   7782 mar 11 18:39 README
-rw-r--r-- 1 root root  17274 mar 11 18:39 service-login.ogg
-rw-r--r-- 1 root root  14573 mar 11 18:39 service-logout.ogg
-rw-r--r-- 1 root root 397380 mar 11 18:39 Startup1_1.ogg
-rw-r--r-- 1 root root 408878 mar 11 18:39 Startup1_2.ogg
-rw-r--r-- 1 root root 413931 mar 11 18:39 Startup1_3.ogg
-rw-r--r-- 1 root root  41886 mar 11 18:39 system-ready.ogg
-rw-r--r-- 1 root root   8869 mar 11 18:39 trash-empty.ogg
-rw-r--r-- 1 root root   2860 mar 11 18:39 uninstall.sh
-rw-r--r-- 1 root root  11114 mar 11 18:39 window-close.ogg
-rw-r--r-- 1 root root  10120 mar 11 18:39 window-maximized.ogg
-rw-r--r-- 1 root root  11114 mar 11 18:39 window-minimized.ogg
-rw-r--r-- 1 root root  10284 mar 11 18:39 window-unmaximized.ogg
-rw-r--r-- 1 root root  11439 mar 11 18:39 window-unminimized.ogg
marco@marco-desktop:~$ env | grep GTK
GTK_MODULES=canberra-gtk-module:canberra-gtk-module
marco@marco-desktop:~$ 



Now? 

Thanks a lot! Ciao!

Marco

---

### Post by Toz on 2014-03-18
Everything looks right. I'm sorry but I don't know why the sounds aren't working for you.

---

### Post by Marvel0169 on 2014-03-19
Hi Toz, I see. It is no a standard situation and is no even possible to adjust everything... We have tried! 

Just a question, for my personal curiosity: The  [COLOR=#000000]~/.xprofile file [/COLOR]has allowed us to make the login.ogg sound audible. 
If I add to [COLOR=#000000]~/.xprofile file all the sounds of Borealis/stereo folder, whit the same syntax ([/COLOR][COLOR=#000000]canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/[/COLOR][COLOR=#ff0000][SIZE=4]**nnnnnn**[/SIZE][/COLOR][COLOR=#000000].ogg &), do you think this might work and allowed to make all the sounds audibles?

Last curiosity....maybe a silly question: why [/COLOR][COLOR=#000000]~/.xprofile file allows to hear login sound?

[/COLOR]Thank you endlessly for all your help and patience!!!

Ciao!

Marco

---

### Post by Toz on 2014-03-19
> **Marvel0169 said:**
> Just a question, for my personal curiosity: The  [COLOR=#000000]~/.xprofile file [/COLOR]has allowed us to make the login.ogg sound audible. 
If I add to [COLOR=#000000]~/.xprofile file all the sounds of Borealis/stereo folder, whit the same syntax ([/COLOR][COLOR=#000000]canberra-gtk-play -f /usr/share/sounds/Borealis/stereo/**nnnnnn**[/SIZE].ogg &), do you think this might work and allowed to make all the sounds audibles?
No, that won't work. It will just play them all sequentially, which isn't what you want.

> Last curiosity....maybe a silly question: why ~/.xprofile file allows to hear login sound?
When you log in, the .xprofile file, if it exists, is run. By putting the command to play the sound in that file, the sound is played.

---

### Post by Marvel0169 on 2014-03-20
Hi Toz, many thanks for your explanations! :P

Well, yesterday I emailed the author of Borealis, and maybe there is a sense for non working Borealis in xubuntu environment; this is his reply: 
> Thanks for your interest. I actually haven\'t been using *-look.org site  for so long that I had to reset my password. The theme has been  designed for KDE 3.x series, so the installer will not work for anything  else. You may still be able to install it on other window managers but  you will have to assign sounds manually.

Hope this helps!

If I understand I must to create a new set of sounds. How can assign sounds manually? If it could work could also be useful for someone else...I think...

Many thanks! Ciao!

Marco

---

### Post by Toz on 2014-03-20
> **Marvel0169 said:**
> If I understand I must to create a new set of sounds. How can assign sounds manually? If it could work could also be useful for someone else...I think...
I don't think the issue with your setup is the sound theme - I think there is something else going on that is preventing the sound from playing. Unfortunately, I'm not sure what it is. 

There is no easy way to assign sounds manually. The only method that I know of is to put sound files in a theme's stereo folder using names as per the [freedesktop sound spec]("http://0pointer.de/public/sound-naming-spec.html") using only names that are supported by the [libcanberra]("https://gitorious.org/libcanberra/mainline/source/ac5ac9e486aa33f7be0cd9ddd315c03780676795:src/canberra-gtk-module.c#L3") implementation. Which is what was done with the modified Borealis theme that you tried (which I know works because it works on a number of systems that I have installed it in).

---

### Post by Marvel0169 on 2014-03-21
Hi Toz, I am agree whit you, I hear cd, youtube videos, radio streaming without problem, so, maybe, the problem is in my Xubu installation. It is no a big problem, all the rest works fine. It would have been nicer whit sounds also but I'll try to survive...;). I set desktop sounds theme once again but still does not work....

I very appreciate you helps and your patience. Many thanks again. 

Oh, if you have an idea for test again, let me know, please and we'll see what happens.

Ciao!

Marco

---

### Post by Toz on 2014-03-22
One more thought....

Do you have at-spi2-core installed?
```
apt-get cache policy at-spi2-core
```

If not, can you install it:
```
sudo apt-get install at-spi2-core
```
...reboot, and try again?

---

### Post by Marvel0169 on 2014-03-24
Hello Toz, no, I haven't [COLOR=#000000]at-spi2-core. This afternoon I'll install it and I let you know.

Many thanks! Ciao!

Marco[/COLOR]

---

### Post by Marvel0169 on 2014-03-24
> **Toz said:**
> One more thought....

Do you have at-spi2-core installed?
```
apt-get cache policy at-spi2-core
```

If not, can you install it:
```
sudo apt-get install at-spi2-core
```
...reboot, and try again?

I Toz, I checked and I have already at-spi2-core at the most recent version....
Many thanks!  Ciao!

Marco

---

### Post by Marvel0169 on 2014-03-25
Hi Toz, yesterday I rediscovered an old video card, GeForce 3 max...etc, I installed it in place of Savage 4 and the graphic are very improved. 
So I thought, if I could put a sound card maybe I could have the same effect... My pc has an ASUS P4S800D mother board: wich kind of sound card could  I  to install on it? I thought to a Soundblaster (Creative Soundblaster 5.1 or Creative Soundblaster Audigy, or some other...).
Could you suggest me which one, please? Maybe on ebay I could to find a cheap sound card...

Many thanks! Ciao!

Marco

---

### Post by Marvel0169 on 2014-04-06
Hello guys, well, finally I have xubuntu system sounds and login and logout sounds! HURRAAA!!=d>\\:D/.

I follow this usefull guide by Gianlic on a linux italian forum: [http://www.istitutomajorana.it/forum/Thread-Xubuntu-attivare-suono-Login-e-Logout](http://www.istitutomajorana.it/forum/Thread-Xubuntu-attivare-suono-Login-e-Logout)

Now all works fine!

Many thanks to all! Ciao!

Marco

---

