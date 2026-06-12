---
title: "Yet another firefox/flash/sound problem"
date: 2006-05-19
forum: Desktop Environments
---

### Post by f3tus on 2006-05-19
Okay, so I searched the forum about this, every topic had a link to another topic and at the end I realised I was going in a circle of links. I found out 2 or 3 ways I can fix this, but none worked. One is, to edit the /etc/firefox/firefoxrc file. BUT, I don't have such a folder/file. I extracted firefox1.5.0.3.tar.gz into my /home/username and that's it. I don't have a firefoxrc file in there, I do in fact have /etc/mozilla-firefox/mozilla-firefoxrc, but that's for the firefox that's in the repositories I assumed. Nonetheless, I tried, and no, it didn't work.

How can I fix this now :/? Is there any other file I can edit?

---

### Post by aysiu on 2006-05-19
Is the problem that Firefox plays Flash but has no sound?

---

### Post by f3tus on 2006-05-19
Exactly.

---

### Post by aysiu on 2006-05-19
Have you tried pasting this into a terminal? ```
killall firefox
sudo apt-get update
sudo apt-get install alsa-oss
firefox
```

---

### Post by f3tus on 2006-05-19
Yeah I've done that. But if I run firefox from the console, It opens 1.0.8. That's because I followed these steps [https://wiki.ubuntu.com/FirefoxNewVersion#head-26d21f8b635c06a9858f7bef322b3821c7545598-2](https://wiki.ubuntu.com/FirefoxNewVersion#head-26d21f8b635c06a9858f7bef322b3821c7545598-2)
so this doesn't work.

/*I've got both 1.0.8 (from the ubuntu repositories) and 1.5.0.3 which is actually just an extracted .tar.gz archive.*/

---

### Post by aysiu on 2006-05-19
[QUOTE=f3tus]Yeah I've done that. But if I run firefox from the console, It opens 1.0.8. That's because I followed these steps [https://wiki.ubuntu.com/FirefoxNewVersion#head-26d21f8b635c06a9858f7bef322b3821c7545598-2](https://wiki.ubuntu.com/FirefoxNewVersion#head-26d21f8b635c06a9858f7bef322b3821c7545598-2)
so this doesn't work.

/*I've got both 1.0.8 (from the ubuntu repositories) and 1.5.0.3 which is actually just an extracted .tar.gz archive.*/[/QUOTE] If you followed those steps completely, *firefox* should open the 1.5.0.3 version, not the Ubuntu version.

Regardless, open up the 1.5.0.3 version and see if it works now.

---

### Post by f3tus on 2006-05-19
Hmmm, strange, it opened 1.0.8 before, I've checked. It opens it with 1.5.0.3 now, yeah... But the sound is still not working.

---

### Post by aysiu on 2006-05-19
[QUOTE=f3tus]Hmmm, strange, it opened 1.0.8 before, I've checked. It opens it with 1.5.0.3 now, yeah... But the sound is still not working.[/QUOTE] So *alsa-oss* didn't do the trick, huh?

I'm not sure. I have 1.5.0.3, but I have an /etc/firefox/firefoxrc file.

What happens when you type: ```
sudo updatedb
locate *firefoxrc
```?

---

### Post by vidak on 2006-05-20
what about /etc/mozilla-firefox/mozilla-firefoxrc?

---

### Post by f3tus on 2006-05-20
```
f3tus@w00t:~$ sudo updatedb
f3tus@w00t:~$ locate *firefoxrc
/etc/mozilla-firefox/mozilla-firefoxrc
f3tus@w00t:~$ 
```

I put aoss instead of none. Doesn't work.

I'll try to reinstall firefox the standard way, we'll see...

Nope... Sound doesn't work, and I still don't have an /etc/firefox/firefoxrc file. Sound worked in 1.0.8 though, although it was out of sync. Maybe I should put something other than aoss? I have alsa for xmms so I guess if I put alsa in, I won't be able to listen to xmms while watching flash. I have artsdsp for amsn. So, what else could I try?

---

### Post by [S|G] on 2006-05-20
Ok, you could try something really silly (but worked for me and a friend of mine)
Go to K control panel, then go to multimedia. There change the "Auto-suspend if Idle after:" to 1 second instead of 60. Apply settings and restart your browser.

I found out that arts kept my sound device busy for a long time, and setting auto-suspend to 1 second would make it let go.

---

### Post by f3tus on 2006-05-20
No, unfortunately that didn't work :/

---

### Post by Rui Pais on 2006-05-21
Hi,
if you don't have an firerefoxrc file (strange because that should be installed by firefox package according to synaptic) you could try launching firefox with:
```
aoss firefox
```
to see if it works...

---

### Post by f3tus on 2006-05-21
Ho ho, /me love you long time now :)))

And it's even in sync now! Wow!

Thanks all!

---

