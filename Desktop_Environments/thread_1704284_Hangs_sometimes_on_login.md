---
title: "Hangs sometimes on login"
date: 2011-03-10
forum: Desktop Environments
---

### Post by daniel.cotter on 2011-03-10
I've had my system about a month -- 10.10, i7, 8GB Ram

Last week, I installed KDE and xFce desktop environments.

Two things I wonder if you can comment on:
1) It boots up into kubuntu instead of Ubuntu, and presents the kubuntu login screen, even when I last used the Gnome environment.   This is the _curiosity_.

When I log in, the screen brightens and then plays the Ubuntu default sound, and drops me into the Gnome desktop.

2) This is the _issue_ -- every so often , maybe every 5 or 6 logins, after I have logged in, the screen brightens up as normal, but just sits there, empty.  I have to Ctrl+[F2] to log into the text interface and issue init 6 to reboot.  On the second attempt, it takes me into the Gnome desktop as at other times.

Any thoughts?

<dc><

---

### Post by Krytarik on 2011-03-10
Hi,

1) You seem to be using KDM instead GDM. I believe it is the results of your installation of KDE. So, that behaviour is as expected. If you want to use GDM instead, run
```
sudo dpkg-reconfigure gdm
```2) Check the following logs after that happened the next time:
- "/var/log/Xorg.0.log", respectively "Xorg.0.log.old"
- "~/.xsession-errors", respectively "~/.xsession-errors.old"

---

### Post by daniel.cotter on 2011-03-11
Ok,  I ran that utility(only gave the choice of KDE or GNOME, not Xfce), and it has set my session to GNOME again, but there are several things changed.

I have been able to get to the GNOME desktop all along, through the KDE login menu, and it looked as it has since installing, once I logged into the display.

I have been trying hard to retrace my steps and remember what I did to boot into KDE, because the GNOME login menu does not give an option to choose sessions, as the instructions say it should.  I did find a way to get to the KDE menu, and was able to select KDE, GNOME, or Xfce from there.  Now, I get only the GNOME login screen, with no option to select another.

Also, before running the utility you showed me, the window buttons (close, maximize, minimize) were colored circles on the left side of the window border.  Now they are icons on the right side, like MS Windows.

Also before, the terminal had a maroon, transparent background, and now it is black on solid white.
There are other minor changes to the "feel" of it, which are not worth wasting time detailing.

I downloaded the KDE and Xfce environments, according to the instructions here:
[https://help.ubuntu.com/10.10/config-desktop/C/other-desktops.html](https://help.ubuntu.com/10.10/config-desktop/C/other-desktops.html)

It hasn't hanged on me again...

---

### Post by Krytarik on 2011-03-11
> **daniel.cotter said:**
> I did find a way to get to the KDE menu, and was able to select KDE, GNOME, or Xfce from there.  Now, I get only the GNOME login screen, with no option to select another.

Do you have to enter your password at the login screen (not talking about autologin)?
If not, enable the password query via "System -> Administration -> Users and Groups", otherwise you are not able to choose a session.
> **daniel.cotter said:**
> 
Also, before running the utility you showed me, the window buttons (close, maximize, minimize) were colored circles on the left side of the window border.  Now they are icons on the right side, like MS Windows.

Are you talking about *after* login? Could you provide a screenshot!?
> **daniel.cotter said:**
> 
Also before, the terminal had a maroon, transparent background, and now it is black on solid white.
 
You can modify the color options via "Edit -> Profile Preferences -> Colors".
> **daniel.cotter said:**
> 
There are other minor changes to the Z"feel" of it, which are not worth wasting time detailing.
Do you notice some major differences, like missing desktop items, or panel items, or differences in your home directory?

---

### Post by daniel.cotter on 2011-03-12
> Do you have to to enter your password at the login screen (not  talking about autologin)?Yes, I have never used autologin

> Are you talking about *after* login? Could you provide a screenshot!?I have attached one...not sure how to paste it into the message.   Before the changes I made[IMG]http://ubuntuforums.org/home/daniel/Pictures/Screenshot.png[/IMG], these functions were in animated lights on the left side of the window border, red, yellow and green circles.

> Do you notice some major differences, like missing desktop items, or panel items, or differences in your home directory?No, everything is there, and working fine. I just don't understand the changes in appearance.

---

### Post by Krytarik on 2011-03-12
Again, do you have to enter your password at the login screen?

Maybe you used Emerald before, try this:
- press Alt+F2
- enter
```
emerald --replace
```**EDIT:** I now saw that you said *"Yes"* to the first question. When you click at your name, you don't get the "Session" options at the bottom?

---

### Post by daniel.cotter on 2011-03-12
Ok, I don't remember using emerald, but I tried the replace command, and it tells me it's not installed, as I thought.

When I click my username, I get the password field, and the fungerprint-gui field opens up.  No other options for changing sessions.  Only the kdm login menu gives me that.

---

### Post by Krytarik on 2011-03-12
> **daniel.cotter said:**
> Ok, I don't remember using emerald, but I tried the replace command, and it tells me it's not installed, as I thought.

Then you may have used another theme/borders before, you should know it better.
> **daniel.cotter said:**
> 
When I click my username, I get the password field, and the fungerprint-gui field opens up.  No other options for changing sessions.  Only the kdm login menu gives me that.
Not that kind of option?:
[http://ubuntuforums.org/showthread.php?t=1694837](http://ubuntuforums.org/showthread.php?t=1694837)

---

### Post by daniel.cotter on 2011-03-12
Wow!  Don't I feel silly.  I have wasted your time.  I have terrible tunnel vision, it seems...it has been there all along, with all the same options I see in KDE, and I NEVER SAW IT!!

You have been way too patient with me, and for that, I thank you!!

Vielen Dank!!

---

### Post by Krytarik on 2011-03-13
> **daniel.cotter said:**
> Wow!  Don't I feel silly.  I have wasted your time.  I have terrible tunnel vision, it seems...it has been there all along, with all the same options I see in KDE, and I NEVER SAW IT!!

You have been way too patient with me, and for that, I thank you!!

Vielen Dank!!
Hey, you are not the first one who missed those option, and definetely not the last! ;-)

And it could always be that some kind of misconfiguration, missing packages, bugs or whatever prevent those options from showing up as expected.

You're welcome! And check your themes.

PS: Here is another, funny example: [http://ubuntuforums.org/showthread.php?p=10337981](http://ubuntuforums.org/showthread.php?p=10337981) :-)

---

