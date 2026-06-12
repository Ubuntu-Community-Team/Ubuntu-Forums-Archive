---
title: "FreeNX Gnome-classic session shows no file icons and top bar is black"
date: 2014-02-28
forum: Desktop Environments
---

### Post by antony3 on 2014-02-28
I have a remote server running 12.04 and connect to it with FreeNX (running on the Server) and the NoMachine Client.
Everything seems to working apart from one thing: most icons are missing. The left part of the top bar is black, the Application and Files tab are black, but show up when I click on it, all bars are a simple grey and generally there seems to be a graphical glitch of some sorts...
The only thing I have tried to play with is the /etc/nxserver/node.conf where I have this line
COMMAND_START_GNOME="/usr/bin/gnome-session --session=gnome-classic"
(gnome-fallback does the same and so does removing the /usr/bin/ bit)


Here is an image of what I get: 
[http://imgur.com/cUbhzQp](http://imgur.com/cUbhzQp)




Any ideas?
PS: unity-2d doesn't work either, it returns an error saying unity-2d session not found.

---

### Post by ibjsb4 on 2014-02-28
Can you reset the panel?

```
killall gnome-panel

```
What about Alt + Right-click on a blank spot on the panel and go to Properties and change background color.

In my /usr/bin I would have two choices:

COMMAND_START_GNOME=gnome-session-fallback

or

COMMAND_START_GNOME=gnome-session

---

### Post by antony3 on 2014-02-28
killall gnome-panel refreshes the screen, but that's all. The problem persists.

Changing the background color helped a bit, but the issue is that file, folder and more icons are missing as well...
(Although why the default system theme background was pitch black, still bothers me)

Apart from that, I have both of the tried out and both as a session=gnome-classic and session-gnome-fallback and end up with the same result.

Thanks for the first tip though, I can't believe I didn't think of it by myself... :P

---

