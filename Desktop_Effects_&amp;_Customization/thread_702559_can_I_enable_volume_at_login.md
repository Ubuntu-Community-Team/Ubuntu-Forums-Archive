---
title: "can I enable volume at login?"
date: 2008-02-20
forum: Desktop Effects &amp; Customization
---

### Post by avdzm on 2008-02-20
Hey all,

I was wondering if i can load gnome-volume-manager at login?
or be able to adjust the volume.

I have a laptop and sometimes the login sound can be loud in some places.


thanks

---

### Post by avdzm on 2008-02-21
bump

---

### Post by SomeGuyDude on 2008-02-22
Mute it before you shut down or log out or whatever. It'll save your volume settings from when you last logged in. I have the same issue.

---

### Post by Mad_Gouki on 2008-02-22
I couldn't find anything on the default volume, there may or may not be a way to set that, as it may be in the bios, but I did find this
[http://blog.websitestyle.com/index.php/2007/01/19/how-to-disable-ubuntu-startup-shutdown-sounds/](http://blog.websitestyle.com/index.php/2007/01/19/how-to-disable-ubuntu-startup-shutdown-sounds/)
> Go to:

1) System -> Preferences -> Sound
2) This will open a preferences window.
3) At the top of the window, click the tab that says &#8216;Sounds&#8217;
4) At the bottom of the list of system sounds, find &#8216;Log out&#8217; and &#8216;Log in&#8217;
5) Using the arrows to the right of those sections, change the option for both to &#8216;No sound.&#8217;
6) Close the window.

and the other part
> On Feisty, go to [Administration,] Login Window, Accessibility Tab, uncheck &#8216;Login Screen Ready&#8217; under Sounds

---

### Post by avdzm on 2008-02-22
> **SomeGuyDude said:**
> Mute it before you shut down or log out or whatever. It'll save your volume settings from when you last logged in. I have the same issue.

Ya i am forced do that too, 
thanks though

---

### Post by avdzm on 2008-02-22
> **Mad_Gouki said:**
> I couldn't find anything on the default volume, there may or may not be a way to set that, as it may be in the bios, but I did find this
[http://blog.websitestyle.com/index.php/2007/01/19/how-to-disable-ubuntu-startup-shutdown-sounds/](http://blog.websitestyle.com/index.php/2007/01/19/how-to-disable-ubuntu-startup-shutdown-sounds/)

and the other part

Hey, 
I don't want to remove the sounds,

thanks though

---

### Post by avdzm on 2008-02-22
So i take it i can't load the gnome-volume-manager at startup....:(

thanks for your help, guyz

---

### Post by chrisccoulson on 2008-02-22
Just to clarify, gnome-volume-manager has nothing to do with audio or audio volume. It is responsible for automounting media and autorunning programs in response to various hotplug events

---

### Post by avdzm on 2008-03-12
Hey all,

since there is no way to load a volume controller at login,
i thought of another alternative,

to run this command "amixer set PCM 45 > /dev/null"
somewhere during  the boot process.

can some1 point me to the right file?

I want to run this command in all accounts not just mine.

thanks for anyhelp

---

### Post by Zorael on 2008-03-12
I think you could add it to /etc/init.d/rc.local to have it run at boot with root privileges.

To make things neat, make it into an external script first, then add a reference to it in that file.

Like:
```
$ sudo nano /usr/bin/fixvolume

*(enter the following into the file:)*

[indent][b]#!/bin/bash

amixer set PCM 45 > /dev/null[/b][/indent]

*(Ctrl+O to save, Ctrl+X to exit)*

$ sudo chmod /usr/bin/fixvolume +x
```

Then add '/usr/bin/fixvolume' to rc.local, somewhere above the 'exit 0' line.

Might work, not sure.

---

### Post by avdzm on 2008-03-25
Hey all,
no it doesn't work,
It sets the volume after login.
I need to set the command sooner.

---

