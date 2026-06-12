---
title: "Stuck on login screen after upgrade to 12.04: not enough rights to .profile"
date: 2012-09-01
forum: Desktop Environments
---

### Post by mathwizard44 on 2012-09-01
Recently, after upgrading a netbook to 12.04, I ran into a problem where I would try to login, the screen flickers, and it brings me back to the login screen. The guest session can log into the desktop fine, by the way. I was not too concerned, as this has happened before on another upgrade, and I knew that the answer was within reach of a web search.

When I searched the Web, I saw that this was a common problem, and that some of the common fixes were pressing Ctrl-Alt-F1 to get onto console mode, deleting the ~/.Xauthority file, reinstalling Compiz*, trying gdm as default, and some others. I tried all of them that I found, but none of them worked.

Then I saw a post where someone checked his ~/.xsession-errors file. I dropped back to console and examined the file. All it said was

```

/usr/sbin/lightdm-session: 27: .: Can't open /home/mathwizard44/.profile

```

From what I can gather, this explains very well why the other fixes have not worked. In this case, it seems like I don't have enough rights. I don't know how to proceed. Should I delete this .profile, hoping that a restart would provide me with a fresh copy that I could access? Has something else messed up and I need to follow a list of instructions to get those rights back? Will I have to reinstall the system?

Thanks in advance for any answers.

---

### Post by mathwizard44 on 2012-09-01
I just tried my first suggestion, but instead of deleting it, I renamed ~/.profile into ~/.profile-old. (I needed sudo to do this, by the way.)

Now I rebooted the system, and when I tried to log in, I got a popup error:

```
Could not update ICEauthority file /home/mathwizard44/.ICEauthority
```

The button says to log out. And I'm back at the login screen again.

I also did not notice this before... but when I press Ctrl-Alt-F1 to reach the console, after logging in it says that /home/mathwizard44/.profile is Permission denied.

I guess this makes sense in light of my previous observation. I will restore my .profile file and await any other suggestions. Thanks in advance.

---

### Post by Krytarik on 2012-09-01
Make sure all files/directories in your home directory are owned by you, not by 'root', or even yet another user:
```
sudo chown USERNAME:USERNAME -R /home/USERNAME
```Notes: Replace all occurrences of "USERNAME" with your actual username, obviously. You may get an error message reg. the directory '.gvfs', that would be ok.

Regards.

---

### Post by mathwizard44 on 2012-09-02
I ran the above suggestion, using 'chown' on the files of my home folder. Then I rebooted, and I was able to log in. Thank you very much for the help.

The solution makes sense, as previous to doing the clean install of 12.04, I did a poor man's backup: I copied my "~" folder to an external hard drive, then copied it back in place after the install. The .profile file must have been overwritten. I'll make sure to use the backup utility next time. Once again, I appreciate the assistance.

---

