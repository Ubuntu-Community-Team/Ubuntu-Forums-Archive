---
title: "Where to place -- Option         &quot;Coolbits&quot; &quot;4&quot; -- This is for fan control"
date: 2017-01-03
forum: Desktop Environments
---

### Post by angel-sosa on 2017-01-03
Hi Everyone,

  This question has been answered in the traditional sense but I don't believe there is an up to date answer that fits how Ubuntu is working with X currently. I see that the xorg.conf has gone away and is broken up into smaller subsection inside of "/usr/share/X11/xorg.conf.d/". This is my request, has anyone tried to place the  following option --- Option         "Coolbits" "4" --- in a seperate file inside of "/usr/share/X11/xorg.conf.d/" so that it follows Ubuntu current standards. Ultimately it so that the fans can be controlled via  the command line and through nvidia-settings. 

The only way I was able to get this to work is as follows and is the traditional answer:

1. Load the proprietary NVIDIA drivers
2. Run nvidia-xconfig -- which creates the following xorg.conf in the /etc/X11 directory 

3. Then I added the following statement --- Option         "Coolbits" "4" --- with out the dashes to xorg.conf to the Section "Screen"

             Section "Screen"
                    Identifier     "Screen0"
                     Device         "Device0"
                     Monitor        "Monitor0"
                    DefaultDepth    24
                    **Option         "Coolbits" "4"**
                    SubSection     "Display"
                        Depth       24
                    EndSubSection
        EndSection

4. Rebooted 
5. I was able to manipulate the on board fans on my GeForce GTX 970 video controller.

Creating an /etc/X11/xorg.conf is counter intuitive to how Ubuntu wants to deal with "X". I would like to avoid taking this route and I would like to follow how Ubuntu is moving forward with "X". In the end everyone will have the most up to date method when it comes to Nvidia video controllers 

Thanks In advance

---

