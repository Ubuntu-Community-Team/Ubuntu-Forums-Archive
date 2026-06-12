---
title: "ive made a terrible mistake... S.O.S.!!!"
date: 2008-12-18
forum: Desktop Environments
---

### Post by shogunmidas on 2008-12-18
i was running ubuntu ibex and was doing a tutorial making it look like mac osx leopard. things were going fine, but i had a hang up trying to install gnome global menu applet. i ren this in the terminal -

cd Mac_files
wget [http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz](http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz)
tar zxvf gnome-globalmenu-0.4-svn964.tar.gz
cd globalmenu
sudo dpkg -i *.deb

and it looked like it downloaded fine. after that i tried to add it to the panel and for some reason it wouldnt. then i realized that any time i tried to open any file it would try and open it for a while then it would just disappear and nothing would open. i couldnt get any file to open, i couldnt make any mp3 play, and i couldnt make any video play. so i tried to restart, and it make it to the ubuntu loading screen but it would pause there and never actually get to the point where i put in my user name and password. it would just be in limbo forever. now i cant even get that to come up. i think i seriously fed up here and i need some help. i spent all this time making ubuntu work for me and i (with the help of this forum) figured out a fair amount of problems and got it working fine.

now this.

someone please help me get my ubuntu back.

just in case it would help the tutorial i was using was at this web site -

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

PLEASE HELP!!!

---

### Post by shogunmidas on 2008-12-18
anyone? any suggestions? please?

---

### Post by otchie1 on 2008-12-18
You've lost your window manager.

The simplest way to recover is to just reinstall, doesn't take more than 15 minutes or so.

There are other ways to recover by logging in to a terminal and working in text but I guess if you could do that then you would already :-)

You did set your home directory to be on a separate partition didn't you?

---

### Post by donkyhotay on 2008-12-18
> **otchie1 said:**
> You've lost your window manager.

The simplest way to recover is to just reinstall, doesn't take more than 15 minutes or so.

There are other ways to recover by logging in to a terminal and working in text but I guess if you could do that then you would already :-)

You did set your home directory to be on a separate partition didn't you?

Wouldn't reinstalling gnome from the CLI fix this as well without having to wipe the entire OS?

---

### Post by shogunmidas on 2008-12-18
lol...

no everything is on the same partition. damn it.

but why would me trying to install the gnome global menu do this?

and whats the cli fix? if i dont have to completely reinstall that would be great. ive just spent the last 2 or so weeks getting everything in ubuntu just right.

---

### Post by shogunmidas on 2008-12-19
why have the ubuntu gods punished me?

i have done everything that they have asked of me. i have even converted more followers to the cult of ubuntu. and now this! the ubuntu gods must require a sacrifice.

---

### Post by sigurnjak on 2008-12-20
maybe this helps:

    rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Get back to your GUI desktop by hitting CTRL + ALT + F7.

Login and VOILÀ! Just like the first time you ever logged into your Gnome desktop.

---

