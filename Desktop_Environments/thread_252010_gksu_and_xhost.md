---
title: "gksu and xhost"
date: 2006-09-06
forum: Desktop Environments
---

### Post by haz2a on 2006-09-06
In Breezy I used to run several apps as another user on the same machine via 'gksu -u <other-username> <cmd>'
(after giving the other user's password to gnome-keyring when prompted). Now I've upgraded to Dapper this fails. No prompt for password, just the errors:-

    Xlib: connection to ":0.0" refused by server
    Xlib: No protocol specified

    unable to display ":0.0"

It works if I just do 'gksu <cmd>' to run the cmd as root, but not with '-u <username>' to run the cmd as a different user.

If I do: 'xhost +local:' first (as my main user and sudoer), then I can use 'gksu -u' without any problems. But I need to accomplish this from launchers without having to enter the xhost command first.

I've tried creating /etc/X0.hosts (with a zero) and adding the line: 'local:', then restarting X. This seems to do part of the job. If I then do 'xhost' it shows 'LOCAL:' as needed,
BUT if I do 'gksu -u <otheruser> <cmd>',
or 'sudo -u <otheruser> xhost', I just get the Xlib errors.
I've also tried lots of other possibilities in X0.hosts eg: 'localhost', '<username>', '+local:', etc, etc.

In a terminal I can do:-
'xhost +local:; gksu -u <otheruser> nautilus' on one line, but this won't work from the launcher - it doesn't seem to like the special characters ';' or '&&'.

The only way I can find to do 'xhost +local:' automatically is to put the xhost cmd and the gksu-app cmd into a separate script eg:
```
xhost +local:
gksu -u <otheruser> nautilus
```
then to call the scripts from the launchers.

Since I have several apps to be launched on several different machines, this seems overly complicated and laborious. I don't really want to allow other users to connect from the network via TCP, just other users on the same machine.

Surely there must be a more elegant way to do this!? - eg: via /etc/X0.hosts or similar?

---

### Post by Xtreme it on 2006-10-18
I think this problem is related (if not the same) with the post [pptpconfig errors in Ubuntu]("http://www.ubuntuforums.org/showthread.php?t=31554") where I also posted, but got no answer yet.

If you get to find an answer for this problem please let the community know, posting an HowTo here.

I'll do the same.

---

