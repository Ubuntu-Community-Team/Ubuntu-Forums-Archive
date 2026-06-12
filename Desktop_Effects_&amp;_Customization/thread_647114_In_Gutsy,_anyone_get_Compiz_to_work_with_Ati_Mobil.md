---
title: "In Gutsy, anyone get Compiz to work with Ati Mobility Radeon out of the box?"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by tepidarium on 2007-12-22
Did anyone?  I have the Ati x1400, just wondering if it's easy to get Compiz to run.  

Thanks.

---

### Post by hollaburoo on 2007-12-22
You can get it to run easily using XGL but its not quite as nice.
I'm holding off on compiz right now, I'm waiting for Hardy when it should work as well as with nvidias.

---

### Post by peitschie on 2007-12-22
I got it running using this guide: [http://ubuntuforums.org/showpost.php?p=3547657&postcount=7]("http://ubuntuforums.org/showpost.php?p=3547657&postcount=7")

---

### Post by twist2b on 2007-12-22
i forgot were... but theres a official compiz guide that worked for me (i dont have your compy) just saying.... all the others didnt work for me but that one just worked on a dime

---

### Post by Afkpuz on 2007-12-22
I have an x700 Mobility and all I had to do was install restricted driver and then xgl-server.  Card works great after restricted driver and xgl install, but not "out of the box" per se.

---

### Post by tepidarium on 2007-12-23
Thanks for the responses. I guess I should have qualified my question.  I've currently got Feisty and Beryl working using XGL.  I'm wondering if I do a fresh install of Gutsy, download the new ATi drivers releases on December 20 and install....will Compiz work on AIGLX on my system...

---

### Post by peitschie on 2007-12-23
It *may* work with AIGLX... I found mine wanted to use xgl by default though.  A quick internet search and about 2mins of tweaking fixed that (I can supply a link if you want) so it ran using AIGLX.

But definitely, fresh install Gutsy, I would recommend using the albertomilone Envy scripts ([http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")) to get the latest ATI drivers (He just updated on Dec22nd)... Then boot up and appreciate compiz fusion! :)

---

### Post by dizee on 2007-12-23
I used Envy to install the fglrx drivers, the Restricted Drivers Manager in Gutsy didn't work for my Radeon Xpress 200M unfortunately.

Using XGL for Compiz, not sure if there's AIGLX support for my graphics card yet.

---

### Post by adam.tropics on 2007-12-24
> **dizee said:**
> I used Envy to install the fglrx drivers, the Restricted Drivers Manager in Gutsy didn't work for my Radeon Xpress 200M unfortunately.

Using XGL for Compiz, not sure if there's AIGLX support for my graphics card yet.

Just so you know, yes there is. Not perfect, firefox has scrolling problems, but still worth the change.

---

### Post by shareMenaPeace on 2007-12-24
i got a xpress 200, but wonder what means 
Atheros Hardware Access Layer(HAL) Do i need this?
And as someone above mentioned, can i just enter aiglx into the xorg.conf instead of flglx?

---

### Post by adam.tropics on 2007-12-24
The atheros is related to your wireless networking, so if you use that, yes, you need it.

Leave fglrx where it is, and add or check you have, or edit (whatever!) in /etc/X11/xorg.conf the following...
```

Section "Extensions"
    Option "Composite" "1"
EndSection

Section "ServerFlags"
    Option "AIGLX" "on"
EndSection

Section "DRI"
    Mode         0666
EndSection
```This assumes you have the latest drivers. [Download here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.443.1-x86.x86_64.run")....[Install guide here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"), method 2.

---

### Post by shareMenaPeace on 2007-12-24
Hmm i teste daround ... i get it working with envy but iuninstalled it ..and enabled restricted drivers, which now shows enabled but not installed in status ...tried reinstall with synaptic but no luck  so can i just start with this method 2 from your link? Or shoudl i uninstall everything as mentioned in the other link with the feisty upgrade, which would be bad as i had much configured so far... i mean this uninstall instructions ..do i realyl have to do this? 

.[http://ubuntuforums.org/showthread.php?p=3547657#post3547657](http://ubuntuforums.org/showthread.php?p=3547657#post3547657)

---

### Post by adam.tropics on 2007-12-24
Just had a look, and the [new envy has]("http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb") the right drivers, so you could just install that, enable aiglx and composite as posted above, in your xorg.conf, then install compiz etc...if you haven't already.

---

### Post by shareMenaPeace on 2007-12-24
Thx i will try this now, as the method 2 howto gave me a cache permission error .... tried sudo too ...

---

### Post by shareMenaPeace on 2007-12-25
works again ..i have to run tsts now to see if this is more stable and better performance than just fglrx before :)

Ty very much adam!

:popcorn:

---

### Post by shareMenaPeace on 2007-12-25
currently kiba + screenlets and compiz :) hihi

---

### Post by adam.tropics on 2007-12-25
> **shareMenaPeace said:**
> currently kiba + screenlets and compiz :) hihi

Good for you. Merry Christmas. (Never did make my mind up with regards to screenlets...may try them again)

---

### Post by shareMenaPeace on 2007-12-25
Well its not very much yet, in compare to vista desklets or what they called, but i hoep they become better.... but maybe they work better now wher ei got the better driver .... testing :)

---

### Post by shareMenaPeace on 2007-12-25
moment i make a video :)

---

### Post by hilariousness16 on 2007-12-25
sharemenapeace, you kinda ditched me -.- lol

---

### Post by shareMenaPeace on 2007-12-25
What do you mean?
Did you got it working, use envy than add the above code to the corg.conf!

Its much better ...

btw the video has to wait a little i post later :)

:guitar:

Cheers

---

### Post by hilariousness16 on 2007-12-25
Well, it's working, but I am getting some other issues, look at my thread please god, I mean sharemena:lolflag:

---

### Post by adam.tropics on 2007-12-25
> **hilariousness16 said:**
> Well, it's working, but I am getting some other issues, look at my thread please god, I mean sharemena:lolflag:


lol which one....you seem to be posting multiples...make a decision, pick a favourite!!

---

