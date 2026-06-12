---
title: "run multiple command at the same time in one window terminal using multiplexer"
date: 2011-10-08
forum: Desktop Environments
---

### Post by jao_madn on 2011-10-08
Hi,

I would like to ask if someone knows or accomplished this task in the terminal multiplexer in a single window with multiple splitted pane:

In the script run multiple command at the same time in diff splitted pane or simulatneously.
As an example: I would like to run iptraf, iotop, htop, etc, in a single window with 4 splitled pane in a multiplexer and write it in a single script for easy one click or run script.

---

### Post by Toz on 2011-10-08
Gnu screen will do this.
```
sudo apt-get install screen
```

This .screenrc file will create 4 panes:
```

activity "%c activity -> %n%f %t"
autodetach on
altscreen on
bell "%c bell -> %n%f %t^G"
defflow auto
defscrollback 10000
defutf8 on
msgwait 2 # 1 second messages
startup_message off # disable the startup splash message
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
bind 'V' split -v

# F8 to turn the status bar off
#bindkey -k k8 hardstatus alwayslastline
# F9 to turn the status bar on
#bindkey -k k9 hardstatus alwaysignore
# F5 and F6 to move one screen forward or backward
bindkey -k k5 prev
bindkey -k k6 next


split
screen -t top top
split -v
focus up
screen -t bash1 bash
focus up
screen -t bash2 bash
focus down
split -v
screen -t bash3 bash
focus down
select bash1

```
Edit as required.

---

### Post by jao_madn on 2011-10-09
> **Toz said:**
> Gnu screen will do this.
```
sudo apt-get install screen
```This .screenrc file will create 4 panes:
```

activity "%c activity -> %n%f %t"
autodetach on
altscreen on
bell "%c bell -> %n%f %t^G"
defflow auto
defscrollback 10000
defutf8 on
msgwait 2 # 1 second messages
startup_message off # disable the startup splash message
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
bind 'V' split -v

# F8 to turn the status bar off
#bindkey -k k8 hardstatus alwayslastline
# F9 to turn the status bar on
#bindkey -k k9 hardstatus alwaysignore
# F5 and F6 to move one screen forward or backward
bindkey -k k5 prev
bindkey -k k6 next


split
screen -t top top
split -v
focus up
screen -t bash1 bash
focus up
screen -t bash2 bash
focus down
split -v
screen -t bash3 bash
focus down
select bash1

```Edit as required.

Thanks for the input i know i can be done..
The last part is useful to me and trying to modify something thats fits my needs..

Thanks by the way..

---

### Post by Toz on 2011-10-09
Can you please mark the thread Solved from the Thread Tools link above?

---

### Post by jao_madn on 2011-10-09
> **Toz said:**
> Can you please mark the thread Solved from the Thread Tools link above?


I will but please im not finish yet configuring the screenrc, or maybe theres a good chance a much better multiplexer like tmux or other. i may have some questions in further configuration. i will mark it solve as soon as i finish..

Thanks and Best Regards

---

