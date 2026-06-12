---
title: "Fast BIOS clock? (Inspiron 1420)"
date: 2008-09-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by perryrt on 2008-09-04
Ok, so this one is a little strange, and I don't THINK it's Ubuntu related, but still..

I own a Inspiron 1420 with Ubuntu. Recently, I was having problems with the disc check occasionally failing with a fsck exit status 3. Following the advice I found here, I was planning to change the date in the BIOS to fix this.

However, when I got to the BIOS to do this....I saw something else. 

My BIOS clock thinks time moves....really fast. I go into the setup routine, and my guess is that my BIOS clock advances about a day every 5-10 (actual) seconds. I hadn't noticed it because I am automatically synchronizing my clock to the internet, so when I log in, the system looks up the time (via NTP, presumably) and it fixes itself in about 30 seconds.

So.... I dunno. I haven't updated the BIOS or anything. 

Has anyone else run into this one?

I started to notice this after I upgraded to Hardy....there's no way that's related?

This has to be a hardware issue...right?

---

### Post by SuperSonic4 on 2008-09-04
Sounds like a BIOS issue. Have you checked to see if it's the latest version of the bios? If not take it up with dell, flashing the bios can ruin your pc!

---

### Post by damis648 on 2008-09-04
You may update your BIOS within Ubuntu if you do not have Windows using the following terminal commands as your normal user:

```
wget -q -O - http://linux.dell.com/repo/firmware/bootstrap.cgi > bootstrap.sh
sudo bash bootstrap.sh
sudo aptitude install firmware-addon-dell
sudo aptitude install $(sudo bootstrap_firmware -a)
sudo update_firmware
```

If the last command returns that new BIOS has been found and can be updated, prepare the update with:

```
sudo update_firmware --yes
```

When it completes, let the BIOS update by performing a soft reboot by going to System>Quit... and click "Restart". After Ubuntu shuts down, the screen will remain black for about 1-2 minutes. The computer will then reboot, reporting the updated BIOS version. This might fix the clock issue. Good Luck!

---

### Post by perryrt on 2008-09-04
I'll look into that. I have to admit, I'd prefer NOT to flash the BIOS unless I have to. It's my understanding that updating the BIOS is just about the only thing you can do with a computer that is potentially unrecoverable... if you screw it up, it could brick your laptop.

Yah, I know, it's very unlikely. However, it is a possibility, so I figured I'd try to see if there's some other way to go first.

---

### Post by damis648 on 2008-09-07
Just checking up, have you found out anything new yet?

---

### Post by perryrt on 2008-09-08
[QUOTE=damis648]Just checking up, have you found out anything new yet?[/QUOTE]

No, I hadn't. But I've been on the road - won't be back at home until Saturday. Right now this is my only computer and my link to the outside world - I've learned the hard way not to install software or make changes to it unless I have time and restore discs at hand. :)

Was planning to probably flash the BIOS next week. I was just hoping there was a easy solution.... (never is!)

---

### Post by GeorgeFisher on 2008-10-09
Did you sort out the problem?  One of my PCs (Dell Optiplex GX150) has a BIOS clock that races to the extent that I first thought that the seconds were milliseconds.  

After running diagnostic tests the only thing I found wrong was that the "port base addresses 2f8h and 3f8h" were transmitting at 111999cps instead of an expected 5600cps.  I have no idea what this means, but I guess it might be related...

---

### Post by notwen on 2008-10-09
Odd.  I'll be sure to check my Inspiron 1420n's BIOS when I get a chance.  Keep us informed if/when you try flashing your BIOS and if it resolves your issue.

---

