---
title: "I think Gnome just broke on my install"
date: 2015-02-27
forum: Desktop Environments
---

### Post by Neko_no_Nya on 2015-02-27
Or rather I broke Gnome :cry:. I am running a dual boot Windows 7 Pro x64 and Ubuntu Gnome 14.04 x64 setup using UEFI mode and currently can not log in using Gnome anymore. This is a fairly fresh install, just a few days old. Everything has been running smoothly until now. I am using the proprietary Nvidia drivers for a G210 if that matters.

I was using my comp with no problems and left the room for a bit. When I came back my screen had locked due to inactivity. I went to unlock the machine but under where I enter my password it just kept flashing access denied or something along those lines. I couldn't type my password because as soon as I input the first character, it was like it would automatically press enter for me and I would get the access denied message. I tried unplugging the wireless mouse and keyboard receiver but that didn't help. I have had this happen a few times in the past and always just reboot the machine without any problems.

I was just going to manually power off the PC since I wasn't working on anything that wasn't saved but then I had an idea. I thought maybe I could  CTRL-ALT-F1, login that way, and then start x manually. I have done this before when I just got a blank screen when booting on a previous install. This must have been a bad idea though because I got a whole bunch of lines of text and then at the bottom it said:

> xinit: connection to X server lost

waiting for X server to shut down (EE) Server terminated successfully.

I was trying to start X not shut it down. So I ran the reboot command thinking I would just log in normal now. Instead what happens is I get the Ubuntu splash screen but then am taken to just a plain purple GUI login screen. When I click next to my username to select my desktop environment, the only option I have is for Kodi (the media player, formerly XBMC). Actually, I have two entries that say Kodi but both seem to do the same thing. When I login Kodi launches on one of two monitors and the other screen is just all discombobulated. If I quit Kodi I am just taken back to the login screen.

I tried reinstalling Gnome using:
```
sudo [FONT=Ubuntu Mono]apt-get remove gnome && apt-get install gnome[/FONT]
```

That just gives me a bunch of text with this at the end:
> could not open the lock file /var/lib/dpkg/lock - open (13: permission denied)
unable to lock the administration directory (/var/lib/dpkg/), are you root

One more thing, which I'm not sure if it is relevant but I installed MakeMKV during my last session and it asked me if I was using GDM or lightGDM. I thought I was using GDM so that is what I selected. I don't know if that could be relevant.

Any help would be greatly appreciated. I'm not very proficient with the command line so I'm not really sure what I should be doing here.

---

### Post by deadflowr on 2015-02-27
I'm not really sure what happened to your system, but for future reference, the double & (&&) means that the second command is entirely its own, so you would need to add sudo to it. Sudo is a per command function.
If that helps.

(Though I doubt it will be, beyond just that)

---

### Post by Neko_no_Nya on 2015-02-28
Deadflowr, thank you so much!!! That piece of information was invaluable to solving this problem!

With this new information in hand, I went back to try again. At the login screen I used CTRL+ALT+F1 to bring up the terminal and this time, by itself, I entered:

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]apt-get remove gnome[/FONT][/COLOR]
```

This told me that the Gnome package wasn't installed (can't remember exact wording).

So then I just entered:
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get install gnome[/FONT][/COLOR]
```

This told me that it would take up like 600+MB of space to install. So somehow Gnome was deleted off my machine, apparently. The package files for installation and all the dependencies must have been on my machine though because I didn't have to download anything. During the install it asked me if I wanted to use gdm or lightdm. I choose gdm. After install I rebooted via the terminal.

After restarting I was right back at my normal login display and able to select Gnome again! For some reason the first boot up I saw a message on that grey splash screen that some drive was not ready or something along those lines. It went by too fast for me to read. However, upon subsequent restarts, that message has not displayed again and everything seems to be back to normal.

So it turns out your FYI for future reference turned out to be the key to fixing this ;)

Again, thanks so much!

EDIT: I thought I would just make a quick update that it wasn't just Gnome that was randomly affected. I went to launch Steam after this all happened and Steam was no longer installed. I had the Steam folder with my game saves and such but the application was gone. Re-installing just resulted in the installation failing once I tried to open the Steam client to finish installing. I had to completely delete the Steam folder before I could re-install. Very weird. I don't know why both Gnome and Steam disappeared like this.

---

