---
title: "KDE 4: black screen"
date: 2008-01-23
forum: Desktop Environments
---

### Post by Kris001 on 2008-01-23
Hi everyone,
I'm new here. Today I wanted to try Kubuntu with KDE 4. Everything went well. Then I tried to change some settings, and it all went wrong. When I applied the settings, the screen went black, I couldn't do anything anymore. I restarted the X-server (Ctrl+Ald+D), and logged in again. But the screen still was black.

How can I get everything back?

Thanks in advance, Kris

---

### Post by Kris001 on 2008-01-24
Is there a way to restore this?
Or can I make a new user with the terminal?

Help, please :)

---

### Post by Toxicio on 2008-01-24
If you have access to the terminal (you say "logged in again", so you should), you can run the following command:

sudo rm /etc/X11/xorg.conf

It deletes config file for X server, it will be regenerated when you start X server again.Everything should go well, but, of course, you can make backup copy. I've done it myself, but not on a Kubuntu. Maybe you should delete not this file, but file ~/.xorg.conf (config for your user in your home dir) or /usr/X11R6/lib/X11/xorg.conf (another common config file). In my case command above work well. Sorry for giving such a dangerous answer, you know that I just a newbie ;-) But if it helps I will be glad :-)

---

### Post by Toxicio on 2008-01-24
Less dangerous way: you can rename the file instead of deleting it. Just type the following:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

I tried this at home. Result is interesting. Nothing dangerous happens, and even more, xorg.conf
is not recreated. It is not needed here at all? :-) Maybe Ubuntu uses different way for all 
this stuff, I tried it on other distro.

If all this is useless, you can indeed try to create another user. Use the command:

sudo adduser user2

It will create new user with login name user2. You will enter password here, too, it will be
prompted. Try it.

---

### Post by Ziggy Stardust on 2008-01-24
A better way would be to move (rename) your KDE 4 settings folder. Type this in a terminal:

mv ~/.kde4 ~/.kde4.BAK

That should restore the KDE settings to default. One little tip, though. Try to wait for a minute after you've logged in and see if anything happens. If not, try to press CTRL + ALT + DEL. That worked for me when I was testing KDE 4 and encountered the same problem. You might want to check that out before you move / rename the settings folder.

By the way, after you've renamed .kde4 you have to log out and in again.

---

### Post by Kris001 on 2008-01-24
Thanks for the replies everyone!!

But I already reinstalled everything today. :)

---

### Post by p_alexander on 2008-02-07
I had the same issue (black screen after changing a setting for desktop effects). Deleting the .kde4 folder fixed the problem at next login.

Thanks!

---

### Post by ryanVickers on 2008-02-07
It's just one if it's many flaws.  The way around I found was to go back to gnome, change its options, and try again ;)

---

### Post by mutzinet on 2008-02-07
I also got the black screen (only the mouse pointer was visible) after changing some settings. But weirdly, I had the desktop effect "Present windows" switched on and activating that by pushing the mouse in one of the corners of the screen would bring anything to normal again... :confused:

I haven't encountered the problem in the last few days.

---

### Post by silentmonkey on 2008-04-27
I had a similar problem today.  I changed a few visualisation settings and when I logged into KDE4 next the screen was black except for the mouse cursor.  I could still do things, but it was difficult without, you know, being able to see it.

I found a few suggestions on-line on how to set it back how it was.  I tried the least damaging one first:

Edit the file ~/.kde4/share/config/kwinrc and replace

       [Compositing]
       Enabled=true

with

       [Compositing]
       Enabled=false

Simple as that.

Hope this helps someone else one day.

---

### Post by NipitMaster on 2008-04-30
> **p_alexander said:**
> I had the same issue (black screen after changing a setting for desktop effects). Deleting the .kde4 folder fixed the problem at next login.

Thanks!

That worked for me too. Thanks!

---

### Post by Jedioscuro on 2008-05-06
> **silentmonkey said:**
> I had a similar problem today.  I changed a few visualisation settings and when I logged into KDE4 next the screen was black except for the mouse cursor.  I could still do things, but it was difficult without, you know, being able to see it.

I found a few suggestions on-line on how to set it back how it was.  I tried the least damaging one first:

Edit the file ~/.kde4/share/config/kwinrc and replace

       [Compositing]
       Enabled=true

with

       [Compositing]
       Enabled=false

Simple as that.

Hope this helps someone else one day.

Hello!
I had the same problem, I've changed kwinrc and it works just fine.
But... is there any chance to enable 3d acceleration on my ati x1650pro videocard?
I installed and uninstalled many times the official drivers manually and using envy, but it didn't worked.
Simply black screen on boot up (because of kdm-kde4 choice i think) or on kde4 desktop when i try to enable 3d acceleration.
Any idea what to do it?
Thanks in advance

---

