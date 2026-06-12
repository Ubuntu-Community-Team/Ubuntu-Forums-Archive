---
title: "Conky still doesn't work"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by Tavorisch on 2007-07-05
All my xorg.conf say load "dbe" placed correctly, and I know I'm editing the right one. because i was able to force direct rendering upon the card.. This is how I downloaded conky.. just the regular one line install command, and than conky all from "username"@computername so... patrick@laptop  and conky opens up and works. but its a window in and of it self and matches the backround for a couple seconds than flickers to gray, mean while it hangs at drawing double buffer... I have placed many conkyrc files in the home and don't seem to change a thing about how it acts... howver when i run it from root@laptop is semi works and is imprinted in the bottom left.... but flickers..  I have the latest X11 drivers,   direct rendering and SGI in the glxinfo | grep etc. command.....  Conky has been harder to get working than packet injection WTF?! everytime i also played with conky it seems like it creates a new conf in the X11  folder with an extra ~ on the filename..  thus beryl screws up.. So i have completely uninstalled beryl and all its components and am starting from scratch to get conky working first! someone please help me for the love of god hehe.. most frusterating eye candy tool ever.. what is the exact filename of the conkyrc, how do i get conky to use it? is this even possible on my ATI radeon 9600  mobileif i got beryl working in 1600x1024 just fine.. conky should be easy right? anyway thank you so much in advance.

---

### Post by Tavorisch on 2007-07-05
okay i have placed the conkyrc file in every thinkable place... still nothing
when in terminal under root if i type conkyrc i get /usr/bin/conkyrc Permission denied.
pretty positive i placed that file there, but why would it go to that one? is the bin the list of commands in terminal?? if it is oops haha i have no idea what im doing.
also I think i may have created this but under my home directory, i have a conkyrcbackup and also a conkyrcbackup~ i may have created those throughout this 4 day endeavor as well.

---

### Post by Alex Fernandez on 2007-07-05
~/.conkyrc is the config file
/usr/bin/conky is the executable

---

### Post by Nythain on 2007-07-05
and dont forget to edit your ~/.conkyrc and enable double buffering in it too... just enabling it in xorg doesnt do much except allow you to use it... now you have to tell conky to use it... you can forum search for conkyrc and get loads and loads of example conkyrc setups

---

### Post by orb9220 on 2007-07-05
This is mine which solved the flicker problem.

> # This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
#own_window no
#own_window yes
#own_window_type override
#own_window_transparent 1

own_window yes
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer Yes

My xorg.conf
> 
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
   ** Load           "dbe"**
    Load           "dri"


Hope that helps.

---

