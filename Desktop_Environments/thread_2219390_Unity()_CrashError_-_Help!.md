---
title: "Unity(?) Crash/Error - Help!"
date: 2014-04-23
forum: Desktop Environments
---

### Post by misterpockets on 2014-04-23
I recently upgraded to Ubuntu 14.04 from 13.10. Everything was working fine until today. I left my computer for lunch, and when I can back, there was an error stating that Ubuntu had encountered an error. No big deal, I've had that pop-up before with no problems. I clicked "Continue" (or whatever the button is) but noticed just before it closed that this error was located in "Natilus" (I'm not sure what the complete location was). I then began to have issues with my comp being really laggy. So I restarted. When it booted back up, everything worked fine, but many windows/programs had a distinctly different look to them, almost XP-esque. Most text was also now set to a different font (I'm guessing Times New Roman, but I'm bad at recognizing fonts). I tried rebooting again; most windows/programs had returned to normal, but the fonts were still different.

 I decided to try resetting Unity with "unity -reset". This was apparently the wrong command, and the terminal told me as much. I then entered "unity -option" (or perhaps "unity option". I'm not certain.) trying to get the options list. This apparently did something nasty as my sidebar, topbar, window edges, and all other non-window UI features disappeared. I still had the terminal, so I rebooted. When I logged back in, I was presented with the background image and the one program I have set to auto-start. Nothing more. Ctrl+Alt+T fails to bring up a terminal.

Do any of you have any ideas what I did or how to undo it?

---

### Post by misterpockets on 2014-04-23
I booted into recovery via GRUB and then selected filesystem check. It sat there for a few minutes before I got tired of waiting (it didn't appear to actually be doing anything; no HDD activity, no new text displaying). I then booted into Windows to post the original question. When I rebooted into Ubuntu, I decided to try the Guest login. Everything was normal (also, apparently you are forbidden from using sudo in the Guest account). I then logged into my account. Everything here is normal as well. I have no idea what fixed it.

---

