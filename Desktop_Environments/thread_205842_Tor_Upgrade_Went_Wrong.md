---
title: "Tor Upgrade Went Wrong"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Luke771 on 2006-06-29
While looking for something else I accidentally hit [_this thread_]("http://ubuntuforums.org/showthread.php?t=202909"), so I followed the link to the [_Tor-on-Debian Wiki_ ]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")page and then followed the instructions and everything went fine.

That's what I though, anyway.

When trying out the new Tor version I got some problems:

First I got a 404 so I guessed Tor was not running.

Comes out it wouldn't run using the standard line ```
/etc/init.d/tor start
``` but it would run simply typing ```
sudo tor
```
Also it wasn't being loaded at startup as it is supposed to be.
I used Boot Up Manager to disable Tor loading at startup, then I clicked Start/System/Preferences/Sessions/Startup and added the line```
/etc/init.d/tor start
``` 

I restarted to check if Tor was being auto-loaded but it was not.
Trying to launch it manually, I got nothing less than the output```
 there is no /var/run/tor directory
```

I could run Tor anyway, all I had to do was:

1 - Changing the owner of **/var/lib/tor** to root (was Debian-tor). I did that by right-clicking the folder and doing Properties/permissions.

2 - Making a symbolic link to **/var/lib/tor** in the **/var/run** directory ```
ln -s /var/lib/tor /var/run
```( I didn't use Sudo because I was running Terminal as root)

3 - Creating an empty file called **tor.pid** and saving it in **/var/run/tor** 

4 - In a root terminal window, run ```
tor
``` (or "sudo tor" in a regular terminal window)

It did work but it wasn't auto loading at startup, enabling or disabling the Tor entry in Boot Up Manager made no difference, clicking **Start/System/preferences/Sessions/Startup ** and adding the entry ```
gksudo tor
``` didn't work either.
I only could manually launch it and I could only do that as root and using the command "tor" instead of the proper line "etc/init.d/tor start" as regular user. Using that line resulted in the output ```
can't access /var/lib/tor. Are you root?[code]

Running the same line as root ... sorry I don't remember the exact output. I can only say that there was some problem with that too (can't recreate it because I downgraded again)

It was working in some way but the setup was not proper and it wasn't being auto-launched at startup.

As if that wasn't bad enough, I could only run it as root which should not be needed.

So what I did in the end was removing Tor using Synaptic's "Complete Uninstall" feature; removing the Tor repositories 
[code]deb     http://mirror.noreply.org/pub/tor dapper main
deb-src http://mirror.noreply.org/pub/tor dapper main 
```
from the repositories by selecting them one at the time and hitting the "Remove" button; updating (hit "reload") and eventually searching for Tor and installing it again, in the old version.

It's working fine now, but it's not the latest version.

Anybody knows what could have gone wrong?

Are there other ways to get the latest Tor version?

System is AMD Duron 1600MhZ/512RAM

OS: dual boot WinXP Pro on hda1, Dapper on hda2, loaded by Grub in MBR

---

