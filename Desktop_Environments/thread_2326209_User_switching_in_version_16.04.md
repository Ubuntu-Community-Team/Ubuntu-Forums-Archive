---
title: "User switching in version 16.04"
date: 2016-05-29
forum: Desktop Environments
---

### Post by p_schott on 2016-05-29
Since upgrade to 16.04, I don't see the user switching feature in its usual location in gnome-shell. The network connection and current user appear but there is no mean in the top-right menu to leave the current user account running and log into another, as it was possible with version 15.10 and below.
The problem had already been reported for the beta version here: [http://ubuntuforums.org/showthread.php?t=2309544]("http://ubuntuforums.org/showthread.php?t=2309544").
A bug report is also opened here : [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1577049]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1577049"), but it does not seem to raise much interest :-(.
Does anyone else experience the same issue ?

---

### Post by jim_deadlock on 2016-05-30
It is as you say in 16.04 (Gnome Shell 3.18) and also seems quite slow to log in/out in general. It doesn't bother me personally because I never switch users, but I imagine it would be quite annoying for someone who does.

---

### Post by R Smit on 2016-05-30
Same problem here; it is the reason I will not switch to Gnome3.:(

---

### Post by rainerw2 on 2016-05-31
Greetings. I have installed numerous 16.04 OS's on PC's and L-top's and Netbook's without experiencing the dilemma you describe. The Guest-Session is visible and activates. As I had never used it before I was surprised that its functions are of a temporary nature and any performance is not permanently stored - which is a good thing as far as I'm concerned.
I wonder of it is the difference between updating to 16.04 vs. installing? I hope you get it sorted.
Allow me to say; I am on many computers, for which I'm responsible, with 'the brilliance of ubuntu' since 14.04 to 16.04 without a failure, a crash, a calamity or total disaster (unlike Windows) - the odd stumble - yes, but than again, if one does not put the audio plug in the proper socket, of cause there is no sound.[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG] - and it took 4 hours of one of my finest colleagues to find out.

---

### Post by R Smit on 2016-05-31
> **rainerw2 said:**
> Greetings. I have installed numerous 16.04 OS's on PC's and L-top's and Netbook's without experiencing the dilemma you describe. The Guest-Session is visible and activates. As I had never used it before I was surprised that its functions are of a temporary nature and any performance is not permanently stored - which is a good thing as far as I'm concerned.
I wonder of it is the difference between updating to 16.04 vs. installing? I hope you get it sorted.
Allow me to say; I am on many computers, for which I'm responsible, with 'the brilliance of ubuntu' since 14.04 to 16.04 without a failure, a crash, a calamity or total disaster (unlike Windows) - the odd stumble - yes, but than again, if one does not put the audio plug in the proper socket, of cause there is no sound.[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG] - and it took 4 hours of one of my finest colleagues to find out.

You seem to be slightjy off topic.
W're talking about Ubuntu Gnome, right?
Fresh installation, 2 users.
When user one is logged in, the menu does not give the option to switch user, only to log off.
See attachment.

---

### Post by rainerw2 on 2016-05-31
Hi R Smit, you got me there! Your thumbnail Pic is news to me - never knew about the function, never seen it. Do I ever stop finding another tweak to exploit.
Beside a Guest user, I have never worked on one OS with a variety of users. Have always installed 2 to 4 OS's on one computer next to each other, in virtual boxes or separate harddrives, or obviously using a server. I even find this now flawed and insecure to some extend. (you may have seen my other post on this.)
I apologize for the misunderstanding and partially for my ignorance. [IMG]http://ubuntuforums.org/images/icons/icon3.png[/IMG]

---

### Post by dcmay-f on 2016-06-17
> **R Smit said:**
> Same problem here; it is the reason I will not switch to Gnome3.:(

The menu item is missing on my system, as well.

However, by using a workaround, it's possible to have multiple active logins:

[LIST]
[*]<Super>L locks the screen, from where it's possible to switch users. 
[*] <Ctrl><Alt><F7> goes to GDM which allows secondary logins. 
[/LIST]
  Then, there are two ways to switch users:

[LIST]
[*]<Ctrl><Alt><Fx> goes straight to the other user session (probably F2=1st user, F3=2nd user, but this depends in part on whether you've opened virtual terminals before the second user login); or 
[*]<Ctrl><Alt><F7> goes to GDM which acts like an unlock screen. 
[/LIST]
The first takes a fair number of seconds (7-10) on my system (3 screens: 1 tablet, 2 monitors) for Xrandr to finish and the screens to settle down. The second takes longer. Centos/RedHat EL7 seems faster.

I've had a bit of instability in the display configurations when initially switching users (eg. one monitor will turn off, and I have to configure Display Settings), but after switching 2 or 3 times, it works stably.

Just logged in under CentOS 7 (stock, except FC23 kernel and FC23 xorg intel driver).

What a difference! Full switch from one user to another in 1/2 second or less (using <Ctrl><Alt><Fx>. No long delays during switching, no flashing of screens, no screens turning off unexpectedly, no X/gnome session lock-up. It works cleanly and smoothly.

---

### Post by R Smit on 2016-06-17
> **dcmay-f said:**
> Just logged in under CentOS 7 (stock, except FC23 kernel and FC23 xorg intel driver).

What a difference! Full switch from one user to another in 1/2 second or less (using <Ctrl><Alt><Fx>. No long delays during switching, no flashing of screens, no screens turning off unexpectedly, no X/gnome session lock-up. It works cleanly and smoothly.

Thank you.
But this solution is not user-friendly I think. This spoils the otherwise nice Gnome interface.

---

### Post by dcmay-f on 2016-06-17
The "Switch User" menu item uses GDM to switch to another account - even once the other account is already logged in.

I just tried this under CentOS 7. Just like Ubuntu, there are substantial (5+ second) delays, flashing of screens, and GDM session lock-ups. (Fortunately, <Ctrl><Alt><F1> still worked ...)

I think *that* spoils the otherwise nice Gnome experience :). So I feel that <Ctrl><Alt><F1> is much more user friendly -- at least in RedHat / CentOS where it effects an almost instantaneous switch. In Xenial, it's not.

But I fully agree this menu item should be there! I tried Xenial in tablet mode -- and it seems there's no way to switch users without a keyboard! unless this menu item gets added.

---

### Post by kurt18947 on 2016-06-17
Yes, and rather irritating isn't it? I discovered a work around but it may or may not work properly depending on graphics chipset. I prefer light-dm over gdm and there's a package - dm-tool that enables user switching. The command is 

```
dm-tool switch-to-greeter
```

I've installed that function and a couple others as .desktop files and use a Gnome extension to activate the .desktop file. The AMD board using integral AMD graphics (HD4200) works as expected. A T410 ThinkPad with Intel graphics doesn't work correctly. The ThinkPad will launch the greeter page and will switch users but when switching back to the original user, the mouse pointer disappears. It's active, I can see indications when I move the pointing stick around but there's no pointer on the screen. Logging out and logging back in restores the pointer but that's rather pointless. Possibly a different theme or cursor on the Thinkpad would help, I haven't experimented with it.

Edit: Apparently the Intel bug is well known. It has to do with locked sessions/screens.

---

### Post by jbicha on 2016-09-13
Hi, this bug is fixed now. You should find Switch User by clicking your name in the system status menu in the top right corner of GNOME Shell.

---

### Post by experimancer on 2016-10-28
No it isn't. I'm on Ubuntu 16.04.1 with the latest updates of all thje packages (27.10.2016) and the Swicth User is not displayed in the graphical desktopI. Also none of the workarounds (pressing super-L or CTRL-ALT-L) do not work - they only lock the screen, but do not let anyone but thje same logged-in account to unlock it.

Your above post, @jbicha  is false, please remove or correct this bug that is serious regression in Ubuntu/Linux UI and user experience in general.

---

### Post by jbicha on 2016-10-28
@experimancer I did fix the original bug.

Are you using gdm or lightdm?

How did you add the other user?

Have you restarted the computer after applying updates?

About the workaround, on the unlock screen, there should be "Log in as another user"

---

### Post by experimancer on 2016-10-28
> **dcmay-f said:**
> The menu item is missing on my system, as well.

However, by using a workaround, it's possible to have multiple active logins:

[LIST]
[*]<Super>L locks the screen, from where it's possible to switch users. 
[*] <Ctrl><Alt><F7> goes to GDM which allows secondary logins. 
[/LIST]
  Then, there are two ways to switch users:

[LIST]
[*]<Ctrl><Alt><Fx> goes straight to the other user session (probably F2=1st user, F3=2nd user, but this depends in part on whether you've opened virtual terminals before the second user login); or 
[*]<Ctrl><Alt><F7> goes to GDM which acts like an unlock screen. 
[/LIST]
The first takes a fair number of seconds (7-10) on my system (3 screens: 1 tablet, 2 monitors) for Xrandr to finish and the screens to settle down. The second takes longer. Centos/RedHat EL7 seems faster.

I've had a bit of instability in the display configurations when initially switching users (eg. one monitor will turn off, and I have to configure Display Settings), but after switching 2 or 3 times, it works stably.

Just logged in under CentOS 7 (stock, except FC23 kernel and FC23 xorg intel driver).

What a difference! Full switch from one user to another in 1/2 second or less (using <Ctrl><Alt><Fx>. No long delays during switching, no flashing of screens, no screens turning off unexpectedly, no X/gnome session lock-up. It works cleanly and smoothly.

The above does not work in Ubuntu/16.04.1, using super-L or ctrl-alt-Fx keys just locs the screen but does not let another user log in (the functionality that Switch User provides is still missing). This is not a *workaround* but just false and OT misi-information that does not relate to thish bug nor Ubuntu/16.04.

---

### Post by experimancer on 2016-10-28
> **jbicha said:**
> @experimancer I did fix the original bug.

Are you using gdm or lightdm?

How did you add the other user?

Have you restarted the computer after applying updates?

About the workaround, on the unlock screen, there should be "Log in as another user"

1. Using lightdm (and gdm in another install)

2. Other users added manually (adduser in bash) and in system UI (uids > 1001)

3. Computer restarted several times after updating to accountservice 0.6.40-2ubuntu11.2

4.  Workarounds do not work, there is no "Login as another user" -option   after super-L or ctrll-alt-L, the screen just gets locked and only the   original user can unlock, pressing ctrl-alt-f7 does nothing and   ctrl-alt-f1 just lets to log in as console user (not with graphical UI   like the Switch User would).

---

### Post by jbicha on 2016-10-28
> **experimancer said:**
> This is not a *workaround* but just false and OT misi-information that does not relate to thish bug nor Ubuntu/16.04.

Please stop using the word false and try to be more respectful here.

There was a bug and the bug was fixed. The issue you are experiencing is a different issue and will require a different solution once we figure out what's different about your situation and what's not working.

If you have some time, could you try starting from a virtual machine install of either Ubuntu 16.04 (default with Unity) or Ubuntu GNOME 16.04. If you can reproduce the bug, list the steps that you took. I did this in the original bug (in the Test Case in the bug description). When I said "Add user" there, I meant using the GNOME Settings app and clicking Users, then Unlock, then Add User.

---

### Post by kurt18947 on 2016-10-31
Here is a workaround I used until the bug was fixed (which I just became aware of due to this thread). I created a desktop file - I'm using lightdm on Ubuntu Gnome 16.04.1 64 bit.  Here's my desktop file:
```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=system
Name[en_US]=Switch-Users
Exec=dm-tool switch-to-greeter
Name=
Comment=
```

There is a similar workaround for GDM but I don't have access to it right now. It uses something other than switch-to-greeter.

---

