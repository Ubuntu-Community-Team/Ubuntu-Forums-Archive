---
title: "GDM Themes and 10.10"
date: 2011-02-16
forum: Desktop Environments
---

### Post by Raindance on 2011-02-16
Hey all!

Sorry if this is posted anywhere, I didn't get the memo...

So, I'm an Ubuntu rookie, not very familiar with it. I wanted to get a few new themes, splashes, and login screens going, but I cannot for the life of me get them to work. After about a half hour of goggle'ing and several failed methods, I decided to try here. 

How go I get;
a) Login Screens installed,
b) A different splash/loading screen on startup going?

Thanks for your time!

---

### Post by jerrrys on 2011-02-17
check here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+login+screen&as_qdr=all&sa=Google+Search&lang=en#847](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+login+screen&as_qdr=all&sa=Google+Search&lang=en#847)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+splash+screen&as_qdr=all&sa=Google+Search&lang=en#909](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+splash+screen&as_qdr=all&sa=Google+Search&lang=en#909)

---

### Post by Krytarik on 2011-02-17
It's currently not possible to set a special look to the login screen as it was in earlier releases of Ubuntu. But you can change all the settings you know from your own "Appearance" dialog, except from those in the "Visual Effects" tab:

- copy "/usr/share/applications/gnome-appearance-properties.desktop" into "/usr/share/gdm/autostart/LoginWindow"
- logout
- change the settings, make sure to re-select "LoginIcons" in the "Customize" dialog in "Themes"
- login
- remove the file again
detailed commands: [http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

Regarding the look of the boot menu, I use the purple background image of those pack:
[http://gnome-look.org/content/show.php/Grub2+Splash+Image+?content=125657](http://gnome-look.org/content/show.php/Grub2+Splash+Image+?content=125657)

Guides to modify its look:
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming]("https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming")
[http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Splashimages.html")

To change the boot splash, just go to gnome-look.org, choose one of the few splash themes and follow its included instructions, my favorite is this one:
[http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696](http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696)

There is also a very popular one in the official repos, called "Solar", package "plymouth-theme-solar", commands to choose the theme after the install:
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

---

### Post by Copper Bezel on 2011-02-17
> There is currently no way to use a special login screen look, you only can change the usual settings you see also in your own "Appearance" dialog, apart from the "Visual Effects":

Wow, that's a really interesting and weird process for it. 

He said he's new, though - it's really a lot easier with, you know, the login window customization package.

[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

---

### Post by jerrrys on 2011-02-17
> **Copper Bezel said:**
> it's really a lot easier with, you know, the login window customization package.

[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

nice package

---

### Post by Krytarik on 2011-02-17
I also have gdm2setup installed, but I don't recommend using it, and I also don't wont to check right now if all options are also available in it. Since everytime I use it, it screws up my GDM config, and I have to edit it manually after running it. Is that what you call easy?! ;)

---

### Post by Copper Bezel on 2011-02-17
Oh wow, no, I didn't realize. I've never had that problem!

... Maybe just Ubuntu-Tweak, then? = )

---

### Post by Krytarik on 2011-02-17
> **Copper Bezel said:**
> Oh wow, no, I didn't realize. I've never had that problem!
Maybe because you don't use autologin?
> **Copper Bezel said:**
> ... Maybe just Ubuntu-Tweak, then? = )
With Ubuntu-Tweak you can only set the background and the logo.

---

### Post by Copper Bezel on 2011-02-18
Strangely, I *do* use auto-login. But you're scaring me now, because I've only rebooted like once since installing gdm2setup and tweaking my login screen. = ) (Presently having fun with the whole, "how long can you run your Linux system without rebooting," thing.)

---

### Post by Krytarik on 2011-02-18
> Strangely, I do use auto-login. But you're scaring me now, because I've only rebooted like once since installing gdm2setup and tweaking my login screen. = ) (Presently having fun with the whole, "how long can you run your Linux system without rebooting," thing.)
LOL.:D I usually, but more rarely, run my system two 2 days in a row, yesterday for example.

As preventive help, here is my "/etc/gdm/custom.conf", gdm2setup (at least at my system) adds all the entries another time, but with different cases in the names:
```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=krytarik
AutomaticLogin=krytarik
TimedLoginDelay=30
DefaultSession=gnome
```

---

### Post by Copper Bezel on 2011-02-18
Oh wow, my cases *are* off. Thanks!

