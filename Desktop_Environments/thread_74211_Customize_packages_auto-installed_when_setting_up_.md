---
title: "Customize packages auto-installed when setting up OS?"
date: 2005-10-11
forum: Desktop Environments
---

### Post by helwitch on 2005-10-11
Is there a way to customize which packages are installed when the OS is installed? For example, to modify it so that kopete is not installed and GAIM is, and openofficeorg2 is installed rather than openofficeorg? These along with other packages are ones that I routinely end up removing/adding after a fresh install (which I do fairly often, as I'm learning and have a talent for breaking things.) Is there a script on the CD I could modify, or what? Where does the installer get the list of programs it's going to auto install? I've got to say, that was something I quite liked about the fedora installer, it asked me which packages I wanted installed and which I didn't.
I know one can install as a server, and then apt-get various things, but from what I've read, that can lead to problems, and wouldn't save me any time anyway. What I'd ideally like is my own customized kubuntu install CD, with only the packages I wanted installed at boot, and none of the packages I didn't want.
Thanks for any help!

---

### Post by mlomker on 2005-10-11
> Is there a script on the CD I could modify, or what? Where does the installer get the list of programs it's going to auto install? 

The best things to do is to set up your machine exactly like you want it and then use this command to output a list of installed packages on your system.

```

dpkg --get-selections >> mypackages.txt

```

Then when you reload the box you select the 'server' installation option to load as little as possible and get to a prompt.  Configure your /etc/apt/sources.list and then:

```

sudo apt-get update
sudo cat mypackages.txt | dpkg --set-selections
sudo apt-get upgrade

```

---

### Post by helwitch on 2005-10-11
[QUOTE=mlomker]The best things to do is to set up your machine exactly like you want it and then use this command to output a list of installed packages on your system.

```

dpkg --get-selections >> mypackages.txt

```

Then when you reload the box you select the 'server' installation option to load as little as possible and get to a prompt.  Configure your /etc/apt/sources.list and then:

```

sudo apt-get update
sudo cat mypackages.txt | dpkg --set-selections
sudo apt-get upgrade

```[/QUOTE]

Ok, see, now, THAT I can live with! Thanks! Anyway I can modify the sources.list that's on the CD tho, so I could skip that step?

---

### Post by mlomker on 2005-10-11
I'd imagine that you could modify the contents of the .iso (.iso's can be mounted like they are disks) prior to burning it to a CD.  I've never looked into it, though.

I'd recommending just keeping your /home in a separate partition so that you can reinstall the operating system to / and then easily copy those two files over from /home.

---

### Post by whoscheesemine on 2008-01-17
came accross this today and then remembered reading this topic earlier today, thought it might help ya, or at least be of interest.

[http://ubuntulinuxhelp.com/customize-your-own-ubuntu-derivative-with-minibuntu/](http://ubuntulinuxhelp.com/customize-your-own-ubuntu-derivative-with-minibuntu/)

---

