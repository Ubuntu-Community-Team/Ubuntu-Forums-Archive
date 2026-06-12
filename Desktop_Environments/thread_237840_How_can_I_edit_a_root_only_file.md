---
title: "How can I edit a root only file?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by pidey on 2006-08-16
Hey, I'm trying to use a solution found in [http://ubuntuforums.org/showthread.php?p=1187967](http://ubuntuforums.org/showthread.php?p=1187967)
to fix a sound problem, but I'm having some problems,

More specifically, when he said > 
Then, create the file ~/.asoundrc and copy these lines in it:

```
pcm.dsp0 {
    type plug
    slave.pcm "dmix"
}

ctl.mixer0 {
    type hw
    card 0
}

pcm.!default {
        type plug
        slave.pcm "dmix"
}
```


I am unsure how to create a file where he asks, or where ~/.asoundrc is. (I don't know what the tilde or the dot means)


I am also unsure how to modify a root only text file.

> 
After that, edit /etc/firefox/firefoxrc and replace the line beginning with FIREFOX_DSP by this one :```
FIREFOX_DSP="aoss"
```

When I open it up, I cannot modify the contents, as I need root permissions to do so, and I don't know how.

---

### Post by camtech on 2006-08-16
Don't yell at me if I'm wrong (being a newb) but open terminal (Applications> terminal). Then type:

gksudo geit /etc/firefox/firefoxrc

---

### Post by aysiu on 2006-08-16
Or ```
sudo cp /etc/firefox/firefoxrc /etc/firefox/firefoxrc.backup
gksudo gedit /etc/firefox/firefoxrc
```

More info here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by catlett on 2006-08-16
The asound file is hidden. That is why the line and dot. It will be in your home folder when you are done. First I'll give you the commands ans then I'll explain.
```
sudo gedit ~/.asoundrc 
```
Then copy and paste the line into the blank page. Make sure the spacing and line setup is the same.
```
sudo gedit /etc/firefox/firefoxrc
```
Again copy and paste.

sudo gives you root priveleges so prefix any command with sudo if you need root priveleges. 
gedit is a text editor. You just use the word gedit before the file you want to open.
So use sudo gedit to edit a root document.

P.S. I didn't want to confuse you with gksudo and sudo but there are previous posts stating gksudo. gksudo would be the preferred way to open a gui application from the terminal. sudo works but there are a few cases where that will cause an issue. gksudo is the command to use the application as a different user. It is the command that causes the password prompt when you select synaptic package manager or something in administration that needs root.

---

### Post by camtech on 2006-08-16
Also if you're going to be doing this a lot try this:
------------------------------------
Create a launcher with the following command:

Code:
gksudo "gnome-open %u"


When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.
----------------------------------
And I take no credit for that. Orginally posted by _23meg_ here:
[http://www.ubuntuforums.org/showthread.php?t=24008&highlight=open+root+launcher](http://www.ubuntuforums.org/showthread.php?t=24008&highlight=open+root+launcher)

---

### Post by catlett on 2006-08-16
> **camtech said:**
> Also if you're going to be doing this a lot try this:
------------------------------------
Create a launcher with the following command:

Code:
gksudo "gnome-open %u"


When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.
----------------------------------
And I take no credit for that. Orginally posted by _23meg_ here:
[http://www.ubuntuforums.org/showthread.php?t=24008&highlight=open+root+launcher](http://www.ubuntuforums.org/showthread.php?t=24008&highlight=open+root+launcher)

Hey Camtech thanks for posting that. That is a new one to me and it beats the  right click menu  entry  "open as root" (at least to me because I am a drop and drop freek :D  ) Just wanted to acknowledge it.
 That is why the Ubu forums are great. I learn new stuff all the time just by being a part of a thread.

---

### Post by pidey on 2006-08-16
First off, thank you, I think you have solved the problem (though I don't have access to the computer in question at this hour, so I can't test it)

But, Catlett, you said something about a right click menu open as root option?  I saw no such on the computer when I rightclicked the file I needed to in file browser (can't check right now, don't have access at this hour, might be wrong)  Also, why isn't the rightclick run as root enabled by default?  It seems to me that by having that it would prevent people from having to use the konsole (which is scary to most non-computer people)

---

### Post by catlett on 2006-08-16
It is not a default option. Ubuntu sticks to a strict "one cd installation" for the OS. This means they only have 700mb for the entire OS and applications. There are many things that would be nice to have as a default. Hopefully Ubuntu will take a "one DVD install" approach. Until then, things will have to be added aftyer install.
  The "hack" is a nautilus script that is on the forum somewhere originally but is now in the Dapper guide [http://doc.gwos.org/index.php/DapperGuide#How_to_open_files_as_root_user_via_right_click](http://doc.gwos.org/index.php/DapperGuide#How_to_open_files_as_root_user_via_right_click)
Before I list the commands, you mentioned Konsole. This particular script is for Gnome/Ubuntu. If you are using Kubuntu this won't work. There is a way to do it in konqueror but I do not use KDE so I do not know it.
 But if you are using ghnome/ubuntu here are the commands from that link.

Enter this in the terminal 
```
gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```
When the file opens, insert this line
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do gksudo "gnome-open $uri" & done
``` Save the file and enter this command to set the mode to executable 
```
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root 
```
I don't remember if it works rigth away or if it takes effect the next time you log in to gnome.
What that does, is create a menu entry when you rigth click on a file. The menu will have a "scripts" entry. When you scroll to it and highlight it, another option menu slides out. It will say "open as root".

---

