---
title: "GTK theming not applied to applications (Xfce 17.10)"
date: 2017-10-26
forum: Desktop Environments
---

### Post by mrouilla515 on 2017-10-26
Just install Xubuntu 17.10 on 2 computers. Themed them with a dark theme like Adapta Nokto and while Thunar and the settings panels are correctly using the dark theme, some of the applications don't use it (calibre, qbittorent, albert etc ..).They stay white.  There is something missing in the release. 

I also have Manjaro Xfce 17.0.6 installed and the theming works perfectly there.

P.s Calibre is a special case as by default, it doesn't accept gtk theme after install. However it complain that "QGtkStyle could not resolve GTK. Make sure you have install the proper librairies"


Tx

---

### Post by vasa1 on 2017-10-26
I suspect that the applications that don't accept your themes maybe based on qt.

You could try running the following two commands that are mere simulations and not harmful. Don't use *sudo*. There's no need!
```
apt-get remove -s libqt4* | grep Remv | cut -d ' ' -f 2
``````

apt-get remove -s libqt5* | grep Remv | cut -d ' ' -f 2
```

If they are indeed qt apps that don't theme well, you'll need to wait for someone to help you.

Edit: all the three applications mentioned use qt5.

For more, read [https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications](https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications) and [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=822697](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=822697)

You will get quite a few hits if you search the 'net for *qt5 apps on gnome systems*.

---

### Post by mrouilla515 on 2017-10-26
Hello vasa, thank you for your quick reply. Getting use to Ubuntu here. I did the 2 commands. Only the last one return this. Yes I think they do use qt5. 
Does that mean that Xubuntu doesn't support that library  ?

>>>>>
maurice@xubuntu-IL9-Pro:~$ apt-get remove -s libqt5* | grep Remv | cut -d ' ' -f 2
qbittorrent
libqt5svg5
qt5-gtk-platformtheme
libqt5gui5
libqt5network5
libqt5dbus5
libqt5xml5
libqt5widgets5
libqt5core5a

---

### Post by vasa1 on 2017-10-26
Xubuntu is gtk-based. If you install applications requiring other toolkits, you may need to do some extra legwork!

I don't use Xubuntu or a gtk-based distro and so can't help you further. Sorry about that. But I'm sure someone will come along to assist you :)

