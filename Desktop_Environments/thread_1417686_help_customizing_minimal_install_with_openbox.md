---
title: "help customizing minimal install with openbox"
date: 2010-02-27
forum: Desktop Environments
---

### Post by Mykle87 on 2010-02-27
I have been using Ubuntu Desktop on my laptop for a couple of years now and absolutely love it. I also use Ubuntu Server on my server box and am learning so much about the command-line. For my laptop, I am starting to think that as great as Ubuntu is, it comes with a lot of stuff I don't need. What I would like to do is start with a minimal command-line only install and add Openbox to it because I really like the way Openbox looks and feels. What I am afraid of is not being able to do routine things on it such as connect to a wireless network with the click of a button. I know I have to install gnome-network-manager or wicd if I want to do that but I just want to make sure that this setup is still functional. What packages do you recommend I add? I think I would like to have the system menu from Gnome but maybe I don't need it? I would prefer to not have a login manager. What do you guys think? Have any of you done this? Thanks.

---

### Post by Tibuda on 2010-02-27
If you want something more out-of-the-openbox, I'd recommend you to try [Crunchbang]("http://crunchbanglinux.org/"), which is an Ubuntu derivative that uses Openbox. They have two flavors: Standard with more apps and Lite with only basic functionality. If this is not what you want, go the [Minibuntu route]("http://www.psychocats.net/ubuntu/minimal").


This guide covers almost everything you need to know about Openbox:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

> I know I have to install gnome-network-manager or wicd if I want to do that but I just want to make sure that this setup is still functional.
If you choose wicd, install the wicd package and add **wicd-client &** to your ~/.config/openbox/autostart.sh file. I recommend also to add a systray to that file, so you can see wicd/nm icon. urukrama guide covers it.

> I would prefer to not have a login manager. What do you guys think? Have any of you done this?
About the login manager, you can start x after the tty login, if you add the following to your ~/.bashrc: ([reference]("http://wiki.archlinux.org/index.php/Start_X_at_Boot"))
```
if [[ -z "$DISPLAY" ]] && [[ $(tty) = /dev/tty1 ]]; then
  startx
  logout
fi
```
it will run your ~/.xinitrc file, so create this file and add the following:
```
exec openbox-session
```

---

### Post by mkvnmtr on 2010-02-27
You have a point about Ubuntu coming with a lot of stuff I do not want or need. I like to use the ninimal install but I find it difficult to get all the little things to make it work like you want. For example what program are you going to install to mount automaticly USB sticks? What program do I install to get the ability to right click and have theoption to execute the file? Sometimes I get it right and sometimes not. You might try Crunchbang. It is built from a minimal install and uses open box and seems to give you a good start with almost no fluff. The only thing I found I did not like was gdm. I find it uses a good bit of resources for no purpose when i can log in from the command line. 
Try installing in virtual box and you can try a lot of options and just delete when you do not like it.

---

### Post by Tibuda on 2010-02-27
> **mkvnmtr said:**
> For example what program are you going to install to mount automaticly USB sticks?
Thunar or PCManFM

> What program do I install to get the ability to right click and have theoption to execute the file?
what?

---

### Post by Mykle87 on 2010-02-27
@danielrmt
Thanks for the help. I've read those links and I guess what I am most worried about is things like mounting usb drives and stuff. I guess I could just install the minimal and actually use it for a little while and if I can't get something to work, revert back to good ol' gnome.

@mkvnmtr
Its funny that you mention Virtualbox because that is exactly what I'm doing. I tried Crunchbang and I think it is ok but I don't think I would use it. I will keep building my virtualbox minimal install until I get it the way I like. Thanks.

---

### Post by Mykle87 on 2010-02-27
> **danielrmt said:**
> Thunar or PCManFM

Thunar can automatically mount usb drives? Good to know. I figured I would have to use Nautilus but I would rather use Thunar.

---

### Post by Tibuda on 2010-02-27
> **Mykle87 said:**
> Thunar can automatically mount usb drives? Good to know. I figured I would have to use Nautilus but I would rather use Thunar.
Yeah, you should start it as daemon in your openbox autostart.sh file.
```
thunar --daemon &
```
If you install thunar-volman, you'll be able to choose what to do when different kind of devices (cameras, video dvds, etc) are plugged.

---

### Post by Mykle87 on 2010-02-27
> **danielrmt said:**
> Yeah, you should start it as daemon in your openbox autostart.sh file.
```
thunar --daemon &
```

Thanks. What do you recommend for changing the resolution of the monitor?

---

### Post by Tibuda on 2010-02-27
> **Mykle87 said:**
> Thanks. What do you recommend for changing the resolution of the monitor?

lxrandr

Also, to install proprietary drivers, install jockey-gtk.

---

### Post by Mykle87 on 2010-02-27
> **danielrmt said:**
> lxrandr

Also, to install proprietary drivers, install jockey-gtk.

Ok great. Anything else you can think of? I am certainly not as worried as I once was about going minimal.

---

### Post by Tibuda on 2010-02-27
> **Mykle87 said:**
> Ok great. Anything else you can think of? I am certainly not as worried as I once was about going minimal.

Here's a list with some core functionality:
nitrogen to set a wallpaper
tint2 to get a taskbar
xcompmgr to have compositing
gmrun to launch different apps (you have to add a key binding to it)
obmenu to edit the openbox menu
obconf to edit openbox settings
lxappearance to edit your gtk and icon themes

---

### Post by Mykle87 on 2010-02-27
> **danielrmt said:**
> Here's a list with some core functionality:
nitrogen to set a wallpaper
tint2 to get a taskbar
xcompmgr to have compositing
gmrun to launch different apps (you have to add a key binding to it)
obmenu to edit the openbox menu
obconf to edit openbox settings
lxappearance to edit your gtk and icon themes

Thanks for the list. I have read about all those applications and understand they are what I need. Once that is all setup, I'll add OpenOffice, Firefox, Pidgin, etc. whatever else I use on a daily basis. Thanks again for all your help.

---

### Post by Tibuda on 2010-02-27
> **Mykle87 said:**
> Thanks for the list. I have read about all those applications and understand they are what I need. Once that is all setup, I'll add OpenOffice, Firefox, Pidgin, etc. whatever else I use on a daily basis. Thanks again for all your help.

glad to help :)

---

### Post by Tibuda on 2010-02-27
I should also recommend you to not install the tint2 from ubuntu repositories, but from the devs PPA:
[http://code.google.com/p/tint2/wiki/Install#For_Ubuntu_9.10_%28Karmic%29](http://code.google.com/p/tint2/wiki/Install#For_Ubuntu_9.10_%28Karmic%29)

---

