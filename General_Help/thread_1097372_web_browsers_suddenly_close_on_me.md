---
title: "web browsers suddenly close on me"
date: 2009-03-15
forum: General Help
---

### Post by jli024 on 2009-03-15
i am new to ubuntu and dont know much, so if replies can be written out as simple to read as possible, that would be greatly appreciated. i do have an okay knowledge of using the terminal basic ubuntu-ness. 
web browsers keep suddenly closing on me, and it started off annoying, and has gotten to be a problem. i tried downloading and using differant browsers like seamonkey, but found the same problem. it actually just suddenly exxited out and i restored it luckily to find that this txt is still here. they just suddenly close out..

---

### Post by fragos on 2009-03-16
There's little you can do unless a Firefox extesion is the cause. You can disable all extensions and bring them back one at a time. There are some browser bugs which can cause a crash regardless of extensions. I've changed to Epiphany which uses the same Gecko rendering engine as Firefox. It only occasionaly crashs for me when closing a tab. It also restarts much faster than Firefox or Seamonkey. Being faster and more stable are where Epiphany wins. Since the occassional crash only happens when closing a tab I don't loose anything and Epiphany restarts exactly where it would be if the tab just closed.

If the browser crashed when starting you could delete the configuration files or try starting the browser on the command line with a text file argument which would clear out some elements of the configuration.

---

### Post by jwbrase on 2009-03-16
Have you tried Opera? I switched to it after having the same problem with Firefox.

---

### Post by fragos on 2009-03-16
> **jwbrase said:**
> Have you tried Opera? I switched to it after having the same problem with Firefox.

I used Opera a ways back but I'm not interested in the PIM extras in Opera as I've settled on the GPE PIM family which runs both on my Ubuntu desktop and my Nokia N810 handheld.

---

### Post by jli024 on 2009-03-16
is opera on the synapic pack manager, if so, whats it called exactly?

---

### Post by fragos on 2009-03-16
It doesn't appear in the Ubuntu repositories but you can download a package tailored for your version of Ubuntu at [http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by Bapabooiee on 2009-03-16
> **jli024 said:**
> is opera on the synapic pack manager, if so, whats it called exactly?

Actually, Opera is not the Ubuntu repository, so you'll have to download it from Opera's website and use dpkg to install it...

That, oooooooor you can check the following link out - it has a list of some pretty epic repositories you should add. One of the listed ones is Opera's repository, so you'll be able to install it via apt-get or synaptic ^_^

[http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html]("http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html")

---

### Post by csmgj on 2009-07-18
Well, I'm about to go nuts. I am an experienced user, but new to Linux. I have Ubuntu Hardy installed on a T61 Lenovo Laptop. First it was browsers closing on me. I tried other browsers, but they also closed. I disabled Totem on Mozilla to no avail. I think it has closed out other programs. BUT IT IS ANNOYING AS HELL. Sorry to yell, but I'm quite aggravated. If you could give me some tips on getting to the bottom of this, I'd appreciate it. I don't see any reason why Ubuntu shouldn't be able to run Mozilla. 

Thanks.

---

### Post by ArchCast on 2009-07-18
Did any of the webpages have Flash right before the browsers closes on you, by any chance?

---

### Post by csmgj on 2009-08-02
Could be. Seems generally there is several tabs open. Often facebook tabs. Seems GMail is flash too, so that could be the issue. What can I do? Is there any logs I can check?

---

### Post by ArchCast on 2009-08-02
> **csmgj said:**
> Could be. Seems generally there is several tabs open. Often facebook tabs. Seems GMail is flash too, so that could be the issue. What can I do? Is there any logs I can check?

GMail uses Flash to upload files at certain points, although that can be changed in: Settings -> Attachments -> Basic attachment features - Attach one file at a time and don't show progress bars.

---

### Post by fragos on 2009-08-02
Try starting Firefox from a terminal window. When the ap crashes you should get some messages in the terminal window. Note that closing the terminal window will also close any ap, Firefox in this case, as well.

---

### Post by csmgj on 2009-08-04
Ok, trying terminal. Left Mozilla up all day. Still no problems. Just figured I'd post what I have so far, and will definitely post again when it crashes. Thanks.

user@marty-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

---

### Post by kspringer on 2009-08-04
I use Hardy also and had this problem for months.

Finally found this somewhere in the forum here:

Move or rename the hidden folder .macromedia in your home directory.

I moved mine from .macromedia to .macromediaold.  It worked great for me!


k

---

