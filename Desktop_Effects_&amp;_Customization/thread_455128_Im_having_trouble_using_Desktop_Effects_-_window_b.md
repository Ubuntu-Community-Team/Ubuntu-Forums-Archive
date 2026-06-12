---
title: "Im having trouble using Desktop Effects - window borders (that you drag with) GONE"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by bishop9226 on 2007-05-26
When I turn selectwindows effects, even if i dont check any of the options off for the multiple cube workspace or for wobble effect, all the windows get rid of their title page, see pics below. doesnt matter waht is checked. the wobble works because some of the little yellow popup windows would wobble, but why isnt the rest of it working:

thanks a lot, id appreciate it

---

### Post by Kobalt on 2007-05-26
You might want to check [this]("http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29") out.

---

### Post by bishop9226 on 2007-05-26
thanks ill look at that but i dont even have beryl on there yet. i got the x86 version of ubuntu for my laptop's intel core duo with geforce go 7300.  i had no problem with it on my desktop's onboard nvidia geforce 6100 series 
see, 

[IMG]http://www.geocities.com/missthighs2xl/screenshot.png[/IMG]

[IMG]http://www.geocities.com/missthighs2xl/screenshot2.png[/IMG]

---

### Post by screaminj3sus on 2007-05-26
Same thing happened to me using the built in one bishop, use this step from the link above

5. Add this entry in ' Section "Screen" ' :

 Option "AddARGBGLXVisuals" "True"

I had to add that to the xorg.conf

---

### Post by Irishpolyglot on 2007-05-26
I'm having exactly the same problem. I tried adding > Option "AddARGBGLXVisuals" "True" to the xorg.conf and it didn't make any difference. The rest of the steps from Kobalt's link were already implemented in the xorg conf. I'm on a DELL 9400 with Nvidia 256MB GeForce Go 7900.

---

