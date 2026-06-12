---
title: "Personal summary of installing and enabling Beryl in Feisty"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by chunchengch on 2007-04-30
After many times trial and error, I enable Beryl running gorgeously on my laptop an hour ago, I am glad to share all of these with who need it!


1. Open a terminal. copy and paste all the following text into the Terminal in one action. [Select all the text. Then middle button click in terminal]


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.beryl-script
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup.beryl-script
echo "deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main" | sudo tee -a /etc/apt/sources.list
wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install beryl beryl-manager emerald-themes
sudo nvidia-xconfig --add-argb-glx-visuals
sudo cp /usr/share/applications/beryl-manager.desktop /etc/xdg/autostart/beryl-manager.desktop
cp /usr/share/applications/beryl-manager.desktop ~/Desktop/beryl-manager.desktop
echo -e "Logout now and then press \e[0;31mCTRL+ALT+BACKSPACE\e[0m to restart xorg"
echo "Installation completed !"


2. Now Logout and then press [CTRL+ALT+BACKSPACE] to restart xorg
3. Open a terminal and type "beryl-manager" to install Beryl Manager
4. Adding a startup script to the GNOME Desktop Environment

System > Preferences > Sessions
Click on the "Startup Programs" tab and subsequently click "add."
Type "beryl-manager" into the text field, and click on "OK".

5. Restart Ubuntu and enjoy Beryl.



reference: " Install Beryl on Ubuntu Feisty with nVidia
From Beryl Wiki"

---

### Post by rolf-c on 2007-04-30
This seems to work pretty well as long as the nVidia card is new enough.  On one box I had to install a legacy nVidia driver (not hard to do).

---

### Post by chunchengch on 2007-04-30
I have nVidia GEFORCE GO 7300 (128MB) in my laptop

---

### Post by rolf-c on 2007-04-30
I have a GeForce 4200 Ti in one desktop and used the nVidia 9631 driver.

---

### Post by Weezer on 2007-04-30
Thanks man, this worked for me.

(If it's helpful, I'm running the AMD64 version and have an nvidia 7950GT)


...*boing*

---

### Post by chunchengch on 2007-05-01
I find there are many threads complaining or looking for help for using Beryl, however I do enjoy the desktop effects Beryl provides, although sometimes (in fact rarely) it starts without window border or blank desktop, I just need to restart my Feisty Fawn and then everything goes fine. If you are using a nVidia card and Ubuntu 7.04, I recommend you to follow the instructions above to install Beryl, it really works!

---

### Post by marlinnhag on 2007-05-02
SO I did the above and the manager is installed I went through selected a theme from emerald and chose some effects I want ( the water one is what I really want) but nothing has changed I dont see a difference at all in the way things look)

Any suggestions???

---

### Post by chunchengch on 2007-05-02
I had the same question before, but this morning while I was using OpenOffice.org Spreadsheet, the water effect appeared when I tried to delete a sheet or to close a file or to click on side bar of a color-selection window, so I realize that some effects will pop out when something activates it, it is amazing for a Linux newbie like me.:)

---

### Post by marlinnhag on 2007-05-02
Just saw this post below on Craigslist.org (no one helped him) and it is the exact issue I am having.... Maybe this is a better description of my problem:

[COLOR="Blue"]Im stuck though. as to how to use it. I cant switch over to it from the "gnome manger?" that ununuts using. I actually get to a selections where i can choose beryl or metacity (Gnome Window Manger). The option is on metacity by default. So i select Beryl. And it looks like the monitor flickers, the windows do a little dance, as if a windows manager just switch. But no. After everything flickers. The tab is still on Metacity, instantly. So now. I tried to use some of the binded ALT+F keys to see if beryl is reactive. And nope. Just as it indicates Metacity is still in charge of my window enviornment. Whatdo I do?[/COLOR]

---

### Post by chunchengch on 2007-05-02
right click on the Beryl Manager icon (a ruby gem) on right upper side of the desktop, and click on "select Desktop Manager" (see remark) and select "Beryl", 

Remark: as I use Traditional-Chinese Ubuntu, maybe the menu titles in English are somewhat different to what I mentioned.

---

### Post by marlinnhag on 2007-05-02
That is what I do when the screen just flashs and then it is back to the original setting when I go back and look at it...

---

### Post by firecat53 on 2007-05-02
Maybe slightly easier way for Feisty nVidia users

sudo aptitude install beryl beryl-ubuntu emerald emerald-themes   (these are already in the feisty repositories)
sudo nvidia-xconfig -composite; sudo nvidia-xconfig -allow-glx-with-composite
 sudo nvidia-xconfig -render-accel; sudo nvidia-xconfig --add-argb-glx-visuals   (automatically backs up xorg.conf)
Ctrl-alt-backspace to restart X

Applications -> System Tools -> Beryl Manager
Add to startup sessions if desired and....

Enjoy :)

Scott

Note see:[ http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia]("http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia") for more info, if needed.

---

### Post by jackmorelli on 2007-05-03
Hi,  I'm running ubuntu feisty with kde, and i did everything specified above to get beryl to work.  i think typed "beryl" in my console, and low and behold beryl works great.  awesome.

my konsole, however, prints out "reloading options" as the last line and doesn't return me to prompt.  if i exit out of it, everything crashes.  suggestions?

much thanks,
jack

---

### Post by jackmorelli on 2007-05-03
Also,  one other thing, my resolution drops down from 1440x900 to 1024x680, and if i try to upgrade the resolution, i get weird fuzzy spots at the top and left side of my screen.

thanks,
jack

---

### Post by joshlindsay on 2007-05-03
Im having trouble installing the NVIDIA driver on a HP DV6000 with a Go 7400.. When I click enable in the Restricted Drivers Window the window goes gray for around 5 seconds then reverts back to normal without installing anything.

I see that chunchengch is using a Go 7300... Just wondering if you have any advice on how to fix my problem.

Thanks

Josh

---

### Post by chunchengch on 2007-05-03
Hi Josh,

I am just a Linux newbie and still learning how to solve lots of hardware compatibility problems, I am afraid that I am unable to give you any suggestion, however, as I tried before, I suppose that if you re-install Beryl according to the procedures mentioned above instead of just installing nVidia driver will probably make everything works.

---

### Post by TekNullOG on 2007-05-04
> **marlinnhag said:**
> SO I did the above and the manager is installed I went through selected a theme from emerald and chose some effects I want ( the water one is what I really want) but nothing has changed I dont see a difference at all in the way things look)

Any suggestions???

I have the same problem. Everything is installed but when I select a theme and then hit Reload Window Decorator, nothing happens. Beryl is properly selected.

I can still switch between the built in themes. Just not the emerald ones.

I have an ATI X300 video card on an IBM T43. I use the ATI drivers (not the open source ones) Any suggestions?

Thanks in advance

---

### Post by chunchengch on 2007-05-24
share some Beryl 3D effects of my laptop.

---

### Post by bobandirus on 2007-08-25
goodness knows how, because i have intell inbuilt grafix, but that code worked! thank you so much!!!!

---

### Post by TennesseeAborigine on 2007-08-26
chunchengch,

Thanks, your code worked flawlessly. I used it on a fresh ubuntu install and update. i had also configured the restricted drivers on my nvidia 6200 video card. no disappearing title bars or anything!\\:D/  

now to install wine[-o<

---

