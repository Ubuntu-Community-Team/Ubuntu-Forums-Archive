---
title: "Thinwhiteliquid"
date: 2009-02-02
forum: General Help
---

### Post by blowupman on 2009-02-02
I have downloaded the program "Thinwhiteliquid" on ubuntu to encode and transfer videos unto my new ipod
however
i come across 2 problems whenever I try using it
when I install it
i get this at the end of the installation
> 
------------------------------
Clearing old installations ...
------------------------------
Traceback (most recent call last):
  File "/home/arta/Desktop/thinliquidfilm/install.py", line 104, in <module>
    if os.path.isfile(kdedir + '/share/apps/konqueror/servicemenu/thinliquidfilm.desktop'):
NameError: name 'kdedir' is not defined
root@arta-desktop:/home/arta/Desktop/thinliquidfilm# 


and whenever I run the program itself by running the python script,
everytime I try adding a file to encode or transfer
the program tells me that it had a problem opening the file,
the file may be corrupt,
and this comes up on the terminal
> root@arta-desktop:/home/arta/Desktop/thinliquidfilm# '/home/arta/Desktop/thinliquidfilm/thinliquidfilm.py' 
Session management error: None of the authentication protocols specified are supported
[]
ffmpeg supports xvid
ffmpeg supports h264
tab changed
changed to "encode"
/root/.thinliquidfilm/latest
1.0
Version Check:  Update message already shown
Version Check:  This is the latest version
tab changed
changed to "encode"
/home/arta/Step.Brothers[2008][Unrated.Edition]DvDrip-aXXo/Step.Brothers[2008][Unrated.Edition].avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from '/home/arta/Step.Brothers[2008][Unrated.Edition]DvDrip-aXXo/Step.Brothers[2008][Unrated.Edition].avi':
  Duration: 01:45:36.2, start: 0.000000, bitrate: 929 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 664x268 [PAR 1:1 DAR 166:67], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unable to find a suitable output format for '/dev/null'
Values:
parsing error


I want to be able to encode and transfer my movies unto my ipod all in one place, and nothing has worked and thinwhitefilm looks promising
someone please help me
I'm a noob and I liked ubuntu up until i got an ipod :(

---

### Post by alienclone on 2009-09-01
just found this fix.

> I had this error using Gnome and Ubuntu Gutsy and solved the problem by opening the [COLOR=#a76100]**install**[/COLOR].py file in a text editor and # out the lines from clear old installs to the end of that section [see below]. It then installed ok [I had no old [COLOR=#a76100]**install**[/COLOR] anyway!] 
 
#clear old installs 
#if os.path.isfile(kdedir + '/share/apps/konqueror/servicemenu/thinliquidfilm.desktop'): 
#    print 'Removing ' + kdedir + '/share/apps/konqueror/servicemenu/thinliquidfilm.desktop sevicemenu' 
#    os.remove(kdedir + '/share/apps/konqueror/servicemenu/thinliquidfilm.desktop') 
#if os.path.isfile('/usr/local/bin/thinliquidfilm'): 
#    print 'Removing symlink to main application' 
#    os.remove('/usr/local/bin/thinliquidfilm') 
#if os.path.exists('/usr/local/thinliquidfilm'): 
#    print 'Removing /usr/local/thinliquidfilm directory' 
#    shutil.rmtree('/usr/local/thinliquidfilm') 
#print '' 
#print 'Old installations cleared' 
#print ''                                                       then ran
```
python install.py
```

---

