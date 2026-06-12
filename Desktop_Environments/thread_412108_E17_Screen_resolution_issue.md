---
title: "E17 Screen resolution issue"
date: 2007-04-17
forum: Desktop Environments
---

### Post by DeathStar on 2007-04-17
Hi All,

I am having a problem with my screen resolution when using E17.

My resolution is set to 1600 x 1200, so it's quite high. The problem is that when I open applications that aren't part of E17 (Gnome applications for example) then they seem to display at a lower resolution. by this, I mean that the text and button are quite large.

A good example of this is Open Office Writer. When I open it, everything looks huge (as if running a lower resolution). I have to manually go into the menu and change the UI to 80%. In Gnome, it work fine.

Has anyone else had, or heard of this problem. Does anyone know if it can be corrected?

Thanks,
DS.

---

### Post by markupstart on 2007-04-18
see post below

---

### Post by markupstart on 2007-04-18
I had a similar problem, only in openoffice.  I had to install "openoffice.org-gtk" package and it fixed it right up.

But I also created my own .gtkrc-2.0, which looks like below.

gtk-font-name = "Bitstream Vera Sans 10"
gtk-theme-name = "Whitey"
gtk-icon-theme-name = "Tangerine"
 


You can use any gtk theme and icon set, just change those lines to something you have/use.

---

### Post by DeathStar on 2007-04-19
Hi Markupstart,

Thanks for you help, but I am a bit unsure as to what you mean.

The only place I found any gtk files was in /etc/gtk.

I created a file called gtkrc-2.0 exactly as you had, but then what do I do with it?

Cheers,
DS

---

### Post by RedSquirrel on 2007-04-19
Note that the file is named .gtkrc-2.0 **(with a dot in front)**.

You just place it in your home directory, that is, in **/home/yourusername**

Unless you know you have installed the theme "Whitey" and the icon them "Tangerine", I would start with more traditional ones, such as IndustrialTango (theme) and Tango (for icons), but you can use whatever you like as long as you install the themes you specify in .gtkrc-2.0.

Did you try installing the **openoffice.org-gtk** package first to see if that helped? (Using Synaptic, for instance.)

---

### Post by DeathStar on 2007-04-20
Hi RedSquirrel,

Thanks fo the help. I have moved this file, renamed it and now it looks much nicer.

I know it was only an aesthetic bug, but it was annoying me. Now I am enjoying my enlightenment experience even more!

And Thank you to MarkUpstart for his initial reply.

Thanks again,
DS
:)

---

### Post by RedSquirrel on 2007-04-20
Yeah, interface issues like that can be annoying to look at day after day. Glad you got it looking nicer. :)

---

### Post by markupstart on 2007-04-20
Yes, plus E17 looks so nice, you hate to have a few programs look bad.


> **RedSquirrel said:**
> Yeah, interface issues like that can be annoying to look at day after day. Glad you got it looking nicer. :)

---

### Post by toylas on 2007-05-20
Hi all,

This is not exactly related to Ubuntu but is related to Enlightenment and X in general. I have a really old desktop on which I have installed Elive. The problem is that enlightenment does not seem to consider higher resolutions for the monitor. My xorg.cof has all the resolutions specified

#####################################################################
.
.Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc 3D Rage I/II 215GT [Mach64 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

.
.
.
#######################################################################

But when I log into enlightenment, it comes up only in 800x600. When I try to change it from configuration panel,
it gives me options only for 800x600 & 640x480. I've searched a lot over the net but the only things I could find were modifying the xorg.conf but that does not seem to work for me (maybe I'm missing something here). Any suggestions or pointers will be great help.

Thanks,
Tulasi

---

