---
title: "Folder names appearance in terminal"
date: 2016-09-14
forum: Desktop Environments
---

### Post by gigi3 on 2016-09-14
Hi, I just installed Ubuntu16.04 on my old Acer TravelMate laptop and it works just fine. I got an annoying behaviour in listing a folder content with ll (ls -la) as you can see in the snapshot below. How can I do to change these strange background/foreground colors? Thanks
Gigi
[ATTACH=CONFIG]271163[/ATTACH]

---

### Post by CantankRus on 2016-09-14
You can turn off ls color support in your ~/.bashrc file.
eg I have a section
```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    [COLOR="#FF0000"]alias ls='ls --color=auto'[/COLOR]
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```
Comment out the [COLOR="#FF0000"]alias ls[/COLOR] line.
Then reload your ~/.bashrc with...
```
source ~/.bashrc
```

"man ls" says...
> Using color to distinguish file types is disabled both by default and with --color=,never/. With --color=,auto/, ls emits color codes only when standard output is connected to a terminal. 
The LS_COLORS environment variable can change the settings. Use the dircolors command to set it.

I've never changed colors but if you just want to get rid of the annoying color, it seems you would have to look into the **dircolors** command.
This askubuntu topic may help....
[**_[COLOR="#B22222"]What do the different colors mean in the terminal?[/COLOR]_**]("http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal")

---

### Post by CantankRus on 2016-09-14
I've been having a read and can remove the green background by adding this line to the bottom of my ~/.bashrc file...
```
export LS_COLORS=$LS_COLORS:"tw=30;00":"ow=34;00" 
```
After saving reload your ~/.bashrc...
```
source ~/.bashrc
```

---

### Post by vasa1 on 2016-09-14
I like the ~/.dircolors route. I don't have background colors for anything but I find text colors useful.

---

### Post by gigi3 on 2016-09-14
Thanks CantankRus, it worked for me also. I'll investigate more deeply on dircolors, thanks to all

---

### Post by &amp;KyT$0P# on 2016-09-14
[https://ubuntuforums.org/showthread.php?t=2314329&page=2&p=13509658&viewfull=1#post13509658](https://ubuntuforums.org/showthread.php?t=2314329&page=2&p=13509658&viewfull=1#post13509658)

---

### Post by him610 on 2016-09-14
You did not say, but the terminal application you are using looks like "Gnome Terminal." If that is true you can change both background and foreground colors from within.
Move your mouse to upper bar of terminal; you should see seven options. Click on Edit > Profile Preferences. A window will open that has a tab labeled Colors - click on it, you will be able to modify your FG & BG colors.

---

