---
title: "gdm failed to start"
date: 2009-06-08
forum: General Help
---

### Post by ciberglo on 2009-06-08
After I was changing my python (and trying to install python gtk), and rebooted, I realized that gdm couldn't start anymore.

Didn't remember me removing anything, just changing, reinstalling or upgrading
but, don't know for sure

I just know that:

When I boot, my screen blinks 2 or 3 times, black, and then, the cursor shows up (it variates, sometimes the cursor shows up, sometimes its only a black screen) waiting for the login screen, but still only the cursor and a black screen in the background, but nothing about the login screen

tryed to change the terminal  (CTRL + F#) (# a number), and typed this commands:

apt-get install gdm
apt-get install gdm --reinstall
aptitude install gdm
aptitude reinstall gdm
apt-get build-dep gdm
dpkg-reconfigure gdm

and tried all of this with ubuntu-desktop too

then, tried removing my nvidia driver, and also nothing
tried typing:

dkpg-reconfigure xserver-xorg


and still nothing.

The first time I tried to install ubuntu-desktop, the terminal told that it was not installed, and after downloading all the packages necessary, the terminal paused too much time trying to install a hal*... something, but so much time that I had to type a CTRL+C and type the command to install again
but when I typed the command (apt-get install ubuntu-desktop) the terminal told that it was already installed
so I just followed by typing --reinstall after the command, and the terminal reinstalled ubuntu-desktop
but then nothing fixed

so, I'm here

asking for help, with any ideas

=/

please!

---

### Post by The Cog on 2009-06-08
I would try (from the terminal) - first make sure GDM is really stopped with
**sudo /etc/init.d/gdm stop**
and then try to start X by hand:
**startx**
and see i the error messages give any useful clue.

---

### Post by ciberglo on 2009-06-08
Now I can't start neither the terminal

The boot pauses after loading bluetooth interface
something like that

tried to edit grub and change the "quiet splash" with "single", but nothing too

so, I need more help now:

Need to have a terminal first.
How can I get there?

I'm realizing that there's no way to fix this error.

If anyone could help, I'd really thank you for that.

and also thanks Cog, when I get there, I'll try your idea.
thk'u so much

---

### Post by The Cog on 2009-06-09
Sotty, but I really don't know where to go from there. Maybe use a live CD to get my data backed up, and then reinstall.

---

### Post by ciberglo on 2009-06-09
Yeap, I did that.

=/

That's the only solution.

Thks all that helped me.

---

