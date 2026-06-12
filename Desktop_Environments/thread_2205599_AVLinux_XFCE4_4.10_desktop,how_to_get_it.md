---
title: "AVLinux XFCE4 4.10 desktop,how to get it"
date: 2014-02-14
forum: Desktop Environments
---

### Post by Ralph_Lam on 2014-02-14
Wow;

I really like the desktop environment that the new AVLinux 6.0.2 is using.  It says that it is XFCE4 4.10

I have downloaded and used the XFCE environment for Ubuntu, and it does not look and feel like the AVLinux desktop.

Does anyone know how I might get ubuntu to look and feel like AVLinux 6.0.2?

I can't use AVLinux 6.0.2 at this time because while using it, the top 5 keys put out the wrong character, something I am trying to get answers on in forum for AVLinux...

Cheers

---

### Post by Jonathan Precise on 2014-02-15
There is a different icon theme installed. I think the closest icon theme is the faenza/faince set.
```
sudo add-apt-repository ppa:tiheum/equinox
sudo apt-get update && sudo apt-get install faenza-icon-theme
```

Also, You have to remove the bar on the bottom.

The bar on the right is made with avant-window navigator. Depending on your ubuntu version, there are different steps in installing (especially in 13.10)

---

### Post by Frogs Hair on 2014-02-15
I have created a favorites panel with both an XFCE panel or Dockbarx. My current XFCE Session installation uses just an additional  panel .

---

### Post by Ralph_Lam on 2014-02-16
Since I posted this thread, I learned about the XFCE interface. That what SolydX (one of my favorite distros) uses.

I have since learned how to install teh xubuntu desktop on ubuntu and login using it most of the time.

That said, I still like the Mac-like animation of the side panel on AVLinux 6.0.2.

I have spent some time on 

[http://xfce-look.org/](http://xfce-look.org/)

messing around with some changes.

Also, the default package has a bunch of pre-loaded schemes that can be fooled around with.  Many of which ae very liable, but none of which seem to give me that animation.

Jonathan Precise - 

will
```

sudo add-apt-repository ppa:tiheum/equinox
sudo apt-get update && sudo apt-get install faenza-icon-theme
```
 give me the ability to log in to ubuntu unity, xcfe, etc along with this theme?

Frogs hair -

I like the look of the panel in your screen shot.  Is it animated so that the icons swell when you mouse over them?

Thanks all for your responses.

By the way, how do you attach a picture to a post like that?

---

### Post by Frogs Hair on 2014-02-16
The panel isn't animated it is just an additional XFCE panel set to transparent . You would need a dock application to achieve that and I think AV uses a customized version of awn which has a new maintainer because the project died when Gnome 3 came out. [http://www.webupd8.org/2013/11/avant-window-navigator-gets-new.html](http://www.webupd8.org/2013/11/avant-window-navigator-gets-new.html)


To attach a picture use the paper clip symbol on the reply bar .

---

