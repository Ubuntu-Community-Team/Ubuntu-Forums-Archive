---
title: "Gnome look &amp; feel"
date: 2008-07-14
forum: Desktop Environments
---

### Post by sr_guy on 2008-07-14
I installed unbuntu about two weeks ago. I've got most everything molded as far as software is concerned. However, the gnome desktop has more of a Win98 feel & look to is rather something a little more modern. 

Would I find a desktop theme from here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

or would there be another place?

---

### Post by o.besner on 2008-07-14
[http://www.gnome-look.org/](http://www.gnome-look.org/)

this is probably the best place to find what you're looking for.

Customizing a desktop seems like hard work at first, but it's not that bad once you've done it once or twice. 

One thing though : The best wallpapers are on DeviantArt ([http://www.deviantart.com/](http://www.deviantart.com/)), and not on Gnome look.

---

### Post by sayakb on 2008-07-14
See: Futurelooks thread in Desktop Effects and Customization and the Ubuntu customization link in my sig.

---

### Post by coffeecat on 2008-07-14
A few more tips:

Another gnome theme site:

[http://art.gnome.org/](http://art.gnome.org/)

I much prefer that to gnome-look. Install some Gtk engines and some Metacity (Window Border) themes. You'll be amazed at what you can do.

If you don't like the minimalist Gnome desktop that Ubuntu defaults to, and want Computer, home folder, trash icons on your desktop, go to System > Preferences > Main Menu. Find System Tools and tick Configuration Editor. You have to do this first step in order to get the Configuration Editor into the Main Menu. :roll:  Now go to Applications > System Tools > Configuration Editor. (We're almost there. :wink: ). Now, apps > nautilus > desktop. Tick whichever you want.

Lastly - defaults fonts in Ubuntu are **ghastly** imo. I hesitate here because if you put 12 Linux devotees in a room you'll get 36 opinions about font-rendering. Notwithstanding that, here are my suggestions. Firstly, go to Synaptic Package manager and install msttcorefonts. This will give you essentials like Times New Roman. Next, open a terminal (sorry) and type:

```
sudo dpkg-reconfigure fontconfig-config
```Intuitive, isn't it? Choose 'Autohinter' with the first question, and then 'Never' and 'No' for the next two. You have to logout and login (restart the X-server) to see the difference. If you don't like autohinting (a sort of Mac-esque effect rather than the gritty look of Windows), just run that command again and choose 'Native' for the first question. If you want to change your system fonts, go to System > Preferences > Appearance > Fonts. I prefer Verdana (one of the msttcorefonts) to the default Sans, but that's down to personal choice.

---

