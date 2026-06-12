---
title: "How to combine commands in the terminal?"
date: 2009-03-18
forum: General Help
---

### Post by Pipps on 2009-03-18
I would like to combine a number of install and uninstall commands in the terminal. For instance, "sudo apt-get install vlc", and in the same single terminal command, also entering "sudo apt-get remove mplayer", and many more, all as one single long command made up of lots of these separate sections.

I would like to compile my long command in Gedit and then paste it into the terminal after a fresh system boot, hit enter and then just watch everything arrive and depart as desired.

How should I go about writing a command, and separating the separate commands within the command, in order to do this?

---

### Post by whitegourd on 2009-03-18
you can alias it in your .bashrc file ...

(ex.)
alias update='sudo apt-get update -qy; sudo apt-get upgrade -qy; sudo apt-get autoremove'

you could also use '&&' in between the commands.

---

### Post by Pipps on 2009-03-18
So to confirm, typing in the terminal: 

```
sudo apt-get install vlc && sudo apt-get remove mplayer
```

would install VLC and remove Mplayer. both at the same time?

---

### Post by Dr Small on 2009-03-18
> **Pipps said:**
> So to confirm, typing in the terminal: 

```
sudo apt-get install vlc && sudo apt-get remove mplayer
```

would install VLC and remove Mplayer. both at the same time?
Since dpkg locks the program from initating multiple times, thus corrupting the package database, both programs will not run simultaneously. Of course, using '**&&**' is like saying '**run next command after the previous one exited with a status of zero**'. If the previous command failed to complete with an exit status of zero (meaning, the previous command failed), then the next command will not start.

If you want to run one command and then another, whether or not the previous command completed successfully, then use '**;**' to join the commands.

---

### Post by D3ath on 2009-03-18
you could just write a script like this:
```

#!/bin/sh
#32 bit machine only Ubuntu 8.10
script_name="thescript.sh"

# Script must run as root
if [ $USER != "root" ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi

# Update the package manager
sudo apt-get update


# Add Medibuntu to your software sources
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

# Add the Medibuntu gpg key
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

# Update the software list
sudo apt-get update

# Install Ubuntu Restricted Extras
sudo apt-get -y install ubuntu-restricted-extras

# Install alien
sudo apt-get -y install alien

```

just add whatever you want and save it as file.sh.  The code in the beginning is to make sure your running as root.

You can also put:
```
sudo apt-get -y remove alien
```
Just do a
```
sudo apt-get update
```
At the end of the file to make sure everything is updating.

Then all you would have to do is run this.
```
sudo ./file.sh
```

---

### Post by Pipps on 2009-03-18
> **Dr Small said:**
> ... use '**;**' to join the commands.
Brilliant! Thank you, Sir!

---

### Post by Pipps on 2009-03-18
> **D3ath said:**
> you could just write a script like this:...
Whoa... that looks beautiful, yet rather technical, too! Thank you!

---

### Post by D3ath on 2009-03-18
> **Pipps said:**
> Whoa... that looks beautiful, yet rather technical, too! Thank you!

I wrote one of those for new installs on Ubuntu 8.10 for friends or someone new trying ubuntu. I can take my drive over to their house install the system and run the script and they all have the same things installed. Least for those type of users what they might like.  I also have a very long one that installs everything that i need and want then removes all the stuff i don't like to use at all.  Its very handy!

---

### Post by bodhi.zazen on 2009-03-18
Take two commands, command_1 and command_2

# Executes command 1 then command 2 (not at the same time)
command_1; command_2

# Execute command 1 and 2 at the same time (in the background):
command_1 &
command_2 &

# Executes command 2 only if command 1 is completed without errors.
# If command 1 generates an error , command 2 will not run
command_1 && command_2

# Executes command 1 or command 2. 
# Command 2 runs only if command 1 fails.
command_1 || command_2

---

### Post by Pipps on 2009-03-19
> **D3ath said:**
> ...I also have a very long one that installs everything that i need and want then removes all the stuff i don't like to use at all.  Its very handy!
It is exactly the same reason that I am hoping to write something similar!  Thanks! :)

---

### Post by Pipps on 2009-03-19
> **bodhi.zazen said:**
> Take two commands, command_1 and command_2...
This is all brilliant advice. Thank you! :)

---

### Post by D3ath on 2009-03-19
> **Pipps said:**
> It is exactly the same reason that I am hoping to write something similar!  Thanks! :)
Good Luck!

---

### Post by Pipps on 2009-03-19
Thank you!

And one more question if I may, which I have just encountered:

When I use the following command in the terminal:

