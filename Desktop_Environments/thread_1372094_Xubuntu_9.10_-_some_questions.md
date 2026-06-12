---
title: "Xubuntu 9.10 - some questions"
date: 2010-01-04
forum: Desktop Environments
---

### Post by night-wing on 2010-01-04
Hello.

After trying ubuntu 9.10 I decided to go back to 8.10, because it works better on my samsung notebook. No I wanted to give karmic a new try and this time I took a look at xubuntu 9.10.
This worked much better than ubuntu karmic and also better than the 8.10 - xubuntu.

Of course, xfce is something different than gnome and has some issues as well, I got the most working as I wanted. But some minor things are left, which I did not find using the search or google. Maybe someone could help me here?

- Is there any way to put a "shutdown sound" in a script (where?) to make xubuntu play this when shutting down or rebooting? Of course, I know, that xfce from itself not provides system sounds, but maybe there is a hint?
- I often have the problem, that usb sticks won't unmount in thunar correctly. External (usb) drives do, so I don't understand, why sticks won't.
- I think, xubuntu has a lot of gnome stuff within. Can somebody tell me from her/his experiences, which things can be removed or replaced with others to make xubuntu a little bit "thinner"?

Regards
Nightwing

---

### Post by night-wing on 2010-01-04
Oh. I forgot:
- Audio CDs are not shown in thunar. Not even opening thunar as root shows them. But sound-juicer or ripoff can rip them (what means, these programs "see" the cds). A little bit strange...

---

### Post by XubuRoxMySox on 2010-01-04
> **night-wing said:**
> 

- I often have the problem, that usb sticks won't unmount in thunar correctly. External (usb) drives do, so I don't understand, why sticks won't.
- I think, xubuntu has a lot of gnome stuff within. Can somebody tell me from her/his experiences, which things can be removed or replaced with others to make xubuntu a little bit "thinner"?

Regards
Nightwing

I'm a newbie to Xubuntu myself, and I'm delighted with its speed and ease. I can't answer your shutdown sound question (yet), but I can offer a little of what I've learned so far about the Gnome/Xfce "likeness."

What the two desktop environments have in common is GTK. So "Gnome applications" like Abiword and Gnumeric are also Xfce applications. Midori (the web lightweight web browser) recently joined as an Xfce project but was independent before. But being GTK-based, and lightweight, it made sense to associate it with Xfce. It could just as well have been a "Gnome application," but again, it's GTK rather than strictly either Gnome or Xfce. The uber-lightweight LXDE environment is also GTK-based.

You need Thunar to manage the desktop panels and icons and such, but I found that I like the PCManFM file manager better (from the LXDE project) because it seems to auto-detect external media better than Thunar does (at least on my machine). It's in the repositories, just grab it with Synaptic and try it out. It even has a "**Tools > Open as Root**" option so you can assign defaults, change permissions, all kindsa neat stuff.

I never tried Xubuntu until Karmic because of all the stuff I had read describing Xubuntu as "bloated and heavy - no lighter than regular Ubuntu." Perhaps that was true in earlier versions, but it sure doesn't seem to be the case in Karmic Xubuntu. The only "bloat" I have found so far is that it ships with both OpenOffice *and* Abiword/Gnumeric when you really only need one or the other. It ships with Brasero (Gnome) instead of Xburn (Xfce), but that decision was pro'lly based on Brasero's popularity. To lighten up your Xubuntu Karmic, try Midori instead of Firefox (sweet, light, fast), Abiword/Gnumeric in place of the OpenOffice suite, Xburn in place of Brasero, etc. There's a list of Xfce apps on Xfce's [web site]("http://www.xfce.org/").

Hope that helps,
Robin

---

### Post by night-wing on 2010-01-06
Hello.
Thanks for your post.
I've tested midori. You're right - its lightweight and fast - but most of the more complex webpages are not shown properly (i.e. amazon).
XFBurn was a good hint - thanks! Works better than my nero for lin.

I've also removed usplash and replaced gdm with slim. Brought some seconds in boottime.

Still searching for the shutdown sound problem. Seems, that I am the only one here, who wants to "hear", when the pc is going down...
Regards
Nightwing

---