### Post by csmgj on 2009-08-05
Well, let's see if this posts. Usually if I don't reboot, Firefox will keep on crashing:
user@marty-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault
user@marty-laptop:~$ 
user@marty-laptop:~$ firefox
Segmentation fault
user@marty-laptop:~$ 
user@marty-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

Let's see, everything was good, and then the graphical part of Ubuntu restarted. I then opened firefox again using the terminal, and it ended even before I went anywhere. Sure would like to know what "Segmentation fault" is.

---

### Post by csmgj on 2009-08-06
I even tried renaming my .macromedia folder to .macromedia.old and restarted firefox only to immediately get the Segmentation Fault.

---

### Post by fragos on 2009-08-06
Have you tried disabling all extensions and then adding them back one at a time to see if they are the cause to the segmentation faults?

---

### Post by csmgj on 2009-08-14
I turned them all off. Then turned on a couple to watch a video, and it gave me the first segmentation fault. Then I disabled all, and started it again, and it froze and gave me an interesting error message:

user@marty-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault
user@marty-laptop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
*** glibc detected *** /usr/lib/firefox-3.0.8/firefox: double free or corruption (out): 0x0c332410 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d84a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7d884f0]
/usr/lib/xulrunner-1.9.0.8/libmozjs.so[0xb7c91309]
/usr/lib/xulrunner-1.9.0.8/libmozjs.so[0xb7c5059c]
/usr/lib/xulrunner-1.9.0.8/libmozjs.so(JS_GC+0x45)[0xb7c2c5fc]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb7158488]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb792a7b6]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb792a87c]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb7510f30]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb751238a]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb78f7d5b]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb78f83a8]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb743445c]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb792166a]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb7921c43]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb791f176]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb78ee607]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb786f3e2]
/usr/lib/xulrunner-1.9.0.8/libxul.so[0xb76fe7f6]
/usr/lib/xulrunner-1.9.0.8/libxul.so(XRE_main+0x2020)[0xb714f0b0]
/usr/lib/firefox-3.0.8/firefox[0x8049033]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d2f450]
/usr/lib/firefox-3.0.8/firefox[0x8048cc1]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:07 721174     /usr/lib/firefox-3.0.8/firefox
0804f000-08050000 rw-p 00006000 08:07 721174     /usr/lib/firefox-3.0.8/firefox
08050000-0c6a6000 rw-p 08050000 00:00 0          [heap]
ad37f000-ad380000 ---p ad37f000 00:00 0 
ad380000-adb80000 rwxp ad380000 00:00 0 
ae381000-ae382000 ---p ae381000 00:00 0 
ae382000-aeb82000 rwxp ae382000 00:00 0 
aeb82000-aec01000 rw-p aeb82000 00:00 0 
aecd0000-aedd1000 rw-p aecd0000 00:00 0 
aedd1000-aee7c000 r--p 00000000 08:07 624693     /usr/share/icons/Tangerine/icon-theme.cache
aeefd000-aeeff000 r-xp 00000000 08:07 15712350   /lib/libnss_mdns4.so.2
aeeff000-aef00000 rw-p 00001000 08:07 15712350   /lib/libnss_mdns4.so.2
aef06000-aef12000 r-xp 00000000 08:07 410094     /usr/lib/gnome-vfs-2.0/modules/libfile.so
aef12000-aef13000 rw-p 0000b000 08:07 410094     /usr/lib/gnome-vfs-2.0/modules/libfile.so
aef8e000-af2df000 rw-p aef8e000 00:00 0 
af2df000-af300000 ---p af2df000 00:00 0 
af300000-af500000 rw-p af300000 00:00 0 
af500000-af600000 rw-p af500000 00:00 0 
afd0b000-afdcc000 rw-p afd0b000 00:00 0 
afdcc000-afe47000 r--p 00000000 08:07 525958     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
afe47000-afe8b000 r--p 00000000 08:07 525962     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Italic.ttf
afed0000-aff15000 r-xp 00000000 08:07 426614     /usr/lib/mozilla/plugins/mplayerplug-in.so
aff15000-aff17000 rw-p 00045000 08:07 426614     /usr/lib/mozilla/plugins/mplayerplug-in.so
aff17000-aff5c000 r-xp 00000000 08:07 426642     /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
aff5c000-aff5e000 rw-p 00044000 08:07 426642     /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
aff5e000-affa3000 r-xp 00000000 08:07 426646     /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
affa3000-affa5000 rw-p 00044000 08:07 426646     /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
affa5000-affea000 r-xp 00000000 08:07 426644     /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
affea000-affec000 rw-p 00044000 08:07 426644     /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
affec000-b0031000 r-xp 00000000 08:07 426648     /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
b0031000-b0033000 rw-p 00044000 08:07 426648     /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
b0033000-b0060000 r-xp 00000000 08:07 819254     /usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/libjavaplugin_nscp.so
b0060000-b0066000 rw-p 0002d000 08:07 819254     /usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/libjavaplugin_nscp.so
b0066000-b007c000 r-xp 00000000 08:07 827396     /usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so
b007c000-b0080000 rw-p 00015000 08:07 827396     /usr/lib/jvm/java-6-sun-1.6.0.07/jre/plugin/i386/ns7/libjavaplugin_oji.so
b0080000-b0095000 r-xp 00000000 08:07 475885     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
b0095000-b0096000 rw-p 00014000 08:07 475885     /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
b0096000-b00a7000 r-xp 00000000 08:07 475884     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b00a7000-b00a8000 rw-p 00010000 08:07 475884     /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
b00a8000-b00bf000 r-xp 00000000 08:07 475378     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b00bf000-b00c0000 rw-p 00017000 08:07 475378     /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
b00c0000-b00d2000 r-xp 00000000 08:07 475377     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
b00d2000-b00d3000 rw-p 00012000 08:07 475377     /usr/lib/totem/gstreamer/libtotem-cone-plugin.so
b00d3000-b00ea000 r-xp 00000000 08:07 475376     /usr/lib/totem/gstreamer/libtotem-complex-plugin.so
b00ea000-b00eb000 rw-p 00017000 08:07 475376     /usr/lib/totem/gstreamer/libtotem-complex-plugin.so
b00eb000-b00fc000 r--s 00000000 08:07 475464     /usr/share/mime/mime.cache
b00fc000-b10fc000 rw-p b00fc000 00:00 0 
b10ff000-b110e000 r-xp 00000000 08:07 475375     /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
b110e000-b110f000 rw-p 0000f000 08:07 475375     /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
b110f000-b1a7c000 r-xp 00000000 08:07 410166     /usr/lib/adobe-flashplugin/libflashplayer.so
b1a7c000-b1aaf000 rw-p 0096c000 08:07 410166     /usr/lib/adobe-flashplugin/libflashplayer.so
b1aaf000-b1b9a000 rw-p b1aaf000 00:00 0 
b1bae000-b1baf000 ---p b1bae000 00:00 0 
b1baf000-b23af000 rwxp b1baf000 00:00 0 
b23af000-b23f4000 r-xp 00000000 08:07 393732     /usr/lib/nss/libnssckbi.so
b23f4000-b23ff000 rw-p 00044000 08:07 393732     /usr/lib/nss/libnssckbi.so
b23ff000-b2439000 r-xp 00000000 08:07 393651     /usr/lib/nss/libfreebl3.so
b2439000-b243a000 rw-p 0003a000 08:07 393651     /usr/lib/nss/libfreebl3.so
b243a000-b245a000 r-xp 00000000 08:07 393731     /usr/lib/nss/libnssdbm3.so
b245a000-b245b000 rw-p 0001f000 08:07 393731     /usr/lib/nss/libnssdbm3.so
b245b000-b24be000 r-xp 00000000 08:07 378933     /usr/lib/libsqlite3.so.0.8.6
b24be000-b24c0000 rw-p 00062000 08:07 378933     /usr/lib/libsqlite3.so.0.8.6
b24c0000-b24f0000 r-xp 00000000 08:07 393730     /usr/lib/nss/libsoftokn3.so
b24f0000-b24f1000 rw-p 00030000 08:07 393730     /usr/lib/nss/libsoftokn3.so
b24f1000-b24f2000 ---p b24f1000 00:00 0 
b24f2000-b2cf2000 rwxp b24f2000 00:00 0 
b2cf2000-b2cf4000 r-xp 00000000 08:07 15712351   /lib/libnss_mdns4_minimal.so.2
b2cf4000-b2cf5000 rw-p 00001000 08:07 15712351   /lib/libnss_mdns4_minimal.so.2
b2d08000-b2d09000 ---p b2d08000 00:00 0 
b2d09000-b3509000 rwxp b2d09000 00:00 0 
b3539000-b357e000 r--p 00000000 08:07 525929     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
b357e000-b3584000 r-xp 00000000 08:07 410143     /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so
b3584000-b3585000 rw-p 00006000 08:07 410143     /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so
b3585000-b3616000 r--p 00000000 08:07 525926     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b3642000-b365b000 r--p 00000000 08:07 540738     /usr/share/fonts/type1/gsfonts/n021003l.pfb
b366c000-b3683000 r--p 00000000 08:07 540744     /usr/share/fonts/type1/gsfonts/n021023l.pfb
b368f000-b36a5000 r--p 00000000 08:07 540747     /usr/share/fonts/type1/gsfonts/n021024l.pfb
b36a5000-b36be000 r--p 00000000 08:07 540741     /usr/share/fonts/type1/gsfonts/n021004l.pfb
b36be000-b36de000 r-xp 00000000 08:07 409816     /usr/lib/gio/modules/libgvfsdbus.so
b36de000-b36df000 rw-p 0001f000 08:07 409816     /usr/lib/gio/modules/libgvfsdbus.so
b36df000-b37e3000 rw-p b36df000 00:00 0 
b37e3000-b386a000 r--p 00000000 08:07 525925     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b386a000-b389c000 r-xp 00000000 08:07 378308     /usr/lib/libcroco-0.6.so.3.0.1
b389c000-b389f000 rw-p 00031000 08:07 378308     /usr/lib/libcroco-0.6.so.3.0.1
b389f000-b38cf000 r-xp 00000000 08:07 378562     /usr/lib/libgsf-1.so.114.0.7
b38cf000-b38d2000 rw-p 0002f000 08:07 378562     /usr/lib/libgsf-1.so.114.0.7
b38d2000-b38d3000 rw-p b38d2000 00:00 0 
b38d3000-b397e000 r--p 00000000 08:07 624693     /usr/share/icons/Tangerine/icon-theme.cache
b397e000-b3b00000 rw-p b397e000 00:00 0 
b3b00000-b3b02000 r-xp 00000000 08:07 378951     /usr/lib/libtotem-plparser-mini.so.10.1.1
b3b02000-b3b03000 rw-p 00001000 08:07 378951     /usr/lib/libtotem-plparser-mini.so.10.1.1
b3b03000-b3b33000 r-xp 00000000 08:07 378885     /usr/lib/librsvg-2.so.2.22.2
b3b33000-b3b34000 rw-p 00030000 08:07 378885     /usr/lib/librsvg-2.so.2.22.2
b3b34000-b3b7f000 r--p 00000000 08:07 525930     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf
b3b86000-b3b8e000 r-xp 00000000 08:07 378957     /usr/lib/libtrackerclient.so.0.0.0
b3b8e000-b3b8f000 rw-p 00007000 08:07 378957     /usr/lib/libtrackerclient.so.0.0.0
b3b8f000-b3b9e000 r-xp 00000000 08:07 378391     /usr/lib/libhal.so.1.0.0
b3b9e000-b3b9f000 rw-p 0000e000 08:07 378391     /usr/lib/libhal.so.1.0.0
b3ba1000-b3bb2000 r--s 00000000 08:07 475464     /usr/share/mime/mime.cache
b3bb2000-b3bb5000 r-xp 00000000 08:07 15712287   /lib/libattr.so.1.1.0
b3bb5000-b3bb6000 rw-p 00002000 08:07 15712287   /lib/libattr.so.1.1.0
b3bb6000-b3bbd000 r-xp 00000000 08:07 378402     /usr/lib/libfam.so.0.0.0
b3bbd000-b3bbe000 rw-p 00006000 08:07 378402     /usr/lib/libfam.so.0.0.0
b3bbe000-b3bc4000 r-xp 00000000 08:07 15712281   /lib/libacl.so.1.1.0
b3bc4000-b3bc5000 rw-p 00005000 08:07 15712281   /lib/libacl.so.1.1.0
b3bc7000-b3bca000 r-xp 00000000 08:07 460550     /usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so
b3bca000-b3bcb000 rw-p 00002000 08:07 460550     /usr/lib/pango/1.6.0/modules/pango-hebrew-fc.so
b3bcb000-b3be8000 r-xp 00000000 08:07 409815     /usr/lib/gio/modules/libgiohal-volume-monitor.so
b3be8000-b3be9000 rw-p 0001c000 08:07 409815     /usr/lib/gio/modules/libgiohal-volume-monitor.so
b3be9000-b3bed000 r-xp 00000000 08:07 475571     /usr/lib/xulrunner-addons/plugins/libnullplugin.so
b3bed000-b3bee000 rw-p 00003000 08:07 475571     /usr/lib/xulrunner-addons/plugins/libnullplugin.so
b3bee000-b3bf2000 r-xp 00000000 08:07 15738351   /lib/tls/i686/cmov/libnss_dns-2.7.so
b3bf2000-b3bf4000 rw-p 00003000 08:07 15738351   /lib/tls/i686/cmov/libnss_dns-2.7.so
b3bf4000-b3c03000 r-xp 00000000 08:07 15712294   /lib/libbz2.so.1.0.4
b3c03000-b3c04000 rw-p 0000f000 08:07 157122Killed
user@marty-laptop:~$ 

