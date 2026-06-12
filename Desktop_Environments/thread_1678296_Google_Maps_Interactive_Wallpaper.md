---
title: "Google Maps Interactive Wallpaper?"
date: 2011-01-30
forum: Desktop Environments
---

### Post by uba704 on 2011-01-30
Hi,

I'm running Kubuntu 10.04 and have activated the interactive map wallpaper.
Anyone know if it is possible to install Google Maps ([http://maps.google.com/](http://maps.google.com/)) as an interactive wallpaper instead?

Thanks!

---

### Post by uba704 on 2011-02-19
Or maybe just have some web browser as background - then I could point it to [http://maps.google.com/](http://maps.google.com/) - anyone know if that is possible?

---

### Post by ankspo71 on 2011-02-19
Hi,
Try using one of the web browser type plasmoids. They can be resized to fit the whole desktop. 

The "Web Browser" plasmoid can display [http://maps.google.com/](http://maps.google.com/) just fine, but it has the default homepage of [http://kde.org/](http://kde.org/), so every time it starts it shows kde.org. I tried searching my system but I can't figure out how or where to change its homepage. You might need 'kdeplasma-addons' to be installed in order to have Web Browser plasmoid. 

More KDE plasmoids can be found at [http://kde-apps.org/](http://kde-apps.org/).
Search the site for "SmoothWebView", "Web Snipplet", and "Web Fetch" and other plasmoids.

If you download a *.plasmoid package, you can try installing them by using this example command in the terminal:
```
plasmapkg -i /path/to/file.plasmoid
```

Some plasmoids might require compiling the package yourself too, like this:
> [http://kde-look.org/help/index.php?type=70](http://kde-look.org/help/index.php?type=70)
    tar -xvf plasmoid.tar.gz
    cd plasmoid
    mkdir build
    cd build
    cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
    make
    sudo make install OR su -c "make install"
    Have fun! :-) 
if not they should have instructions inside the package you downloaded.

Hope this plasmoid idea helps. :D

---

