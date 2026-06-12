---
title: "Black screen after login, failsafe Gnome works"
date: 2009-07-21
forum: Desktop Environments
---

### Post by MrNiceguy on 2009-07-21
Hardware is an Acer Aspire One, (hard drive model) running the Netbook Remix.  When I log in, I get a black background and the mouse cursor, nothing more.  I can Ctl-Alt-Fkey to the other terminals.  Logging in using the failsafe Gnome session works fine.

I'm not 100% sure what brought on the problem.  Before the problem started, I had been working on getting anonymous browsing working with TOR and Vidalia, and I believe I had installed updates on my last normal boot.

What I've tried so far:  My first thought was bad or mis-installed updates, so I ran aptitude in text mode and brought all packages up to date.  No change.

Searching both the Ubuntu Forums and the web at large, I found several mentions of similar problems fixed by running "sudo dpkg --configure -a" but that hasn't helped either.

I backed up my xorg.conf and then ran the xorg setup again.  Still no luck.

I also found several mentions of the problem stemming from Compiz.  Netbook Remix runs with Compiz disabled, so I thought it might have somehow gotten enabled and created my problem.  I used aptitude to remove compiz and compiz-core.  Still no change.

Anyone have a suggestion?  I can post whatever logs or configuration files may be helpful.

---

### Post by MrNiceguy on 2009-07-24
Anyone?

---

### Post by MrNiceguy on 2009-07-28
More info on this problem:

I created a test account and logged in using that account.  Everything is normal with the test account.

Apparently, nothing is wrong with the xorg configuration, it's simply a user settings issue.  I'm guessing the problem is either with gnome or the netbook launcher.

I did try renaming all the .gnome* files to old.gnome*, but I still had the same old black screen, white mouse cursor.

Can anyone help with this?

---

### Post by rwwkv6 on 2009-07-29
I'm having the exact same issues, except I'm on an HP 2140 (graphics, Intel 945ME). Creating a test account allows me to login with xscripts running. If I try to login normally I have to use the Failsafe Gnome, or my login hangs with a black screen and white cursor. I was messing around with external monitor settings using the "Display" system tool before this problem began, but I haven't been able to find anything linking it necessarily to the xorg.conf file.

---

### Post by MrNiceguy on 2009-07-29
Got mine working!  Turns out, the problem was with Pulse Audio.

The real breakthrough was when I found the file .xsession-errors in my ~ directory.  Apparently this file is generated on every login, so I can't quote the exact error messages, but there was a line complaining that my account was not a member of pulse-rt.  I added my user to this group and things seem to be working.

One way you can test to see if you're having the same problem I am:  try the standard login, then when the machine is stuck at the blank screen with cursor, hit Ctrl-Alt-F2 to switch to an alternative console.  Log in, then type the command, "sudo killall pulseaudio"  If your problem is the same as mine, the gui session will complete the login, but without sound.  (Alt-F7 to switch to the gui console)

---

### Post by rwwkv6 on 2009-07-29
killing the pulseaudio worked for me too! thanks! how do you add your username to the group?

---

### Post by MrNiceguy on 2009-07-29
Turns out adding your user to the pulse-rt group isn't the best option.  If I read things correctly, that puts you using "real-time" audio, where audio processing is given super-high priority.  This is useful for pro audio recording and the like, but hurts performance in general use.  (I noticed things running a LOT slower myself)

For the record, you can change the group memberships under "Administration", "Users and Groups".  Hit the "Unlock" button and enter your password, hit the "Manage Groups" button to bring up a list of defined groups, find the pulse-rt group and highlight it, then hit "Properties" and check the box next to your user name.  There's a way to do it via command line that's probably a lot easier, but I can't remember it at the moment.

Here's how to actually fix the problem.  I had created a test account while I was troubleshooting this.  If there aren't any other user accounts on your box, you'll need to create one.  You can do this using the same "Users and Groups" item in the GUI, or with the useradd command under the command line.

For the example code below, replace "test" with whatever you called your test account, and "user" with whatever your standard username is.  Log in with this test account and make sure it works.  Then log out and switch to a text console with Ctrl-Alt-F2.  Log in with your standard account, then use the following commands:

```
mv .pulse old.pulse
mv .pulse-cookie old.pulse-cookie
```

This just backs up your existing config files.  Not sure if the .pulse-cookie is necessary, but I figured it's better to make sure.

```
sudo cp -R /home/test/.pulse /home/user/.pulse
sudo cp /home/test/.pulse-cookie /home/user/.pulse-cookie
```

This copies the config files from the test account to your regular account.  Not sure if this last step is necessary - I assumed it would be.

```
sudo chown -hR user:user /home/user/.pulse
sudo chown user:user /home/user/.pulse-cookie
```

This sets your user account as the owner of the stuff we just copied over.  Make sure to replace "user" with your user name.

---

### Post by latanerp on 2009-09-27
> **rwwkv6 said:**
> I'm having the exact same issues, except I'm on an HP 2140 (graphics, Intel 945ME). Creating a test account allows me to login with xscripts running. If I try to login normally I have to use the Failsafe Gnome, or my login hangs with a black screen and white cursor. I was messing around with external monitor settings using the "Display" system tool before this problem began, but I haven't been able to find anything linking it necessarily to the xorg.conf file.

Thank you MrNiceguy and rwwkv6 ... I had the same problem as above on my Toshiba Satellite, spent all day trying to fix it, found this thread through Google, and though I was skeptical at first that this would work since I too had been messing around with my graphics (plugged the laptop into the TV) just before it crashed, it did work. Thanks!!!

---

### Post by openess on 2009-10-09
thanks to the both of you, I got this problem while upgrading a week ago on my acer aspire one (SSD-model) but with the regular 09.04..

I got as far as the .xsession-errors and pulse but dismissed it as irrelevant, I wouldn't have guessed it was a sound issue (I don't, apparently play a lot of sound on my laptop)..

Thanks again, I was close to reinstalling.

---

