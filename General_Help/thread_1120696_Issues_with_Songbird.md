---
title: "Issues with Songbird?"
date: 2009-04-09
forum: General Help
---

### Post by aptenodytes on 2009-04-09
Songbird. I've tried to install trying a number of methods (mostly the top 10 hits from a google search for 'ubuntu songbird install') to no avail. It *seems* installed, but when I go to Applications>Sound&Video>Songbird, it starts to open (Starting Songbird appears in the bottom dock) but then an error message comes up saying something to the effect of songbird is already open ... can't open etc. Also, the icon in the menu is a blue egg rather than the yellow bird, I don't know if that makes a difference.

Which it isn't. Even upon a clean boot or pkill Songbird right before I open the app, I still get this message. It seems like people have had this problem before, but I haven't found a solution anywhere. It seems like great software. Any suggestions?

---

### Post by Nano_ext3 on 2009-04-09
Download the tar.gz from "http://www.getsongbird.com/" And extract the folder to a dir on your machine.  To be sure, do a "chmod u+x songbird.sh" inside the dir of the folder you have know after extracting it. I think thats the name of the installer, doing "ls -la" in that folder will show the .sh file.  Then do ./songbird.sh and it should run.  Now to create a menu entry go to System > Preferences > Main Menu.  Add an entry where you wish and point it to "/dir/songbird/sonbird/songbird.sh" and you'll know its a script by the icon.  This has never failed for me.  The community "auto installers" always suck and never seem to fully work the way I want.  I believe their is a repository for songbird but I always just get it off the website if I experience a bug or want a new version.

Cheers!

_Nano

---

### Post by aptenodytes on 2009-04-09
Thanks. I don't understand how to do almost any of that (I just installed Ubuntu a couple days ago), but I have a good friend who will probably know what all that means, so I'll ask him this afternoon when I see him. I have faith that your answer will solve my problem ... if not, I'll check back in tonight.

Thank you.

---

### Post by Nano_ext3 on 2009-04-09
Your welcome, it should not be hard, if you need a detailed step by step just ask me, your friend should know if he has used linux before. Sorry I didnt say, things like "ls -la" and "chmod" are used in the "Terminal" (Applications > Accessories > Terminal). 

See my blog on how to use the terminal: [My Blog]("http://thelinuxcauldron.wordpress.com/2009/03/20/today-in-terminal-love-thy-cli-basic-terminal-commands-for-new-users/")


Cheers!

_Nano

---

### Post by Nano_ext3 on 2009-04-09
To recap:

[LIST=1]
[*][http://www.getsongbird.com/](http://www.getsongbird.com/)
[*]download the package which should be a "tar.gz" file which is just like a .zip file but slightly diff.
[*]Go to that folder with your file manager aka "my computer"
[*]Right click > Extract Here
[*]Open up terminal , Applications > Accessories > Terminal
[*]"cd /dir/to/songbird" where the dir is the path to the place you extracted the folder.  If you click on the notepad icon to on the "address bar" in your file manager it should switch views to the path in the format of "/xx/xx/xx/file"
[*]do a "ls -la" in that dir in Terminal
[*]do "./sonbgird.sh" , or what they call the the sh file.  That is a "script file" that can be run.
[*]If it does not run, do "chmod u+x songbird.sh" then run it again like above
[*]To add this to your menu, go to System > Preferences > Main Menu
[*]Add a "new item" in the menu you want , and browse to that same script file in the dir you extracrted the initial tar.gz file
[/LIST]

There ya go,

Cheer!

_Nano

---

### Post by aptenodytes on 2009-04-09
Thank you, that is exactly what I needed. I'm gonna try it right now and will report back.

---

### Post by aptenodytes on 2009-04-09
[Never mind, problem solved]

---

### Post by MysticGold04 on 2009-04-09
To be honest with you, I'd get rid of what you have and go grab the appropriate .deb from here for your machine, so that if you have unsolved dependencies, package manager will install them... 

```

http://www.getdeb.net/

```

---

### Post by aptenodytes on 2009-04-09
Problem solved!

Thanks to both of you for all the assistance.

---

### Post by MysticGold04 on 2009-04-13
Glad to share my limited knowledge (getting better every day) and that it might have helped! :)

