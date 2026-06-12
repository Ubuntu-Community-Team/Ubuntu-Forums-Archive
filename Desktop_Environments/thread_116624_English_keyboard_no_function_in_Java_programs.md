---
title: "English keyboard: no function in Java programs"
date: 2006-01-13
forum: Desktop Environments
---

### Post by esperantisto on 2006-01-13
I have installed Sun's Java Runtime Environent v. 1.5.0_06 (the latest available) and removed the JVM that came with Ubuntu originally. I've used one of FAQs found here:
- donwloaded JRE as a .bin file;
- became root;
- did:
```
mv jre-1_5_0_06-linux-i586.bin /usr/local
cd /usr/local
chmod a+x jre-1_5_0_06-linux-i586.bin
sh jre-1_5_0_06-linux-i586.bin 
```
and accepted the license agreement etc.
- then installed it for FireFox:
```
cd /usr/lib/mozilla-firefox/plugins
ln -s /usr/local/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so
```
- then
```
ln -sf /usr/local/jre1.5.0_06/bin/java_vm /usr/bin/java_vm
update-alternatives --install /usr/bin/java java /usr/local/jre1.5.0_06/bin/java 1 
```

So, now Sun JRE 1.5.0_06 is the only in the system.

I tried to launch two programs: Tekstilo (text editor, [http://www.javamul.org](http://www.javamul.org)) and OmegaT (CAT tool [http://www.omegat.org/omegat/omegat.html](http://www.omegat.org/omegat/omegat.html)) both with one strange and disappointing result: the programs do run, but the English (US) keyboard layout does not function in any of them (also it's not problem in other programs: OOo, gedit, vim and termial), so no character can be typed in, and no keyboard shortcut (such as Ctrl+O to open a file) works. I have two more layouts installed: Belarusian and Russian. With both, however, I can type (although shortcuts do not function either) and the respective characters appear correctly.

Any advise?

---

### Post by esperantisto on 2006-01-17
What, no ideas?

I see in the command line the following:
```
/usr/share/themes/Human/gtk-2.0/gtkrc:7: Failed to parse property value " GTK_SH ADOW_NONE " for `GtkMenuItem::shadow-type'
/usr/share/themes/Human/gtk-2.0/gtkrc:58: Engine "clearlooks" is unsupported, ig noring 
```

Might this cause the problem? How to rectify?

---

