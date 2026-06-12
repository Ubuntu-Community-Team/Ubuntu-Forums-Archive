---
title: "Gnome not working"
date: 2009-04-11
forum: General Help
---

### Post by adimania on 2009-04-11
I installed gfxboot themes after which many of my applications stop starting so I restarted my laptop and from that point my gnome display manager has failed to load. Instead my laptop starts command line showing tty1.
I also tried "sudo gdm" but I got an error i.e.:
symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime

---

### Post by Tipped OuT on 2009-04-11
Re-install Ubuntu, and next time google things before screwing with stuff like that. Sorry man.

---

### Post by adimania on 2009-04-11
Thanx man, you really made my day.
If I had to reinstall UBUNTU then whats the use of this forum!!!

---

### Post by Tipped OuT on 2009-04-11
Well you seem like a beginner. And I'm no linux professional either. When ever I mess up I just re-install. Trial by error, that's how you learn man. Try to go into safe graphics mode, I'm not sure. But it sounds like you messed it up badly to the point it can't boot. If you have MSN Messenger, contact me at [email]ckm_hexed@live.com[/email]

---

### Post by adimania on 2009-04-11
It is booting perfectly but instead to GUI It booting to terminal mode, anyways reinstalling is the last option....
Let me try to fix it first somehow

---

### Post by Xispa on 2009-04-11
try to type:

sudo /etc/init.d/dbus restart
sudo /etc/init.d/gdm restart

---

### Post by adimania on 2009-04-11
I tried 
sudo etc/init.d/gdm start

It says Gnome Display Manager            [Fail]

---

### Post by killerdogg77 on 2009-04-11
Have you tried this sudo dpkg-reconfigure -phigh xserver-xorg If that dont work you may have to reinstall your video driver

---

### Post by lisati on 2009-04-11
> **Tipped OuT said:**
> Well you seem like a beginner. And I'm no linux professional either. When ever I mess up I just re-install. Trial by error, that's how you learn man. Try to go into safe graphics mode, I'm not sure. But it sounds like you messed it up badly to the point it can't boot. If you have MSN Messenger, contact me at [email]xxxxxx[/email]

Be careful of sharing email addresses on these forums - they are "spidered". I have one email address which I only have associated with [www.ubuntuforums.org](www.ubuntuforums.org), and from time to time I get junk emails to it. They could only have learnt my email address from my profile page.

---

### Post by mreude on 2009-04-26
Are you still working on this problem?

If so you might be able to uninstall the packages affecting your gdm. I'm not sure exactly how to do that with the package you installed, but if it was from source code you might try something like: 

```
cd <to source directory>
make uninstall
```

I had an issue installing glib via source and was able to get my gdm to start after uninstalling the package that way.

Hope this helps.

---

