---
title: "How to Autostart apps in Lubuntu"
date: 2010-10-23
forum: Desktop Environments
---

### Post by SteveDee on 2010-10-23
Isn't Lubuntu FAB! And it's very easy to customise...once you know how.

It took me a while to discover how to auto-start applications, so I thought I'd share this with you.

**To autostart an application for all users**
Edit the autostart file as root by typing in a terminal:-
```

sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

```

Then add a line like this at the end of the file:-
```

@skype %U

```

**To autostart an application for a specific user**
Create an autostart directory in the users .config directory, if one does not already exist (i.e. /home/{user name}/.config/autostart/)

Then from a terminal type:-
```

ln -s /usr/share/applications/skype.desktop ~/.config/autostart/

```

---

### Post by cavalier911 on 2010-10-23
**Autorun a local user script located in ~/bin**
```
nano ~/.bashrc
```
Uncomment section to activate script in .bashrc which adds ~/bin to local users $PATH
Logout/in,verify from terminal that script in ~/bin executes as regular user. 
```
nano ~/.config/lxsession/Lubuntu/autostart
```
Add @your.script.name to autostart file

---

### Post by SteveDee on 2010-10-29
> **cavalier911 said:**
> **Autorun a local user script located in ~/bin**
...Uncomment section to activate script in .bashrc which adds ~/bin to local users $PATH...

Hi Cavalier911, can you explain this bit more, as I could not see the section you mention.

I'm auto-starting a script to start x11vnc server by putting it into a directory already included in $PATH (i.e. /usr/bin), and then adding to the autostart file:-
```

@startvnc.sh

```

---

### Post by cavalier911 on 2010-10-29
Forgot I copied from ~/.profile where it doesn't work.:oops:

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```
On a per user add to ~/.bashrc
On a global basis for all users add to /etc/bash.bashrc

This was solution autorun script to use smbnetfs to browse/automount samba shares,it must be mounted by local user in a directory owned by the user.

---

### Post by jgratero on 2011-06-07
> **SteveDee said:**
> Isn't Lubuntu FAB! And it's very easy to customise...once you know how.

It took me a while to discover how to auto-start applications, so I thought I'd share this with you.

**To autostart an application for all users**
Edit the autostart file as root by typing in a terminal:-
```

sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

```

Then add a line like this at the end of the file:-
```

@skype %U

```

**To autostart an application for a specific user**
Create an autostart directory in the users .config directory, if one does not already exist (i.e. /home/{user name}/.config/autostart/)

Then from a terminal type:-
```

ln -s /usr/share/applications/skype.desktop ~/.config/autostart/

