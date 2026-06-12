---
title: "Problem with xserver/graphics driver?"
date: 2009-04-13
forum: General Help
---

### Post by hubbabubba on 2009-04-13
I don't often boot into ubuntu having a dualboot with vista.
But as my scanner doesn't work in vista and I know it works in ubuntu, I was going into ubuntu to do some scanning...
But after the boot screen, where everything seemed absolutely fine the screen went black and I even though I let it be for 20 minutes it didn't get to the login screen.
I ran a couple of reboots to check if it was just a temporary problem, but no the same thing happened every time.
After a while I started thinking about what I could have done to make this happen.
Then I realised that I had been tinkering around alot with the drivers for my ATi 4870 graphics card and that maybe my try for a manual installation of catalyst 9.2 may have destroyed my xserver.
So I decided to run recovery at boot instead and there I chose to run the repair xserver thingy without any previous knowledge about this command other than that it could fix your xserver.
I then rebooted and everything looked just fine at the boot screen as usual, and then for the moment of truth: I saw something scrambled at the top of the screen to begin with and I started to think someting went wrong.
When the screen that should be the login screen appeared everything was totally scrambled and it was like when you choose a channel on your tv where there is no channel.
I then started to google for things that could repair your xserver as I feared that I had destroyed it completely.
After a while I came across a command that looked like it might help me which looks like this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I tried this in the shell command prompt as this was the only way for me to get to an commmand line, when I tried the ctrl+alt+F2 command after boot screen, when everything was scrambled nothing happened..
So I tried the command as root in the shell prompt and rebooted but no change.
I then tried the command without the -phigh part but that didn't work either...
So is my problem xserver related or is it something else and how do I fix this?
The reason for me tinkering around with the catalyst driver for my ati card was that I wanted to have compiz without flickering so I am also wondering if it is possible to get this with my ati card at the time?
I realise my knowledge on ubuntu and linux in general is limited but I wasn't sure if I should post this in the beginner section, so I posted it in general help, please move this thread if I was wrong in doing so...

EDIT: I reinstalled ubuntu, I couldn't be bothered with trying to fix it as I had numerous problems with my install and no important files on it...

---

