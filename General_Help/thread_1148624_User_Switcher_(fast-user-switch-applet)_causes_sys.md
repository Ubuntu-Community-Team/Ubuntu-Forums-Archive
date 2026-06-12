---
title: "User Switcher (fast-user-switch-applet) causes system crash and corruption"
date: 2009-05-04
forum: General Help
---

### Post by Willard on 2009-05-04
Greetings.

I just installed Jaunty Jackalope on my Asus F8SA notebook.

[[COLOR="RoyalBlue"]Notebook specification[/COLOR]]("http://www.asus.com/Product.aspx?P_ID=cqAQLgmnndFyHdO3")

The most noteworthy details are that the notebook has:

[list][*]an Intel® Core™2 Duo Processor, and[*]an ATI Mobility™ Radeon®HD 2600 graphics card[/list]

I installed the 64 bit (amd64) desktop version of Jaunty.

Everything was running smoothly, until I decided to try out the Guest user in the "User Switcher" applet. I click the applet, select "Guest", and the computer crashes and reboots.

When I get back to the login screen, I log in, but when I am back in gnome, my keyboard and mouse don't work. I attach a USB keyboard and mouse and then I can interface with my computer again.

Perhaps I should have stopped there. But being [[COLOR="RoyalBlue"]a scientist[/COLOR]]("http://xkcd.com/242/"), I decided to try to create a new user account, and see if this was only a problem with the "Guest" user (then I thought I could just create my own sandboxed Guest user, and let other users who borrow my machine use that user).

I click the user (his name was "hat") in the User Switcher, and the computer crashes and reboots again. However, this time, when I get to the "gdm" login screen, "gdm" will not authenticate neither me, nor the new user "hat". So I am "locked out" of my machine.

I tried restarting in single-user mode and running "fsck" with no luck. I was curious to know what went wrong, so I wanted to get a root prompt and poke around, but the prompt asked for a password, which is nonexistent.

I haven't lost anything of importance (except for a few hours of my life, but this experience was also interesting). All my files are backed up, so I am planning on doing a re-install, and just not use the "User Switcher". I can live without it (after all, I was only curious about it in the first place. But what was that proverb about curiosity and cats again?).

However, I find it **quite severe** that a silly applet can cause all this damage. I have a live CD, so I have access to all files on my drive, so I am willing to post whatever logs or configurations you like to see to get to the root of this problem, for the sake of other people who might end up in the same problem, without the options I have at my disposal (backup & re-install). The best thing, of course, would be if I did not need to reinstall Jaunty. ;)

If this is a known issue, then we can just leave it at that.

In case it is relevant, here are a few non-standard configurations I made on my Ubuntu:

[list][*]I run Gnome with Xmonad instead of Metacity. I followed [[COLOR="RoyalBlue"]this guide[/COLOR]]("http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome") for the setup, and have customised Xmonad to my liking in ~/.xmonad/xmonad.hs [*]I have 3 partitions for Ubuntu: 1 for swap, 1 for /home, 1 for /. I am using ext3 on /home and /, with the options noatime, nodiratime, data=writeback, nobh, commit=60 enabled (I also enabled them in grub). [*]I have 1 partition for Windows Vista. But it is not mounted on startup, so it should be irrelevant.[/list]

I would appreciate if you at least tell me very soon which files you would like to see from my drive, so I can get my notebook up and running again as soon as possible (I need it functional).

Best regards,
Willard.

---

### Post by Willard on 2009-05-04
As I urgently need my notebook operational, I am re-installing Jaunty (just hope this won't happen again...). I have made a backup of all hidden files in my home directory, as well as all of / excluding /home, in case someone wishes to investigate this quite severe hick-up. I will keep those files for a while (several weeks).

-- Willard

---

