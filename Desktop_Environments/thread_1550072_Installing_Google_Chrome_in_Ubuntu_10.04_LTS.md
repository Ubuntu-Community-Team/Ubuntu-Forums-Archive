---
title: "Installing Google Chrome in Ubuntu 10.04 LTS"
date: 2010-08-10
forum: Desktop Environments
---

### Post by riku88 on 2010-08-10
Sorry if this is in the wrong thread...

I downloaded the Google Chrome for Linux off of their website, and tried the install it. The Package manager gave me the error: "Wrong architecture 'i386'" So I used the terminal and tried to bypass the error by doing this:
```
sudo dpkg -i --force-architecture /home/chris/Downloads/google-chrome-stable_current_i386.deb
```

It worked, and Google Chrome appeared to be installed. But whenever I click the shortcut, nothing happens. It won't open.

Did I do it wrong?
-Chris

---

### Post by Spice Weasel on 2010-08-10
Try this:

```
sudo apt-get install chromium-browser
```

It's exactly the same as Google Chrome.

---

### Post by StealthCP on 2010-08-10
Make sure you remove the Chrome browser package first.  Chromium is the actual project name for the Chrome browser, and is included in the Ubuntu repos.  So you'll find it in the Software Centre and via apt at the Terminal, as Spice Weasel demonstrated.  It's important to install the right package for your architecture, this is probably why Chrome didn't work (are you on amd64?)

---

### Post by KdotJ on 2010-08-10
Aside from installing Chromium from the repo's, it is possible to install Google chrome by downloading the .deb from their website. However, is **is important** that you get the correct architecture and not just to force it in the terminal. You will need the 64 bit deb if you're running amd64 ubuntu, and the 32 bit one if you're running the i386 ubuntu.

---

### Post by samijam on 2010-08-21
> **KdotJ said:**
> Aside from installing Chromium from the repo's, it is possible to install Google chrome by downloading the .deb from their website. However, is **is important** that you get the correct architecture and not just to force it in the terminal. You will need the 64 bit deb if you're running amd64 ubuntu, and the 32 bit one if you're running the i386 ubuntu.

Can't you use the 32-bit Chrome on 64-bit Ubuntu?  I'm wanting to try it instead of using nspluginwrapper which I never had any luck with before.  If so, what would be the best way to install the 32-bit version, from a repo or just downloading the .deb?

---

### Post by jzvbrt on 2010-08-22
Chromium (5.0.375.125 (53311) on Ubuntu 10.04) doesn't download files. It reports increasingly larger download remaining time and than shuts down. Tried to reinstal Ubuntu and Chromium but get the same result. Does anyone have the same problem or even the solution?

---

