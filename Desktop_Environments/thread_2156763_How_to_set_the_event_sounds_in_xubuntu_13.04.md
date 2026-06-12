---
title: "How to set the event sounds in xubuntu 13.04?"
date: 2013-06-23
forum: Desktop Environments
---

### Post by hackson99 on 2013-06-23
Hi , i just install succesffuly the xubuntu 13.04. Everything is ok, I can play mp3 and movies, JUST no system event sounds.

As a guid that is five years ago in this forum, i make out the login sound ! Sounds perfect! But no eny event sounds :(

How can i do? Why the development team did not make the xubuntu auto play sound? That is very hard for them? I think that is very hard for me -- for the people who like me. 
Maybe the xubuntu 13.04 is just a[COLOR=#ff0000] **SEMIFINISHED**[/COLOR] product?:confused::confused::confused:

Oh, my god. who can help me?

Thanks a lot!

---

### Post by Toz on 2013-06-23
Hello and welcome to the forums.

[This thread]("http://ubuntuforums.org/showthread.php?t=1869787&highlight=xfce+sound") describes how to get event sounds working in Xfce. It is still valid for 13.04.

In a nutshell (and to summarize that thread):
[LIST=1]
[*]Make sure you have the necessary packages installed:
```
sudo apt-get install gnome-session-canberra ubuntu-sounds sox xfconf
```
[*]Enable the event sounds. Go to SettingsManager->Settings Editor and locate the following keys and set the values to:
- xsettings/net/EnableEventSounds = checked
- xsettings/net/EnableInputFeedbackSounds = checked
- xsettings/net/SoundThemeName = (a name of a sound theme - they are located in /usr/share/sounds)
Note: The thread talks about have dconf installed - I don't need it for sounds to work.
.
[*]Enable the GTK-MODULES environment variable. From a terminal window:
```

gksu mousepad /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
```
...enter your password when prompted and copy/paste the following code:
```

if [ -z "$GTK_MODULES" ] ; then
	GTK_MODULES="canberra-gtk-module"
else
	GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi
export GTK_MODULES
```
...and save the file. Then,
```

gksu mousepad /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
```
...copy/paste the following code:
```

if [ -z "$GTK_MODULES" ] ; then
	GTK_MODULES="canberra-gtk-module"
else
	GTK_MODULES="$GTK_MODULES:canberra-gtk-module"
fi
export GTK_MODULES
```
...and save the file.
[*]Create a login sound event:

```
mousepad ~/.profile
```

...and add the following line:
```
canberra-gtk-play -f </path/to/login/sound/file>
```

...change </path/to/login/sound/file> to point to a valid sound file. Then make that file executable:

```
chmod +x ~/.xprofile  
```


[*]Log out and back in again.
[*]
[/LIST]
More sound themes can be found [here]("http://xfce-look.org/index.php?xcontentmode=25&PHPSESSID=faa48b83da7398aef66aa7ec3031416c").

Note: I also had to increase the System Sounds volume level so that I could her the effects.

---

### Post by hackson99 on 2013-06-23
OK, I will try.

---

### Post by hackson99 on 2013-06-23
OK, when i download a sound theme named Dream from xfce-look.org, put it into /usr/share/sounds/, modify xsettings->net->SoundThemeName, after that, when i clean the trash, there is an event sound! When i close my firefox, there is an envent sound! Great!

Thank u Toz!

Another question: i want to add the logout sound event. How can i do? Hope you can give me an answer. Thank u !

---

### Post by Toz on 2013-06-23
> **hackson99 said:**
> Another question: i want to add the logout sound event. How can i do? Hope you can give me an answer.
This one is a little tougher, but this should work.

1. Create a script to play the file:
```
gksudo mousepad /usr/local/bin/logout_sound
```
...with the following content:
```
canberra-gtk-play -V 0.1 -f </path/to/logout/sound/file> &
```
...change </path/to/logout/sound/file> to point to a valid sound file. Save and then make that file executable:
```
sudo chmod +x /path/to/logout/sound/file
```

2. Configure lightdm and enable the session-cleanup-script:
```
gksudo mousepad /etc/lightdm/lightdm.conf
```
...and add to the botton of the file:
```
session-cleanup-script=/usr/local/bin/logout_sound
```
...and save the file.

3. Logout and back in again to test.

---

### Post by hackson99 on 2013-06-23
Thank u.

But i sovled myself ,by adding a script in the /etc/init.d/, just including one line "play /usr/share/sounds/ubuntu/desktop-logout.ogg", and link it from /etc/rc0.d/ and /etc/rc6.d/, after that whatever i reboot or halt my system, always i can hear the log out sound. Great. But when i log off, no sound. 

Your method is better. As you guid, whatever log off , reboot, halt, there always is a logout sound. Great!

Hope the develop team do [COLOR=#008000]**add the event sound into the next release**[/COLOR] --xubuntu 13.10. That, we will not   meat the same trouble.

But, they will???:o

---

### Post by hackson99 on 2013-06-25
> **Toz said:**
> This one is a little tougher, but this should work.

1. Create a script to play the file:
```
gksudo mousepad /usr/local/bin/logout_sound
```
...with the following content:
```
canberra-gtk-play -V 0.1 -f </path/to/logout/sound/file> &
```
...change </path/to/logout/sound/file> to point to a valid sound file. Save and then make that file executable:
```
sudo chmod +x /path/to/logout/sound/file
```

2. Configure lightdm and enable the session-cleanup-script:
```
gksudo mousepad /etc/lightdm/lightdm.conf
```
...and add to the botton of the file:
```
session-cleanup-script=/usr/local/bin/logout_sound
```
...and save the file.

3. Logout and back in again to test.


Hello,

Done,But no logout sound in *[SIZE=5][COLOR=#ff8c00]**ubuntu**[/COLOR][/SIZE] *13.04. How can i do?

---

### Post by Toz on 2013-06-25
> **hackson99 said:**
> 
Done,But no logout sound in ubuntu 13.04. How can i do?
You are right, it doesn't work. I just had a closer look and it appears that session-cleanup-script runs _after_ the X session is terminated and the command doesn't run. I tried a number of other commands with no luck.

After some researching on google, I found that this is a common issue. I tried a number of suggested solutions and was only able to get one to kind of work. It involves putting a wrapper around xfce4-session that allows for the executaion of a logout script.

To do this, create an xfce4-session wrapper script in /usr/local/bin that both calls the real xfce4-session and the logout script command:
[LIST=1]
[*]Create the wrapper script:
```
gksudo mousepad /usr/local/bin/xfce4-session
```
[*]Add the following code:
```
#!/bin/bash

# run the real xfce4-session exectuable
/usr/bin/xfce4-session

# after it terminates (on logout), play your logout sound
canberra-gtk-play -V 0.1 -f </path/to/logout/sound/file>
```
.....make sure you change </path/to/logout/sound/file> to a real sound file
[*]Save the file and make it executable:
```
sudo chmod +x /usr/local/bin/xfce4-session
```
[*]Logout and back in again to enable the script. Then logout again to hear the logout sound.
[/LIST]

The one thing that I noticed in testing this is that the appearance theme disappears for all displayed windows while the logout sound plays making the windows look very blocky and 80s-like.

---

