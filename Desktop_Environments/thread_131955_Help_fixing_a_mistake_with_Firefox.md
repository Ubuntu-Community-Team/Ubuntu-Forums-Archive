---
title: "Help fixing a mistake with Firefox"
date: 2006-02-17
forum: Desktop Environments
---

### Post by atomicmoose on 2006-02-17
I am new to Ubuntu, and I need your help.

I loaded 5.10 earlier in week and I am really enjoying using this distro. I had previously used Mandrake back in the 7.xx days.

Anyway, I was trying to upgrade the version of FireFox that comes with 5.10 and I made a typo, not realizing it until I was finished. It occured when I was making the symbolic links for Firefox. I was follwing the guide from the wiki.

Here is the error I made:

Instead of typing this, "sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox"

I typed this, "sudo dpkg-divert --divert /usr/bin/firefox.u**d**untu --rename /usr/bin/firefox"

Stupid, I know. How can I fix this so that Firefox launches correctly? As of now, I cannot launch Firefox from the menu, or in the terminal.

I can browse to the file via /usr/bin/firefox.uduntu and launch it, but it isn't right.

The error that I get when I try to launch it is "Failed to execute child process firefox(no such file or directory).

Help!:confused:

---

### Post by heimo on 2006-02-17
I'm not confident giving this advice, because I somehow believe that if you otherwise followed the instructions, including creating the symlink, you should be able to launch firefox. But anyway, this is not too dangerous to try, so I would first remove the /usr/bin/firefox file - or let's just rename it.
```
sudo mv /usr/bin/firefox /usr/bin/firefox_bak
```

Then you could remove the diversion (I've never tried this myself) - using something like:
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

If that went well, you probably got a text saying:
> Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.uduntu'

Now redo the diversion, this time without typo
```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```

And create the symlink:
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

And if it works. \\:D/ Otherwise :oops:

---

### Post by atomicmoose on 2006-02-17
Just did that all and it appears to be working!

Thank you very much. I was stuck on trying to remove the symlink.

Again, Thanks!!!\\:D/

---