```
apt-get install k3b ; apt-get install vlc
```

I am asked, before each packaged is installed, whether I wish to continue on the basis of the expected disc usage after fulfillment of the operation. I of course hit 'y' and 'enter'. However, is there a way of using some sort of 'pre-command', so that the terminal does not ask me these questions?

---

### Post by D3ath on 2009-03-19
> **Pipps said:**
> Thank you!

And one more question if I may, which I have just encountered:

When I use the following command in the terminal:

```
apt-get install k3b ; apt-get install vlc
```

I am asked, before each packaged is installed, whether I wish to continue on the basis of the expected disc usage after fulfillment of the operation. I of course hit 'y' and 'enter'. However, is there a way of using some sort of 'pre-command', so that the terminal does not ask me these questions?

```
sudo apt-get -y install wine
```

the -y will answer yes to all.

---

### Post by Dr Small on 2009-03-19
> **Pipps said:**
> Thank you!

And one more question if I may, which I have just encountered:

When I use the following command in the terminal:

```
apt-get install k3b ; apt-get install vlc
```

I am asked, before each packaged is installed, whether I wish to continue on the basis of the expected disc usage after fulfillment of the operation. I of course hit 'y' and 'enter'. However, is there a way of using some sort of 'pre-command', so that the terminal does not ask me these questions?
Try:
```
apt-get -y install k3b ; apt-get -y install vlc
```

---

### Post by mcduck on 2009-03-19
> **Pipps said:**
> Thank you!

And one more question if I may, which I have just encountered:

When I use the following command in the terminal:

```
apt-get install k3b ; apt-get install vlc
```

I am asked, before each packaged is installed, whether I wish to continue on the basis of the expected disc usage after fulfillment of the operation. I of course hit 'y' and 'enter'. However, is there a way of using some sort of 'pre-command', so that the terminal does not ask me these questions?

You shoul also know that you can install/uninstall many packages at the same time with apt-get:
```

sudo apt-get install k3b vlc
```

---

### Post by Pipps on 2009-03-19
> **D3ath said:**
> ...the -y will answer yes to all.
Perfect. Thank you! :)

---

### Post by Pipps on 2009-03-19
> **mcduck said:**
> You shoul also know that you can install/uninstall many packages at the same time with apt-get:
```

sudo apt-get install k3b vlc
```
Oh you beauty! That will make my mega-command even more efficient!

---

### Post by Pipps on 2009-03-19
Would the following command be correct?

```
sudo apt-get -y remove tomboy rhythmbox mplayer totem pidgin thunderbird giver xchat brasero firefox
```

---

### Post by D3ath on 2009-03-19
> **Pipps said:**
> Would the following command be correct?

```
sudo apt-get -y remove tomboy rhythmbox mplayer totem pidgin thunderbird giver xchat brasero firefox
```

Yea but why don't you like pidgin or thunderbird great apps there. Also rhythmbox? but yea that seems about right there...

---

### Post by Pipps on 2009-03-19
You're right, but I don't ever get the chance to use either of them, and as I am obsessive about keeping my system components at a minimum, they had to go! 

PS: I use Swiftfox instead of Firefox! :)

---

### Post by D3ath on 2009-03-19
> **Pipps said:**
> You're right, but I don't ever get the chance to use either of them, and as I am obsessive about keeping my system components at a minimum, they had to go! 

PS: I use Swiftfox instead of Firefox! :)

What system specs do you have to keep your system resources that low?

If you really wanna keep things low. Why not use pork. Its a terminal base messenging client! Or links2 for browsing the web via terminal.

```
sudo apt-get -y install pork links2
```

---

### Post by mcduck on 2009-03-19
> **Pipps said:**
> Would the following command be correct?

```
sudo apt-get -y remove tomboy rhythmbox mplayer totem pidgin thunderbird giver xchat brasero firefox
```

Yes, it should work. Although I'd advice against trying to remove Firefox, it's required for several other things to work (for example the help viewer in Gnome uses Gecko (part of the Firefox package) for HTML rendering,a s do many other programs. Removing Firefox would break or uninstall all of them as well.

---

### Post by D3ath on 2009-03-19
> **mcduck said:**
> Yes, it should work. Although I'd advice against trying to remove Firefox, it's required for several other things to work (for example the help viewer in Gnome uses Gecko (part of the Firefox package) for HTML rendering,a s do many other programs. Removing Firefox would break or uninstall all of them as well.

True totally forgot about all that!

---

### Post by Pipps on 2009-03-19
Yipes! Thank yuo for the complete advice. I think I should reinstall Firefox, then!

---

