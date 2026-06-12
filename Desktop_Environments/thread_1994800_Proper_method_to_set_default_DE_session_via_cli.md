---
title: "Proper method to set default DE session via cli???"
date: 2012-06-03
forum: Desktop Environments
---

### Post by kansasnoob on 2012-06-03
I actually have two silly questions so bear with me :)

First of all my main reason for reexamining this is at least three people have had trouble selecting the proper session after following my [Precise classic (no effects) guide]("http://ubuntuforums.org/showthread.php?t=1966370"). I'm aware that the standard classic session has some Compiz related problems such as a borked panel layout, garbled graphics, or even still booting to a Unity DE. Since I've never really cared for Compiz anyway I'm hardly the person to try and figure out these issues ;)

So **question #1** regards the proper CLI method to set the default session. Clear back when Oneiric was first released it was necessary to manually set that anyway due to a bug in lightdm. So I still had some notes about setting that using:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s <session-name>
```

And you could see the available sessions by running "ls /usr/share/xsessions", example:

```
lance@lance-desktop:~$ ls /usr/share/xsessions
gnome-classic.desktop  gnome-fallback.desktop  ubuntu-2d.desktop
gnome.desktop          gnome-shell.desktop     ubuntu.desktop

```

So I'd replace "<session-name>" with the proper one of those options, eg:

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-fallback
```

But I wonder what file reflects that change?

And does that change effect all users or just the user account that's logged in?

Or is this even the best (or proper) method to set the default DE session?

I can see that "/etc/lightdm/lightdm.conf" is not effected:

```
lance@lance-desktop:~$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
autologin-guest=false
autologin-user=lance
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=lightdm-gtk-greeter
```

Now for **question #2**. I can see looking at "/usr/share/xsessions" that both "gnome" and "gnome-shell" exist. Now I know what the other 4 sessions are, but which of those two is the proper session to set for booting a true gnome3/gnome-shell DE?

I rather suspect it's gnome-shell, but what exactly does just "gnome" do?

---

### Post by matt_symes on 2012-06-03
Hi

Question #1.

```
sudo bash -c "strace /usr/lib/lightdm/lightdm-set-defaults -s gnome.desktop"
```

gives ...

```
<snip>
close(3)                                = 0
munmap(0x7fd0463bb000, 4096)            = 0
rename("/etc/lightdm/lightdm.conf.HLOZEW", "/etc/lightdm/lightdm.conf") = 0
exit_group(0)
```

```
matthew@matthew-Aspire-7540 /etc/init.d
 % cat /etc/lightdm/lightdm.conf                                               

[SeatDefaults]
user-session=gnome.desktop
greeter-session=unity-greeter
matthew@matthew-Aspire-7540 /etc/init.d
```

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu.desktop
```

```
matthew@matthew-Aspire-7540 /etc/init.d
 % cat /etc/lightdm/lightdm.conf                                                

[SeatDefaults]
user-session=ubuntu.desktop
greeter-session=unity-greeter
matthew@matthew-Aspire-7540 /etc/init.d
 % 
```

Therefore..

```
/etc/lightdm/lightdm.conf
```

I do not understand why it's not reflected in your lightdm.conf :confused: This is on 12.10.

EDIT:

```
matthew@matthew-Aspire-7540 /etc/init.d
 % ls /usr/share/xsessions 
gnome.desktop  ubuntu-2d.desktop  ubuntu.desktop
matthew@matthew-Aspire-7540 /etc/init.d
 %
``` 

Question #2.

No idea. I am not using gnome shell at the moment. :P

Kind regards

---

### Post by kansasnoob on 2012-06-05
> **matt_symes said:**
> Hi

Question #1.

```
sudo bash -c "strace /usr/lib/lightdm/lightdm-set-defaults -s gnome.desktop"
```

gives ...

```
<snip>
close(3)                                = 0
munmap(0x7fd0463bb000, 4096)            = 0
rename("/etc/lightdm/lightdm.conf.HLOZEW", "/etc/lightdm/lightdm.conf") = 0
exit_group(0)
```

```
matthew@matthew-Aspire-7540 /etc/init.d
 % cat /etc/lightdm/lightdm.conf                                               

[SeatDefaults]
user-session=gnome.desktop
greeter-session=unity-greeter
matthew@matthew-Aspire-7540 /etc/init.d
```

```
sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu.desktop
```

```
matthew@matthew-Aspire-7540 /etc/init.d
 % cat /etc/lightdm/lightdm.conf                                                

[SeatDefaults]
user-session=ubuntu.desktop
greeter-session=unity-greeter
matthew@matthew-Aspire-7540 /etc/init.d
 % 
```

Therefore..

```
/etc/lightdm/lightdm.conf
```

I do not understand why it's not reflected in your lightdm.conf :confused: This is on 12.10.

EDIT:

```
matthew@matthew-Aspire-7540 /etc/init.d
 % ls /usr/share/xsessions 
gnome.desktop  ubuntu-2d.desktop  ubuntu.desktop
matthew@matthew-Aspire-7540 /etc/init.d
 %
