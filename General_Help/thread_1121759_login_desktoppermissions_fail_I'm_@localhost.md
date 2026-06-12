---
title: "login desktop/permissions fail: I'm @localhost"
date: 2009-04-10
forum: General Help
---

### Post by agnes on 2009-04-10
Hello everybody,

recently I did ```
chmod -R 777 *
``` to all files on my ubuntu system. 
Ok, by now I know this is not really smart... (to say the least).
So I got that error at login, about the .dmrc file and home directory having too much permissions.

There's already a specialized thread about that topic. So I rebooted to root-prompt, and I typed in those advised commands:
```
sudo chown -R username /home/username/.dmrc
chmod 755 /home/username
chmod 644 /home/username/.dmrc
```
and also
```
chmod 644 /home/username/.ICEauthority
```

After that, when I logged in, I indeed no longer saw an error message, but...:

==> Ubuntu can't find audio device (or some error like that, it still plays audio by the way);
==> Ubuntu can't connect to internet/ssh/etc.; 
==> Ubuntu does not open external harddrives 
  (e.g. USB stick, Windows partition): they're in the file manager, but I can't open or use them;
==> In the Terminal, I'm logged in as username@localhost :-s (instead of username@MyComputerName) 

This last thing is especially strange since when I reboot to that root-prompt, and I log in, 
I'm just logged in normally, as username@MyComputerName.
(By the way in that prompt I can also not find my USB stick.)

Because I could'nt also anymore use sudo (Terminal said something like: you have to get setuid sudo) 
I did again reboot to root-prompt and typed
```
 chmod 0440 /etc/sudoers
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
chmod 4755 /bin/su
```

Then I could use sudo, but the abovementioned problem persisted.

I've also tried to create a new user, and added this user to the groups: adm, admin, audio, cdrom, dialout, disk, floppy, fuse, lpadmin, plugdev and video.
But logged in as this new user the problem also persisted.

](*,)

By the way I also see, at the Ubuntu login display (when you have to type in your username) in the right bottom corner, something like: "localhost@localcomputer", I don't think that's right.

Any help would be strongly appreciated.

---

### Post by mikewhatever on 2009-04-10
It's time to backup and reinstall, hope you've learned the lesson.

---

### Post by agnes on 2009-04-10
Yeah, I already anticipated that... (fortunately I have so far saved all my 'documents' on my Windows partition). 
Good occasion to learn somewhat more about chmod, I guess. :rolleyes:

---

