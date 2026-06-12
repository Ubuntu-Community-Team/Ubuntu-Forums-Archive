---
title: "synaptic will not open"
date: 2009-04-07
forum: General Help
---

### Post by tocilog on 2009-04-07
I'm using Ubuntu 8.10. This started happening after I tried changing the permissions for a couple of files. I used the code
```
sudo chmod -R 777 /
```

When I login this message pops up:

"Users $HOME/dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned b user and have 644 permissions. users $HOME directory must be owned by user and not writable by other users."

Another problem is that I can't apt-get anything. the message 

```
sudo: /etc/sudoers is mode 0777, should be 0440
```

pops up in the terminal.

Any ideas as to how to fix this so I don't mess ubuntu up anymore?

---

### Post by adult swim on 2009-04-07
that was a very bad thing to do :)
you will most likely run into problems all over you system after doing that.  there are two alternatives here, manually reset every file/folder's permissions to what they are supposed to be (not worth it) OR backup and reinstall.  you can backup your personal files documents/music/etc by booting a live cd and copying the files you want to keep to some external media.  if you dont have any means to back up, you could create a partition on your hard drive where you could store the files.

---

### Post by kanikilu on 2009-04-07
If you have 8.10, when you turn your computer on, press ESC to get to the grub boot menu and choose to boot into recovery mode. After this starts, you'll be prompted with a menu, choose to drop to a root shell.

Now that you are at a root prompt, you can start fixing some permissions. There may be more things you need to fix, but start with the following (you won't need sudo, because you are already root):```
chmod 755 /home/username
chmod 644 /home/username/.dmrc
chmod 440 /etc/sudoers
```

Replace "username" with your login/user name.

...changing permissions recursively on / to 777 was a bad idea, hopefully you didn't get that in a howto or advice here... :(

---

### Post by InGunsWeTrust on 2009-04-07
edit: oops, kanikilu beat me to it :)

feel free to delete this post

---

### Post by tocilog on 2009-04-07
> **adult swim...]backup and reinstall. you can backup your personal files documents/music/etc by booting a live cd and copying the files you want to keep to some external media. if you dont have any means to back up, you could create a partition on your hard drive where you could store the files.[/QUOTE]
Since I JUST installed 8.10 before I screwed it up I wouldn't mind doing that. 

[QUOTE=kanikilu said:**
> If you have 8.10, when you turn your computer on, press ESC to get to the grub boot menu and choose to boot into recovery mode. After this starts, you'll be prompted with a menu, choose to drop to a root shell.

Now that you are at a root prompt, you can start fixing some permissions. There may be more things you need to fix, but start with the following (you won't need sudo, because you are already root):```
chmod 755 /home/username
chmod 644 /home/username/.dmrc
chmod 440 /etc/sudoers
```

Replace "username" with your login/user name.


ok ill try that later today and let you guys know what happens. 

> ...changing permissions recursively on / to 777 was a bad idea, hopefully you didn't get that in a howto or advice here... :(
....actually I did, but I'm thinking it didn't apply to my situation. I'll read more carefully the next time I need to search for something.

---

### Post by kanikilu on 2009-04-07
If you just installed and don't really have a lot to backup, I would say reinstalling will be your quickest and most thorough option. Changing the permissions on the directories I listed may help, but there are undoubtedly other files or directories that either can't, or shouldn't (for best practices) be 777.

---

### Post by tocilog on 2009-04-07
ok, so this all started when I tried copying a data dvd full of my music onto my fresh Intrepid. I dragged n' dropped. It all copied over and I could play my mp3's but I couldnt rename, move, etc. Is there a specific way to do this so I have permissions over this stuff?

---

### Post by oldos2er on 2009-04-07
> **tocilog said:**
> ok, so this all started when I tried copying a data dvd full of my music onto my fresh Intrepid. I dragged n' dropped. It all copied over and I could play my mp3's but I couldnt rename, move, etc. Is there a specific way to do this so I have permissions over this stuff?

 Do it as root. In CLI, use "sudo" in front of your copy command. In Gnome, use "gksu nautilus" to open the file manager as root.

---

### Post by tocilog on 2009-04-07
That happened tremendously! Thank you guys.

---