### Post by 3Miro on 2010-01-06
Currently I hold the position that XFCE is the only good DE for Ubuntu. Also, I do not use XUbuntu, but rather Ubuntu and then install xfce4 package. In this way, I have both and I can use whichever one I need. Under XFCE I still use Totem and Rhythmbox and I have both Thunar and Nautilus on shortcuts. When I want to mount/unmount and do other advanced things, I use nautilus, for regular file browsing copy/cut/move/paste, Thunar is faster.

For your sound thing, I may have a solution, but it is somewhat tricky. First, I don't think sound is being played on reboot, but rather on logout, which precedes reboot (unless you do a hard reboot). Here is what may work (I emphasize MAY):

1. In /usr/share/applications, there is a logout file called xfce4-logout.desktop. You need to backup and edit that:

```

sudo cp /usr/share/applications/xfce4-logout.desktop /usr/share/applications/xfce4-logout.desktop_mybackup
gksudo gedit /usr/share/applications/xfce4-logout.desktop

```
Note: this uses gedit, but you can use another editor if you want.

Edit the line that says Exec=xfce4-session-logout and change it to say 
Exec=xfce4-session-mylogout, save and exit. Basically this:
```
[Desktop Entry]
Version=1.0
Type=Application
Encoding=UTF-8
Exec=xfce4-session-logout <- Change this line
Icon=system-log-out

```
Should look like this
```
[Desktop Entry]
Version=1.0
Type=Application
Encoding=UTF-8
Exec=xfce4-session-mylogout <- Changed line
Icon=system-log-out

```

Right now logout will not work for your system, since it will call xfce4-session-mylogout, which doesn't yet exist. We are going to create it.

Note: to undo any changes here, just return the xfce4-logout.desktop back in its original form, or:
```

sudo cp /usr/share/applications/xfce4-logout.desktop_mybackup /usr/share/applications/xfce4-logout.desktop

```

2. Now we need to create a logout script xfce4-session-mylogout
```

gksudo gedit /usr/bin/xfce4-session-mylogout

```

Put the following code in it:

```

#!/bin/bash

# Add sound or whatever you want here
aplay mysound.wav

xfce4-session-logout

```

Replace the mysound.wav file with whatever file you want. Use full file path (i.e. /home/myusername/Music/myLogOutMusic.wav). For some reason I only got aplay to work with .wav files, you can convert files to .wav format with Audacity (get it from the Ubuntu software center/Synaptic).

Save the file and now try to logout to see if it works.

As I said, I am not expert enough to give any guarantees.

---

### Post by night-wing on 2010-01-07
Hello.

Thanks for your post.
I'm sorry to say, but it didn't work. Thanks anyway!

---

### Post by Jose Catre-Vandis on 2010-01-07
Remember to make the new script executable ?

---

### Post by 3Miro on 2010-01-07
> **night-wing said:**
> Hello.

Thanks for your post.
I'm sorry to say, but it didn't work. Thanks anyway!

Jose Catre-Vandis is right, the script has to be made executable.

```
sudo chmod 755 /usr/bin/xfce4-session-mylogout
```

---

### Post by night-wing on 2010-01-08
Hello.

Yes, I did change the permissions. Oh, seems, that I found out, what was wrong... I did never use the "log off" from the xfce menu but the "door icon" at the right side of the xfce panel - of course another .desktop-file.
Awkward...

But I think we misunderstood each other - I did not want a sound, when the logoff - box appears but the classic shutdown sound, which plays, when the system is really going down - what means after you have clicked "log off" or "restart" and the xorg wents away - like it's in gnome or kde...
What we now have is not a shutdown sound but a sound before the shutdown dialog appears.

Regards
Frank

---

### Post by 3Miro on 2010-01-08
> **night-wing said:**
> Hello.

Yes, I did change the permissions. Oh, seems, that I found out, what was wrong... I did never use the "log off" from the xfce menu but the "door icon" at the right side of the xfce panel - of course another .desktop-file.
Awkward...

But I think we misunderstood each other - I did not want a sound, when the logoff - box appears but the classic shutdown sound, which plays, when the system is really going down - what means after you have clicked "log off" or "restart" and the xorg wents away - like it's in gnome or kde...
What we now have is not a shutdown sound but a sound before the shutdown dialog appears.

Regards
Frank

I am out of ideas. xfce4-session-logout actually pulls out the menu where you can chose what to do. This is not a script and hence we cannot easily edit it. 

Sorry!

---

