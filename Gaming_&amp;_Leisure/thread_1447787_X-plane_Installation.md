---
title: "X-plane Installation"
date: 2010-04-05
forum: Gaming &amp; Leisure
---

### Post by SamHowells on 2010-04-05
Hello, new here.
I installed Ubuntu a few days ago, and am trying to get X-Plane demo to work. I've downloaded the linux installer, but when I run it from the gui icon it doesn't work. 

i then did some reading and found I needed an openal package, which I downloaded from the synaptic package manager, now when I run the installer from the terminal I get the following error:

```
./X-Plane Demo Installer Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

```

What have I done wrong, I have tried the command:
```
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
```
but this hasn't helped either.

Any help would be greatly appreciated.

Regards
Sam

---

### Post by Perfect Storm on 2010-04-06
Are you using 64-bit?

---

### Post by SamHowells on 2010-04-06
Yes, I am.

---

### Post by Perfect Storm on 2010-04-06
```
sudo ln -s /usr/lib32/libopenal.so.1 /usr/lib32/libopenal.so.0
```

---

### Post by SamHowells on 2010-04-06
Hi,
That worked a treat, thanks! Just out of curiosity, what exactly does that command do, does it point a program to use a different file?

Regards
Sam

---

### Post by Perfect Storm on 2010-04-06
X-plane run only 32-bit. When you install 64-bit you had at some point installed 32-bit libraries (They go to /usr/lib32) with the package ia32-libs. The 32-bit libraries are identical to the 64-bit libraries (in name). The OpenAl have moved from so.0 to so.1 therefore you had to make symblink.

The command you used made a symblink. You created a link called (32-bit) libopenal.so.0 which point to libopenal.so.1 (32-bit)

It works for most with symblinks, but sometimes there's so huge difference between libraries versions that a symblink isn't enough to solve the problem. But in this case it is ^_^

---

### Post by Robbyjhb on 2010-06-26
Hello Guys , I am a new user as well

