---
title: "Remove irssi"
date: 2005-12-24
forum: General Help
---

### Post by zoan on 2005-12-24
HI, for some days ago i installed irssi to test it but now i feel like its not the right client for me so i wana remove it. Only one problem i did not installed it via the apt-get command. i complied it. So how do i remove it.

Sorry for bad english.

---

### Post by dcast on 2005-12-24
sudo apt-get -r irssi 

i believe would be the command or maybe

sudo dpkg -r irssi

---

### Post by zoan on 2005-12-24
```
bdn@Laptop:~$sudo dpkg -r irssi
dpkg - Warning: ignore request to remove irssi thats not have been installed.

```

Hm, it seems its not installed but it is.

---

### Post by dcast on 2005-12-24
what about apt-get -r does that work?
 look in synaptic and uninstall it from there

---

### Post by zoan on 2005-12-24
irssi are not installed in synaptic and apt-get -r does not work.

---

### Post by ardchoille on 2005-12-24
If I remember correctly, irssi is installed with Ubuntu 5.10.. so it may have been already installed when you installed it manually. Sounds like you overwrote it when you installed it manually.

You should get into the habit of checking whether the app is already installed before manually installing it. You can check to see if an app is installed with:

```

dpkg -l | grep appname

```
OR
```

which appname

```

If you installed irssi with ./configure, make, sudo make install, you can hopefully uninstall it with ./configure, make, sudo make uninstall.. that is provided the devs of that app included an uninstall script.

---

### Post by zoan on 2005-12-25
none of the above worked, :\ which irssi just gave me: /usr/local/bin/irssi

i can't translate all the text that i got from the commands above.

---

### Post by anil_robo on 2005-12-26
[quote=ardchoille] If you installed irssi with ./configure, make, sudo make install, you can hopefully uninstall it with ./configure, make, sudo make uninstall.. that is provided the devs of that app included an uninstall script.[/quote]

I installed something (./configure, sudo make install) that I couldn't just remove with whatever. But I searched at forums, read this post, and was indeed able to remove with "sudo make uninstall" command. Thanks Ardchoille!

---

### Post by ardchoille on 2005-12-26
[QUOTE=anil_robo]I installed something (./configure, sudo make install) that I couldn't just remove with whatever. But I searched at forums, read this post, and was indeed able to remove with "sudo make uninstall" command. Thanks Ardchoille![/QUOTE]
You're welcome. Being able to remove the app with sudo make uninstall means the devs included an uninstall script.. which is what I wish ALL devs would do.

---

