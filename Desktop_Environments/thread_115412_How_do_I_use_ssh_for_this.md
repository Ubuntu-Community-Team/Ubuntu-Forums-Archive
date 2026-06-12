---
title: "How do I use ssh for this?"
date: 2006-01-10
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-10
I use Ubuntu 5.10 because I love this distro. Face it, Ubuntu ROCKS! Lately I have been learning how to do things at the command line. In fact, the only gui apps I use anymore are Firefox and Evolution. Once yuo get to know how to do things in cli, everything just flies. So, here is the next thing I'd like to learn.

I like to experiment with different desktop environments and window managers. Someone mentioned that I could run irssi from tty1 and ssh into it from tty7 (the desktop). This would be awesome in that I can log in and out of various DE's/WM's without having to disconnect irssi. I have a feeling this would involve using screen.

I know how to use irssi and I tried it in tty1 but that disallows me from clicking on a link in irssi to open Firefox and I don't know how to utilise copy/paste in tty1.

Can anyone provide a link to a how to or tutorial about ssh'ing into tty1 from tty7 so that I can use an app that is running in tty1?

Let me know if I have not made this question clear enough, I am a bit confused about the whole thing myself.

---

### Post by nxn on 2006-01-10
You don't need to mess with tty1 at all, and you don't need anything from ssh to do this. Just start a new terminal in gnome, type 'screen -S <come up with some name that's easy to remember for you, like irssi>' a new screen will be started, then start irssi, connect to a server, whatever. You can now safely close the window and irssi will still be running, to bring it back you can write 'screen -r <name of screen you picked>' and it will bring it back. You can do this in a new terminal or you can switch to tty1 and recall it there, whatever. You can also switch DEs/WMs after a started screen as much as you want and irssi will not be killed along with X since it's in a screen.

Another thing you should know about is 'screen -d' which detaches the screen if you didn't close it first, this is usefull if you leave and want to ssh home to get your irssi session that was still up when you left. Simply ssh in, do 'screen -dr <name>' and it will detach, then recall the screen over ssh to you. Ssh is only needed when you want to connect to your computer from a remote location, there shouldn't be a reason to use it on the computer you're already in front of to begin with.

I don't know how to help you with your copy and paste thing in tty1, but since going into tty1 isn't necessary in what you want to do, I doubt this matters.

---

### Post by ardchoille on 2006-01-10
[QUOTE=nxn]You don't need to mess with tty1 at all, and you don't need anything from ssh to do this. Just start a new terminal in gnome, type 'screen -S <come up with some name that's easy to remember for you, like irssi>' a new screen will be started, then start irssi, connect to a server, whatever. You can now safely close the window and irssi will still be running, to bring it back you can write 'screen -r <name of screen you picked>' and it will bring it back. You can do this in a new terminal or you can switch to tty1 and recall it there, whatever. You can also switch DEs/WMs after a started screen as much as you want and irssi will not be killed along with X since it's in a screen.

Another thing you should know about is 'screen -d' which detaches the screen if you didn't close it first, this is usefull if you leave and want to ssh home to get your irssi session that was still up when you left. Simply ssh in, do 'screen -dr <name>' and it will detach, then recall the screen over ssh to you. Ssh is only needed when you want to connect to your computer from a remote location, there shouldn't be a reason to use it on the computer you're already in front of to begin with.

I don't know how to help you with your copy and paste thing in tty1, but since going into tty1 isn't necessary in what you want to do, I doubt this matters.[/QUOTE]
Wow! Thnk you for this awesome info. I'll be sure to give this a try when I get home. Thank you for posting :) This sounds exactly like what I need.

---

### Post by ardchoille on 2006-01-10
[QUOTE=nxn]You don't need to mess with tty1 at all, and you don't need anything from ssh to do this. Just start a new terminal in gnome, type 'screen -S <come up with some name that's easy to remember for you, like irssi>' a new screen will be started, then start irssi, connect to a server, whatever. You can now safely close the window and irssi will still be running, to bring it back you can write 'screen -r <name of screen you picked>' and it will bring it back. You can do this in a new terminal or you can switch to tty1 and recall it there, whatever. You can also switch DEs/WMs after a started screen as much as you want and irssi will not be killed along with X since it's in a screen.

Another thing you should know about is 'screen -d' which detaches the screen if you didn't close it first, this is usefull if you leave and want to ssh home to get your irssi session that was still up when you left. Simply ssh in, do 'screen -dr <name>' and it will detach, then recall the screen over ssh to you. Ssh is only needed when you want to connect to your computer from a remote location, there shouldn't be a reason to use it on the computer you're already in front of to begin with.

I don't know how to help you with your copy and paste thing in tty1, but since going into tty1 isn't necessary in what you want to do, I doubt this matters.[/QUOTE]
This works perfectly for what I needed. Thank you for posting :)

---

