---
title: "Fix- Configuration details gnome power manager not installed correctly error"
date: 2012-02-18
forum: Desktop Environments
---

### Post by threepot on 2012-02-18
Hi, I am not after support as I dug through every fix I could find on here to sort out my computer ubuntu 10.10 machine.

It would boot to a blank gnome window, with the error message in the top right hand corner:-

"Configuration defaults for gnome power manager has not been installed correctly"

I tried all these possible fixes without success:-

Firstly check if your out of disk space with

df -h

Make sure no drives are at 100% if they are maybe try a bit of:-

sudo apt-get autoclean
sudo apt-get clean

or delete some stuff from somewhere.

Then I searched everywhere for any possible solution:-

sudo dpkg --configure -a

sudo apt-get remove powermgmt-base
sudo apt-get install powermgmt-base

sudo apt-get purge gnome-power-manager
sudo apt-get install gnome-power-manager

sudo apt-get --reinstall install ubuntu-desktop

sudo gconftool-2 --recursive-unset /apps/gnome-power-manager

Apparently access rights to the temp folder can cause this issue (not for me though):-

sudo chmod a+rwxt /tmp

sudo chmod 0777 /tmp

Or the Gnome config folder is screwed up??! :-

sudo mkdir /var/lib/gconf/default

Or your nvidia driver is causing the problem:-

sudo apt-get remove nvidia-current





But after non of this worked and I was thinking nothing would solve my problem I found this solution on a site somewhere:-

sudo mv .gconfd/saved_state saved_state.old

This fixed my machine!!

Why and how, I don't know, but it did.

As you can tell I'm really no ubuntu expert, but I'm learning. I thought I would post up my last 3 hours of head bashing to maybe help someone else. I was really getting close to reinstalling everything. Good luck!

---

### Post by threepot on 2012-02-19
Thought I'd expand on this a little more for those with no idea what they are doing!

Above is a list of commands you need to try, but I guess your saying where do I put them in...

So you've booted to the screen with the error message:-

"Configuration details for gnome power manager has not been installed correctly"

And if you sit there for long enough my cursor does appear but just as a cross.

When you get the error message and the machine does nothing you need to hold down the Ctrl and Alt keys and press F1. 
This will open you up a new session window. (or F2 or F3, these are just different sessions, if you press Ctrl Alt F7 this takes you back to the gnome session)

Now you need to enter your username,
Then your password, don't worry the letters don't come up on the screen, nor do you get any stars **** like you do on other things.

Then you'll get a prompt like:-

you@your-computer:~$

This is where you enter the above commands, more often than not the error is caused by a full disk, but not always, thus why I have listed out all the various fixes for you to try.

Hope it helps someone. In return, please share the ubuntu love to all your friends and colleges!

---

