---
title: "trying to install a game ( .tar.bz2)"
date: 2012-06-10
forum: Gaming &amp; Leisure
---

### Post by tropic on 2012-06-10
I'm using lubuntu & I need to install a game called Zero Ballistics. I tried to install it from playdeb.net , installed the playdeb package and all,but when I click on the install now button here - [http://www.playdeb.net/software/Zero%20Ballistics]("http://www.playdeb.net/software/Zero%20Ballistics") 
a small dialog box opens up saying

```
external protocol request

chromium needs to launch extrnal application to handle apt:links link requestd here is apt:zeroballistic.....

the following appln wil be launchd if u accpt request:
xdg-open apt:zero ....

....
```

so I abandoned this method and downloaded a .tar.bz2 file (which is a "tarball" as I came to know later)from source forge[zeroballistics]("http://sourceforge.net/projects/zeroballistics/files/release/linux/")
googled on how to install such type of files... I ended up here [http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/]("http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/") & here [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")
followed instructions given there ..installed build essential,mercurial, apt file and everything. I couldn' extract to /usr/src as it said I had no write permission even though I had run the sudo chown and chmod commands.
Googled again about file permissions ..nothing clicked..
Went to this site tried to follow instructions there..
did the first step
couldnt do the 2nd step as permission was denied..ran this command ```
sudo nano /etc/apt/sources.list
``` added the lines but I dont know how to save the changes.

So now I've got a headache so I decided to ask about it here ](*,)

---

### Post by BcRich on 2012-06-10
Hi tropic
sounds like you've really tried to get it working, bummer that it's not playing nice :(
I don't have the game installed so I won't be able to give you an exact command list to get it running. But maybe I can still help? a tarball file is simply an archive file (kinda like a zip file), if you click/double click the file you should be able to open the archive with something like archive manager or ark? From there you can simply extract the file to whatever location you like (preferably somewhere in your home directory eg. /home/tropic/games/zb/ ).
From what I remember of this game it's already compiled, so you can skip all of that stuff you were trying to do before (which was attempting to build it from source, it seems?). There should be a file in there called start_client.sh or something like that. You simply run this file to start the game which attempts to connect you to a remote server.
If you double click the file and nothing happens, then you might need to set the executable bit for the file. In that case right click on the file and choose Properties. Then go to the Permissions tab and click the checkbox that says "executable" or "allow running as program" or something to that effect depending on your desktop environment.
So basically you don't always need to install a program in order to run it as some programs are already pre-compiled. However, this is not the most common method of deployment for games on Linux because it does not resolve missing dependencies (nor does building from source either). As a result the easiest way to install software in Ubuntu is to use a package manager, which basically takes care of everything for you. Ubuntu Software Center and Synaptic are probably the most common package managers for Ubuntu. Unfortunately not all software available for Ubuntu is accessible by default through the repositories that the package managers use to bring applications to your desktop. So sometimes you might need to extend the list that the package managers are accessing, in which case you will need to add an additional PPA. For example here's a link to a PPA for getdeb.net [http://www.ubuntuupdates.org/ppa/getdeb_games?dist=precise](http://www.ubuntuupdates.org/ppa/getdeb_games?dist=precise)
Please only install the PPA if you're sure you understand what it's all about :)
Hope that helps?

---

### Post by tropic on 2012-06-11
Thanks BcRich, yes there was a file by the name start_client.sh .It was already marked as executable but double clicking on it just made a small black screen (the terminal perhaps?) flash for a fraction of a second. But nevermind though, now I've got it installed using 2 .deb packages from pckgs.org
[http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics_2.0-1~getdeb4_i386.deb.html]("http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics_2.0-1~getdeb4_i386.deb.html")
[http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics-data_2.0-1~getdeb4_all.deb.html]("http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics-data_2.0-1~getdeb4_all.deb.html")

---

### Post by BcRich on 2012-06-11
> **tropic said:**
> Thanks BcRich, yes there was a file by the name start_client.sh .It was already marked as executable but double clicking on it just made a small black screen (the terminal perhaps?) flash for a fraction of a second. But nevermind though, now I've got it installed using 2 .deb packages from pckgs.org
[http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics_2.0-1~getdeb4_i386.deb.html]("http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics_2.0-1%7Egetdeb4_i386.deb.html")
[http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics-data_2.0-1~getdeb4_all.deb.html]("http://pkgs.org/ubuntu-12.04/getdeb-games-i386/zero-ballistics-data_2.0-1%7Egetdeb4_all.deb.html")
Awesome! Glad to hear you got it installed :)
If you think the problem has been resolved you can mark the thread as solved, by clicking on "thread tools"
Have fun :popcorn:

---

