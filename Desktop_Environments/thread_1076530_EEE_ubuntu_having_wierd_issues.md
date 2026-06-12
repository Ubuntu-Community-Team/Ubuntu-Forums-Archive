---
title: "EEE ubuntu having wierd issues"
date: 2009-02-21
forum: Desktop Environments
---

### Post by svguy on 2009-02-21
So i've had a full 8.04 install of Easy Peasy, or EEE ubuntu, on my little Asus for over a month now and it's been great. I've got compiz fusion running well and smoothly. Everything works great.

Then earlier this week I went to boot it up and it seemed to just 'freeze' once it reached the desktop.  Conky was frozen, but the mouse could move, but nothing would respond, not even the keyboard.

That then happened once more about the middle of the week.

Then today I go to turn it on and the Easy Peasy desktop won't stop launching, and I can't make it go away.  One of my panels is half visible at the top, and conky keeps trying to run over it.  And i've double confirmed that Maximus and UME-desktop launcher are removed from startup sessions, so I don't know what gives.

Has anyone else run in to this?

---

### Post by blackened on 2009-02-21
Easy Peasy was never stable on my 900. Never could figure out what was causing problems (hard freezes, keyboard lockouts), so I saved myself some hassle and switched to eeebuntu ([http://eeebuntu.org/]("http://eeebuntu.org/")) instead. After you change away from the crap default theme and install maximus it works like a charm.

---

### Post by svguy on 2009-02-25
Thanks for the reply Blackened.

I ended up finding some autostart files in /etc/xdg/autostart/  that I guess had recently come up during an update.  I moved the files in relation to maximus and UME-launcher and now I don't have THAT problem anymore.

However, i'm still getting weird issues on boot maybe 25% of the time.

This morning, I got to work, booted up, and it asked me for my keychain password to connect to the network.  Typed that in via my bluetooth keyboard.
It connected, got an IP and was all happy, then I noticed that conky stopped moving.  I hit my hotkey for pulling up a terminal, and top worked, and showed conky as running. But when I did a kill -HUP conky didn't restart.
I also did a kill -9 and conky did not go away.  I did that 4 or 5 times and conky never went away.

My bluetooth mouse wasn't working, so I tried to do hidd, and it just dropped a line and blinked.
I opened a new terminal and tried to do poweroff, and of course it wanted me to be root, so I did sudo poweroff now, and nothing happened.
I did sudo reboot, and nothing happened.
I did ctrl-alt-del three times and nothing happened. I clicked the power button, and the shutdown menu did NOT pop up.

I finally had to hold the power button down until it shut off.  I turned it back on, and all was right with the world.

---

