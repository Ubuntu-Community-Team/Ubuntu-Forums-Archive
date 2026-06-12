---
title: "VNC Keyboard problem"
date: 2009-09-20
forum: Desktop Environments
---

### Post by Taus on 2009-09-20
Hi all,

i have installed turbovnc and turbojpeg along with virtualgl to try a streaming of games experiment. I experience a problem with my keyboard mapping.

when i connect to vnc and try to write some text in a console the keys is all messed up.

when i hit q it writes c
when i hit w it writes .
when i hit e it writes g
when i hit r it writes v
when i hit t it writes n
etc etc

I was on IRC earlier today where someone was mentioning it as being a DVORAK vs QWERTY problem. I'm not sure how or where to change this, or even if it's the problem. I tried to change the keyboard layouts in system -> preferences -> keyboard on both the client and the server. that didn't have any effect.

I also tried what was written in this post: [http://ubuntuforums.org/showthread.php?t=1202231](http://ubuntuforums.org/showthread.php?t=1202231)

that didn't seem to work for me either.

i've been struggeling with this for a few days now and would very much appreciate any point in the right direction.

thanks a million
cheers

---

### Post by Taus on 2009-09-21
i now tried to run: 

```
setxkbmap us 
```

which returned this error:
```
XKB extension not present on :1.0
```

anyone knows if the above error has something to do with my problems?

---

### Post by Taus on 2009-09-21
Still haven't figured out the solution to this problem however i'm not sure i need to anyhow... I made another attempt to stream the games using xforwarding and virtualgl which seems to have done the trick...

finally i have my GTX295 virtually binded from my super desktop computer to my laptop.

time to go play some games! yeeey

cheers all

---

### Post by aamir.nedian on 2010-08-26
ok. Now I have to ask you to please share your solution. I also need to bind my laptop to NVIDIA GPU's in a supercomputer.

---

### Post by Taus on 2010-08-27
It is quite a while since i did this so i can't remember how i did everything. Buy luckily i wrote it all down on a blog back then. I hope the commands are still the same:

[http://fanbetastic.wordpress.com/2009/09/25/streaming-games-using-ubuntu-9-04-jaunty/]("http://fanbetastic.wordpress.com/2009/09/25/streaming-games-using-ubuntu-9-04-jaunty/")

FYI I still use this setup once in a while, it works perfectly! It's so awesome to be able to play newer games on the lappy.

I remember updating the virtualgl to a newer version where it wasn't nescessary to install turbojpeg - you should maybe look into that as well. Anyways if you have any trouble or need any help. Just lemme know.

Cheers
-Taus

---

### Post by ngsngn on 2010-09-03
Hi Taus, you mentioned that you solve the keyboard mapping issues using xforwarding. 

May i know the xforwarding you are talking about is it the 'X11Forwarding yes' as mentioned in your blog post to aamir.nedian or isit another software as google results doesn't seem to provide much info to me.

Also, let say the client is a Windows laptop, how do you go about setting the 'ssh IPADRESS' on the client as you mentioned your laptop is linux as well. OR isit under TurboVNC viewer in windows client I can directly type on the terminal?

I am looking forward to try the game streaming but as I am a linux newbie, your help is appreciated.

---

### Post by Taus on 2010-09-03
hi ngsngn,

the program used for streaming games is VGLConnect. You can use it in different ways, but i found that X11Forwarding solved the keyb issue. If you follow the blog it should work just fine.

I have never tried to stream to a windows computer so I do not know how well it works. However I remember reading about a VGLConnect client called Exceed - It should work the same way as VGLConnect for linux.

-Taus

---

### Post by ngsngn on 2010-09-04
Hi Taus,

VGLConnect is under virtualGL isit. You use the 'VGLConnect' in the terminal to invoke the application am i right?

i would like to ask you is X11Forwarding is same as ssh? Let say i skip away the ssh process, the keyboard mapping would come back? Did you try other VNC program such as TigerVNC or ultravnc etc? as i think the mapping problem is limited to turbovnc only? i'm not sure though, did not test out other vncs yet...

I googled for Exceed, realise its a payable program, thanks anyway, was looking for open-source as i am exploring this area for my project.

Regards,
ngsngn

---

### Post by Taus on 2010-09-04
hi ngsngn,

Aye you use VGLConnect instead of ssh. It works the same way.

I think i have tried pretty much them all. I found that vglconnect was by far the best solution. the new versions has turbo vnc implemented as far as i remember. so you won't need to install that.

Exceed is open source as the rest of the clients. You should be able to download it from sourceforge: [http://sourceforge.net/projects/virtualgl/files/VirtualGL/](http://sourceforge.net/projects/virtualgl/files/VirtualGL/)

-Taus

---

### Post by ngsngn on 2010-09-05
Hi Taus,

Thanks for the information.

The link u posted is VirtualGL which i had at first downloaded version 2.1.4 which i thought is the stable version. Only did i clicked the the beta 2.1.90 (2.2beta1) i realise there is an actually an 'Exceed' inside. So did i need to uninstall the current version 2.1.4 version before installing 2.1.90 or i can just use the exceed.exe from 2.1.90 for 2.1.4 ?

Regards,
ngsngn

---

### Post by nautilus on 2011-07-12
Ancient problem, but I found a workaround, where it seems no search of Google could find:

It seems TurboVNC's vncserver wrapper launches Xvnc using the default session manager by default on the new display, in my case Gnome.  As a test, I modified my $HOME/.vnc/xstartup.turbovnc to begin with:

```
#!/bin/sh

if [ "${XINITRC}x" != 'x' ]; then
  exec ${XINITRC}
fi

```

then, I launched vncserver like so:

XINITRC=/usr/bin/xterm /opt/TurboVNC/bin/vncserver -nootp -name GLDesktop -geometry 1024x560

..and like magic my keys weren't being mangled, AND enter and backspace worked as expected.  OpenGL is nice and snappy (using my primary display to render).

Granted this method drops you into an ugly xterm, but one could make a script and set that to XINITRC to give them a basic desktop.  Launching Gnome in TurboVNC appears to gibble things, so I'm using IceWM.

I really wonder if this is a bug with TurboVNC or not?

---

