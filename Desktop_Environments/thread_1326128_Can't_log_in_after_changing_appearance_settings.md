---
title: "Can't log in after changing appearance settings"
date: 2009-11-14
forum: Desktop Environments
---

### Post by oldmankit on 2009-11-14
Hello,

I've got quite a weird problem.  For the first time ever I tried 'emerald --replace' which didn't seem to work that well, it started going really slow, and then I think I typed 'metacity --replace', but I'm not sure (it didn't find it's way into bash history).  The system locked up pretty badly, so I restarted.

When I try to log in to gnome, or even fail safe terminal, there is a fairly long pause, the screen goes blank and shows some errors I can't read quickly enough, and then back to the login screen.  So I can't log in.

The funny thing is that there is another user on this machine and she can log-in fine.  From that user I can even log in to the problematic account in the bash terminal (exec sudo login -p).  It's not a password problem, for sure.  However, I cannot genuinely log-in as this problematic user. 

I've restarted the computer a few times to no avail.

Why would I be unable to login in the fail safe terminal, when I can log in to this this user in a bash session using a different user's account?  What logs / configuration files should I be looking at?

Any suggestions?  Thank you.

---

### Post by oldmankit on 2009-11-16
Update:

After logging in to the bash terminal as user 'kit' (the one that isn't working), I tried to open thunderbird from the terminal.  The following error came up:

```
kit@kit-laptop:~$ No protocol specified

(thunderbird-bin:26904): Gtk-WARNING **: cannot open display: :0.0

```I can successfully open thunderbird using the alternate user.  Does this help?

I also tried the following:
```
kit@kit-laptop:~$ metacity --replace
No protocol specified
Window manager error: Unable to open X display :0.0

```

---

### Post by oldmankit on 2009-11-17
Solved.  It had nothing to do with changing the appearance settings.  The problem was, I was using ecryptfs (according to Bodhizazen's tutorial [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)).  I wanted to remove the Private folder, and didn't do it the 'proper' way (see [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)).

As far as I can remember, I just unmounted the Private folder, then deleted it and the .Private folder, and removed 'auto-mount' from ~/.ecryptfs.  Whatever I did, it stopped me logging in again.

To solve the problem, I re-created ~/Private and ~/.Private, re-mounted the encrypted folder (see Bodhizazen's tutorial) and then created auto-mount again.  Then I could log-in fine.

---