See if [https://askubuntu.com/questions/910012/how-can-i-get-qt5-applications-to-use-the-gtk-theme-in-ubuntu-17-04](https://askubuntu.com/questions/910012/how-can-i-get-qt5-applications-to-use-the-gtk-theme-in-ubuntu-17-04) helps even though it's for 17.04.

---

### Post by mrouilla515 on 2017-10-26
> **vasa1 said:**
> Xubuntu is gtk-based. If you install applications requiring other toolkits, you may need to do some extra legwork!

I don't use Xubuntu or a gtk-based distro and so can't help you further. Sorry about that. But I'm sure someone will come along to assist you :)

See if [https://askubuntu.com/questions/910012/how-can-i-get-qt5-applications-to-use-the-gtk-theme-in-ubuntu-17-04](https://askubuntu.com/questions/910012/how-can-i-get-qt5-applications-to-use-the-gtk-theme-in-ubuntu-17-04) helps even though it's for 17.04.

Thanks for the legs work but reading that link, they totally lost me. It is way over my Linux knowledge. I may have to change distro then.

---

### Post by flocculant on 2017-10-27
Install qt5-style-plugins 

Trying hard to remember if I did anything but logout/in, bash_history isn't saying I did anything. Try that first

This is all I've got which dpkg knows is qt5

```
ii  qt5-gtk-platformtheme:amd64 5.9.1+dfsg-10ubuntu1         amd64        Qt 5 GTK+ 3 platform theme
ii  qt5-qmake:amd64             5.9.1+dfsg-10ubuntu1         amd64        Qt 5 qmake Makefile generator tool
ii  qt5-style-plugins:amd64     5.0.0+git23.g335dbec-2build1 amd64        Qt 5 extra widget styles
```

So I didn't install anything else (my qt5 'stuff' is installed from git)

---

### Post by mrouilla515 on 2017-10-27
Yes that did it after login off/in for qbittorrent. I install albert and it brought a bunch of qt5 stuff too. Albert is now properly themed. There is only Calibre which does not want to take it and complain about that QGtkStyle error. Still that's pretty good.

---

### Post by vasa1 on 2017-10-27
On my system when I check for calibre dependencies, I see this:```
$ apt depends calibre
calibre
  Depends: python2.7
  Depends: python-dbus
 |Depends: python-pil
  Depends: python-imaging
  Depends: python-lxml (>= 3.2.1)
  Depends: python-mechanize (>= 0.2.5)
  Depends: python-beautifulsoup (>= 3.0.5)
  Depends: python-pkg-resources
  Depends: python-cssutils (>= 0.9.9~)
  Depends: python-cssselect (>= 0.7.1)
  Depends: python-cherrypy3 (>= 3.1.1)
  Depends: python-dateutil
  Depends: python-feedparser
  Depends: python-markdown
  Depends: python-pyqt5 (>= 5.5.1+dfsg-3ubuntu5~xenialoverlay11~1)
  Depends: python-pyqt5.qtwebkit
  Depends: python-pyqt5.qtsvg
  Depends: python-pyparsing
  Depends: python-routes
  Depends: python-chardet
  Depends: python-netifaces
  Depends: python-apsw (>= 3.7.17)
  Depends: xdg-utils
  Depends: imagemagick
    graphicsmagick-imagemagick-compat
  Depends: poppler-utils
  Depends: fonts-liberation
  Depends: libjs-mathjax (>= 2.1+20121028-1)
  Depends: calibre-bin (>= 2.55.0+dfsg-1build1~~xenialoverlay1~1)
  Recommends: python-dnspython (>= 1.6.0)
$
```Why don't you check and see if you have all the dependencies in place?

BTW, how did you install calibre and from where?

Please read oldos2er's posts in this thread: [https://ubuntuforums.org/showthread.php?t=2368617&highlight=calibre](https://ubuntuforums.org/showthread.php?t=2368617&highlight=calibre)

---

### Post by flocculant on 2017-10-27
Not sure if this has changed, but [https://www.mobileread.com/forums/showpost.php?p=3026176&postcount=4](https://www.mobileread.com/forums/showpost.php?p=3026176&postcount=4)

Installed it here - not much liking the icons (but they're easily changed it seems) but generally it's not looking too out of place for me.

---

### Post by mrouilla515 on 2017-10-27
I install calibre through their site. The use a python script for Linux ;
"sudo -v && wget -nv -O- [https://download.calibre-ebook.com/linux-installer.py](https://download.calibre-ebook.com/linux-installer.py) ..." bla bla. 

May be I should just install it through the depot. I have to un-install it first. Let you know.

---

### Post by mrouilla515 on 2017-10-27
> **mrouilla515 said:**
> I install calibre through their site. The use a python script for Linux ;
"sudo -v && wget -nv -O- [https://download.calibre-ebook.com/linux-installer.py](https://download.calibre-ebook.com/linux-installer.py) ..." bla bla. 

May be I should just install it through the depot. I have to un-install it first. Let you know.

Ok they have a python script to remove it "calibre-uninstall". It got rid of it. I then install it from the archive. It pull all the necessary stuff with it. Calibre is fine, however the developer (I had an argument with him about that) has decide not to activate GTK theming by default. You have to set this environment variable to get it. It then take the theme.
CALIBRE_USE_SYSTEM_THEME=1

So all is good now,. What was missing from the official install is that package "qt5-style-plugins". I guest most of the archive programs and ppa will pull what they need.

Ok I have to go to bed. It's 1:00H in the morning. Thank you very much with your support. My first experience with that was awesome. 

Cheers !

---

### Post by vasa1 on 2017-10-27
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jpberes on 2017-10-29
I'm using XFCE (Xubuntu 17.10) and did install Calibre BUT I did install it via the Software Center, and no problems with the adapted theme ...

---

