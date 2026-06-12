---
title: "Installing HoN and Steam (HELP)"
date: 2013-06-17
forum: Gaming &amp; Leisure
---

### Post by MiloSx7 on 2013-06-17
Hello Guys and Girls!

I really like this OS and would like to keep it. I mainly use PC for gaming, but this OS is giving me some troubles.

As I try to install Steam through "Ubuntu Software Center", the installation aborts at about 20%, and gives me error code: 

```
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details: The following packages have unmet dependencies:

steam-launcher: Depends: libc6 (>= 2.15) but 2.17-0ubuntu5 is to be installed

```

Also, I downloaded HoN from official site (altough my PC restarted for updates, interrupting download which i resumed manually later, so maybe that is what caused the problem), i launched it (honblahblah.sh), and then window appeared and after about 5 seconds it stopped responding.

If anyone could help me i would be really thankful !!

---

### Post by merc669 on 2013-06-17
I am on Ubuntu 13.04 coming from 12.10. I had no issues with STEAM. But in my case I downloaded from STEAM and not the Software Center. You might try that. Also if you have the Synaptic Package Manager installed, you may want to verify if you have libc6 2.15 or greater installed. Also are you running a 32Bit or 64Bit version?

---

### Post by SL61 on 2013-06-17
It would help to say what "HoN" is. Is it Heroes of Newerth?

---

### Post by Zirts on 2013-06-18
Well... standard procedure..   Tell us about your computer...  specs, 64bit 32bit? exact OS version and DE. Post it and then people will be able to help better maybe.

---

### Post by jll339 on 2013-06-18
For steam, it sounds like it needs libc6 to download.

I did a quick check to see if I had libc6 by trying to install it, but I do have it ask 'libgconf2-4'.

So for you I'd say,
Try typing this in the terminal: 'sudo apt-get install libc6' {enter}, and when it asks to continue just hit {enter} again (yes is default).

Once completed, retry the download for steam.

------

As for HoN not continuing its install... that's weird. So it is freezing up? I'm not entirely sure but I would suggest deleting it and re-downloading it from the site like you did, but uninterrupted this time if possible.

---

