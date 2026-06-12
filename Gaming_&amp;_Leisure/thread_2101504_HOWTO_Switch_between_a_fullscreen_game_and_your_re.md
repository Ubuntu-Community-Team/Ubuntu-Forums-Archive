---
title: "HOWTO: Switch between a fullscreen game and your regular desktop"
date: 2013-01-04
forum: Gaming &amp; Leisure
---

### Post by Emblem Parade on 2013-01-04
Yay, gaming on Ubuntu!

Unfortunately, you know the problem: when a game is fullscreen, ALT+TAB often does not work, or otherwise makes your system go a bit ... crazy. In such cases, the only way to safely switch out of your game is to quit it. Annoying!

Well, a terrific solution, which I will guide you to here, is to run the game on a *separate desktop* (an X server). As a side effect, the gaming desktop will run without Compiz, so you *might* get a bit better graphics performance on it. Win, win, win!

[SIZE="3"]**GAME LAUNCHER!**[/SIZE]

Because I'm awesome, I wrote a very small and handy application that does all this for you. It's called ... Game Launcher!

Game Launcher shows you all the applications you have installed, and lets you launch them in the separate gaming desktop. It also lets you mark games to always launch in the gaming desktop, even if you don't launch them from Game Launcher. It even lets you bookmark a few favorite games, so you don't have to scroll through the long list...

To install Game Launcher, open a terminal:
```

sudo add-apt-repository ppa:emblem-parade/gamelauncher
sudo apt-get update
sudo apt-get install gamelauncher

```
You can now launch it from your dash. Game Launcher! Win, win, win!

The full source code is available [here]("http://code.google.com/p/gamelauncher/source/checkout"). Please report bugs [here]("http://code.google.com/p/gamelauncher/issues/list").

If you don't want to use Game Launcher, or would rather learn how it works, follow the steps below. They do exactly what Game Launher does manually. I've tried to make this guide as easy as possible for novices, and it should only take you a few minutes to go through. All steps are reversible and none will compromise your system.

[SIZE="3"]**INITIAL SETUP**[/SIZE]

We will first need to enable two specific permissions.

First, let's give your user permission to use audio even on another desktop. Open a terminal:
```

sudo usermod -a -G audio username

```
...where "username" is your Ubuntu username. You need to logout/login for this to take effect, so do it now.

Second, let's give you (and all users) persmission to start another desktop. Open a terminal again:
```

gksudo gedit /etc/X11/Xwrapper.config 

```
In this text file, you'll see this row:
```

allowed_users=console

```
Replace it with this:
```

allowed_users=anybody

```
Save the file and exit gedit. (No need to logout, the change took place immediately this time.)

OK, you now have permissions to run a new desktop with full sound.

[SIZE="3"]**LAUNCHING THE GAME**[/SIZE]

Now, find the command you usually need to run your game.

Often the command is just the name of the game, but sometimes it's a bit different or has a directory prefix. To find it, you can look in the game's launcher. The launchers are in your "/usr/share/applications/" directory. Browse this directory with the file browser, right click on the game's launcher, and choose "Properties." You will see a "Command" entry. That's it! For example, I'm playing Super Meat Boy, and the command is:
```

/opt/supermeatboy/SuperMeatBoy

```

To run the game in its own desktop, in your terminal wrap the above command with "/usr/bin/xinit" in front and "-- :1" after it. For my example, it would be so:
```

/usr/bin/xinit /opt/supermeatboy/SuperMeatBoy -- :1

```
(Yes, those are *two* dashes.)

[SIZE="3"]**PLAYING THE GAME**[/SIZE]

To switch to your regular desktop: **CTRL+ALT+F7**

To switch to your gaming desktop: **CTRL+ALT+F8**

Easy, clean and neat. Better in some ways than ALT+TAB. It would be nice if there was a way in Ubuntu to configure this for all applications, no?

Notes:

1) The game does not automatically pause when you switch to the regular desktop. Likewise, applications on the regular desktop will continue to run.