```

I'm trying to force Dropbox to autostart, only for my session, and according to LXDE wiki, one is supposedly add an autostart file on:

> /.config/lxsession/<profile>/autostart file

Which in Lubuntu case would be:

> /.config/lxsession/lubuntu/autostart file

So I placed an autostart file there, that reads:

> @home/user/.dropbox-dist/dropboxd

But nothing happens. I have to start Dropbox manually...

---

### Post by ajgreeny on 2011-06-07
> **jgratero said:**
> I'm trying to force Dropbox to autostart, only for my session, and according to LXDE wiki, one is supposedly add an autostart file on:



Which in Lubuntu case would be:



So I placed an autostart file there, that reads:```
@home/user/.dropbox-dist/dropboxd 
```But nothing happens. I have to start Dropbox manually...
You need to make a script and point to that in the autostart file, but without the @ at the start in that file.

As far as I can see the @ is required only in the /etc/xdg/lxsession/Lubuntu/autostart, not in the one in ~/.config

You could also simply add the dropbox executable (or shell script if that is what it is) to /usr/bin or even to ~/bin if you have such a folder in your /home, and then make sure ~/bin is in your $PATH by adding appropriate lines to .bashrc, all as shown in cavalier911's posts.

---

### Post by jgratero on 2011-06-15
> **ajgreeny said:**
> You need to make a script and point to that in the autostart file, but without the @ at the start in that file.

As far as I can see the @ is required only in the /etc/xdg/lxsession/Lubuntu/autostart, not in the one in ~/.config

You could also simply add the dropbox executable (or shell script if that is what it is) to /usr/bin or even to ~/bin if you have such a folder in your /home, and then make sure ~/bin is in your $PATH by adding appropriate lines to .bashrc, all as shown in cavalier911's posts.

The fix from cavalier911 is to be inserted at the end of .bashrc?

---

### Post by poikiloid on 2011-08-01
In order to get Dropbox to autostart at logon, I did this:
made a new file in my autostart folder here:
/home/GUS/.config/autostart
(you should change GUS to whatever your own username is)
Call the file "Dropbox.desktop"
Open it in your text editor and paste these lines, again changing GUS to your username in the line that starts with "Exec":

```
[Desktop Entry]
Encoding=UTF-8
Name=Dropbox
Comment=RunDropbox
Icon=/usr/share/icons/elementary/panel/22/dropboxstatus-logo.svg
Exec=bash /home/GUS/.dropbox-dist/dropboxd
Terminal=false
Type=Application
```

Save it. Logout. Login. Be happy.

By the way, in order to get dropbox installed, I followed the instructions here: [http://www.omgubuntu.co.uk/2010/04/how-to-install-dropbox-in-lubuntu/](http://www.omgubuntu.co.uk/2010/04/how-to-install-dropbox-in-lubuntu/)

---

### Post by kerry_s on 2011-08-01
Don't forget about lxshortcut, makes it easier to create custom commands.
Example: lxshortcut -o ~/.config/autostart/name.desktop
Or say you want a desktop icon
Lxshortcut -o ~/Desktop/name.desktop

---

### Post by jgratero on 2011-08-03
> **poikiloid said:**
> In order to get Dropbox to autostart at logon, I did this:
made a new file in my autostart folder here:
/home/GUS/.config/autostart
(you should change GUS to whatever your own username is)
Call the file "Dropbox.desktop"
Open it in your text editor and paste these lines, again changing GUS to your username in the line that starts with "Exec":

```
[Desktop Entry]
Encoding=UTF-8
Name=Dropbox
Comment=RunDropbox
Icon=/usr/share/icons/elementary/panel/22/dropboxstatus-logo.svg
Exec=bash /home/GUS/.dropbox-dist/dropboxd
Terminal=false
Type=Application
```

Save it. Logout. Login. Be happy.

By the way, in order to get dropbox installed, I followed the instructions here: [http://www.omgubuntu.co.uk/2010/04/how-to-install-dropbox-in-lubuntu/](http://www.omgubuntu.co.uk/2010/04/how-to-install-dropbox-in-lubuntu/)

It worked flawlessly... Many thanks poikiloid! :D

---

### Post by SteveDee on 2011-11-06
> **SteveDee said:**
> **To autostart an application for all users**
Edit the autostart file as root by typing in a terminal:-
```

sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

```

Then add a line like this at the end of the file:-
```

@skype %U

