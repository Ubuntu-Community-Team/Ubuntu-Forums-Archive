---
title: "WMP took over MPlayer in FF! (crossoveroffice)"
date: 2006-04-11
forum: Desktop Environments
---

### Post by nismoskys on 2006-04-11
i just installed windows media player 6.4 through crossover office and now when visiting websites w. embedded content, it plays with wmp instead of mplayer, and lags alott and has no audio. 

how can i tell firefox to go back to using MPlayer instead?

thanks.

---

### Post by nismoskys on 2006-04-11
i tried reinstalling mplayer and mozilla mplayer, but it didnt work.

also, now firefox is trying to use quicktime to play movies (such as on apple.com/trailers) instead of mplayer like it used to.

it opens up a "windows" window and asks me to configure quicktime/says quicktime needs to be upgraded.

how can i just go back to mplayer? thanks.

---

### Post by art on 2006-04-12
Go to the ~/.mozilla/firefox directory. There you will see a file called pluginreg.dat. 
cp pluginreg.dat pluginreg.dat_bckp
And thed 
gedit pluginreg.dat
now carefully remove all the plugins you want to be disabled, like quick-time or WMP. Restart FF, and try it out.

---

### Post by nismoskys on 2006-04-12
thanks, but sorry im not too sure which lines to remove. i still want the filetypes to work, but with mplayer instead.

heres my pluginreg.dat

