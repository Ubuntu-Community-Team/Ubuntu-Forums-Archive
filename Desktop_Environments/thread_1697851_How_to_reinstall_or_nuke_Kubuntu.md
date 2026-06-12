---
title: "How to reinstall or nuke Kubuntu?"
date: 2011-03-01
forum: Desktop Environments
---

### Post by mma8x on 2011-03-01
Well, found a deal-breaker bug for me in KDE 4.6 (kontact no longer syncs with google-resource).  So I'm trying to revert to kde 4.5.  I did a fresh install of 10.10 on a USB drive, then upgraded to 4.6 (to see if the problem was with KDE or my original install got buggered).  Then I tried to downgrade using ppa-purge.  Now I can't boot into KDE at all.  I get the KDM login, and can boot into gnome from there, but when I boot into KDE it starts to load and then kicks me back to the login screen.  I tried purging every KDE package on the system, deleting my .kde directory and reinstalling, but same problem.  No error messages that I can find in the logs.  So I need to figure out how to totally remove KDE and reinstall (best).  If I do this on my main drive, I'd like to keep my settings as well.  Alternatively, what would be the best way to do a fresh 10.10 install? Should I just backup my /home directory, and start from scratch on the main drive (currently only 1 main+swap partition on the drive)?

---

### Post by Zorael on 2011-03-01
Did you check kdm.log? It often lists errors that Xorg.0.log doesn't.

---

### Post by mma8x on 2011-03-01
Here's the log.  Looks like there are some errors, but I don't know what to make of them.

---

### Post by Zorael on 2011-03-01
It doesn't look like what's causing this is getting logged there.

The only thing I could suggest, unless you're comfortable adding debug statements to the session script, is that you **purge** KDE completely and then reinstall the version you want. Perhaps there are configuration files in /etc that aren't touched when simply removing or downgrading the packages. (Purge removes a package's installed files and its configuration files, remove leaves the configuration files in place.)

The culprit here is likely kdm or kdebase-workspace-bin. If the startup scripts in those end abruptly, X just returns to the login screen as you describe. There were some late changes in Kubuntu's session startup script handling in 4.6, so perhaps the configuration files you have are from 4.6 and the startkde script you have is from 4.5.x. And perhaps they just don't work together.

On another note, if you're going to do a fresh installation keeping your home directory is often enough. You may have weird menu entries from earlier installed programs, but you can clean those out pretty easily. (Have a look at **~/.local/share/applications** and **~/.config/menus**.)

---

### Post by mma8x on 2011-03-01
I had used "purge" to remove KDE previously.  I had assumed I had a non-compatible config file of some sort.  Any ideas where else the offending files might be hiding? I guess I can re-purge, then just search for "kde" and delete.  What a PITA.

Oh, and I had assumed that if KDM were the culprit, I wouldn't be able to use it to load gnome...which I can.

---

### Post by Zorael on 2011-03-02
If you purged and it still didn't work, that's curious. Hmm.

The files I'm concerned about are the ones **kdm** installs into **/etc/kde4/kdm/**, and how well they play together with the startup script **/usr/bin/startkde** from **kdebase-workspace-bin**. If you purge **kdm**, are those configuration files removed properly?

As far as I understand, there are several stages to X startup for which each login manager provides their own script. Taken entirely from memory and likely to be at least slightly incorrect, you have Xwilling to see if the X is willing to accept a connection, then Xsetup and Xstartup to actually start X, and then the session startup script, which in KDE's case is startkde. startkde in turn runs (sources) Xsession, which runs (sources) a lot of other smaller scripts to set up stuff like input method management and whatnot. And if any smaller scripts suddenly fail midway, it just exits with an error and you get sent back to the login screen.

I once had a script in **~/.kde/env** that had a small typo in it, so when Xsession ran (sourced) it, it exited with an error and login silently failed. It took lots of work to find out what was happening. I basically added debug statements to startkde and Xsession that wrote to a log saying how far into the script it actually managed to get.
```
echo "managed to get to point A" >> /tmp/error.log
*[...]*
echo "managed to get to point B" >> /tmp/error.log
*[...]*
echo "now sourcing /etc/kde4/kdm/Xsession" >> /tmp/error.log
*[...]*
echo "now sourcing /etc/X11/Xsession" >> /tmp/error.log
*[...]*
```
Then I followed the execution by reading that log and noted where it just stopped. In my case, it was when it was sourcing .kde/env scripts.

As I mentioned, there was a change to how it sources startup scripts in 4.6 betas to 4.6 release. It used to be that somewhere along the startup process, either in startkde or /etc/kde4/kdm/Xsession, it sourced the generic /etc/X11/Xsession, which in turned had all these little scripts in /etc/X11/Xsession.d/ taking care of dbus startup, input method management, automatically running xmodmap and more. In the 4.6 betas, the KDE Xsession had stopped sourcing the generic Xsession and instead incorporated some of the key startup Xsession.d scripts into itself (notably dbus, polkit, ...). So the desktop worked, but I was missing the functionality of those other small scripts.

If there is indeed version differences between the scripts (Xsession/startkde/other), then perhaps they all think someone else takes care of starting the key stuff, and ultimately it doesn't get done. And then you try to login without dbus and everything goes wrong.

---

### Post by mma8x on 2011-03-02
I purged everything in the "KDE" section of synaptic, then did a "kde" search in synaptic, purged everything there, then did a find / -iname "*kde*", then deleted everything remaining.  Then for good measure cleaned out my cache, reinstalled kubuntu-desktop from 10.10 sources, and...
same problem.  I'll try once more and specifically look for the files you mentioned, but I'm getting pessimistic about this being an easy process on my main drive.  Wish they'd fix that bug.

---

### Post by mma8x on 2011-03-03
3rd time's the charm I guess.  Tried the same method, this time it worked.  BTW, purging still left quite a few KDE files around.  This time I searched for anything KDM or KDE related, and deleted it all after the purging was done.  Reinstalled kubuntu-desktop, and all is well.

---