I cannot get x-plane to install if I try the x-plane web site ([http://wiki.x-plane.com/Linux_Installation_Walkthrough](http://wiki.x-plane.com/Linux_Installation_Walkthrough)) way I get this
robert@ubuntu:~$ sudo ln –s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
ln: target `/usr/lib/libopenal.so.0' is not a directory
robert@ubuntu:~$ sudo ln –s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
ln: target `/usr/lib/libopenal.so.0' is not a directory
robert@ubuntu:~$ and when I try this way([http://www.ilovelinux.co.uk/xplane910-2.php](http://www.ilovelinux.co.uk/xplane910-2.php)) I get this 
robert@ubuntu:/media/XPLANE9$ ./Installer_Linux
./Installer_Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
robert@ubuntu:/media/XPLANE9$ sudo ln -s libopenal.so.1.8.466 /usr/lib/libopenal.so.0
[sudo] password for robert: 
ln: creating symbolic link `/usr/lib/libopenal.so.0': File exists
robert@ubuntu:/media/XPLANE9$ ./Installer_Linux
./Installer_Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
robert@ubuntu:/media/XPLANE9$ I have libopenal1 installed using ubuntu 10.04 LTS 32 bit, I dont know where to turn to next,PLEEEEEEASE help.

Robert

---

### Post by Perfect Storm on 2010-06-27
If you're using 64-bit you need to symblink the libopenal in /usr/lib32 instead of /usr/lib

---

### Post by Robbyjhb on 2010-06-27
But I am using 32bit

---

### Post by drjrjones on 2010-06-27
this is what i did to install x-plane

xplane
first time load no usb plugged in except mouse and keyboard

synaptic package
X libsmpeg0
X joystick
X libopenal1
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0

it fought me too but now it works except for the yoke

---

### Post by Robbyjhb on 2010-06-29
**Re: Installing X-Plane 9.4 Demo -  missing libopenal.so.0 library** 			
 			 			 		   		 		 		Do not know what the hell is going on with ubuntu this is what I get, running 32bit ubuntu 10.04
robert@ubuntu:~$ [COLOR=Red][B]sudo ln -s /usr/lib/libopenal.so.1.12.854 /usr/lib/libopenal.so.0
ln: creating symbolic link `/usr/lib/libopenal.so.0': File exists[/B][/COLOR]
robert@ubuntu:~$ cd Desktop
robert@ubuntu:~/Desktop$ ./&#8221;X-Plane DVD Installer Linux&#8221;
bash: ./&#8221;X-Plane: No such file or directory
  I am really getting eager to get x-plane installed now.It is such a pity because ubuntu is such a nice operating system, but i cannot change from windows to ubuntu until this is sorted. 

Robert

---

### Post by Perfect Storm on 2010-06-29
```
cd /usr/lib
sudo rm -rf libopenal.so.0
sudo ln –s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
cd
```

---

### Post by Robbyjhb on 2010-06-29
Hello Artificial intelligence

Please could you check if i entered this correctly, thanks for the help really appreciating it.

Robert

robert@ubuntu:~$ cd /usr/lib
robert@ubuntu:/usr/lib$ sudo rm -rf libopenal.so.0
[sudo] password for robert: 
robert@ubuntu:/usr/lib$ sudo ln &#8211;s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
ln: target `/usr/lib/libopenal.so.0' is not a directory
robert@ubuntu:/usr/lib$ cd
robert@ubuntu:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory
robert@ubuntu:~$

---

### Post by Perfect Storm on 2010-06-29
When you want to execute the x-plane binary, make sure to change into the x-plane directory.

eg.

cd /home/<username>/x-plane

or

cd ~/x-plane

you can also drag the x-plane folder into the terminal.

---

### Post by Robbyjhb on 2010-07-03
I still do not have x-plane installed so therefore I cannot execute it yet, I am still trying to install x-plane.Thanks for the replies mate ,hope I can get this sorted asap.

Robert

---

### Post by Perfect Storm on 2010-07-03
I was referring to this:

> robert@ubuntu:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory

You need to change directory to execute Installer_Linux.

---

### Post by Robbyjhb on 2010-07-03
I have tried to drag the installer into the terminal but no luck,all these codes soumd like giberish to me.Still no such file or directory

---

### Post by Perfect Storm on 2010-07-03
Where do you have installer file?

---

### Post by Robbyjhb on 2010-07-03
on the x-plane dvd disc 1

---

### Post by Perfect Storm on 2010-07-03
> **Robbyjhb said:**
> on the x-plane dvd disc 1

Ah ok.

Then you should;

```
cd '/media/name-of-DVD'
./Installer_Linux
```

cd = change directory


EDIT:
Made a screenshot, just with a game called Jets'n'Guns

---

### Post by Robbyjhb on 2010-07-03
robert@ubuntu:~$ cd /media/XPLANE9
robert@ubuntu:/media/XPLANE9$ ./Installer_Linux
./Installer_Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
robert@ubuntu:/media/XPLANE9$

---

### Post by Perfect Storm on 2010-07-03
Can you save this to a .txt file and attached it to the post.

```
cd /usr/lib
ls -a
```

and you are sure you're on Ubuntu 32-bit and not 64-bit?

---

### Post by Robbyjhb on 2010-07-03
i am sure it is 32bit but how can I check it just in case,i typed in the code you gave me above into the terminal and I got a whole lot of stuff appearing in the terminal , do you want me to put that on here all that stuff in the terminal?

---

### Post by Perfect Storm on 2010-07-03
If you post it, just make sure to use the forum code tags

[ code] [/code] without the space between [ and c



We can check your kernel to see if you're using 32-bit or 64-bit

```
uname -a
```

---

### Post by Robbyjhb on 2010-07-03
robert@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

---

### Post by Perfect Storm on 2010-07-03
> **Robbyjhb said:**
> robert@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-21-generic **#32-Ubuntu** SMP Fri Apr 16 08:10:02 UTC 2010 **i686** GNU/Linux

Yep, 32-bit.
Now I just need the list of libs in your /usr/lib

---

### Post by Robbyjhb on 2010-07-03
I do not have a clue what you mean by forum post tags cant I e-mail the text doc to you

---

### Post by Robbyjhb on 2010-07-03
l

---

### Post by Perfect Storm on 2010-07-03
> **Robbyjhb said:**
> I do not have a clue what you mean by forum post tags cant I e-mail the text doc to you

I haven't recieved anything :confused:


The code tags is almost like quote tags, you just replace "quote" with "code"
It makes it easier to read on the forum.

You can also use the **#** button in the reply message box to display the code tags.

---

### Post by Robbyjhb on 2010-07-03
```
libpanel.so.5.7
libpanelw.so.5
libpanelw.so.5.7
libpango-1.0.so.0
libpango-1.0.so.0.2800.0
libpangocairo-1.0.so.0
libpangocairo-1.0.so.0.2800.0
libpangoft2-1.0.so.0
libpangoft2-1.0.so.0.2800.0
libpangomm-1.4.so.1
libpangomm-1.4.so.1.0.30
libpangox-1.0.so.0
libpangox-1.0.so.0.2800.0
libpangoxft-1.0.so.0
libpangoxft-1.0.so.0.2800.0
libpaper.so.1
libpaper.so.1.1.2
libpathplan.so.4
libpathplan.so.4.0.0
libpcap.so.0.8
libpcap.so.1.0.0
libpciaccess.so.0
libpciaccess.so.0.10.8
libpci.so.3
libpci.so.3.0.0
libpcreposix.so.3
libpcreposix.so.3.12.1
libperl.so.5.10
libperl.so.5.10.1
libpisock.so.9
libpisock.so.9.0.2
libpisync.so.1
libpisync.so.1.0.3
libpixman-1.so.0
libpixman-1.so.0.16.4
libplc4.so
libplc4.so.0d
libplds4.so
libplds4.so.0d
libplist.so.1
libplist.so.1.1.1
libpolkit-agent-1.so.0
libpolkit-agent-1.so.0.0.0
libpolkit-backend-1.so.0
libpolkit-backend-1.so.0.0.0
libpolkit-gobject-1.so.0
libpolkit-gobject-1.so.0.0.0
libpolkit-gtk-1.so.0
libpolkit-gtk-1.so.0.0.0
libpoppler-glib.so.4
libpoppler-glib.so.4.0.0
libpoppler.so.5
libpoppler.so.5.0.0
libportaudio.so.2
libportaudio.so.2.0.0
libpostproc.so.51
libpostproc.so.51.2.0
libprotobuf-lite.so.5
libprotobuf-lite.so.5.0.0
libprotobuf.so.5
libprotobuf.so.5.0.0
libprotoc.so.5
libprotoc.so.5.0.0
libproxy
libproxy.so.0
libproxy.so.0.0.0
libpspell.so.15
libpspell.so.15.1.4
libpst.la
libpst.so
libpst.so.4
libpst.so.4.0.0
libpthread.a
libpthread_nonshared.a
libpthread.so
libpth.so.20
libpth.so.20.0.27
libpulse-browse.so.0
libpulse-browse.so.0.1.1
libpulsecommon-0.9.21.so
libpulsecore-0.9.21.so
libpulsedsp.so
libpulse-mainloop-glib.so.0
libpulse-mainloop-glib.so.0.0.4
libpulse-simple.so.0
libpulse-simple.so.0.0.3
libpulse.so.0
libpulse.so.0.12.2
libpurple-client.so.0
libpurple-client.so.0.6.6
libpurple.so.0
libpurple.so.0.6.6
libpyglib-2.0-python2.6.so.0
libpyglib-2.0-python2.6.so.0.0.0
libpython2.6.so.1
libpython2.6.so.1.0
libqt-mt.so.3
libqt-mt.so.3.3
libqt-mt.so.3.3.8
libqui.so.1
libqui.so.1.0
libqui.so.1.0.0
libraptor.so.1
libraptor.so.1.2.0
librarian.so.0
librarian.so.0.0.0
librasqal.so.2
librasqal.so.2.0.0
libraw1394.so.11
libraw1394.so.11.0.1
librdf.so.0
librdf.so.0.0.0
libresolv.a
libresolv.so
librhythmbox-core.so.0
librhythmbox-core.so.0.0.0
librom1394.so.0
librom1394.so.0.3.0
librpcsvc.a
librsvg-2.so.2
librsvg-2.so.2.26.2
librt.a
librt.so
libsamplerate.so.0
libsamplerate.so.0.1.7
libsane.la
libsane.so.1
libsane.so.1.0.20
libsasl2.so.2
libsasl2.so.2.0.23
libschroedinger-1.0.so.0
libschroedinger-1.0.so.0.2.0
libsctp.so.1
libsctp.so.1.0.11
libSDL-1.2.so.0
libSDL-1.2.so.0.11.3
libsensors.so.4
libsensors.so.4.2.1
libsgutils2.so.2
libsgutils2.so.2.0.0
libshout.so.3
libshout.so.3.2.0
libsidplay.so.1
libsidplay.so.1.0.3
libsigc-2.0.so.0
libsigc-2.0.so.0.0.0
libsilc-1.1.so.2
libsilc-1.1.so.2.1.0
libsilcclient-1.1.so.3
libsilcclient-1.1.so.3.0.0
libslp.so.1
libslp.so.1.0.1
libsmbclient.so.0
libsmime3.so
libsmime3.so.1d
libSM.so.6
libSM.so.6.0.1
libsndfile.so.1
libsndfile.so.1.0.21
libsnmp.so.15
libsnmp.so.15.1.2
libsoup-2.4.so.1
libsoup-2.4.so.1.3.0
libsoup-gnome-2.4.so.1
libsoup-gnome-2.4.so.1.3.0
libspectre.so.1
libspectre.so.1.1.3
libspeechd.so.2
libspeechd.so.2.1.1
libspeexdsp.so.1
libspeexdsp.so.1.5.0
libspeex.so.1
libspeex.so.1.5.0
libspi.so.0
libspi.so.0.10.11
libsqlite3.so.0
libsqlite3.so.0.8.6
libsqlite.so.0
libsqlite.so.0.8.6
libssl3.so
libssl3.so.1d
libssl.so.0.9.8
libstartup-notification-1.so.0
libstartup-notification-1.so.0.0.0
libstdc++.so.6
libstdc++.so.6.0.13
libstlport_gcc.so.4.6
libswscale.so.0
libswscale.so.0.7.1
libtag.so.1
libtag.so.1.6.1
libtalloc.so.2
libtalloc.so.2.0.1
libtasn1.so.3
libtasn1.so.3.1.7
libtcl8.4.so.0
libtdb.so.1
libtdb.so.1.2.0
libtelepathy-farsight.so.0
libtelepathy-farsight.so.0.1.0
libtelepathy-glib.so.0
libtelepathy-glib.so.0.32.2
libthai.so.0
libthai.so.0.1.5
libtheoradec.so.1
libtheoradec.so.1.1.4
libtheoraenc.so.1
libtheoraenc.so.1.1.2
libtheora.so.0
libtheora.so.0.3.10
libthread_db.so
libtiff.so.4
libtiff.so.4.3.2
libtk8.4.so.0
libtotem-plparser-mini.so.17
libtotem-plparser-mini.so.17.0.0
libtotem-plparser.so.17
libtotem-plparser.so.17.0.0
libts-0.0.so.0
libts-0.0.so.0.1.1
libtwolame.so.0
libtwolame.so.0.0.0
libubuntuone-1.0.so.1
libubuntuone-1.0.so.1.0.0
libungif.so.4
libungif.so.4.1
libungif.so.4.1.6
libunique-1.0.so.0
libunique-1.0.so.0.100.6
libuniquewm-1.2.so.0
libuniquewm-1.2.so.0.8.0
libuno_cppuhelpergcc3.so.3
libuno_cppu.so.3
libuno_purpenvhelpergcc3.so.3
libuno_salhelpergcc3.so.3
libuno_sal.so.3
libupower-glib.so.1
libupower-glib.so.1.0.1
libusb-0.1.so.4
libusb-1.0.so.0
libusbmuxd.so.1
libusbmuxd.so.1.0.0
libutil.a
libutil.so
libv4l
libv4l1.so.0
libv4l2.so.0
libv4lconvert.so.0
libvcard.so.0
libvcard.so.0.0.0
libvdpau_nvidia.so
libvisual
libvisual-0.4
libvisual-0.4.so.0
libvisual-0.4.so.0.0.0
libvorbisenc.so.2
libvorbisenc.so.2.0.6
libvorbisfile.so.3
libvorbisfile.so.3.3.2
libvorbis.so.0
libvorbis.so.0.4.3
libvte9
libvte.so.9
libvte.so.9.12.1
libwavpack.so.1
libwavpack.so.1.1.4
libwbclient.so.0
libwebkit-1.0.so.2
libwebkit-1.0.so.2.17.2
libwine.so.1
libwine.so.1.0
libwmf-0.2.so.7
libwmf-0.2.so.7.1.0
libwmflite-0.2.so.7
libwmflite-0.2.so.7.0.1
libwnck-1.so.22
libwnck-1.so.22.3.26
libwpd-0.8.so.8
libwpd-0.8.so.8.0.14
libwpg-0.1.so.1
libwpg-0.1.so.1.0.3
libwpg-stream-0.1.so.1
libwpg-stream-0.1.so.1.0.3
libwps-0.1.so.1
libwps-0.1.so.1.0.2
libwps-stream-0.1.so.1
libwps-stream-0.1.so.1.0.2
libwx_baseu-2.6.so.0
libwx_baseu-2.6.so.0.3.1
libwx_baseu_net-2.6.so.0
libwx_baseu_net-2.6.so.0.3.1
libwx_baseu_xml-2.6.so.0
libwx_baseu_xml-2.6.so.0.3.1
libwx_gtk2u_adv-2.6.so.0
libwx_gtk2u_adv-2.6.so.0.3.1
libwx_gtk2u_animate-2.6.so.0
libwx_gtk2u_animate-2.6.so.0.3.1
libwx_gtk2u_core-2.6.so.0
libwx_gtk2u_core-2.6.so.0.3.1
libwx_gtk2u_deprecated-2.6.so.0
libwx_gtk2u_deprecated-2.6.so.0.3.1
libwx_gtk2u_fl-2.6.so.0
libwx_gtk2u_fl-2.6.so.0.3.1
libwx_gtk2u_gizmos-2.6.so.0
libwx_gtk2u_gizmos-2.6.so.0.3.1
libwx_gtk2u_gizmos_xrc-2.6.so.0
libwx_gtk2u_gizmos_xrc-2.6.so.0.3.1
libwx_gtk2u_gl-2.6.so.0
libwx_gtk2u_gl-2.6.so.0.3.1
libwx_gtk2u_html-2.6.so.0
libwx_gtk2u_html-2.6.so.0.3.1
libwx_gtk2u_media-2.6.so.0
libwx_gtk2u_media-2.6.so.0.3.1
libwx_gtk2u_mmedia-2.6.so.0
libwx_gtk2u_mmedia-2.6.so.0.3.1
libwx_gtk2u_ogl-2.6.so.0
libwx_gtk2u_ogl-2.6.so.0.3.1
libwx_gtk2u_plot-2.6.so.0
libwx_gtk2u_plot-2.6.so.0.3.1
libwx_gtk2u_qa-2.6.so.0
libwx_gtk2u_qa-2.6.so.0.3.1
libwx_gtk2u_stc-2.6.so.0
libwx_gtk2u_stc-2.6.so.0.3.1
libwx_gtk2u_svg-2.6.so.0
libwx_gtk2u_svg-2.6.so.0.3.1
libwx_gtk2u_xrc-2.6.so.0
libwx_gtk2u_xrc-2.6.so.0.3.1
libX11.so.6
libX11.so.6.3.0
libxapian.so.15
libxapian.so.15.6.9
libXau.so.6
libXau.so.6.0.0
libXaw7.so.7
libXaw7.so.7.0.0
libXaw.so.7
libxcb-atom.so.1
libxcb-atom.so.1.0.0
libxcb-aux.so.0
libxcb-aux.so.0.0.0
libxcb-event.so.1
libxcb-event.so.1.0.0
libxcb-render.so.0
libxcb-render.so.0.0.0
libxcb-render-util.so.0
libxcb-render-util.so.0.0.0
libxcb.so.1
libxcb.so.1.1.0
libXcomposite.so.1
libXcomposite.so.1.0.0
libXcursor.so.1
libXcursor.so.1.0.2
libXdamage.so.1
libXdamage.so.1.1.0
libXdmcp.so.6
libXdmcp.so.6.0.0
libXext.so.6
libXext.so.6.4.0
libXfixes.so.3
libXfixes.so.3.1.0
libXfont.so.1
libXfont.so.1.4.1
libXft.so.2
libXft.so.2.1.13
libXinerama.so.1
libXinerama.so.1.0.0
libXi.so.6
libXi.so.6.1.0
libxkbfile.so.1
libxkbfile.so.1.0.2
libxklavier.so.16
libxklavier.so.16.0.0
libxml2.so.2
libxml2.so.2.7.6
libXmu.so.6
libXmu.so.6.2.0
libXmuu.so.1
libXmuu.so.1.0.0
libXNVCtrl.a
libXpm.so.4
libXpm.so.4.11.0
libXp.so.6
libXp.so.6.2.0
libXrandr.so.2
libXrandr.so.2.2.0
libXrender.so.1
libXrender.so.1.3.0
libXRes.so.1
libXRes.so.1.0.0
libxslt.so.1
libxslt.so.1.1.26
libXss.so.1
libXss.so.1.0.0
libXt.so.6
libXt.so.6.0.0
libXtst.so.6
libXtst.so.6.1.0
libXvMC.so.1
libXvMC.so.1.0.0
libXvMCW.so.1
libXvMCW.so.1.0.0
libXv.so.1
libXv.so.1.0.0
libXxf86dga.so.1
libXxf86dga.so.1.0.0
libXxf86misc.so.1
libXxf86misc.so.1.1.0
libXxf86vm.so.1
libXxf86vm.so.1.0.0
libzephyr.so.4
libzephyr.so.4.0.0
linux-boot-probes
lksctp-tools
locale
lp_solve
m17n-lib
man-db
Mcrt1.o
memtest86+
menu
mesa
midbrowser
mime
ModemManager
mono
mozilla
nautilus
nautilus-sendto
network-manager
NetworkManager
network-manager-pptp
notify-osd
nss
nvidia
nvidia-current
obexd
openoffice
openssh
orbit-2.0
os-prober
os-probes
pango
pcmciautils
perl
perl5
pitivi
pkgconfig
pm-utils
policykit-1
policykit-1-gnome
polkit-1
pppd
ppr
pt_chown
pulse-0.9.21
pulseaudio
purple-2
pymodules
pyshared
python2.6
python3.1
qt3
rhythmbox
rsyslog
rtkit
samba
sane
sasl2
Scrt1.o
seahorse
silc
speech-dispatcher
speech-dispatcher-modules
sse2
ssl
sudo
syslinux
system-service
tasksel
tc
telepathy
tomboy
totem
ts0
tsclient
ubiquity
ubuntuone-client
udev
udisks
update-manager
update-notifier
upower
upstart
ure
valgrind
vdpau
vinagre
vinagre-1
vino
w3m
webkit-1.0-2
wine
X11
xen
xorg
xscreensaver
xulrunner
xulrunner-1.9.2.3
xulrunner-addons
XvMCConfig
xvmcconfig-standard
```

---

### Post by Perfect Storm on 2010-07-04
Seems your terminal is limit to 500 lines so it doesn't show the whole thing.

Instead;
```
find /usr/lib -name libopenal*
```

By the way you did install openal before trying to make the symblink?

---

### Post by aalhamer on 2010-07-06
Another added step is to right click on the installer, Properties> Permissions make sure the all are read and write and the the owner is your user name.

---

### Post by Robbyjhb on 2010-07-07
robert@ubuntu:~$ find /usr/lib -name libopenal*
/usr/lib/libopenal.so.1
/usr/lib/libopenal.so.1.12.854
robert@ubuntu:~$

---

### Post by Malcolm Jackson on 2010-09-21
[B]Regarding installation of X-Plane onto my Ubuntu 10.04, here is the terminal print out which finally succeeded. I have left everything in as I attempted to get X-Plane installed. Taken 5 weeks, but X-Plane is so good it was well worth the effort, and have learned a lot about Ubuntu as well. I removed the original Hard Drive with Vista on it and replaced it with a new 500gb hard drive, and installed Ubuntu 10.04 as the only OS.


malcolm@malcolm-desktop:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ sudo ln -s libopenal.so.1.8.466 /usr/lib/libopenal.so.0
[sudo] password for malcolm:
ln: creating symbolic link `/usr/lib/libopenal.so.0': File exists
malcolm@malcolm-desktop:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ /Installer_Linux
bash: /Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ Installer_Linux
Installer_Linux: command not found
malcolm@malcolm-desktop:~$ sudo ln -s libopenal.so.1.8.466 /usr/lib/libopenal.so.0
ln: creating symbolic link `/usr/lib/libopenal.so.0': File exists
malcolm@malcolm-desktop:~$


After this last line in the terminal, I clicked on the Linux_Instal icon in the X-Plane Nautilus browser, and the program started loading. I only clicked on the icon out of frustration. I didn't know it was going to work. Really happy chance.
[/B]

---

### Post by Noraphalem on 2010-09-22
> **Malcolm Jackson said:**
> [B]Regarding installation of X-Plane onto my Ubuntu 10.04, here is the terminal print out which finally succeeded. I have left everything in as I attempted to get X-Plane installed. Taken 5 weeks, but X-Plane is so good it was well worth the effort, and have learned a lot about Ubuntu as well. I removed the original Hard Drive with Vista on it and replaced it with a new 500gb hard drive, and installed Ubuntu 10.04 as the only OS.


malcolm@malcolm-desktop:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ sudo ln -s libopenal.so.1.8.466 /usr/lib/libopenal.so.0
[sudo] password for malcolm:
ln: creating symbolic link `/usr/lib/libopenal.so.0': File exists
malcolm@malcolm-desktop:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ /Installer_Linux
bash: /Installer_Linux: No such file or directory
malcolm@malcolm-desktop:~$ Installer_Linux
Installer_Linux: command not found
malcolm@malcolm-desktop:~$ sudo ln -s libopenal.so.1.8.466 /usr/lib/libopenal.so.0
ln: creating symbolic link `/usr/lib/libopenal.so.0': File exists
malcolm@malcolm-desktop:~$


After this last line in the terminal, I clicked on the Linux_Instal icon in the X-Plane Nautilus browser, and the program started loading. I only clicked on the icon out of frustration. I didn't know it was going to work. Really happy chance.
[/B]

Ok some infos about the terminal. I hope it is useful. ;-)

malcolm@malcolm-desktop:~$ ./Installer_Linux
bash: ./Installer_Linux: No such file or directory

> The Installer_Linux file was not found because you are in the home directory (Indicated by malcolm@malcolm-desktop:**~**$) and the shell looks in that directory for that. And of course it is the wrong name. ;-)

> malcolm@malcolm-desktop:~**$** indicates that you are logged in as a "normal" user.

Greetings

---