```
Generated File. Do not edit.

[HEADER]
Version:0.08:$

[PLUGINS]
/usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so:$
:$
1125104384000:1:5:$
Java(TM) Plug-in 1.5.0_05:$
Java(TM) Plug-in 1.5.0_05-b05:$
31
0:application/x-java-vm:Java::$
1:application/x-java-applet:Java::$
2:application/x-java-applet;version=1.1:Java::$
3:application/x-java-applet;version=1.1.1:Java::$
4:application/x-java-applet;version=1.1.2:Java::$
5:application/x-java-applet;version=1.1.3:Java::$
6:application/x-java-applet;version=1.2:Java::$
7:application/x-java-applet;version=1.2.1:Java::$
8:application/x-java-applet;version=1.2.2:Java::$
9:application/x-java-applet;version=1.3:Java::$
10:application/x-java-applet;version=1.3.1:Java::$
11:application/x-java-applet;version=1.4:Java::$
12:application/x-java-applet;version=1.4.1:Java::$
13:application/x-java-applet;version=1.4.2:Java::$
14:application/x-java-applet;version=1.5:Java::$
15:application/x-java-applet;jpi-version=1.5.0_05:Java::$
16:application/x-java-bean:Java::$
17:application/x-java-bean;version=1.1:Java::$
18:application/x-java-bean;version=1.1.1:Java::$
19:application/x-java-bean;version=1.1.2:Java::$
20:application/x-java-bean;version=1.1.3:Java::$
21:application/x-java-bean;version=1.2:Java::$
22:application/x-java-bean;version=1.2.1:Java::$
23:application/x-java-bean;version=1.2.2:Java::$
24:application/x-java-bean;version=1.3:Java::$
25:application/x-java-bean;version=1.3.1:Java::$
26:application/x-java-bean;version=1.4:Java::$
27:application/x-java-bean;version=1.4.1:Java::$
28:application/x-java-bean;version=1.4.2:Java::$
29:application/x-java-bean;version=1.5:Java::$
30:application/x-java-bean;jpi-version=1.5.0_05:Java::$
/opt/firefox/plugins/nphelix.so:$
:$
1142898870000:1:5:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.572 built with gcc 3.2.0 on Sep 15 2005:$
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible:$
1
0:audio/x-pn-realaudio-plugin:RealPlayer Plugin Metafile:rpm:$
/opt/firefox/plugins/mplayerplug-in.so:$
:$
1142898870000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
mplayerplug-in 3.17:$
22
0:video/mpeg:MPEG:mpg,mpeg:$
1:audio/mpeg:MPEG:mpg,mpeg:$
2:video/x-mpeg:MPEG:mpg,mpeg:$
3:video/x-mpeg2:MPEG2:mpv2,mp2ve:$
4:audio/mpeg:MPEG:mpg,mpeg:$
5:audio/x-mpeg:MPEG:mpg,mpeg:$
6:audio/mpeg2:MPEG audio:mp2:$
7:audio/x-mpeg2:MPEG audio:mp2:$
8:video/mp4:MPEG 4 Video:mp4:$
9:audio/mpeg3:MPEG audio:mp3:$
10:audio/x-mpeg3:MPEG audio:mp3:$
11:audio/mp3:MPEG audio:mp3:$
12:application/x-ogg:Ogg Vorbis Media:ogg:$
13:audio/ogg:Ogg Vorbis Audio:ogg:$
14:application/ogg:Ogg Vorbis / Ogg Theora:ogg:$
15:video/fli:FLI animation:fli,flc:$
16:video/x-fli:FLI animation:fli,flc:$
17:video/vnd.vivo:VivoActive:viv,vivo:$
18:application/x-nsv-vp3-mp3:Nullsoft Streaming Video:nsv:$
19:video/vnd.divx:DivX Media Format:divx:$
20:audio/basic:Basic Audio File:au,snd:$
21:audio/x-basic:Basic Audio File:au,snd:$
/opt/firefox/plugins/mplayerplug-in-wmp.so:$
:$
1142898870000:1:7:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
Windows Media Player Plugin:$
17
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:video/x-msvideo:AVI:avi,*:$
3:video/msvideo:AVI:avi,*:$
4:application/x-mplayer2:Media Files:*:$
5:application/x-ms-wmv:Microsoft WMV video:wmv,*:$
6:video/x-ms-asf:Media Files:asf,asx,*:$
7:video/x-ms-wm:Media Files:wm,*:$
8:video/x-ms-wmv:Microsoft WMV video:wmv,*:$
9:audio/x-ms-wmv:Windows Media:wmv,*:$
10:video/x-ms-wmp:Windows Media:wmp,*:$
11:video/x-ms-wvx:Windows Media:wvx,*:$
12:audio/x-ms-wax:Windows Media:wax,*:$
13:audio/x-ms-wma:Windows Media:wma,*:$
14:application/x-drm-v2:Windows Media:asx,*:$
15:audio/wav:Microsoft wave file:wav,*:$
16:audio/x-wav:Microsoft wave file:wav,*:$
/opt/firefox/plugins/mplayerplug-in-rm.so:$
:$
1142898870000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
RealPlayer 9:$
7
0:audio/x-pn-realaudio:RealAudio:ram,rm:$
1:application/vnd.rn-realmedia:RealMedia:rm:$
2:application/vnd.rn-realaudio:RealAudio:ra,ram:$
3:video/vnd.rn-realvideo:RealVideo:rv:$
4:audio/x-realaudio:RealAudio:ra:$
5:audio/x-pn-realaudio-plugin:RealAudio:rpm:$
6:application/smil:SMIL:smil:$
/opt/firefox/plugins/mplayerplug-in-qt.so:$
:$
1142898870000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
QuickTime Plug-in 6.0:$
7
0:video/quicktime:Quicktime:mov:$
1:video/x-quicktime:Quicktime:mov:$
2:image/x-quicktime:Quicktime:mov:$
3:video/quicktime:Quicktime:mp4:$
4:video/quicktime:Quicktime - Session Description Protocol:sdp:$
5:application/x-quicktimeplayer:Quicktime:mov:$
6:application/smil:SMIL:smil:$
/opt/firefox/plugins/mplayerplug-in-gmp.so:$
:$
1142898870000:1:5:$
<a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.17<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a> <br>JavaScript Enabled and Using GTK2 Widgets<br>:$
Google VLC multimedia plugin 1.0:$
1
0:application/x-google-vlc-plugin:Google Video::$
/opt/firefox/plugins/libnullplugin.so:$
:$
1142898870000:1:5:$
The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.:$
Default Plugin:$
1
0:*:All types:.*:$
/opt/firefox/plugins/libflashplayer.so:$
:$
1142898870000:1:7:$
Shockwave Flash 7.0 r25:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
/opt/firefox/plugins/nppdf.so:$
:$
1142898871000:1:5:$
The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.:$
Adobe Reader 7.0:$
5
0:application/pdf:Portable Document Format:pdf:$
1:application/vnd.fdf:Acrobat Forms Data Format:fdf:$
2:application/vnd.adobe.xfdf:XML Version of Acrobat Forms Data Format:xfdf:$
3:application/vnd.adobe.xdp+xml:Acrobat XML Data Package:xdp:$
4:application/vnd.adobe.xfd+xml:Adobe FormFlow99 Data File:xfd:$
/home/jaanisar/.cxoffice/win98/desktopdata/cxnsplugin/linux/NPSWF32.dll.so:$
:$
1144725432000:1:7:$
Shockwave Flash 6.0  r4:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Macromedia Flash movie:swf:$
1:application/futuresplash:FutureSplash movie:spl:$
/home/jaanisar/.cxoffice/win2000/desktopdata/cxnsplugin/linux/npqtplugin2.dll.so:$
:$
1144726162000:1:5:$
The QuickTime Plugin allows you to view a wide variety of multimedia content in Web pages. For more information, visit the <A HREF=http://www.apple.com/quicktime/>QuickTime</A> Web site.:$
QuickTime Plug-in 6.5.1 (CrossOver - npqtplugin2.dll):$
2
0:image/x-pict:PICT image file:pict,pic,pct:$
1:image/x-quicktime:QuickTime Image File:qtif,qti:$
/home/jaanisar/.cxoffice/win2000/desktopdata/cxnsplugin/linux/npqtplugin.dll.so:$
:$
1144726162000:1:5:$
The QuickTime Plugin allows you to view a wide variety of multimedia content in Web pages. For more information, visit the <A HREF=http://www.apple.com/quicktime/>QuickTime</A> Web site.:$
QuickTime Plug-in 6.5.1 (CrossOver - npqtplugin.dll):$
8
0:video/quicktime:QuickTime Movie:mov,qt:$
1:video/3gpp2:3GPP2 media file:3g2,3gp2:$
2:audio/3gpp2:3GPP2 media file:3g2,3gp2:$
3:video/x-m4v:Video (protected):m4v:$
4:video/sd-video:SD video file:sdv:$
5:application/x-mpeg:AMC media file:amc:$
6:image/x-macpaint:MacPaint image file:pntg,pnt,mac:$
7:image/pict:PICT image file:pict,pic,pct:$
/home/jaanisar/.cxoffice/win2000/desktopdata/cxnsplugin/linux/NPOFFICE.DLL.so:$
:$
1144726162000:1:5:$
Office Plugin for Netscape Navigator:$
Microsoft Office 2003 (CrossOver - NPOFFICE.DLL):$
1
0:application/x-msoffice:11.0.5510:*:$
/home/jaanisar/.cxoffice/win98/desktopdata/cxnsplugin/linux/npwmsdrm.dll.so:$
:$
1144727180000:1:5:$
Windows Multimedia Services DRM Store Plug-In:$
Microsoft® Windows Media Services (CrossOver - npwmsdrm.dll):$
1
0:application/x-drm:DRM File:dnp:$
/home/jaanisar/.cxoffice/win98/desktopdata/cxnsplugin/linux/npdsplay.dll.so:$
:$
1144727180000:1:7:$
Npdsplay dll:$
Windows Media Player Plug-in Dynamic Link Library:$
9
0:application/asx:Media Files:*:$
1:video/x-ms-asf-plugin:Media Files:*:$
2:application/x-mplayer2:Media Files:*:$
3:video/x-ms-asf:Media Files:asf,asx,*:$
4:video/x-ms-wm:Media Files:wm,*:$
5:audio/x-ms-wma:Media Files:wma,*:$
6:audio/x-ms-wax:Media Files:wax,*:$
7:video/x-ms-wmv:Media Files:wmv,*:$
8:video/x-ms-wvx:Media Files:wvx,*:$
/home/jaanisar/.cxoffice/win2000/desktopdata/cxnsplugin/linux/npwmsdrm.dll.so:$
:$
1144726162000:1:13:$
Windows Multimedia Services DRM Store Plug-In:$
Microsoft® Windows Media Services (CrossOver - npwmsdrm.dll):$
1
0:application/x-drm:DRM File:dnp:$

```
thanks alot, again.


