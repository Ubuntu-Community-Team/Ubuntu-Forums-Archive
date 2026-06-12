---
title: "804x86 - SCIM missbehaviour"
date: 2008-05-08
forum: Desktop Environments
---

### Post by xerman on 2008-05-08
Hello there:

As for the late updates in 804, I've been experiencing the following issues, NOT SOLVED yet.

Preface:

Ubuntu - Gnome 804x86
2GB RAM, 250GB HD, Bluetooth dongle
LOgitech WAVE desktop
Spanish Gnome Session CJK Support with support only for Chinese and Russian

1- Chinese fonts look chopped everywhere:
[INDENT]Window title[/INDENT]
[INDENT]Nautilus File Icon name[/INDENT]
[INDENT]Default font face in any app[/INDENT]
(This did not happen in 704 or 710. So I presume there was some change in default CJK fonts in 804, or font rendering, or whatever...)

2- When Firefox gets control of SCIM no other app is able to type again in CJK:
[INDENT]When using GTK App with SCIM Chinese, and switch app to Firefox, it is possible to type chinese in Firefox.
When switching back to GTK App, seems like SCIM got locked by Firefox and there is no way to type Chinese.
The only way to type Chinese Again is to deactivate SCIM and Reactivate SCIM Again.[/INDENT]

3- When SCIM active: Alternating from Chinese to Latin by pressing the appropriate key, in Latin mode there is no way to type acute vowels (áéíóó) while it is possible to type ñ.

4- When SCIM active: Selecting a phrase in the list in the float table causes phrase to be placed in another place different than cursor on current document. [INDENT]E.G.: Use any text doc app, ooo writer, gedit, evolution, ... and have some lines of text in it. Try to type in the middle of the document and write a chinese sentence, most of the time, when selecting the global sentence to be placed on the document, instead of being placed over cursor position, it gets located somewhere else. This implies do some copy/cut/paste to get the sentence in its right place.
[/INDENT]

Today I ASK the forum managers to open a Forum Category to deal specifically with multilanguage support, so all multilanguage issues could be grouped and easily accessed.

Thanks all.
Regards

Xerman

---

### Post by Zorael on 2008-05-08
> **xerman said:**
> 2- When Firefox gets control of SCIM no other app is able to type again in CJK:
[INDENT]When using GTK App with SCIM Chinese, and switch app to Firefox, it is possible to type chinese in Firefox.
When switching back to GTK App, seems like SCIM got locked by Firefox and there is no way to type Chinese.
The only way to type Chinese Again is to deactivate SCIM and Reactivate SCIM Again.[/INDENT]
I think I can help you with this one, at least.

Open up **/etc/X11/xinit/xinput.d/scim** in an editor with superuser permissions, such as by opening a run box with Alt+F2 and entering **gksu gedit /etc/X11/xinit/xinput.d/scim**. Edit the appropriate lines to make it look like this.
```
XIM=SCIM
XIM_PROGRAM=**/usr/bin/scim**
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes
GTK_IM_MODULE=**"scim-bridge"**
QT_IM_MODULE=**"scim-bridge"**
```
Also, you may want to make sure you've chosen something scim-related when entering the following command.
```
$ sudo update-alternatives --config xinput-all_ALL
```
The output should look something like this.
```
There are 4 alternatives which provide `xinput-all_ALL'.

  Selection    Alternative
-----------------------------------------------
*         1    /etc/X11/xinit/xinput.d/skim
 +        2    /etc/X11/xinit/xinput.d/default
          3    /etc/X11/xinit/xinput.d/default-xim
          4    /etc/X11/xinit/xinput.d/none

Press enter to keep the default[*], or type selection number:
```
I'm running KDE so I don't have the standard scim alternatives, and obviously if you're running Gnome you can't choose skim. But if there's scim-bridge or scim there, pick it.

More semi-relevant info at [http://ubuntuforums.org/showthread.php?p=4878631#post4878631](http://ubuntuforums.org/showthread.php?p=4878631#post4878631).

---

### Post by Zorael on 2008-05-08
Update: FF3 still suppresses the SCIM toolbar, but the input method itself works after modifying said file.

---

### Post by xerman on 2008-05-13
Zorael,

Scim config is already good, so it is not something scim-config-file related. I presume this issue has something to do with default gnome fonts for CJK sessions, as using Feisty (Now at work) the font used for Chinese is different than the one used in 804. So while on Nautilus, or wherever, default font looks nice in 704 while looks like a chopped bitmap in 804.

The firefox thing, I presume is related with firefox programming and its integration in the gnome environment. Using another web browser, more gnome friendly does not produce this issue.

Regards
Xermán

---