I hear if you run Firefox as sudo it will take care of this. I guess a segmentation fault is the program going where it shouldn't be. Seems something is wrong. Thanks for your help. I look forward to your reply.

---

### Post by fragos on 2009-08-14
My firefox is version 3.0.13 running on Ubuntu 9.04. Your error messages said 3.0.8. If you currently aren't running Ubuntu 9.04, I'd recommend upgrade. In the past I had problems with firefox and started using Epiphany which has fewer extensions but runs faster. Of late I've been experimenting with Chromium which is the basis of Google Chrome. Chromium is still in development but looks very promising.

---

### Post by csmgj on 2009-08-15
I'm still thinking this is not a problem with web browsers as I have trouble with every web browser and some other programs. I was using open video editor when my machine went haywire. So after rebooting I decided to check out the system log program. I noticed a bunch of SEGFAULTS, so here they are:

Aug 14 11:00:39 marty-laptop kernel: [ 2620.652629] gnome-app-insta[9212]: segfault at 00743334 eip 080f3d1a esp bfc93a70 error 4
Aug 14 11:15:37 marty-laptop kernel: [  445.613096] cxassoc[7370]: segfault at 00b3ff74 eip b7e0947a esp bfa24bd8 error 4
Aug 15 15:15:28 marty-laptop kernel: [  349.693863] torcs-bin[7242]: segfault at 00000000 eip 00000000 esp bf8f050c error 4
Aug 15 16:06:45 marty-laptop kernel: [ 3400.073169] hal-system-kill[9567]: segfault at 8804e8e3 eip 8804e8e3 esp bfbd6f50 error 4
Aug 15 16:06:45 marty-laptop kernel: [ 3400.261894] syslogd-listfil[9575]: segfault at b73c3090 eip b7eda280 esp bfe2b1f8 error 4
Aug 15 16:07:57 marty-laptop kernel: [ 3472.121442] hal-ipw-killswi[9621]: segfault at bff0dc30 eip bff0dc30 esp bfd56d14 error 4
Aug 15 16:08:09 marty-laptop kernel: [ 3484.124715] hal-system-kill[9628]: segfault at 8cc00000 eip 08055ce5 esp bfb89700 error 4
Aug 15 16:09:39 marty-laptop kernel: [ 3574.162673] hal-ipw-killswi[9704]: segfault at bff3c00c eip b7f1d666 esp bfca1c70 error 4
Aug 15 16:09:45 marty-laptop kernel: [ 3579.419211] gnome-mount[9705]: segfault at 40080000 eip 40080000 esp bfd66eac error 4
Aug 15 16:09:45 marty-laptop kernel: [ 3580.170759] hal-ipw-killswi[9710]: segfault at 774481ce eip 774481ce esp bfccbbfc error 4
Aug 15 16:10:25 marty-laptop kernel: [ 3620.034998] nautilus[9759]: segfault at fff20f5b eip b7f82161 esp bfcad11c error 4
Aug 15 16:10:58 marty-laptop kernel: [ 3652.283494] hal-ipw-killswi[9818]: segfault at 4404a07c eip b7f66e68 esp bf8e64c8 error 4
Aug 15 16:11:00 marty-laptop kernel: [ 3655.132387] gnome-system-lo[9820]: segfault at c8b1c6b0 eip b74aa384 esp bff27890 error 5
Aug 15 16:11:13 marty-laptop kernel: [ 3667.628031] x-session-manag[6121]: segfault at 8c535634 eip b78655a2 esp bfec8298 error 4
Aug 15 16:11:21 marty-laptop kernel: [ 3675.355439] gdmgreeter[9858]: segfault at 400c0000 eip b78590f0 esp bf9b3020 error 4
Aug 15 16:11:28 marty-laptop kernel: [ 3682.895285] gdmgreeter[9890]: segfault at 88609890 eip b77f0868 esp bfbb4c00 error 4

My guess would either be a memory issue, or a video issue. I have noticed that Ubuntu will corrupt files copying them from one device to another. Wonder if that is related, or another problem all together. I would try the newer version of Ubuntu but was told there is more issues with newer releases.

---