** oh, and i just noticed, at the top of the file it says

Generated File. Do not edit.

ignore and do what it says not to do anyways lol, i assume?

---

### Post by art on 2006-04-12
If unsure I would suggest to remove the plugins crossover installed and firefox should fall back on the mplayer. So:
cd /home/jaanisar/.cxoffice/win2000/desktopdata/cxnsplugin/linux/
mv npqtplugin2.dll.so npqtplugin2.dll.so_old
cd /home/jaanisar/.cxoffice/win98/desktopdata/cxnsplugin/linux/
mv npwmsdrm.dll.so npwmsdrm.dll.so_old
cd /home/jaanisar/.cxoffice/win98/desktopdata/cxnsplugin/linux/
mv npdsplay.dll.so npdsplay.dll.so_old

Restart FireFox. Let us know how this went?

---

### Post by nismoskys on 2006-04-12
thankkks..

but it didnt work. ff is still trying to use the QT and WMP plugins.

but ill try restarting my whole comp instead of just ff, and see if that helps

thnx again

---

### Post by nismoskys on 2006-04-12
awesomee, i got Mplayer working in ff but quicktime movies (like on apple.com/trailers) still try to use quicktime, also, crossover's flash player is trying to make itself used as well

could you help a litttle more so i can get back to the way it was?
thanks man.

---

### Post by art on 2006-04-12
Ok, do an 
sudo updatedb
then when it is finished do a 
locate npqtplugin2.dll.so
and whatever it find move to your home directory (move not copy)
Restart FF. This way you remove all plugins crossover installed.
Just remembered that if you have a windows partition, don't move those files found in there, you probably couldn't but just a thought

---

### Post by art on 2006-04-12
When you say to the way it was you mean with crossover or without?

---

### Post by nismoskys on 2006-04-14
without..

k thanks, trying this right now.

---

### Post by nismoskys on 2006-04-14
**perfect** man thank you so much :D

and your directions also helped me remove the cxoffice flash plugin.

thanks again.

---

