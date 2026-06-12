---
title: "Wrong Colors in 6.10 Loading Screen"
date: 2006-12-14
forum: Desktop Environments
---

### Post by RAdams on 2006-12-14
On my 32-bit machine, installing Ubuntu 6.10 was fine - the loading screen (what you see when you are booting Ubuntu, after the kernel is decompressed) looked as it should.

But on the box spec'd in my sig, the loading screen only appears in dark greys - I can barely make out the word "Ubuntu" and the logo.

Note that:
[LIST]
[*]I previously had 6.06 on the box in my sig, and there were no problems there, nor did I have to pass any special terminal commands.
[*]The fglrx drivers are installed, and correctly
[*]I have detected no other video problems, just this little one.
[*]I tried sudo update-alternatives --config usplash-artwork.so, but because there were no other splash screens, the process failed.
[*]"sudo dpkg-reconfigure linux-image-`uname -r`" failed for the same reason.
[/LIST]

Any idea why? Small matter, but I'd like it cleared up all the same.

---

### Post by Sqwishy on 2006-12-14
I also have a similar problem, everything is grey and ugly, and the bottom part that shows the loading progress is only a couple of grey icky dashes! I've installed ubuntu 6.10 on a couple other computers and it was fine. I'm thinking it has something to do with the graphics card maybe. What card do you have?

---

### Post by RAdams on 2006-12-14
> **Sqwishy said:**
> I also have a similar problem, everything is grey and ugly, and the bottom part that shows the loading progress is only a couple of grey icky dashes! I've installed ubuntu 6.10 on a couple other computers and it was fine. I'm thinking it has something to do with the graphics card maybe. What card do you have?

BaH! I made the sig after that post, but I was hoping it would still attach. Look below for my specs. But yeah, I have the exact same thing as you.

---

### Post by IanW on 2006-12-14
I believe this is a known problem with Edgy64.

See [this bug.]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/67545")

---

### Post by RAdams on 2006-12-15
> **IanW said:**
> I believe this is a known problem with Edgy64.

See [this bug.]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/67545")

>.<

That's it. I hope they fix it soon. It's unsexing my machine. How will I make fun of my M$-enslaved contemporaries with such a fubar'd loadscreen?!

---

