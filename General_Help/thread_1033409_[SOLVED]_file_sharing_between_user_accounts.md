---
title: "[SOLVED] file sharing between user accounts"
date: 2009-01-07
forum: General Help
---

### Post by 2handband on 2009-01-07
I have two seperate user accounts on my 8.10 install, one for me and one for my wife. I would like her to be able to play the music files in my /home/Music folder. How can I set her up with that access?

---

### Post by northern lights on 2009-01-07
From your account, run ```
sudo chmod -R 776 /home/USER/Music/
```where USER needs to be replaced by your username.

Subsequently log into your wife's account and add a launcher to the desktop or the panel to launch ```
nautilus /home/USER/Music/
```where USER still is your username (not your wife's).

---

### Post by mcduck on 2009-01-07
After setting the read permissions for the directory you could also create a link from it into your wife's home:

ln -s /home/*yourusername*/Music /home/*yourwife*/Music

This way she doesn't need to browse into your home to access the music files..

(also it should be mentioned that she'll need permissions to both read and _execute_ the directory. Read permissions only allows accessing files if you know their exact names/paths, but execution permission is needed to actually list the files inside the directory.. So the octal mode 776 wouldn't work, it has to be 775 or 777.)

---

### Post by namdung on 2009-01-07
Another method:

Share your Music folder. U may give guest access if security is not an issue.

In ur wife's login create a launcher ```
nautilus smb://localhost
```

Right click on the *Music* folder and open with your favorite music player.

---

### Post by Slim Odds on 2009-01-07
Personally, I'd:

1) create a folder like /home/shared/Music and put the stuff there.
2) create a "shared" group
3) Make /home/shared belong to the "shared" group
4) Add you and your wife to the "shared" group

It's a lot cleaner approach

---

### Post by Foxmike on 2009-01-07
I'm having a similar problem, but a bit more complex.  Here it is:

I'm having a partition containing all my multimedia stuff (pictures, music, videos and podcasts).

Right now, that partition is mounted as "/home/shared", and all my folders are owned by root:users with suid and sgid bits enabled, so then if my wife or me add a file to those folders, then the files will be automatically owned by root:users, so that's all good.  Only my wife and I are member of the users group so we can both read files there.

The thing is we are both sharing the same f-spot library as I want to be able to tag pictures and update her library by the same time, and vice-versa.  What I'm looking for, is a way to set the umask on a per-directory level so files created (or imported for a photo camera, say) into thoses directory not only set user to root:users but also set permission to 0660.

I would also like to do that with sensitive data (budjet) so security is an issue here. 

I've considered using ecryptfs but I can't since we might be both connected at the same time.  I've been looking for the bash/mount/chown/chmod manpages and haven't found anything.  Does anyone has a clue?

Thanks!

-FM

---

### Post by 2handband on 2009-01-07
Got it set up. Thanks to all.

---