```



There is a problem on Lubuntu 11.10 which means that any app entered this way will autostart twice.

The best way now seems to be to add an {app}.desktop file to /etc/xdg/autostart.

Applications added this way will appear in menu Preferences > Desktop Session Settings where you can enable/disable them.

---

### Post by amjjawad on 2011-11-07
> **SteveDee said:**
> There is a problem on Lubuntu 11.10 which means that any app entered this way will autostart twice.

Haven't tested yet but I'll give it a go once I'm free which I don't know when? :(
Could you confirm that please? what about 11.04?

> The best way now seems to be to add an {app}.desktop file to /etc/xdg/autostart.

Applications added this way will appear in menu Preferences > Desktop Session Settings where you can enable/disable them.

I have tired it 2 days ago and it worked, as always. But again, I must be sure about the first part of this post.

---

### Post by jontheid on 2011-11-07
Isn't it easier just to copy the file of the application you want to start automatically from /usr/share/applications to home/username/.config/autostart/ ?
That's what I did for skype, worked fine.
You can even change the executable options by editing the file using leafpad, looking for the 'exec=xxxx' line and adding the options afterwards.
Works for me! As far as I can tell you don't even need root privileges to do it either. 
Jon

---

### Post by amjjawad on 2011-11-07
> **jontheid said:**
> Isn't it easier just to copy the file of the application you want to start automatically from /usr/share/applications to home/username/.config/autostart/ ?
That's what I did for skype, worked fine.
Seems good idea but in case .desktop file doesn't exist, one must be created first :)

---

### Post by SteveDee on 2011-11-07
> **amjjawad said:**
> Haven't tested yet but I'll give it a go once I'm free which I don't know when? :(
Could you confirm that please? what about 11.04?

This is a known bug, see post #5 here: [http://ubuntuforums.org/showthread.php?t=1859751](http://ubuntuforums.org/showthread.php?t=1859751)

11.04 is OK.

> 
I have tired it 2 days ago and it worked, as always. But again, I must be sure about the first part of this post.

Putting an {app}.Desktop file in /etc/xdg/autostart seems to work, but I've had problems running a Gambas app like this today, not sure why.

The {app}.Desktop file is best made by typing in a terminal:-
```

lxshortcut -i  ~/Desktop/{appname}.Desktop

```

---

### Post by amjjawad on 2011-11-07
> **SteveDee said:**
> This is a known bug, see post #5 here: [http://ubuntuforums.org/showthread.php?t=1859751](http://ubuntuforums.org/showthread.php?t=1859751)

I think I've seen that email but didn't pay much attention. Thanks!

> 11.04 is OK.
I'm already using 11.04 still but don't really have time to test anything at the moment :/


> Putting an {app}.Desktop file in /etc/xdg/autostart seems to work, but I've had problems running a Gambas app like this today, not sure why.It's an easy way but yes, it could not work all the time - maybe.


> The {app}.Desktop file is best made by typing in a terminal:-
```

lxshortcut -i  ~/Desktop/{appname}.Desktop

```You mean to create the .desktop file? not on Linux now to try that command.

---

### Post by SteveDee on 2011-11-08
> **amjjawad said:**
> ...You mean to create the .desktop file? not on Linux now to try that command.

Yes, this command launches the Application Shortcut dialog (not sure that there is another way). I thought I'd posted somewhere previously on how to do this...may write something tonight if I can find time.

---

### Post by amjjawad on 2011-11-08
> **SteveDee said:**
> Yes, this command launches the Application Shortcut dialog (not sure that there is another way). I thought I'd posted somewhere previously on how to do this...may write something tonight if I can find time.

For me, I create new Blank File and save it as .desktop and then write the needed lines/codes. This is what I do usually :)

---

### Post by Pednick on 2012-04-25
> **SteveDee said:**
> Isn't Lubuntu FAB! And it's very easy to customise...once you know how.

It took me a while to discover how to auto-start applications, so I thought I'd share this with you.

**To autostart an application for all users**
Edit the autostart file as root by typing in a terminal:-
```

sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

```Then add a line like this at the end of the file:-
```

@skype %U

```**To autostart an application for a specific user**
Create an autostart directory in the users .config directory, if one does not already exist (i.e. /home/{user name}/.config/autostart/)

Then from a terminal type:-
```

ln -s /usr/share/applications/skype.desktop ~/.config/autostart/

```

Thanks for the info btw I didn't have to put %U and mine works fine.

What's that for anyway?

---

### Post by SteveDee on 2012-04-25
> **Pednick said:**
> ...I didn't have to put %U and mine works fine....What's that for anyway?

That's a good question.
The usual answer you get to that question is that:-
%u = a single url
%U = a list of url's
...but that's only half an answer.

The command "skype" is not expecting a list of url's as a command line option.

So %U is probably being used by something else (possibly vfs) to look up data and do something with it. I think skype %U starts skype with the current users config.

But perhaps someone can help us out with this?

---

