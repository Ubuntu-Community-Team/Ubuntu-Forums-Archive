---
title: "How to split GNU/Screen at start?"
date: 2009-02-25
forum: General Help
---

### Post by longman on 2009-02-25
Hello,

Can't figure it out myself or with Google's help, perhaps someone here might help me.

I would like to start the Screen program with several new windows and with a certain layout. So that basically i want predefined layout at start, let's say screen splitted once horizontally and then once vertically (i have applied the patch for vertical splitting). And in each part of the splitted screen a new terminal instance running.

Is there a way to achieve that?
Thanks for help! :)

---

### Post by geraldm on 2009-02-25
The screen program uses the full screen, and allows switching between screens.
You are using a patched program, so you should know what that patch does.
Dividing the screen into subsections would be a software problem.  
Look into a curses program, such as ncurses.  It should do what you are suggesting.

Gerald

---

### Post by geirha on 2009-02-25
Using an unpatched screen, the following screenrc creates a horizontal split with window 0 at top and window 1 at bottom.
```

split
screen
focus
screen

```
Does that help?

---

### Post by Yashiro on 2009-02-25
Or try [http://www.tenshu.net/terminator/](http://www.tenshu.net/terminator/)

---

### Post by longman on 2009-02-26
> **geirha said:**
> Using an unpatched screen, the following screenrc creates a horizontal split with window 0 at top and window 1 at bottom.
```

split
screen
focus
screen

```
Does that help?

Yes, it does exactly what i wanted! Thanks a lot, will try to adjust the .screenrc file.
Wohoo!

PS. Terminator is a nice app, however i need something what would work with or without X's. Screen is really great for that.
PPS. In case someone is interesting, here is my simple .screenrc file:

```

startup_message       off
vert_split
screen
focus
screen -t mc 0 mc

```

Here is great collection of examples: 
[http://www.softpanorama.org/Utilities/Screen/screenrc_examples.shtml](http://www.softpanorama.org/Utilities/Screen/screenrc_examples.shtml)

---

### Post by Lividity on 2009-03-13
I split mine into 4ths. Here's how: 

# Uninstall screen if you have it installed already
```
sudo aptitude purge screen
```

# Install dependencies to build screen
```
sudo apt-get build-dep screen
```

# Create an area to hold the source
```
cd ~/
mkdir screen
cd screen
```

# Get the latest source 
```
wget http://ftp.gnu.org/gnu/screen/screen-4.0.3.tar.gz
```

# Extract the source
```
tar xvf screen-4.0.3.tar.gz
```

# Download extract and apply vertical split patch 
```
cd screen-4.0.3/
wget http://vsp4sdl.yuggoth.org/wrp_vertical_split_0.3_4.0.2.diff.bz2
bunzip2 wrp_vertical_split_0.3_4.0.2.diff.bz2
patch -p1 < wrp_vertical_split_0.3_4.0.2.diff
```

# Build it!
```
./configure && make
```

# Install it!
```
sudo mv screen /usr/local/bin/
```

#Use my .screenrc
```
nano ~/.screenrc
```


##########.screenrc##########
activity "%c activity -> %n%f %t"
autodetach on
altscreen on
bell "%c bell -> %n%f %t^G"
defflow auto
defscrollback 10000
defutf8 on
msgwait 2                 # 1 second messages
startup_message off        # disable the startup splash message
shell -bash
vbell_msg "[[[ ding ]]]"
vbell off
nethack on
zombie cr

# remove some key bindings
bind k
bind W
bind ^k
bind .
bind ^\
bind \\
bind ^h
bind h
# make them safer
bind 'K' kill
bind 'W' windowlist
bind 'V' vert_split

# F8 to turn the status bar off
#bindkey -k k8 hardstatus alwayslastline
# F9 to turn the status bar on 
#bindkey -k k9 hardstatus alwaysignore
# F5 and F6 to move one screen forward or backward
bindkey -k k5 prev
bindkey -k k6 next


split
screen -t rtorrent rtorrent -o http_capath=/etc/ssl/certs
vert_split 
focus up
screen -t irssi irssi
focus up
screen -t bash bash 
focus down
vert_split
screen -t bash bash 
focus down
select irssi

# If you need more terms then uncomment however many you need. 
#screen -t bash bash
#screen -t bash7 bash
#screen -t bash8 bash
#screen -t bash9 bash

########End of script########

---

### Post by drinkableleech on 2012-02-03
In the lastest version of screen, you don't need the patch above. Just use split -v instead of vert_split in the above response.

---

### Post by oldos2er on 2012-02-03
Closed, necromancy.

---