---

### Post by Plan B on 2009-06-11
I have songbird installed and working.  It appears in the apps menu.  But when I right click on an MP3 file in a folder I don't get the option to open it with songbird, only VLC or Rhythmbox, or other application (and songbird isn't in that list).

How can I fix this?

---

### Post by Greenwidth on 2009-06-11
> **Plan B said:**
> I have songbird installed and working.  It appears in the apps menu.  But when I right click on an MP3 file in a folder I don't get the option to open it with songbird, only VLC or Rhythmbox, **or other application** (and songbird isn't in that list).

How can I fix this?

You should see "Use a custom command" underneath the list of programs in use other application, click browse and point it at songbird. If you installed by .deb it should be in /usr/bin, or from tar, where you put the extracted tar.

---

### Post by Plan B on 2009-06-11
Thanks, it's working now.


Sweet.
:)

---

### Post by evol|love on 2009-06-13
FYI - There is no "songbird.sh."  The script is just called "sonbird."

---

### Post by abhigyan91 on 2009-06-16
hey i have the same problem.. i installed songbird drom the deb file i got from getdeb but it doesnt seem to be opening. Ill try and install it from the tar file but in the mean time how do i remove the earlier installation? should i just go to the appropriate folder and manually delete all the files? 

also.. is songbird worth all this hassle? is there a better music player..(in the leagues of itunes)?

---

