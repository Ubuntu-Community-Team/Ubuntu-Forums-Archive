---
title: "need help, please!"
date: 2009-03-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 2roombas on 2009-03-08
I just bought and received my Dell mini two days ago. It uses the Ubuntu 8.04 OS. I loved it ...it was working great until I went into **Systems/Administration/Users and Groups**, unlocked it then chose my account (I'm he only user of this mini). I then clicked **Properties**, then the **Advanced **tab where I "thought" I could simply remove the extra "w" that I incorrectly typed in my name in the set up. I deleted the extra "w" from my name in the Home directory field and the Main Group field.

I have learned the hard way that doesn't work! Now when I boot up I see....

*"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by otter users."*

I then click **OK **and see the message...

*"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."*

There is a "**View detail**" link and those details are below...

/etc/gdm/Xsession: Beginning session setup...
Can't save user-dirs.dirs
Setting IM through: im-switch for locale-en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Could not create gnome accelerators directory '/home/jennette/.gnome2/accels': Permission denied

I then click **OK**... wait for the login screen, then click the little options icon in the bottom left corner. I choose "**failsafe GNOME**" and return to login. Incorrect...invalid.

I have tried repeatedly so I know I have used the correct pswd. This is making me nauseous. I'm deaf and I was all excited to be taking this as a communication aid to a meeting I have next month. I want to cry.:(

---

### Post by ugm6hr on 2009-03-09
I have never done this, but I think the problem is that there is no home directory for your new username.

Try using the Terminal from the login screen:
Ctrl+Alt+Fn+A

If you can get there, then hopefully you can correct this problem.

However, I am not certain if you will be able to log in, since you have changed the admin username.  Try both with and without the "w" (it should be without).

Unfortunately, the way that Dell Ubuntu is set up, there is no way to access the Failsafe Root terminal (and you can't change the settings easily at this stage).

If this doesn't work, it would probably be just as easy to reinstall as it would to rescue the situation.  You *could* use a LiveUSB to edit /boot/grub/menu.lst to allow Recovery Terminal; then use this to edit the username details.

I realise I may have used lots of terms you don't understand; don't worry, if you need more help (after trying to access Terminal), just report back.

Ref: [http://www.freesoftwaremagazine.com/articles/users_in_ubuntu#comment-71870](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu#comment-71870)
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---

### Post by sirebral on 2009-03-09
I see what you did.  Hold on and don't fret to bad.  I am fairly certain this is a fixable problem.

I can tell you what is happening.  When you OS loads, it is looking for a directory that does not exist.  What needs to be done is to edit the configuration so that we add the 'w' and then it will find your file.

Let me try something out for you.  I might have a quicker option.

---

### Post by sirebral on 2009-03-09
Ok back.  Here is something you can try.

Create a New User:
[LIST]
[*]Try using the Terminal from the login screen: **Ctrl+Alt+Fn+A**
[*]Login with your user name and password (if you can)
[*]then type **sudo adduser [USERNAME]**; replace **[USERNAME]** with the name you want.  I don't know if this is going to work.
[*]Restart and login with new user name.
[/LIST]

If that doesn't work, I would suggest contacting DELL. You should be able to get a replacement since your is probably under some warranty.

I can look for more options.

---

### Post by ugm6hr on 2009-03-09
Is this fixed now?

[http://mydellmini.com/forum/i-need-some-help,-please%C7%83-t4861.html](http://mydellmini.com/forum/i-need-some-help,-please%C7%83-t4861.html)

---

### Post by 2roombas on 2009-03-10
tes, thank you!:D

---

