---
title: "OpenGL"
date: 2005-01-29
forum: Gaming &amp; Leisure
---

### Post by peter_barb on 2005-01-29
Okay I am having troubles.. This guide [[http://digital-conquest.ath.cx/wiki/index.php/Cedega-howto#Configuring_Your_Computer_for_Cedega]](http://digital-conquest.ath.cx/wiki/index.php/Cedega-howto#Configuring_Your_Computer_for_Cedega]) says for me to do this..

"output will return "direct rendering:" If this is 'Yes' or 'Enabled' then OpenGL is likely set up correctly.  If it is  listed as 'no' or 'disabled' then double check your 3D setup. " - Mine says no  :-( 

And it says.. "The glxgears program will output an FPS (Frames Per Second) rating to the  command line.  If 3D acceleration is correctly enabled for your video card then the reported FPS should be well over 500 FPS, at the default window size. If the output shows less than 500 FPS then you should double check your 3D setup.".. mine is only running at 330.

You guys know a solution. I am running ATI Radeon 9600XT, and those new drivers don't work!

---

### Post by valadil on 2005-01-29
With that card you should easily be getting 5000-6000 fps.  I didn't see anything in that particular link about drivers for ati cards, so maybe another tutorial would be useful.  Have you installed any of the fglrx packages?

---

### Post by wallijonn on 2005-01-29
Peter,

Install the 3D drivers (see the FAQ section).

300fps is not too bad. There is no way you'll get 5000fps, though.

---

### Post by peter_barb on 2005-01-29
[QUOTE=wallijonn]Peter,

Install the 3D drivers (see the FAQ section).

300fps is not too bad. There is no way you'll get 5000fps, though.[/QUOTE]
 Yeah, I think I gots to install the 3d drivers, I will check the FAQ. Thanks guys!

---

### Post by valadil on 2005-01-29
[QUOTE=wallijonn]Peter,

Install the 3D drivers (see the FAQ section).

300fps is not too bad. There is no way you'll get 5000fps, though.[/QUOTE]

<01:21> valadil@mithrandir:~$ glxgears 
30859 frames in 5.0 seconds = 6171.800 FPS

That's on a GeForce5900fx, which is comprable to the 9600xt.  When I had a 9800pro I was getting over 7000.

---

### Post by Wertigon on 2005-01-29
[QUOTE=valadil]<01:21> valadil@mithrandir:~$ glxgears 
30859 frames in 5.0 seconds = 6171.800 FPS

That's on a GeForce5900fx, which is comprable to the 9600xt.  When I had a 9800pro I was getting over 7000.[/QUOTE]

Remember that nVidia cards got much better OpenGL drivers than aTi, atleast at the moment :(

---

### Post by peter_barb on 2005-01-29
[QUOTE=Wertigon]Remember that nVidia cards got much better OpenGL drivers than aTi, atleast at the moment :([/QUOTE]
 Okay when I run glxgears it says..

Xlib:  extension "XFree86-DRI" missing on display ":0.0". at the starting..... What does this mean? Also how do I configure my 3D settings so it is higher?

---

### Post by peter_barb on 2005-01-30
[QUOTE=peter_barb]Okay when I run glxgears it says..

Xlib:  extension "XFree86-DRI" missing on display ":0.0". at the starting..... What does this mean? Also how do I configure my 3D settings so it is higher?[/QUOTE]
 Okay I isntalled the fglrx control panel, how do I access it?

UPDATE:: Okay I found out how to do it, now I am just having problems with Cedega... it doesn't seem to want to launch an installer :@

---

