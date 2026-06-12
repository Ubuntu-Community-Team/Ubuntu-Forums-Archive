---
title: "Using Nemo in Flashback session - no wallpaper"
date: 2020-10-11
forum: Desktop Environments
---

### Post by kansasnoob on 2020-10-11
I used to use the flashback session a lot prior to 18.04 and drifted away in favor of Mate and/or KDE Plasma, but it's coming time to upgrade the roughly 4 dozen "other people's" PCs that I help maintain and they overwhelmingly want the functionality of flashback, especially due to [this Mate sound bug]("https://bugs.launchpad.net/ubuntu/+source/libmatemixer/+bug/1890061"). There are little things that they don't like about everything else I throw at them, but the only thing in the flasshback session that they don't like is Nautilus (aka: Files).

So I've been playing with Nemo and have it 99% figured out I think. The one thing I can't get is the wallpaper to display on the Nemo Desktop. This post by mc4man was helpful:

[https://ubuntuforums.org/showthread.php?t=2442421&p=13953729#post13953729](https://ubuntuforums.org/showthread.php?t=2442421&p=13953729#post13953729)

Otherwise for the most part the instructions found here are pretty much all that's needed:

[https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu-18-04](https://askubuntu.com/questions/1066752/how-to-set-nemo-as-the-default-file-manager-in-ubuntu-18-04)

So I wonder if there's a way to get the wallpapers to display in flashback with desktop handling handed over to Nemo? I played with the metacity setting for compositing. Metacity compositing-manager = off displays just a blank purple screen (with the Nemo desktop as I prefer) and compositing-manager = on displays what appears to be the ubuntu splash screen with just a black background and the ubuntu logo. I tried Compton which I hadn't played with in nearly a decade but it doesn't have the functionality I'd want.

Oh, just adding additional seconds to the Nemo startup file didn't help either - I tried up to 60 seconds just for the heck of it. Also the same settings I'm using in flashback work perfectly in the standard Ubuntu session, that is Nemo manages the desktop as I wish and desktop wallpaper is displayed just fine, so it is purely a flashback thing.

---

### Post by kansasnoob on 2020-10-14
Just a bump ;)

---

### Post by norobro on 2020-10-16
Since you haven't recieved a response I thought that I would throw this out there.

Have you considered using css? I have used css to style a Gtk widget or two, so I thought I would see if css styling works with the nemo filemanager using flashback. Attached is a screenshot of the nemo file manager with a background image. Here is the css file (.config/gtk-3.0/gtk.css):```
.nemo-window {
    background-image: url("/path/to/palouse.jpg");
    background-repeat: no-repeat;  
    background-size: cover;
}

.nemo-window .view {
    background: rgba(0, 0, 0, 0.0); 
}
```
That pic is pretty much a mess but it does illustrate that styling is possible. Some digging in the source code will probably be necessary to determine class names for further styling (i.e. font color, sidebar bg, etc.).

I don't normally use nemo or gnome-flashback so I don't know how to install nemo-desktop but it seems like if you can style the filemanager you should be able to style nemo-desktop. 

BTW I'm using 20.04. Hope this helps.

---

### Post by kansasnoob on 2020-10-19
> **norobro said:**
> Since you haven't recieved a response I thought that I would throw this out there.

Have you considered using css? I have used css to style a Gtk widget or two, so I thought I would see if css styling works with the nemo filemanager using flashback. Attached is a screenshot of the nemo file manager with a background image. Here is the css file (.config/gtk-3.0/gtk.css):```
.nemo-window {
    background-image: url("/path/to/palouse.jpg");
    background-repeat: no-repeat;  
    background-size: cover;
}

.nemo-window .view {
    background: rgba(0, 0, 0, 0.0); 
}
```
That pic is pretty much a mess but it does illustrate that styling is possible. Some digging in the source code will probably be necessary to determine class names for further styling (i.e. font color, sidebar bg, etc.).

I don't normally use nemo or gnome-flashback so I don't know how to install nemo-desktop but it seems like if you can style the filemanager you should be able to style nemo-desktop. 

BTW I'm using 20.04. Hope this helps.

Thanks. That's certainly a thought. Since as it is I seem to be getting the splash screen I've even considered changing that ............. something in 'plymouth' I think????

---

### Post by tea for one on 2020-10-23
I use Peppermint OS on a cheap 'n' cheerful laptop and Nemo is the default file manager.

Do you have the following setting/preferences:-

Open Nemo > Edit > Plugins > Change Desktop Background (checkbox)

Open Nemo > Edit > Plugins > Set as Wallpaper (checkbox)

There is also an area where you can create your own scripts, although I do not know exactly how it works.

---

### Post by kansasnoob on 2020-10-29
> **tea for one said:**
> I use Peppermint OS on a cheap 'n' cheerful laptop and Nemo is the default file manager.

Do you have the following setting/preferences:-

Open Nemo > Edit > Plugins > Change Desktop Background (checkbox)

Open Nemo > Edit > Plugins > Set as Wallpaper (checkbox)

There is also an area where you can create your own scripts, although I do not know exactly how it works.

Those settings were correct, so no joy :(

---

### Post by kansasnoob on 2020-10-29
Alberts Muktup&#257;vels provided the answer in this existing bug report:

[https://bugs.launchpad.net/ubuntu/+source/nemo/+bug/1742193/comments/9](https://bugs.launchpad.net/ubuntu/+source/nemo/+bug/1742193/comments/9)

I spent a lot of time in dconf-editor but hadn't tried changing "org.gnome.gnome-flashback root-background". That's all it took. I'll try and summarize this after trying it out on a fresh install over the next week or so.

---

