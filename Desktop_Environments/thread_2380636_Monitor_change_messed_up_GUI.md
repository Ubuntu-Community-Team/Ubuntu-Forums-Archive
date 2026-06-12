---
title: "Monitor change messed up GUI"
date: 2017-12-20
forum: Desktop Environments
---

### Post by lnewlfe on 2017-12-20
Running Lubuntu 16 LTS, been stable for over a month now with no issues. Changed my screen from a stand, old 19 inch monitor to a 32 inch TV connected thru VGA, as thats only port my old computer allows. Computer boots up OK, i can read screen, see BIOS. GRUB also loads up ok. Login screen is good, with the correct resolution. Issue is after I now log in through the GUI, I get the black splash with mouse cursor, stays for about 5, 10 seconds, then i loose screen. I can CRT ALT F1 into terminal and sign in no problem. I reinstalled lightdm, Openbox, but same issue. If I sudo service lightdm start from terminal it does not do anything.

Anyone have any ideas on how to start tackling this problem? 

On the plus side at least its not a login loop. On the negative side, there's a lot more information published about login loops :(

EDIT:

xrandr also does not work, as  there's no screen to display, according to message.

---

### Post by Autodave on 2017-12-20
Your restriction to a VGA cable is likely the problem. If your TV is 1080 resolution, your VGA cable is not capable of running that resolution. Additionally, if you have a cheaper VGA cable, it cannot report the resolution of your monitor to the PC because the extra, needed wire is missing.

---

### Post by lnewlfe on 2017-12-20
Its not 1080 its only 720. Why would it work in the login screen though, with the correctly displayed resolution?

---

### Post by lnewlfe on 2017-12-20
Interesting note, switched back to monitor to test, still does not work. If i sign in with Guest it works. Switched back to the TV, killed lightdm from TTY1, which brought me back to login screen. Guest is correctly working, albeit a session error with a pid, but also correct resolution.

I then chown the .Xauthority file as per several posts, nothing.

Im thinking something got corrupted with the lubuntu desktop, or lightdm, but I reinstalled both, so at a loss. Any ideas?

---

### Post by lnewlfe on 2017-12-20
reading this is like watching someone spiraling down into maddess...only its my OS...

So I do not know what I did, but now I really did it, and I do not have ANY GUI. it boots up to TTY1. I resinstalled lightdm, lubuntu-desktop, but nothing changes, and I cannot start services. 

UPDATE: after apt-get removing lightdm, and reinstalling, along with lubuntu-desktop, I have a GUI again, but the background is black at login, not the standard lubuntu background, and when I sign in, it is the same issue as before, I loose video signal, black screen, but I can ctrl-alt-f1 to terminal.
[B]
*"failed to use bus name org.freedesktop.displaymanager - do you have appropriate permissions?"*[/B] is the error I am getting in the terminal.

I am at a loss, and any help will be appreciated...as I fear I will soon be making things worse.......

---