``` 

Question #2.

No idea. I am not using gnome shell at the moment. :P

Kind regards

Thanks for the info :)

Unless they do a Quantal iso-respin today I'm going to test a few things and see what I can blow up :lolflag:

---

### Post by kansasnoob on 2012-06-10
After quite a bit of playing around it appears that I'd actually want to edit .dmrc in home:

```
lance@lance-desktop:~$ ls -a
.              Desktop           .gvfs             Public
..             **[COLOR="Red"].dmrc[/COLOR]**             .ICEauthority     .pulse
.adobe         Documents         .local            .pulse-cookie
.bash_history  Downloads         .macromedia       Templates
.bash_logout   examples.desktop  .mission-control  .thumbnails
.bashrc        .fontconfig       .mozilla          Videos
.cache         .gconf            Music             .Xauthority
.compiz        .gnome2           .opera            .xprofile
.config        .gstreamer-0.10   Pictures          .xsession-errors
.dbus          .gtk-bookmarks    .profile          .xsession-errors.old

```

```
lance@lance-desktop:~$ cat .dmrc

[Desktop]
Session=gnome-fallback

```

But I don't know how I'd do that in a single command :confused:

---

### Post by kansasnoob on 2012-06-10
A bit off-topic, but I did find a way of disabling the overlay-scrollbars on a per user basis:

```
echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile
```

So I suppose that it would be possible to "mv" the old .dmrc and create a new one with the desired content. Not quite sure of the proper syntax to use though.

---

### Post by markbl on 2012-06-10
> **kansasnoob said:**
> After quite a bit of playing around it appears that I'd actually want to edit .dmrc in home

Thanks for this. I've always wondered where that "last session" info was stored.

> 
But I don't know how I'd do that in a single command :confused:

You just want to script a change to this session? Just do a:
```

sed -i 's/^Session=.*$/Session=ubuntu/' ~/.dmrc

```
to change whatever it was to Ubuntu Unity.

---

### Post by kansasnoob on 2012-06-10
> **markbl said:**
> Thanks for this. I've always wondered where that "last session" info was stored.



You just want to script a change to this session? Just do a:
```

sed -i 's/^Session=.*$/Session=ubuntu/' ~/.dmrc

```
to change whatever it was to Ubuntu Unity.

That command works :guitar:

But - yes there is a but :( - on reboot .dmrc changed again so I need to do some more poking around. Since I'd been playing with that installation quite a bit I'm trying a new fresh install. I needed to do so anyway because I'm finding that much of my info is outdated.

I should give a bit of a back-story to explain. Clear back in 12.04's infancy I began to look at getting a classic look & feel in Ubuntu w/Gnome 3. That resulted in this:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

There are links to most of the pertinent info if you're interested in wasting several hours of your life, but I'm now focusing totally on Precise which is actually even easier to "convert" to running a classic DE with Metacity.

I maintain a few dozen PC's and I need to streamline things so a script just makes good sense. So I need to crunch everything into CLI form wherever reasonable, and I want to try and share what little I know so others can use it.

Anyway, back on-topic, the answer from Eliah Kagan here is one of the best sources I've found so far regarding how to change the default boot session:

[http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins](http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins)

When Precise was in it's infancy, and I was also testing classic w/o effects in Oneiric this was one of the issues:

[http://ubuntuforums.org/showpost.php?p=11419923&postcount=10](http://ubuntuforums.org/showpost.php?p=11419923&postcount=10)

But it was soon fixed in both Oneiric and Precise:

[http://ubuntuforums.org/showpost.php?p=11468859&postcount=191](http://ubuntuforums.org/showpost.php?p=11468859&postcount=191)

Sadly I can't say what package update fixed it, but I stumbled upon this in those old notes:

[http://ubuntuforums.org/showpost.php?p=11451409&postcount=128](http://ubuntuforums.org/showpost.php?p=11451409&postcount=128)

> Those commands (sudo /usr/lib/lightdm/lightdm-set-defaults -s ....) write to /etc/lightdm/lightdm.conf

But the setting in there is only used for autologin, if you boot to the login screen then whatever session is set in ~/.dmrc is what will be set on the greeter by 'default'

To further muddle that, at least here, if there are multiple user accounts & one is set to autologin then that's what happens on boot up - goes directly to that user

If more than one user is set to autologin then I believe it's 'last to set the autologin' option becomes the user booted to or restarted to, ( as in only 1 user can autologin at a time

You may be better off looking at writing a new session value to ~/.dmrc 

If I only had a brain :lolflag:

---

### Post by kansasnoob on 2012-06-11
Just finally have a chance to look at this some more. In a freshly installed, totally unmodified Precise I do have a "/etc/lightdm/lightdm.conf":

```

[SeatDefaults]
autologin-guest=false
autologin-user=lance
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter
```

And a .dmrc:

```
[Desktop]
Session=ubuntu
```

Next I'm just going to test what exactly changes when I use the GUI to select a different session :)

---

### Post by kansasnoob on 2012-06-12
I'm marking this solved but things are complicated :frown:

The [info provided here]("http://ubuntuforums.org/showpost.php?p=11451409&postcount=128") is exactly correct **but** apparently only for fresh installs and maybe upgrades from freshly installed Oneiric's.

Upgrades from Lucid, even if choosing 'lightdm' as the display manager, seem to be very finicky :(

But regardless of any of that the devs did a great job of getting the GUI to work so this is simply an instance where it's best to use the GUI.

And just how hard is it to log out, select the proper session, and log back in? If one can't do that then providing CLI info is probably useless ;)

---

### Post by EasyTarget on 2012-10-04
I know this is kind of old, but I figured I should post this in case someone else stumbles upon this later who has upgraded from Lucid.

The solution here worked for me:
[http://tim.purewhite.id.au/2012/05/](http://tim.purewhite.id.au/2012/05/)

---

