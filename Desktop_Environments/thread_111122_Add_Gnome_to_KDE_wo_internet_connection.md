---
title: "Add Gnome to KDE w/o internet connection"
date: 2006-01-01
forum: Desktop Environments
---

### Post by morke on 2006-01-01
Hi!
I just installed Kubuntu a few days ago, but I would like to select environment on login (kde or gnome).
I tried searching the forum but no one here seems to make that switch (everyone ditched gnome or installed KDE on a working gnome).
So - how do I install ubunto and use both?

An important issue is I still couldn't manage to install internet connection on KDE, so I can't get the package installed straight from the web (I dual boot with Windows so I can download and save to a shared FAT32 folder).
I also have the Ubunto (gnome) install cd at hand, but wouldn't want to go through the entire installation (seems needless).

Thanks,
Morke.

---

### Post by kwaanens on 2006-01-01
Start Synaptic (Kynaptic I guess, when you're in KDE). Mark ubuntu-desktop for installation. I guess kubuntu-desktop will now be removed, but that's a dummy package so it doesn't matter. Note that kubuntu-related artwork will disappear also.
Or you could go ahead and install specific gnome-packages. See section "Gnome" in Synaptic

However, Gnome is one thing, KDE is another. You have to choose when you log in each session.

- Ketil

Edit: noticed that you're not online. So: add the Ubuntu-CD to the list of repos in Kynaptic. That should take care of the most important packages at least.

---

### Post by byen on 2006-01-01
Hey morke.
Here is what I did since my installation was similar to yours.
First I see that you have installed kubuntu and also have the ubuntu(gnome) cd.  With the help of the gnome cd you can easily install the gnome desktop environment  using the synaptic package manager.
Step one: Insert the Ubuntu CD which has the desktop-type that you want to install
Step 2: go to System>Administration>Synaptic Package manager 
Step 3: In the package manager do: 
           Edit > add cdrom
Now here the synaptic package manager adds the list of all the programs available to install.
Step4: Now close the package manager
Step5: Open the terminal and type:
          sudo apt-get install ubuntu-desktop   
(this will install the gnome desktop environment alongside kubuntu)
(if you have ubuntu and want to install kde do 'sudo apt-get install kubuntu-desktop')

thats it..once this is done...it will ask you which desktop env you want as default and you can later select it and change it at the login screen (sessions)

Hope it helps goodluck.

---

### Post by morke on 2006-01-01
Thanks Ketil and byen!
I did what you said and it was just right on the money!

Much obliged.
Morke.

---