2) You will *not* get desktop notifications (for instant messages, emails, etc.) on the gaming desktop. But, you *will* hear sounds from all runnning applications. So, if you want to make sure that you are notified of events while playing, make sure to configure obvious sounds that won't be easily confused with noises happening in the game. (Did I just kill a zombie, or is that an email from my mom?)

3) You're only able to run one game at the same time with this method. But that's OK, you should finish your dinner before you get dessert. :)

4) Do *not* use "sudo" to start the game! If you do, xinit will set root permissions on the ".Xauthority" file in your user's home directory, making it impossible for you to start your *regular* desktop in the future (you won't be able to log in to Ubuntu). If this somehow happens to you by mistake, just delete the ".Xauthority" file, and it will be regenerated using standard permissions next time you login.

5) Instead of **CTRL+ALT+#** you can use "sudo chvt #".

[SIZE="3"]**MAKE IT PERMANENT**[/SIZE]

If all works well, you can also change the launcher for the game so it will always launch in a separate desktop. You need administrative permissions for this, so in a terminal let's open a privileged file browser:
```

gksudo nautilus

```

**WARNING: IT'S REALLY EASY TO CAUSE SERIOUS DAMAGE WITH A PRIVILEGED FILE BROWSER. USING IT, YOU CAN DELETE/MOVE IMPORTANT SYSTEM FILES AND BREAK YOUR OPERATING SYSTEM. MAKE SURE TO CLOSE IT AS SOON AS YOU ARE DONE WITH THIS GUIDE.**

Again, find the launcher for your game, right click it, and choose "Properties." You can now change the "Command" entry to be the wrapped command above. (Changing it is only possible because we are using a privileged file browser.)

Close the properties and **make sure to close the file browser**.

You might need to logout/login for the Unity Dash/Launcher to properly pick up your changes. From now on your game will always launch in the gaming desktop.

Note: even though you can *launch* the game from the Unity Launcher, you will *not* be able to switch to the game using the Unity Launcher, nor will the Launcher show the game icon as lit when the game is running. You can only switch to the game using **CTRL+ALT+F8**.

Enjoy!

Tested on Ubuntu 12.10 AMD64.

---

### Post by pardalet on 2013-01-05
Thank you! Will be using this method from now on. :p


One correction, though:

> **Emblem Parade said:**
> First, let's give your user permission to use audio even on another desktop. Open a terminal:
```

sudo useradd -G audio username

```
...where "username" is your Ubuntu username. You need to logout/login for this to take effect, so do it now.


The **useradd** command creates a new user and adds it to the group. If you run the command you posted you'll get an error. Command **usermod** must be used instead:

```
sudo usermod -G audio username
```

---

### Post by Emblem Parade on 2013-01-05
Oops, thanks!

---

### Post by pardalet on 2013-01-05
BEWARE!!!

The command I suggested is wrong! if you execute it as I posted, your user will get removed from the administration group!

Instead you should execute it with the -a option:

```
sudo usermod -a -G audio username
```


Sorry for any trouble I might've caused... :(

---

### Post by pardalet on 2013-01-05
Alternatively one can also use this other command, which does the same:

```
sudo gpasswd -a username audio
```




PS: I've been a victim of my first tip and I lost my administration privileges. Here's a quick guide for anyone that might have been (unintentionally :oops:) tricked by me:

1-Reboot your system

2-At the GRUB screen, press **E**

3-Edit the line that loads the kernel and specifies its parameters (the one that begins with **linux**) and append **single** at the end

4-Press F10 to boot and you'll end at a root console

5-Give yourself back the permissions you lost:

```
gpasswd -a username adm
gpasswd -a username sudo
gpasswd -a username lpadmin
gpasswd -a username sambashare
```

6-Reboot and everything should be back to normal :p

---

### Post by Emblem Parade on 2013-01-05
Fixed again! Thanks for the extra info.

---

### Post by Transhumanist on 2013-01-07
Nice!

Seems like it should be stickied.

---

