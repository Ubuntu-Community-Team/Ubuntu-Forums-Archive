---
title: "where to find application&gt;office&gt;dictionary"
date: 2011-12-24
forum: Desktop Environments
---

### Post by shreyas_patel21 on 2011-12-24
I installed the dictionary using 



sudo apt-get install dictd
sudo apt-get install dict-gcide
sudo apt-get install dict-moby-thesaurus

commands.

but in ubuntu 11.10 icant find applications in start menu.

i have attached the image of what i am not getting in ubuntu 11.10

---

### Post by whatthefunk on 2011-12-24
Go to /usr/share/applications in a terminal.  Find the dictionary.desktop file.  Copy it and paste it here.

---

### Post by shreyas_patel21 on 2011-12-24
Thank you!

I found all the applications installed in usr/share/applications

but there is no dictd, which I have installed.

 there is no any file named dicionary.dektop

I have attached the screen shot of results I found with name dictionary.

---

### Post by whatthefunk on 2011-12-24
You can make your own .desktop file.  It should look something like this:

```
Encoding=UTF-8
Name=Dictionary
Comment=Dictionary
Exec=dictd
Icon=dictd
StartupNotify=true
Terminal=false
Type=Application
Categories=GNOME;Application;Utility;
```

Something like that.  For exec, enter what you would to access the program in the terminal.  You may have to put an icon in /usr/share/icons to get an icon to display properly in the menu.

---

### Post by shreyas_patel21 on 2011-12-24
I got the following error when I etered dictd

:~$ dictd
:E: cannot open pid file '/var/run/dictd.pid'
:E:    err msg: Permission denied
dictd (pid_file_create): :E: terminating due to errors. See log file
:E: terminating due to errors. See log file

---

### Post by Learning Linux 2011 on 2011-12-24
I'm not completely sure, but I think what you are showing in that picture is called gnome-dictionary
That has been the standard dictionary.

I installed it by using the
```

sudo apt-get install gnome-dictionary

```

That's all it took for mine to work

---

### Post by shreyas_patel21 on 2011-12-25
> **Learning Linux 2011 said:**
> I'm not completely sure, but I think what you are showing in that picture is called gnome-dictionary
That has been the standard dictionary.

I installed it by using the
```

sudo apt-get install gnome-dictionary

```That's all it took for mine to work


thAnk you
i installed gnome dictionary using your given code but what is dictd-gcide?

---

### Post by Learning Linux 2011 on 2011-12-25
> **shreyas_patel21 said:**
> thank you
i installed gnome dictionary using your given code but what is dictd-gcide?

Beats me.  Just another dictionary I guess.  There are several dictionaries available in Linux.  Dictd says it is a server that connects to databases, but frankly I don't have any real experience with it.  Gnome-dictionary has been the default for some time and just seems to work straight out of the box, so that's what I use.

You can go to "System -> Administration -> Synaptic Package Manager" and type in "dict" and read more.  Seems like "dictd" is part of a client/server dictionary somehow.

There are a ton of dictionaries for Linux, most of them are for foreign languages (foreign to an English speaker anyway).

---

### Post by stinkeye on 2011-12-26
You might find the package **artha** a more convenient dictionary to use.
Put it in to startup applications and after highlighting a word, use ctrl+alt+w
to show the meaning.

---

### Post by shreyas_patel21 on 2012-01-01
thank you all
I have installed golden dict using command prompt.

I am still unable to install any software using ubuntu software center..

---

