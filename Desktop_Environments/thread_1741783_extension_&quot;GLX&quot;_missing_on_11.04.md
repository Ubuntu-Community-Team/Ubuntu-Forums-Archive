---
title: "extension &quot;GLX&quot; missing on 11.04"
date: 2011-04-28
forum: Desktop Environments
---

### Post by yvsong on 2011-04-28
After upgrading to 11.04, Ubuntu says my hardware are not good enough for Unity, so I have to use Classic desktop. However, I lost OpenGL.

glxinfo shows
[INDENT]Xlib:  extension "GLX" missing on display ":0.0".[/INDENT]
lspci shows
[INDENT]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/INDENT]
[INDENT]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/INDENT]

How can I get OpenGL back?

---

### Post by neven on 2011-04-28
I have same problem, just can't believe that on every other ubuntu version since 9.04 was working without any problem. Btw i have intel hd graphic. I guess i am going to restore my 10.10 installation with clonezilla, will be back in 1 month to install 11.04 again :)

---

### Post by shademere on 2011-04-28
I have a similiar problem. 
Just got Natty Narwhal installed on my system, and I've run into problems; the proprietary drivers are "activated but not in use", meaning Unity won't run, and typing 'unity' at command line returns the above error, and also 

[FONT="Courier New"]Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (bailer) - Info: Ensuring a shell for your session[/FONT]

Then I get a warning from Window manager about an [FONT="Courier New"]_NET_WM_MOVERESIZE message[/FONT]; apparently "[FONT="Courier New"]these messages lack timestamps and therefore suck"[/FONT]

I've looked all over, and the solutions are either outdated or nonrelevant.

Can anybody please help me get Unity back? I suspect this is also causing problems during boot (like [FONT="Courier New"]mountall: disconnected from Plymouth[/FONT], which causes boot-up to hang)

Thanks in advance.

---

### Post by shademere on 2011-05-02
After extensive searching (this problem seems to be quite common with different solutions for different versions of Ubuntu on different machines)I found this thread, which seems to provide some insight:

[http://ubuntuforums.org/showthread.php?t=1722306]("http://ubuntuforums.org/showthread.php?t=1722306")

I haven't had the time to try it yet. It seems as if we have to run

[FONT="Courier New"]ldd /usr/bin/glxinfo[/FONT]

and see if it is loading the "correct" library, libgl from nvidia-current. If not, run [FONT="Courier New"]dpkg -S "address of library" 

(in this case something like /usr/lib/libGL.so.1)[/FONT]. 

This finds out which package the faulty library is coming from. Then delete those libraries. I'm not sure why the guy on the other thread used [FONT="Courier New"]/bin/rm[/FONT] instead of just [FONT="Courier New"]rm[/FONT].

Next run 

[FONT="Courier New"]ldconfig[/FONT] 

to create the links to the libraries, and then run 

[FONT="Courier New"]ldd /usr/bin/glxinfo[/FONT]

again to check that [FONT="Courier New"]libGL.so.1[/FONT] is linking to [FONT="Courier New"]/usr/lib/nvidia-current/libGL.so.1[/FONT]. If it does your problems should be over. I might try this tomorrow if I have time. Maybe you can try it and report back. Note that I haven't tried this yet.

If there is anything wrong with this post I'd be grateful to anyone who points that out. I've tried so many different ways from what solutions I've read online, and none have worked so far. The GNOME shell still works for me if I login to recovery mode, but unity doesn't, and I get the [FONT="Courier New"]mountall: disconnected from Plymouth[/FONT] message when booting normally. Not sure if it is an error message. I'm hoping it is linked to the graphics driver problem and that problem will depart when this one is solved.

---

### Post by yvsong on 2011-05-02
I fixed my computer powered by Intel graphics card by removing nvidia-settings and nvidia-current packages. Thanks for the hint.

---

### Post by shademere on 2011-05-02
Good on you, yvsong. I tried that and it worked a treat. I don't think 3D acceleration still working, but better to have unity working and no problems. I guess I'll mess around a bit more with it when I have time. Have you tried the Experimental 3D support for nvidia cards? It doesn't look too bad.

---

### Post by James78 on 2011-05-30
I had this problem too, and for a long while I didn't bother to fix it (I've tried before). Just now I've managed to fix it though.

I've checked my Xorg log, and saw it was loading GLX as nvidia, even though I use Intel. So I removed nvidia-settings and nvidia-current (this one is the one causing the problem), (might as well remove nvidia-common also). Checked my logs again, and now it's using ATI! So searching again, now I needed to remove fglrx and fglrx-amdcccle. Hope this helped someone!

Update: You can set mesa as the GL driver without uninstalling everything. Just 'sudo update-alternatives --config gl_conf' and select mesa.

---

### Post by balingupjer on 2011-08-09
From theiszm -  [https://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/](https://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/)


Just trying it now...



> I’ve recently upgraded to Ubuntu 10.04, and the first time I ran  SciLab I got no graphics.   I’m using an Intel Corporation Mobile  GM965/GL960 video card, and when I check the implementation this is what  I get:
 tisza@tisza-ubuntu:~$ sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
tisza@tisza-ubuntu:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat


 After poking around a couple of forum pages, I finally got a workaround.  Thank you [~witekk]("https://launchpad.net/%7Ewitekk") for the fix.  So here’s how to do it.  On the terminal (as root):
 sudo apt-get purge nvidia*
sudo apt-get install --reinstall xserver-xorg-video-intel  libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-alternatives --remove gl_conf /usr/lib/nvidia-current/ld.so.conf


 Luckily, this solves the same problem with two other graphic controllers:
  
 
[LIST]
[*]Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated  Graphics Controller (rev 03)
[*]Intel Corporation Mobile 4 Series Chipset Integrated Graphics  Controller (rev 07)
[/LIST]
 There you have it. Enjoy!
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by leonardjensan on 2012-01-24
Thank you. This worked for me.

---

