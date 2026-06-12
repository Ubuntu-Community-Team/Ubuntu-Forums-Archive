---
title: "Nautilus and other application windows controls (Maximize, Minimize, Close)"
date: 2020-07-05
forum: Desktop Environments
---

### Post by mickee384 on 2020-07-05
Hi all!

I was changing desktop environments (ubuntu to Budgie and back) Budgie has the windows controls on the right. When I changed back to ubuntu the controls were mostly on the right. I tried changing the window titlebars using Gnome Tweak and switched window controls to left, now some are on the right others on the left. If I log into ubuntu wayland all controls are on the left. I'm running ubuntu 20.04. Any ideas? It may be that Gnome specific apps have controls on the right whereas other non gnome apps have them on the left. I looked in deconf and they show that the controls are set to the left hand side.

deconf:
/org/gnome/desktop/wm/preferences/button-layout

```
close,minimize,maximize:
```

---

### Post by gdesilva on 2020-07-07
Give this a try....

Open terminal and run

  	 	 	 	   gsettings set org.gnome.desktop.wm.preferences button-layout &#8220;menu:minimize,maximize,close&#8221;


The buttons on left should be defined on the left of ':' and buttons on right should be defined on the right side of ':'

---

### Post by mickee384 on 2020-07-07
Thanks for answering. I already tried that and it didn't fix this. VLC, Solitaire, Firefox, Thunderbird, Libre Office are on the left, looks like the majority are still on the right

---

### Post by mickee384 on 2020-08-09
so I have been quite unsuccessful in getting the windows controls to all move to the left. Still looking for help. Is this in the wrong forum? I think this is a very strange issue. It doesn't seem to matter what theme I use, If it allows me to place controls on the left the only windows that actually change them to the left are Thunderbird and Firefox. Strange indeed! I will gratefully appreciate the help. I tried to re install ubuntu but got a message that due to UEFI it may not boot, so I abandoned that. Does anyone have a possible reason for this?

---

### Post by Frogs Hair on 2020-08-09
Have you tried the  Budgie desktop settings ? Budgie is gnome based, but has its own settings application.

---

### Post by mickee384 on 2020-08-10
@Frogs Hair. I will look for those!

---

### Post by Frogs Hair on 2020-08-10
Should be under the windows tab.

---

### Post by mickee384 on 2020-08-13
do not have those settings

---

### Post by Frogs Hair on 2020-08-15
Search for budgie desktop settings. If you don't have them they can be installed. I have not budgie along side of gnome since 17.04 or 10 , so things may have changed.

---

### Post by mickee384 on 2020-08-15
I have budgie desktop settings but cannot access it. I uninstalled and reinstalled the application, but when I click launch, nothing happens. I also tried using Activities, type in budgie desktop but it doesn't show up at all?

---

### Post by Frogs Hair on 2020-08-15
Could be because you are running budgie as a second desktop. If  budgie is your primary DE you might just want to install Ubuntu Budgie 20.04.

---

### Post by mickee384 on 2020-08-15
It was pre-installed on my ubuntu 20.04 DE, When I booted into Budgie, it changed the boot up screen as well as loading the Budgie DE. I'm looking to stay with ubuntu.(Gnome). You think I should install Budgie and then use the desktop settings to change the windows controls then go back to Ubuntu? Thanks for your help, btw!

---

### Post by Frogs Hair on 2020-08-15
The budgie desktop is only default on Ubuntu Budgie. You would have had to add it to Ubuntu manually some how. If you want to use gnome then you might want to reinstall [Ubuntu]("https://ubuntu.com/download/desktop") because completely removing a second desktop environment is more time consuming. Your login screen changed because UB  uses slick greeter and gnome uses GDM.

---

### Post by mickee384 on 2020-08-16
You solved this for me! I logged into Budgie Desktop and did the button switch to left logged out and logged back into ubuntu and now its all fixed. Awesome! Thanks so much, Frogs Hair!

---

