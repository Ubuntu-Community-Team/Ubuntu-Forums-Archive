---
title: "Problem with xorg.conf and virtual resolution"
date: 2009-04-30
forum: General Help
---

### Post by ipressthebuttons on 2009-04-30
The default virtual resolution is 1600x1200, meaning no matter what I change my resolution to using the "display" item, it won't help. It'll either mess up the screen, or stay 1600x1200.

Once upon a time I managed to edit xorg.conf and added a subsection and changed my virtual resolution to 1280 x 768 (my laptop's resolution) and it fixed the screen perfectly. The idiot I am, however, I managed to edit something and screw this up... and to add to the pain, I forgot exactly what I put into xorg.conf, and if I don't put in the right thing it messes the screen up even more.

As I recall it was a subsection, and it I remember it listed all the modes available on it, and under it was "VirtualResolution 1280 768"

Also, I recall it being about a gateway laptop. My laptop's Model is MX3215, and I recall that being in the google search I used to find the page that helped me edit my xorg.conf properly... but I CAN'T seem to find that page a second time

This is about as detailed as I can get at the moment... 

so essentially, my problem was solved but I forgot how and I need people to either help refresh my memory or help find the page I used (I believe it was a blog)

---

### Post by ipressthebuttons on 2009-04-30
Help. I can't use my operating system because I can't SEE IT ALL.

---

### Post by ipressthebuttons on 2009-04-30
> **ipressthebuttons said:**
> Help. I can't use my operating system because I can't SEE IT ALL.
^^^

---

### Post by ipressthebuttons on 2009-04-30
> **ipressthebuttons said:**
> ^^^
^^^

---

### Post by jcm1107 on 2009-05-01
what is your system hardware? I especially want to know what graphics card you have and motherboard. Is this on a laptop?

---

### Post by ipressthebuttons on 2009-05-01
> **jcm1107 said:**
> what is your system hardware? I especially want to know what graphics card you have and motherboard. Is this on a laptop?
[http://support.gateway.com/support/srt/docs.asp?sn=N636111054262](http://support.gateway.com/support/srt/docs.asp?sn=N636111054262) does this page load?

Aside from that...
no idea how to find out my graphics card.

---

### Post by ipressthebuttons on 2009-05-01
bump

---

### Post by ipressthebuttons on 2009-05-01
bump

---

### Post by ipressthebuttons on 2009-05-01
bump

---

### Post by ipressthebuttons on 2009-05-01
help

---

### Post by Legace on 2009-05-01
Add this to the Screen section of the xorg.conf file:

```

    SubSection "Display"
        Depth        24
        Modes      "1280x768"
        Virtual 1280 768
    EndSubSection

```



End result of the Screen section should be something like (this is for my display, DO NOT COPY):
```

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes   "1024x600" "800x600" "640x480"
                Virtual 2048 2048
        EndSubSection
EndSection

```

And please don't bump that often :)

---

### Post by jcm1107 on 2009-05-03
Try going to System-admin-synaptic package manager
search for S3 graphics click on the box next to lsb-graphics to mark for installation and click apply.I am not for sure about this though I googled your laptop modle and found someone saying that is what their laptop had for integrated graphics. 

Use at your own risk I am not an expert I just see no one is helping and so I am trying to help

---