Edit: Editing from GDM2 re-wrote the whole file, but editing from the normal Login Window options appended my settings from GDM2 instead of replacing them. I'm a little worried about what would have happened if both sets of keys were in there. Thanks again!

---

### Post by Krytarik on 2011-02-18
> **Copper Bezel said:**
> Oh wow, my cases *are* off. Thanks!

Edit: Editing from GDM2 re-wrote the whole file, but editing from the normal Login Window options appended my settings from GDM2 instead of replacing them. I'm a little worried about what would have happened if both sets of keys were in there. Thanks again!
Nothing aside that autologin won't work, I had it that way at least two times on boot. I believe it's because of the different cases in the words, then those entries are not matched when modified again after gdm2setup wrote the file, like the "sed" command works.

---

### Post by MarkoCro on 2011-03-04
I have solution for changing GDM Gnome theme, fonts and wallpaper here:

[http://www.techytalk.info/ubuntu-debian-gdm-login-screen-theme-wallpaper/](http://www.techytalk.info/ubuntu-debian-gdm-login-screen-theme-wallpaper/)

---

### Post by doctortonic on 2011-04-15
It is very strange.

I installed ubuntu (lucid or maverick)then:

 sudo apt-get install kubuntu-desktop
 sudo update-alternatives --config default.plymouth
 switched with kububuntu bootscreen/spalsh manually option
 sudo update-initramfs -u

reboot

The effect was a **Dark Blue** kubuntu splash.

Then I formated partitions, installed kubuntu but, I was having a 
**Light blue** splash screen.

_________

Installed ubuntu (maverick)again.

Installed kubuntu polymonth & some art/themes related (not all kubuntu-desktop package) and here comes:

Configured polymonth to start kubuntu splash, 
and at Shutdown the screen was with DARK Blue, 
and at start-up with **LIGHT blue**.
Restarted again, and now remains **LIGHT blue**.

What is happening? I like the darker version better.

Edit 1:

Now it's like this: [http://t0.gstatic.com/images?q=tbn:ANd9GcSOoGgWcduUoqNfhP_NeR_cVFfIGC2C08akC8VQWHmpTgrNA0ALkw]("http://t0.gstatic.com/images?q=tbn:ANd9GcSOoGgWcduUoqNfhP_NeR_cVFfIGC2C08akC8VQWHmpTgrNA0ALkw")
 
There is a little diffrence between the shades, and I can't figure out why, is there some settings in gdm / themes or in the maverick / lucid or in installing ubuntu and apt-get install kubuntu desktop vs. installing kubuntu and apt-get install ubuntu-desktop

My first kubuntu was looking like this: [http://www.itouchwallpaper.com/images/big/blue-2.jpg]("http://www.itouchwallpaper.com/images/big/blue-2.jpg")

---

### Post by Krytarik on 2011-04-15
@doctortonic: Did you already upgrade your packages after the installation!?

This is the relevant part of the "kubuntu-logo.script":

/lib/plymouth/themes/kubuntu-logo/kubuntu-logo.script:
```
# Previous background colour
# #300a24 --> 0.19, 0.04, 0.14
# New background colour
# #2c001e --> 0.16, 0.00, 0.12
# Ubuntu background color
#Window.SetBackgroundTopColor (0.16, 0.00, 0.12);     # Nice colour on top of the screen fading to
#Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  # an equally nice colour on the bottom

bits_per_pixel = Window.GetBitsPerPixel ();
if (bits_per_pixel == 4) {
    Window.SetBackgroundTopColor (0.00, 0.28, 0.45);
    Window.SetBackgroundBottomColor (0.00, 0.28, 0.45);
    logo_filename = "kubuntu_logo16.png";
    progress_dot_off_filename = "progress_dot_off16.png";
    progress_dot_on_filename = "progress_dot_on16.png";
    password_field_filename = "password_field16.png";
} else {
    Window.SetBackgroundTopColor (0.00, 0.47, 0.76);
    Window.SetBackgroundBottomColor (0.00, 0.00, 0.00);
    logo_filename = "kubuntu_logo.png";
    progress_dot_off_filename = "progress_dot_off.png";
    progress_dot_on_filename = "progress_dot_on.png";
    password_field_filename = "password_field.png";
}
```You see that there *was* indeed a non-gradient, lighter version previously.

Greetings.

---

