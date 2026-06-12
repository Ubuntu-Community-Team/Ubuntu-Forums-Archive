---
title: "sudo - launcher?"
date: 2005-03-30
forum: Desktop Environments
---

### Post by intro on 2005-03-30
Hi, I could be going the wrong way about this, but here goes.

i did

*apt-get install bittornado-gui *

it didnt install an icon, so I tried it from the command line

*bittornado-gui*

this didnt work when i tried to load a torrent, so i tried
[I]
sudo bittornado-gui[/I] and it worked fine.

is there a way to add a panel item that does "sudo bittornado-gui" ?

I cant see how to do it, whenever i create the panel item it doesnt work. Or should i repermission something?


Im using hoary and everything is updated to the latest from the official sources.

---

### Post by Roptaty on 2005-03-30
NO! dont do that... Bittornado does not require root privileges. I am not familiar with the program it self, but torrent programs do not need root access. 

The executable file is called btdownloadgui and not bittornado-gui. 


sudo:
Use gksudo instead of sudo. gksudo will open a graphical dialog asking you for your password.

---

### Post by intro on 2005-03-30
thanks for the answer. it turns out i was too sleepy when i posted this :)

if bittornado-gui has incorrect permissions in the save path, it will not work, obviously, using sudo was a silly way to resolve the problem.

thanks anyway :)

---

### Post by bored2k on 2005-03-30
By the way, bittornado is not the way to go right now . Bittorrent [official] just released the spankin new awsome Bittorrent 4.0.1, and its far better than btdownloadgui, and the GUI is more sleek/simple than any other client on Win/Lin .

[http://www.bittorrent.com/](http://www.bittorrent.com/) [get the source package if u run into trouble]

the new abc client is nice also .

---

### Post by Psquared on 2005-04-29
I get a bunch of errors when I launch btdownloadgui.

> peyre@PTL-Mobile:~ $ sudo btdownloadgui
peyre@PTL-Mobile:~ $ btdownloadgui

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
/usr/share/themes/Nuvola/gtk/gtkrc:313: error: unexpected identifier `xthickness ', expected character `}'


The program starts, such as it is, but it is not very intuitive. It asks me for a file so I gave it the file I usually up and download to and from but it choke. 

Is Azareus easier to use? Will it install on Warty?

---

### Post by bored2k on 2005-04-30
[QUOTE=bored2k]BTW You might find the new official bittorrent 4.0.1 a lot better AND prettier.
You can get it [http://www.bittorrent.com/](http://www.bittorrent.com/) [get the source code]. You just extract it, make the filename btdownloadgui.py executable [right click > properties > permissions > execute on all] and just double click on it and select run. Here is a screenshot of it:
[[IMG]http://img192.echo.cx/img192/7272/official9wt.th.png[/IMG]](http://img192.echo.cx/my.php?image=official9wt.png)
[/QUOTE]

It is very easy to use, its the one I prefer [I use this one and Azureus --sometimes, but I dont like azureus because its written in Java and eats a lot more RAM than the other clients).

Yes it will install on Warty. You need to have Java installed. You wont need azureus after you try the above but, To install java, I prefer one of these two methods:
a) In a command line terminal do this:
```
sudo echo deb http://ubuntu.tower-net.de/ubuntu/ warty java >> /etc/apt/sources.list && sudo echo deb http://archive.ubuntu.com/ubuntu/ warty multiverse && sudo apt-get update && apt-cache search sun-j2
``` Now, the last command will display some names, it could be sun-j2sdk1.5. If that is the case, do (change the name if this is not it) ```
sudo apt-get install sun-j2sdk1.5
```

b)```
sudo echo deb http://archive.ubuntu.com/ubuntu/ warty multiverse && sudo apt-get update && sudo apt-get install build-essential java-package java-common fakeroot 
``` Then, [quote=http://www.ubuntulinux.org/wiki/Java]download the sun jdk from java.sun.com
** edit /usr/share/java-package/sun-j2sdk.sh to reflect the actual JDK 1.5 release version.

$ fakeroot make-jpkg jdk-1_5_0-linux-i586.bin
$ sudo dpkg -i sun-j2sdk1.5_1.5.0_i386.deb (this reports an error but is completed in next step)
$ sudo apt-get install sun-j2sdk1.5debian
$ sudo update-alternatives --config java (see next step for dependancy errors)
$ sudo apt-get -f install (fix dependancy errors if required)[/quote]

---

### Post by Psquared on 2005-04-30
I think I already have java installed. At least it shows in "about:plugins" in Firefox. It's version 1.5.0_01-b08.

Will that do it?

Also, for installing the new bittorrent client do I just install as usual?

untar
./configure
make
make install

---

### Post by bored2k on 2005-04-30
[QUOTE=Psquared]I think I already have java installed. At least it shows in "about:plugins" in Firefox. It's version 1.5.0_01-b08.

Will that do it?

Also, for installing the new bittorrent client do I just install as usual?

untar
./configure
make
make install[/QUOTE]
 No dude

extract it then inside the dir do
python btdownloadgui.py &

You can make that file executable and just double click on it.

---

### Post by MaX on 2005-04-30
[QUOTE=bored2k]By the way, bittornado is not the way to go right now . Bittorrent [official] just released the spankin new awsome Bittorrent 4.0.1, and its far better than btdownloadgui, and the GUI is more sleek/simple than any other client on Win/Lin .

[http://www.bittorrent.com/](http://www.bittorrent.com/) [get the source package if u run into trouble]

the new abc client is nice also .[/QUOTE]
 BitComet for windows still blows away the officiall GUI

---

### Post by bored2k on 2005-04-30
[QUOTE=MaX]BitComet for windows still blows away the officiall GUI[/QUOTE]
 That's really helpful. 1) How TH can any client beat BT, without it there is nothing. Each one is just the curses with a GUI skin. 2) Well, we are here to help people out, not bash a developer's nightmare. If it's good then port it to linux and post again. Dont start a flame war.

---

### Post by Psquared on 2005-04-30
[QUOTE=bored2k]No dude

extract it then inside the dir do
python btdownloadgui.py &

You can make that file executable and just double click on it.[/QUOTE]

Thanks man. 

I just took another look and noticed its a *.deb file. Why would I not use dpkg to install?? Will it register as a *.deb package?

bittorrent-4.0.1.linux_i686-2_all.deb

Sorry, I'm a little confused, but I do appreciate your help.

---

### Post by bored2k on 2005-04-30
I encountered some problems using that .deb package. You can give it a shot. If it works it works, but if you do so, you can't have bittornado and official installed at the same time [they use the same btdownloadgui command]. I still use the .tgz, i create a launcher for it and thats that.

And yes it will be shown in Synaptic if you do so.

---