### Post by abhigyan91 on 2009-06-17
i tried installing the songbird software from the tar file.. it doesnt work :( this is what it says when i run 'songbird' in the terminal:



> 
abhigyan@abhigyan-laptop:~/Songbird$ ./songbird
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0xb38727a0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d44454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d464b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb34e1141]
/usr/lib/libvisual-0.4.so.0[0xb34d8407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb34d85e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb34e7ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb35181f4]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so[0xb3ea52f6]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3ea5bad]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so[0xb3eb0822]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3eb09c7]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so[0xb3e60a44]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so[0xb3e60f30]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so[0xb3e61589]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so[0xb3e61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b45803]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3e5fd1b]
/home/abhigyan/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3e5fe25]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3dad6a3]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3db5a65]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3dbee16]
/home/abhigyan/Songbird/xulrunner/libxul.so[0xb7604a85]
/home/abhigyan/Songbird/xulrunner/libxul.so[0xb7603f47]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3dbbee3]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3dbbf0d]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3dbb6b9]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3db4471]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3db4c40]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3db59c5]
/home/abhigyan/Songbird/lib/sbGStreamerMediacore.so[0xb3dbee16]
/home/abhigyan/Songbird/xulrunner/libxul.so[0xb7604a85]
/home/abhigyan/Songbird/components/sbMediacoreManager.so[0xb4fdfe71]
/home/abhigyan/Songbird/components/sbMediacoreManager.so[0xb4fdfe9e]
/home/abhigyan/Songbird/components/sbMediacoreManager.so[0xb4fdf739]
/home/abhigyan/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4fc8705]
/home/abhigyan/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4fc62d7]
/home/abhigyan/Songbird/components/sbMediacoreManager.so[0xb4fc6654]
/home/abhigyan/Songbird/xulrunner/libxul.so[0xb75e1773]
/home/abhigyan/Songbird/xulrunner/libxul.so[0xb75e1d18]
/home/abhigyan/Songbird/xulrunner/libxul.so[0xb6e75be0]
/home/abhigyan/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6e738c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7ceb685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:06 433886     /home/abhigyan/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:06 433886     /home/abhigyan/Songbird/songbird-bin
08aa3000-08ac4000 rw-p 08aa3000 00:00 0          [heap]
b34c7000-b3503000 r-xp 00000000 08:06 615693     /usr/lib/libvisual-0.4.so.0.0.0
b3503000-b3504000 r--p 0003b000 08:06 615693     /usr/lib/libvisual-0.4.so.0.0.0
b3504000-b3505000 rw-p 0003c000 08:06 615693     /usr/lib/libvisual-0.4.so.0.0.0
b350b000-b3511000 rw-p b350b000 00:00 0 
b3516000-b351c000 r-xp 00000000 08:06 630293     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b351c000-b351d000 r--p 00005000 08:06 630293     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b351d000-b351e000 rw-p 00006000 08:06 630293     /usr/lib/gstreamer-0.10/libgstlibvisual.so
b351e000-b3520000 r-xp 00000000 08:06 278055     /lib/libkeyutils-1.2.so
b3520000-b3522000 rw-p 00001000 08:06 278055     /lib/libkeyutils-1.2.so
b3522000-b3529000 r-xp 00000000 08:06 615461     /usr/lib/libkrb5support.so.0.1
b3529000-b352a000 r--p 00006000 08:06 615461     /usr/lib/libkrb5support.so.0.1
b352a000-b352b000 rw-p 00007000 08:06 615461     /usr/lib/libkrb5support.so.0.1
b352b000-b352d000 r-xp 00000000 08:06 278032     /lib/libcom_err.so.2.1
b352d000-b352e000 r--p 00001000 08:06 278032     /lib/libcom_err.so.2.1
b352e000-b352f000 rw-p 00002000 08:06 278032     /lib/libcom_err.so.2.1
b352f000-b3551000 r-xp 00000000 08:06 613359     /usr/lib/libk5crypto.so.3.1
b3551000-b3552000 r--p 00022000 08:06 613359     /usr/lib/libk5crypto.so.3.1
b3552000-b3553000 rw-p 00023000 08:06 613359     /usr/lib/libk5crypto.so.3.1
b3553000-b35e2000 r-xp 00000000 08:06 614857     /usr/lib/libkrb5.so.3.3
b35e2000-b35e4000 r--p 0008e000 08:06 614857     /usr/lib/libkrb5.so.3.3
b35e4000-b35e5000 rw-p 00090000 08:06 614857     /usr/lib/libkrb5.so.3.3
b35e5000-b360e000 r-xp 00000000 08:06 613249     /usr/lib/libgssapi_krb5.so.2.2
b360e000-b360f000 r--p 00028000 08:06 613249     /usr/lib/libgssapi_krb5.so.2.2
b360f000-b3610000 rw-p 00029000 08:06 613249     /usr/lib/libgssapi_krb5.so.2.2
b3610000-b362f000 r-xp 00000000 08:06 1201932    /usr/lib/libneon-gnutls.so.27.1.2
b362f000-b3630000 r--p 0001e000 08:06 1201932    /usr/lib/libneon-gnutls.so.27.1.2
b3630000-b3631000 rw-p 0001f000 08:06 1201932    /usr/lib/libneon-gnutls.so.27.1.2
b3631000-b363f000 r-xp 00000000 08:06 614047     /usr/lib/libid3tag.so.0.3.0
b363f000-b3641000 rw-p 0000d000 08:06 614047     /usr/lib/libid3tag.so.0.3.0
b3641000-b3657000 r-xp 00000000 08:06 614665     /usr/lib/libmad.so.0.2.1
b3657000-b3658000 r--p 00015000 08:06 614665     /usr/lib/libmad.so.0.2.1
b3658000-b3659000 rw-p 00016000 08:06 614665     /usr/lib/libmad.so.0.2.1
b365d000-b365f000 rw-p b365d000 00:00 0 
b365f000-b3663000 r-xp 00000000 08:06 630221     /usr/lib/gstreamer-0.10/libgstbayer.so
b3663000-b3664000 r--p 00003000 08:06 630221     /usr/lib/gstreamer-0.10/libgstbayer.so
b3664000-b3665000 rw-p 00004000 08:06 630221     /usr/lib/gstreamer-0.10/libgstbayer.so
b3665000-b3668000 r-xp 00000000 08:06 630272     /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b3668000-b3669000 r--p 00002000 08:06 630272     /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b3669000-b366a000 rw-p 00003000 08:06 630272     /usr/lib/gstreamer-0.10/libgstvcdsrc.so
b366a000-b367a000 r-xp 00000000 08:06 630098     /usr/lib/gstreamer-0.10/libgstmad.so
b367a000-b367b000 r--p 0000f000 08:06 630098     /usr/lib/gstreamer-0.10/libgstmad.so
b367b000-b367c000 rw-p 00010000 08:06 630098     /usr/lib/gstreamer-0.10/libgstmad.so
b367c000-b3681000 r-xp 00000000 08:06 615576     /usr/lib/libraw1394.so.8.2.0
b3681000-b3682000 r--p 00004000 08:06 615576     /usr/lib/libraw1394.so.8.2.0
b3682000-b3683000 rw-p 00005000 08:06 615576     /usr/lib/libraw1394.so.8.2.0
b3683000-b368f000 r-xp 00000000 08:06 615355     /usr/lib/libiec61883.so.0.1.0
b368f000-b3690000 rw-p 0000b000 08:06 615355     /usr/lib/libiec61883.so.0.1.0
b3691000-b3696000 r-xp 00000000 08:06 630251     /usr/lib/gstreamer-0.10/libgstneonhttpsrc.so
b3696000-b3697000 r--p 00004000 08:06 630251     /usr/lib/gstreamer-0.10/libgstneonhttpsrc.so
b3697000-b3698000 rw-p 00005000 08:06 630251     /usr/lib/gstreamer-0.10/libgstneonhttpsrc.so
b3698000-b369f000 r-xp 00000000 08:06 630096     /usr/lib/gstreamer-0.10/libgstdvdsub.so
b369f000-b36a0000 r--p 00006000 08:06 630096     /usr/lib/gstreamer-0.10/libgstdvdsub.so
b36a0000-b36a1000 rw-p 00007000 08:06 630096     /usr/lib/gstreamer-0.10/libgstdvdsub.so
b36a1000-b36ab000 r-xp 00000000 08:06 630304     /usr/lib/gstreamer-0.10/libgst1394.so
b36ab000-b36ac000 r--p 00009000 08:06 630304     /usr/lib/gstreamer-0.10/libgst1394.so
b36ac000-b36ad000 rw-p 0000a000 08:06 630304     /usr/lib/gstreamer-0.10/libgst1394.so
b36ad000-b36c4000 r-xp 00000000 08:06 630284     /usr/lib/gstreamer-0.10/libgsttcp.so
b36c4000-b36c5000 r--p 00016000 08:06 630284     /usr/lib/gstreamer-0.10/libgsttcp.so
b36c5000-b36c6000 rw-p 00017000 08:06 630284     /usr/lib/gstreamer-0.10/libgsttcp.so
b36c6000-b36d6000 r-xp 00000000 08:06 615327     /usr/lib/libhal.so.1.0.0






then it just stops and nothing happens...

---

### Post by Greenwidth on 2009-06-17
@abhigyan91
I had that problem when trying out the beta, after removing libvisual plugins it worked fine.

```
sudo apt-get remove libvisual-0.4-plugins
```

---

### Post by abhigyan91 on 2009-06-22
> **Greenwidth said:**
> @abhigyan91
I had that problem when trying out the beta, after removing libvisual plugins it worked fine.

```
sudo apt-get remove libvisual-0.4-plugins
```


sweet... thanks a lot buddy..
how did you figure something like this out? uninstall a random file and viola.. its working!! proism..

---

### Post by ChaiTan on 2009-06-22
> **abhigyan91 said:**
> sweet... thanks a lot buddy..
how did you figure something like this out? uninstall a random file and viola.. its working!! proism..
Well in the error itself theres a line near the top:
```
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb34e1141]
```

---

### Post by abhigyan91 on 2009-06-23
oh.. i didn't even know that that was supposed to indicate an error!! (me ultra noob)
can you help me understand the output ChaiTan? thanks for your patience..

---