### Post by Emblem Parade on 2013-01-07
I agree! :) I've considered writing a nice GUI utility to do this for you. If there's a lot of interest, I'll give it a whirl.

---

### Post by Emblem Parade on 2013-01-08
Because I'm awesome, I went ahead and wrote the app. Game Launcher! I update the main thread post with installation instructions.

---

### Post by cristo-father on 2013-02-21
Love the idea !
Unfortunately it doesn't work on ubuntu 12.04 LTS 64bit :(
I press on the "enable gaming desktop" and insert admin pass and nothing happens, tried maybe 8 times. 
Also pressed add,tried to check the boxes besides the app names and slide down the list of all available apps, but none of these 3 worked.

Edit:
Have a few questions, does the audio from the main desktop xserver carry to the game xserver ? I think an option of that nature is useful, since sometimes i can be playing on a pub and don't mind others highlighting me on xchat, while other times i can be playing a duel and want to focus entirely on the game.

---

### Post by Emblem Parade on 2013-02-21
Have you tried rebooting? You need to reboot for some of the permissions to come through... I should probably add a dialog box explaining that. :/

Also, have you tried the manual method described here? I would very much appreciate help debugging the app!

Yes, audio works on all desktops, and is all mixed together. Indeed useful for getting chat notifications!

---

### Post by pieman711 on 2013-02-22
I've just installed your gameLauncher program. It works really well (if you log out and in as mentioned in the previous post) however my Steam library games don't appear in the list. Is there anyway to have them work with the program?

---

### Post by cristo-father on 2013-02-23
Why are you so awesome ? This app is brilliant and has awesome potential ! I would be very happy to be a lab rat and help debug :p

It works. Seems like a reboot did the charm.

Anyway have a few suggestions and a bug report:

Bug:

Sound passes through perfectly from main desktop to game desktop, but not the other way around, it either doesn't pass on some games, or it does pass, but has that 1 second loophole sound that a pc has when it crashes.

In the first case(sound doesn't pass), the soundtrack from the game, continues(but i cannot hear it) when i go to the main desktop, when i come back to the game desktop, the soundtrack location corresponds the time passed on the main desktop.

In the second case(loophole sound), it pauses the soundtrack and when i come back it continues as it left off.

Haven't tested any in-game-server yet, will post updates in the near future.

Edit: Tested Warsow in-game-server and the sound didn't pass from Game desktop to main desktop

Suggestions:

Also insert restart needed message, after adding games to be launched this way, since i had to reboot to launch them in the other xserver(confirmed with a few games).

Support qlprism( [http://www.qlprism.us/](http://www.qlprism.us/) ), desura games, steam games, unified zips(or launch scripts, custom launchers etc) and wine games.

4 sound options, with the option to have them globally configured(for all games, or different option for each game):
A: Game and main desktop sounds are always audible on both desktops.
B: Game and main desktop sounds are only audible on their own desktops.
C: Game sounds are audible on main desktop, but not vice-versa.
D: Main desktop sounds are audible in Game, but not vice-versa.

If i insert my admin pass, maybe i should be allowed to use admin privileges  for all future actions, instead of inserting my admin pass 7 times, if i want to add 7 games to be launcher this way.

Is there any way to subscribe to a feed of sorts, or newsletter to be notified of future updates  ? and if u need any help from some random dude, i am more then happy to help !

---

### Post by Emblem Parade on 2013-03-26
Oh, oops! Somehow I didn't get notifications about your posts, guys. Thank you very much for your interest, and I will try to look at all the bugs you mention.

Also check out [FSGamer]("http://www.techdrivein.com/2013/03/fsgamer-fullscreen-linux-gaming-simplfied-opensource-tool.html") that seems to do the same, and might work better for you.

If there is an update, I will post about it on this thread for now. And also push to the PPA.

---

### Post by Emblem Parade on 2013-03-26
Hey, I noticed that none of you used the [link]("http://code.google.com/p/gamelauncher/issues/list") mentioned in the first post for opening bugs. It would really be easier for me to track things there, thanks!

---

