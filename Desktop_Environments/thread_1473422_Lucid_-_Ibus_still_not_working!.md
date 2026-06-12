---
title: "Lucid - Ibus still not working!?"
date: 2010-05-05
forum: Desktop Environments
---

### Post by LK_gandalf_ on 2010-05-05
Hi all, I installed Kubuntu 10.04 and wanted to try if, finally, ibus works. 
I installed ibus and ibus-anthy from repository (I need the japanese input), then I launched Ibus preferences from the menu, set it, and the icon appears in the kickbar.
But nothing happens if I press ctrl-space. Same problem there was on 9.10.

I also added the lines to the home/.bashrc as the popup says.

export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus

Do you have any solution? It's really important because until it works I have to use windows, a shame.
Thank you in advance

---

### Post by Zorael on 2010-05-05
Use im-switch instead of modifying .bashrc.

```
$ sudo im-switch -c
```
Pick **ibus** or **ibus-kde**. Omit sudo if you want to make it a user-specific setting. The setting refers to files in **/etc/X11/xinit/xinput.d/**, which you can peruse to see what they actually do. With the latter setting (**ibus-kde**) you'll need to add the Input Method Switcher plasma widget, which in my experience works so-so.

I use UIM instead, which has a native Qt4 widget. Works wonderfully.

---

### Post by LK_gandalf_ on 2010-05-05
I removed and purged the ibus packages (they always carried problems for me) to try UIM.
I installed:
- uim and dependencies
- uim-anthy
- uim-applet-kde

but what should I do now? It seems really difficult to find an updated guide for this things :( I use Kubuntu 10.04 64bit.
Thank you Zorael, you are such an expert on this, you should really create an updated wiki page ;)

EDIT: I found how to launch it, by typing uim-toolbar-gtk-systray in the konsole. In this way it appears the configuration panel, and the icon in the kde-system bar. But now only INPUT PAD works, and it's impossible to write something with it because you have to click on every single symbol...
I was wondering if there is something like on windows?

---

### Post by Zorael on 2010-05-06
Okay, just to be sure it's set up properly;
[list=1][*]Remove those extra variables from your .bashrc. They will just confuse things.
[*]Install: **uim**, **uim-common**, **uim-qt**, **uim-gtk2.0**, **uim-utils** and **uim-xim**.
**uim-qt3** is optional; grab if you still use Qt3 apps. You can also get **uim-applet-kde**, but I find it buggy and inferior to the normal Qt4 applet.
```
$ sudo aptitude install uim uim-common uim-qt uim-gtk2.0 uim-utils uim-xim
```...as well as any *language module-specific* packages. 
[list][*]Japanese: **uim-anthy**
[*]Pinyin: **uim-pinyin**
[*][m17n](http://www.m17n.org/m17n-lib-en/support_input_sum.html): **uim-m17nlib**
[*]Korean: **uim-hangul**
[*]...just do '**apt-cache search uim-**' in a terminal and browse the output to see what there is to pick between. They should pull the needed dependencies automatically.[/list]
[*]Run '**sudo im-switch -c**' and pick **[COLOR="Green"]uim-toolbar-qt[/COLOR]**. If it's not there to pick, make sure you have the **uim-xim** package installed.
[*]Open up **/etc/X11/xinit/xinput.d/uim-toolbar-qt** in a text editor with superuser permissions, such as by hitting Alt+F2 and running '**kdesudo kate /etc/X11/xinit/xinput.d/uim-toolbar-qt**'.
[list][*]Change line *5*: '**QT_IM_MODULE=[COLOR="Red"]uim[/COLOR]**'
to instead read '**QT_IM_MODULE=[COLOR="Green"]xim[/COLOR]**' (until the fixes in [bug 206455](https://bugs.kde.org/show_bug.cgi?id=206455) hit the repos)
[indent]**[COLOR="RoyalBlue"](edit):[/color]** This is fixed in 4.4.3 which is currently in the [Kubuntu Updates ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa) (**ppa:kubuntu-ppa/ppa**). If you use that, just leave this line as '**QT_IM_MODULE=[COLOR="Red"]uim[/COLOR]**' and proceed.[/indent]
[*]Change line *9*: '**XIM_PROGRAM_XTRA="(sleep 10; uim-toolbar-[COLOR="Red"]qt[/COLOR])"**'
to instead read '**XIM_PROGRAM_XTRA="(sleep 10; uim-toolbar-[COLOR="Green"]qt_4_[/COLOR])"**'
[/list]
[*]Log out and back in, or restart the X server, or reboot. Unsure of a simple relogin is enough, but should be.
[/list]
Upon logging in the applet should pop up automatically. Right-click it and pick Preferences to set UIM up, or just run '**uim-pref-qt4**'.

To verify that im-switch is set up as it should, check if those variables you earlier set in .bashrc have now successfully been read from uim-toolbar-qt. See if you get the following output from this command.
```
$ echo -e "\nGTK:\t$GTK_IM_MODULE\nQt4:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS"

GTK:	**uim**
Qt4:	**xim**	*# or* **uim** *if you followed the KDE 4.4.3 instructions above*
XMOD:	**@im=uim**
```
If it does, everything should work. The rest is just to configure UIM and your language module (Anthy et al) in their preferences windows. I only use Anthy (for Japanese), so I don't know much about the others.

---

### Post by cesera on 2010-05-06
Just for your reference: the m17n plugin for uim is called uim-m17nlib.

---

### Post by karatedog on 2010-05-14
Thanks Zorael, it works great!
Can you tell me, how to re-activate the toolbar once I quit it?
uim-pref-qt4 only activates the Preferences window.

---

### Post by Zorael on 2010-05-14
The toolbar binary is called **uim-toolbar-qt4**, obviously located in **/usr/bin**. For what it's worth, it's part of the **uim-qt** package.

There is a GTK toolbar too (**uim-toolbar-gtk**), as well as a GTK system tray applet (**uim-toolbar-gtk-systray**). Aside from loading GTK libraries that you otherwise might not need at startup (depending on what apps you use), the problem is that those are started *before* the QtCurve theming takes effect, that makes your GTK apps look more at home in KDE. In essence this means that both the toolbar and the systray icon will be ugly as sin.

If you really want it as a systray icon instead of a toolbar, the workaround is to set up *KDE* to automatically start it upon login (after QtCurve theming), rather than have X start it way early. To do this, merely comment out the '**XIM_PROGRAM_XTRA="(sleep 15; uim-toolbar-qt4)"**' line in **/etc/X11/xinit/xinput.d/uim-toolbar-qt** (that you modified earlier), by prepending the line with a hashmark/octhorpe (**#**).
```
#XIM_PROGRAM_XTRA="(sleep 15; uim-toolbar-qt4)"
```
Then make a symbolic link in **~/.kde/Autostart** to point to **/usr/bin/uim-toolbar-gtk-systray**.
```
$ ln -s /usr/bin/uim-toolbar-gtk-systray ~/.kde/Autostart/uim-toolbar-gtk-systray
```
I just use the normal Qt4 toolbar and drag it out of the way a bit. But if you have a penchant for system tray icons, it's still an option, albeit an arguably worse one compared to sticking to Qt4 alternatives. Sadly there is no **uim-toolbar-qt4-systray** frontend yet.

Also note that since we're making manual changes to **/etc/X11/xinit/xinput.d/uim-toolbar-qt4**, if you get a package upgrade to the **uim-xim** package, this file *may* get overwritten to previous defaults. *If* your Qt4 panel starts looking ugly or fails to appear at all, dig up that file again and make sure the **XIM_PROGRAM_EXTRA** line properly starts **uim-toolbar-qt_[color="lime"]4[/color]_**, as we modified it to do earlier.

---

### Post by keroro on 2010-05-18
I tried to use Ibus before. When I typed something in kate and pressed return the former signs just disappeared.
So I uninstalled Ibus and followed your instructions to install uim.
Now if I type something in kate and press return the same hiragana appears again. The return key doubles the input. Only difference is that the first hiragana is underlined.
Before I upgraded to Lucid everything worked fine under skim.

---

### Post by Zorael on 2010-05-18
This is [a bug in Kate and KWrite](https://bugs.kde.org/show_bug.cgi?id=206455).

It's fixed in 4.4.3, but on KDE versions earlier than that, the only way to be able to input Japanese (et al) in Kate or KWrite is to use UIM and set QT_IM_MODULE to xim, as I mentioned in the earlier post.

If you upgrade to Lucid and add the Kubuntu updates ppa (**ppa:kubuntu-ppa/ppa**), a full package upgrade should net you 4.4.3. Then you can use UIM with QT_IM_MODULE set to uim (as it is per default), or ibus, or whichever IME you prefer.

---

### Post by keroro on 2010-05-19
Thank you, Zorael. My bad.
Somehow I thought I am already on 4.4.3.

---

### Post by zoku88 on 2010-05-21
I tried doing what you mentioned, but I still get 

GTK:    ibus
Qt4:    ibus
XMOD:   @im=ibus

when I do that echo command.  I previously had ibus installed, but I uninstalled it to install uim.  I had followed these directions before to install ibus [http://wiki.debian.org/I18n/ibus](http://wiki.debian.org/I18n/ibus), so I removed those lines from .xessionrc.  I'm not sure why it still says ibus though...

---

### Post by zoku88 on 2010-05-21
Actually, nvm, I didn't check to make sure that all of the ibus packages were removed when i did apt-get remove ibus.

---

### Post by LK_gandalf_ on 2010-06-15
The first guide by Zorael works perfecly, tested on two kubuntu 10.04. Thank you :) 
I just have a problem, the handwriting option doesn't work. If I click on it, nothing happens. Is there a fix for it?

---

### Post by Zorael on 2010-06-15
> **LK_gandalf_ said:**
> I just have a problem, the handwriting option doesn't work. If I click on it, nothing happens. Is there a fix for it?
It tries to run **uim-tomoe-gtk**, which isn't available from the repositories. You can download it from [its homepage](http://tomoe.sourceforge.jp/cgi-bin/en/blog/index.rb) and compile it yourself, but if memory serves it wasn't very easy. I don't know enough of packaging to make debs of it.

---

### Post by LK_gandalf_ on 2010-06-16
Uhm I cannot find the instruction to install the latest tomoe 0.6; in the folder there is an install-sh file, but I don't know if it's a runnable file. 
So I tried to compile it with the usual configure/make/make install, here what I get:

```
Configure Result:

  * Language Bindings

      Ruby            : no
      Python          : no

  * Dictionary Backends

      Unihan Database : yes
      Hyper Estraier  : no
      Subversion      : no
      MySQL           : no
      Ruby            : no

  * Other Features

      gtk-doc         : no

```

So apparently no errors, but make....

```

$ sudo make
make  all-recursive
make[1]: ingresso nella directory «/home/doc/programmi-linux/tomoe-0.6.0»
Making all in po
make[2]: ingresso nella directory «/home/doc/programmi-linux/tomoe-0.6.0/po»
file=`echo ja | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ja.po
/bin/sh: -o: not found
make[2]: *** [ja.gmo] Errore 127
make[2]: uscita dalla directory «/home/doc/programmi-linux/tomoe-0.6.0/po»
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory «/home/doc/programmi-linux/tomoe-0.6.0»
make: *** [all] Errore 2

```

I don't know how to go on.....

There must be a way to install it from repos!
I found [https://launchpad.net/~japaneseteam/+archive/ppa/+packages](https://launchpad.net/~japaneseteam/+archive/ppa/+packages) where, in the karmic repos, there is tomoe 0.6 (but I cannot find the uim version). 
The same here, with the lucid japanese repos [http://www.ubuntulinux.jp/products/JA-Localized](http://www.ubuntulinux.jp/products/JA-Localized) but no tomoe inside.

Do you know if there are some japanese repos for lucid where we can find it?

P.S. I tried kanjipad in the repository, it works but it's slow and not comfortable to use, it doesn't search the kanji while you are painting, and to insert the character in the document you have to copy/paste it.

---

### Post by LK_gandalf_ on 2010-06-17
still searching for a solution (it seems incredible that on the last version of Kubuntu there is no proper and easy-to-install software for asian languages and handwriting recognition. Still need Windows for this stuffs......), I found a series of packages which are in the repositories:
- tagaki
- zinnia
I installed everything but I don't know how to launch tagaki, and if I type zinnia in the terminal, I get:

```
$ zinnia
libzinnia.cpp(287) [recognizer->open(model.c_str())] recognizer.cpp(84) [mmap_.open(filename)] no such file or directory: 

```

---

### Post by LK_gandalf_ on 2010-06-21
still the same problem...

---

### Post by Zorael on 2010-06-21
Hm hmm.

(This assumes that you have the basic compiling packages installed. build-essential and all that.)
```
$ sudo aptitude install --without-recommends libuim-dev libgtk2.0-dev python-gtk2-dev
$ mkdir ~/src/tomoe
$ cd ~/src/tomoe
$ wget http://heanet.dl.sourceforge.net/project/tomoe/tomoe-gtk/tomoe-gtk-0.6.0/tomoe-gtk-0.6.0.tar.gz
$ wget http://puzzle.dl.sourceforge.net/project/tomoe/tomoe/tomoe-0.6.0/tomoe-0.6.0.tar.gz
$ wget http://kent.dl.sourceforge.net/project/tomoe/uim-tomoe-gtk/uim-tomoe-gtk-0.6.0/uim-tomoe-gtk-0.6.0.tar.gz
$ for file in *.tar.gz; do tar xfv $file; done

$ cd tomoe-0.6.0
[B][COLOR="Green"]$ wget "http://cvs.fedoraproject.org/viewvc/rpms/tomoe/F-10/tomoe-0.6.0-bz502662.patch?sortby=date&view=log"
$ patch -p1 < tomoe-0.6.0-bz502622.patch[/COLOR][/B]
$ ./configure --prefix=/usr
$ make
$ sudo make install
$ cd ..

$ cd tomoe-gtk-0.6.0
$ ./configure --prefix=/usr --without-gucharmap
$ make
$ sudo make install
$ cd ..

$ cd uim-tomoe-gtk-0.6.0
$ ./configure --prefix=/usr
$ make
$ sudo make install

$ cd /usr/share/tomoe/recognizer
$ sudo ln -s handwriting-**ja**.xml handwriting-**en**.xml    *# replace **ja** with **zh_CN** if you want that recognition dictionary instead*

$ uim-tomoe-gtk &      *# try it out!*

```

It's not a neat solution since it pollutes the filesystem with files not tracked by dpkg (and apt). Also it doesn't seem to like being prefixed into the default /usr/local; I got error messages about it not finding libraries in /usr/lib, so prefixing it into /usr here.

---

### Post by Zorael on 2010-06-21
It works! Editing my earlier post to reflect new stuff.

For the record, I got an error about missing symbols, even after having successfully compiled everything.
```
$ uim-tomoe-gtk
uim-tomoe-gtk: symbol lookup error: /usr/lib/tomoe/module/dict/unihan.so: undefined symbol: _tomoe_dict_ptr_array_get_type
```

Googling the symbol name turned up a [Fedora patch for bug 502622](http://cvs.fedoraproject.org/viewvc/rpms/tomoe/F-10/tomoe-0.6.0-bz502662.patch?sortby=date&view=log).

---

### Post by trjones on 2010-08-08
Just come across this post after running into the Kate problem.

Zoreal, I have a quick question. I have never been able to input Japanese text using anthy into java apps like Open Office, rubymine etc.

Using your method with UIM does that work? If so I am definitely changing from ibus

---

### Post by Zorael on 2010-08-09
**@trjones**

(Firstly, you didn't mess around with ~/.gtkrc files or anything, right?)

I believe that Java doesn't use the GTK input module nor the Qt4 one, but instead uses vanilla XIM input. A small program to test this with is **xterm**; a very plain terminal window in the package of the same name. It uses XIM input, much like OpenOffice does. It doesn't work in xterm either, right?

Try the oneliner, and verify that your environmental variables all point to ibus.
```
echo -e "\nGTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n"
```

Furthermore, look to the output of '**im-switch -l**' to see what **/etc/X11/xinit/xinput.d/** file is being read to define those variables. Example follows;

```
$ im-switch -l
Your input method setup under en_US locale as below.
=======================================================
[B][COLOR="Green"]No private "/home/zorael/.xinput.d/en_US or /home/zorael/.xinput.d/all_ALL" is defined.
[/COLOR][/B]=======================================================
[B][COLOR="Green"]The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
 link currently points to _uim-toolbar-qt_[/COLOR][/B]
*[...]*
=======================================================
The available input method configuration files are:
default default.old default-xim lo-gtk none th-gtk th-xim uim uim-systray uim-toolbar uim-toolbar-qt 
=======================================================
```

Yours will likely say "**link currently points to _ibus_**", which means that **/etc/X11/xinit/xinput.d/_ibus_** is the file being read.

Paste the contents of that file here - inbetween code tags, if you would.

---

### Post by trjones on 2010-08-10
Thank you for the help Zorael  Having made that post I then managed to start testing ibus on lucid and it did actually work with things like OpenOffice which was a pleasant surprise.  Somewhat less of a pleasant surprise is the fact that it doesn't now work with Firefox and Thunderbird so no japanese email which is a show-stopper. 

AAAAAARRRRRRRRGGGGGGGHHHHHH  I am a Linux fanboi but I really wish they would make this easier...

I haven't messed with the gtk file you mentioned

```

jjones@jjones-desktop:~$ echo -e "\nGTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n"

GTK:    ibus
Qt:     ibus
XMOD:   @im=ibus

```


```

jjones@jjones-desktop:~$ im-switch -l
Your input method setup under en_GB locale as below.
=======================================================
The configuration "/home/jjones/.xinput.d/en_GB" is defined as a link pointing to
ibus
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
 link currently points to default-xim
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim ibus ibus-kde lo-gtk none th-gtk th-xim 
=======================================================

``` I have however used im-switch -c to set it to ibus. If I use sudo im-switch -c then ibus does not appear as one of the options.

```

jjones@jjones-desktop:~$ sudo im-switch -c
No system wide default defined just for locale en_GB .
Use "all_ALL" quasi-locale and set IM.
System wide default for all_ALL locale is marked with [+].
There are 3 choices for the alternative xinput-all_ALL (providing /etc/X11/xinit/xinput.d/all_ALL).

  Selection    Path                                 Priority   Status
------------------------------------------------------------
  0            /etc/X11/xinit/xinput.d/default       10        auto mode
  1            /etc/X11/xinit/xinput.d/default       10        manual mode
* 2            /etc/X11/xinit/xinput.d/default-xim   0         manual mode
  3            /etc/X11/xinit/xinput.d/none          0         manual mode

Press enter to keep the current choice
[*], or type selection number:

```I have tried all the options in that particular menu just in case

```

jjones@jjones-desktop:~$ im-switch -c

There are 8 candidates which provide IM for /home/jjones/.xinput.d/en_GB:

  Selection    Alternative
  -----------------------------------------------
      1        default
 +    2        default-xim
*     3        ibus
      4        ibus-kde
      5        lo-gtk
      6        none
      7        th-gtk
      8        th-xim
System wide default for en_GB (or all_ALL) locale is marked with [+].
Press enter to keep the current selection
[*], or type selection number:

```for this I tried ibus and ibus-kde but FireFox and Thunderbird still fail.

---

### Post by Zorael on 2010-08-11
Interesting.

ibus not showing up as a choice when performing '**sudo im-switch -c**' sounds like [this bug](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/522814) I filed back in February. It's really just a matter of removing one commenting # in the source, but so far it hasn't been done.

Firefox and Thunderbird both use the GTK module, so make certain that you have the **ibus-gtk** package installed. Use your GUI package manager of choice if you want to.

The terminal way of listing which ibus* packages are installed;
```
$ dpkg -l ibus\* | grep ^ii | awk '{ print $2 }'
```

Or, to check up on **ibus-gtk** directly;
```
$ apt-cache policy ibus-gtk
```

Your environmental variables look right, but the modules themselves not being installed would exhibit the same functionality as the variables not referencing to them. Also try to start Firefox from a terminal and see if it happens then, too.

Any changes you make using im-switch need a logout and a relogin to take effect. It might even need an X restart, which is difficult nowadays except by doing a full reboot.

---

### Post by trjones on 2010-08-11
Zorael

You are a diamond!

ibus-gtk was not installed as you guessed. After installing that Firefox and Thunderbird work perfectly. I made no changes to im-switch from the previous post.

I cannot remember if I installed ibus myself or if it was installed when I added the Japanese language pack to kubuntu. If it is the latter I am quite shocked that ibus-gtk is not automatically installed seeing as firefox, probably the most used package in the system, needs it.

Anyway, for the first time since switching to Linux I now have full Japanese input on all the programs I am using. 

&#12411;&#12435;&#12392;&#12358;&#12395;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290;

---

### Post by Razlo on 2010-10-30
Hello there! I've been trying to install **tomoe** for two days, but I fell like it has been abandoned by developers.

I've tried to follow the code **zaroel** post, but there's a broken link.

> $ cd tomoe-0.6.0
$ wget **[http://cvs.fedoraproject.org/viewvc/rpms/tomoe/F-10/tomoe-0.6.0-bz502662.patch?sortby=date&view=log](http://cvs.fedoraproject.org/viewvc/rpms/tomoe/F-10/tomoe-0.6.0-bz502662.patch?sortby=date&view=log)**
$ patch -p1 < tomoe-0.6.0-bz502622.patch
$ ./configure --prefix=/usr
$ make
$ sudo make install
$ cd ..


I guess that this patch let the program compile. Whithout it, I get the same error that LK_gandalf_:
```
$ sudo make
make  all-recursive
make[1]: ingresso nella directory «/home/doc/programmi-linux/tomoe-0.6.0»
Making all in po
make[2]: ingresso nella directory «/home/doc/programmi-linux/tomoe-0.6.0/po»
file=`echo ja | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ja.po
/bin/sh: -o: not found
make[2]: *** [ja.gmo] Errore 127
make[2]: uscita dalla directory «/home/doc/programmi-linux/tomoe-0.6.0/po»
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory «/home/doc/programmi-linux/tomoe-0.6.0»
make: *** [all] Errore 2
```

After searching and finding once and another the same files, I decided to reply this thread. Any idea?

Thanks.

---

### Post by Zorael on 2010-11-02
> **Razlo said:**
> I've tried to follow the code **zaroel** post, but there's a broken link.
Apologies; it seems like I didn't escape the ampersand (&). Just add a backslash infront of it, or encase the entire url in quotes;
```
$ cd tomoe-0.6.0
$ wget "http://cvs.fedoraproject.org/viewvc/rpms/tomoe/F-10/tomoe-0.6.0-bz502662.patch?sortby=date&view=log"
$ patch -p1 < tomoe-0.6.0-bz502622.patch
$ ./configure --prefix=/usr
$ make
$ sudo make install
$ cd ..
```
I'll edit and update the post.

> **Razlo said:**
> I guess that this patch let the program compile. Whithout it, I get the same error that LK_gandalf_:
```
$ sudo make
make  all-recursive
make[1]: ingresso nella directory «/home/doc/programmi-linux/tomoe-0.6.0»
Making all in po
make[2]: ingresso nella directory «/home/doc/programmi-linux/tomoe-0.6.0/po»
file=`echo ja | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ja.po
/bin/sh: -o: not found
make[2]: *** [ja.gmo] Errore 127
make[2]: uscita dalla directory «/home/doc/programmi-linux/tomoe-0.6.0/po»
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory «/home/doc/programmi-linux/tomoe-0.6.0»
make: *** [all] Errore 2
```
That's not what the patch should fix, but hm. Make sure you have the [**build-essential**](apt://build-essential) and [**gettext**](apt://gettext) packages installed.
```
$ sudo aptitude install build-essential gettext
```

---

### Post by Razlo on 2010-11-02
Well, thanks! It was the *gettext* app that I hadn't, not *build-essentials* (I would worry in that case).

I successfully installed *tomoe* and I'm now with *tomoe-gtk* and *uim-tomoe-gtk*. uim one complained that it needed tomoe-gtk (logic, if you reed the names), but *tomoe-gtk* complained about *gucharmap*.

It seems that I'm having issues for installing things where I shouldn't, but hey, I wanna do this this way -though I haven't proceeded giving the path of *gucharmap*. The complain looks this way:

```

me@home:~/.../tomoe-gtk-0.6.0$ **./configure**

[...]

checking for TOMOE... yes
checking for GUCHARMAP... configure: error: Package requirements (gucharmap >= 1.4.0) were not met:

**No package 'gucharmap' found**

Consider adjusting the **PKG_CONFIG_PATH** environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables **GUCHARMAP_CFLAGS**
and **GUCHARMAP_LIBS** to avoid the need to call pkg-config.
See the pkg-config man page for more details.

me@home:~/.../tomoe-gtk-0.6.0$

```

As I'm executing and not compiling, I don't know how to show the path to him (may need a bible), I suspect it's not like *-i* option in *gcc*. I looked the man of pkg-config, but... well, let's say I get lost.

This is maybe going out of way, if anybody considers there's already a post on this issues or anything, redirect me there ;)

Thanks for your help!

[I]PS: I'm a bit surprised it worked after installing gettext. It should make no difference if its function is to avoid escapes like '&' and so on, as I understood from the description. May it've been coincidence?

And you did forgot the (")'s, but the link is broken anyway :S[/I]

---

