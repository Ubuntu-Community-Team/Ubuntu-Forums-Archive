---
title: "applications losing my settings"
date: 2009-10-13
forum: Desktop Environments
---

### Post by gastr on 2009-10-13
Hello all,

I'm having some very strange issues at the moment. I've done a search on the forums for similar problems and didn't find anything, although it's one of those problems that it's difficult to think of the right keywords for. Anyway...

I've just had Ubuntu lose all my desktop settings, and a few apps within Ubuntu have done the same. Here's a list what I've found so far to have changed:

[LIST]
[*]desktop wallpaper reset
[*]my chosen ubuntu theme is no longer set and it has reverted to the shipped/default one
[*]i now have only two workspaces in my switcher down the bottom (i had customised it to have four)
[*]the terminal emulator (default ubuntu one) has reverted to the default colour scheme instead of the green-on-black one i'd chosen
[*]transmission bittorrent client has forgotten my default destination directory and has started all my active torrents over again on the desktop
[*]it forgot my default wifi connection and i had to choose it from the list and enter the password again
[/LIST]
at first i noticed only the theme and the wallpaper, and would change those back and then reboot only to find that they had again reverted to the default. i then went into Synaptic and re-installed "ubuntu-desktop" and "ubufox" (next paragraph will tell you why i re-installed firefox) and that stopped it from resetting things each time i rebooted, but it didn't bring back my settings for the above-listed apps. it now remembers my wifi connection, too.

on top of that is another problem which to me seems completely unrelated except for the fact that it started happening at the same time: i can no longer use the enter key to run a google search that i've entered in Firefox's google search box that appears next to the address bar. i can't even use the mouse to click on the button to the right of it (ie. i cannot use this search box at all now). i've also found that many forms on web pages no longer accept the enter key to submit them. some even don't let me click go/search/ok with the mouse, but some do. some fields are working fine as before. re-installing the "ubufox" application didn't help.

[5 mins later] i've tried rebooting several times, and on the most recent reboot the google search box has started working again. very odd... in fact all my firefox woes are now gone. perhaps i just needed to reboot after installing that package. i thought i'd leave it in my post though, in case people can see a relationhsip with the other problem.

all that i can think of doing recently that may have brought on these events was to install cGmail and to change my ubuntu desktop theme. i installed cGmail from Synaptic and then found that there was a newer version of it on the internet, so i downloaded the .deb file for the newer version and installed that. the new version didn't work, so i went into Synaptic and did "mark for complete removal" on cGmail to remove it altogether. perhaps this process broke something. when configuring cGmail i told it to add my gmail credentials to the gnome keyring (in case that's related- i guess the wifi thingy in the notification bay also uses that, so thought it might be related).

and like i said, i changed the ubuntu theme but for that i simply went into the Appearance settings, chose "clearlooks" and hit "Close". of course, that shouldn't break anything. i also went into "visual effects" and chose "normal" (it was on "none" before), but i can't be certain that this wasn't after i'd already begun seeing the above-mentioned problems.

i have a dell inspiron 1525 that came pre-installed with ubuntu.
i'm running ubuntu 9.04 (jaunty jackalope) and i've no outstanding updates (i keep up to date when it tells me there are updates).
i'm running gnome 2.26.1.

apologies for the long post, i wanted to make sure i included all the information i could think of. if i've left anything out that could be useful, just shout! :)

thanks in advance, guys.

---

