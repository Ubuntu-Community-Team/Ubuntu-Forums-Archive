---
title: "S.O.S!! Help me restore my font-rendering!!"
date: 2006-08-17
forum: Desktop Environments
---

### Post by latebeat on 2006-08-17
Hello there,

after doing an apt-get dist-upgrade my fonts were f#@#ed :(
First of all antialiasing sucks and font rendering as well.
.fonts.conf in my home dir isn't honoured any more.


**Here are the errors that I get:**

```
 cat /var/log/Xorg.0.log | grep font
(**) FontPath set to "/usr/share/X11/fonts/misc:unscaled,/usr/share/X11/fonts/Type1,/usr/share/fonts/truetype/ttf-bitstream-vera/,/usr/share/fonts/truetype/msttcorefonts/,/usr/share/fonts/truetype/,/usr/share/X11/fonts/100dpi:unscaled,/usr/share/X11/fonts/75dpi:unscaled,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Loading font FreeType
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Loading font Type1
(II) Initializing built-in extension XFree86-Bigfont
Could not init font path element /usr/share/fonts/truetype/ttf-bitstream-vera/, removing from list!
Could not init font path element /usr/share/fonts/truetype/msttcorefonts/, removing from list!
Could not init font path element /usr/share/fonts/truetype/, removing from list!

```

Here's my xorg.conf:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc:unscaled"
	FontPath        "/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/truetype/ttf-bitstream-vera/"
	FontPath	"/usr/share/fonts/truetype/msttcorefonts/"
	FontPath	"/usr/share/fonts/truetype/"
	FontPath	"/usr/share/X11/fonts/100dpi:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi:unscaled"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load  	"GLcore"

EndSection
```


My fonts dir:
```
ls -la /usr/share/fonts/
total 15
drwxr-xr-x   5 root root   152 2006-07-29 16:41 .
drwxr-xr-x 353 root root 10008 2006-08-17 13:29 ..
-rw-r--r--   1 root root    53 2006-08-17 14:50 fonts.cache-1
drwxr-xr-x  26 root root   880 2006-08-17 14:41 truetype
drwxr-xr-x   3 root root   104 2006-05-31 01:56 type1
drwxr-xr-x   2 root root  1072 2006-08-17 14:50 wine

```

My truetype dir:
```
ls -la /usr/share/fonts/truetype
total 14
drwxr-xr-x 26 root root  880 2006-08-17 14:41 .
drwxr-xr-x  5 root root  152 2006-07-29 16:41 ..
drwxr-xr-x  2 root root  136 2006-05-31 01:56 arphic
drwxr-xr-x  2 root root  208 2006-05-31 01:56 baekmuk
drwxr-xr-x  8 root root  392 2006-07-20 14:12 custom
-rw-r--r--  1 root root  584 2006-08-17 14:50 fonts.cache-1
-rw-r--r--  1 root root    2 2006-08-17 14:46 fonts.dir
drwxr-xr-x  2 root root  520 2006-05-31 01:55 freefont
drwxr-xr-x  2 root root  224 2006-05-31 01:56 kochi
drwxr-xr-x  2 root root  304 2006-07-01 15:13 latex-xft-fonts
drwxr-xr-x  2 root root 2192 2006-08-17 14:40 msttcorefonts
drwxr-xr-x  2 root root  112 2006-07-13 21:45 openoffice
drwxr-xr-x  2 root root  936 2006-05-31 01:56 thai
drwxr-xr-x  2 root root 1360 2006-05-31 01:55 ttf-arabeyes
drwxr-xr-x  2 root root  304 2006-05-31 01:56 ttf-bengali-fonts
drwxr-xr-x  2 root root  424 2006-08-17 14:41 ttf-bitstream-vera
drwxr-xr-x  2 root root 1008 2006-05-31 01:55 ttf-dejavu
drwxr-xr-x  2 root root  240 2006-05-31 01:56 ttf-devanagari-fonts
drwxr-xr-x  2 root root  208 2006-05-31 01:55 ttf-gentium
drwxr-xr-x  2 root root  256 2006-05-31 01:56 ttf-gujarati-fonts
drwxr-xr-x  2 root root  336 2006-05-31 01:56 ttf-kannada-fonts
drwxr-xr-x  2 root root  120 2006-05-31 01:56 ttf-lao
drwxr-xr-x  2 root root  144 2006-05-31 01:56 ttf-malayalam-fonts
drwxr-xr-x  2 root root  776 2006-05-31 01:56 ttf-mgopen
drwxr-xr-x  2 root root  112 2006-05-31 01:56 ttf-oriya-fonts
drwxr-xr-x  2 root root  136 2006-05-31 01:56 ttf-punjabi-fonts
drwxr-xr-x  2 root root  392 2006-05-31 01:56 ttf-tamil-fonts
drwxr-xr-x  2 root root  144 2006-05-31 01:56 ttf-telugu-fonts

```



Any suggestions ? :confused: :confused: 

I tried doing mkfontdir in truetype and the rest of the directories but it didn't solve anything. Also let me just say that I didn't change any settings in my xorg.conf or my .fonts.conf. Out of the blue the fonts stopped working.

:(:(

---

### Post by Uncle Spellbinder on 2006-08-17
Seems to have something to do with Compiz repos (at least in part). In any event, the new font rendering is not very popular, to say the least.

There's some info in [THIS thread]("http://www.ubuntuforums.org/showthread.php?t=238127").

---

### Post by Ramses de Norre on 2006-08-17
I'm having the same issue.. my fonts look terrible!

---

### Post by givré on 2006-08-17
Yeah, apparently, they wanted to bring gnome-terminal with true transparency, but they had to update some package with not a lot of success.
The bug in compiz forum : [http://www.compiz.net/topic-3116-fonts-are-now-complete-crap](http://www.compiz.net/topic-3116-fonts-are-now-complete-crap)

---

### Post by Intangir on 2006-08-17
i also have ugly fonts now
im also using compiz

and ya gnome-terminal has real transparency, which is sorta neat

but i dont like how it uses other windows in its background, i use white text on my dark desktop background which was readable, now if theres anything under it, its not readable, but i like my dark desktop background ;(

so i gotta either use straight black, a bitmap, or keep no windows under it


also the fonts are ugly, i turned on subpixel rendering? (for LCD) and it looks a little better, but still ugly

the bold fonts are most noticibly ugly ;)

---

### Post by latebeat on 2006-08-17
You were right guys all fixed now. I had to reinstall all the patched libraries fonts from the: [HOWTO: quickly improve X11 font rendering]("http://www.ubuntuforums.org/showthread.php?t=180647").

I was really confused as I had the impression that I had locked the patched versions in synaptic? It seems that aptitude didn't honour the locks. Very strange. 
Can you please tell me how to lock a package from the command line in apt-get and aptitude (hold or forbid-version)?

thanks

---

### Post by givré on 2006-08-17
locks are different between aptitude & synaptic.

---

### Post by Ramses de Norre on 2006-08-17
That howto worked, I've got decent fonts now. Only issue is aptitude complaining about this: ```
The following packages have unmet dependencies:
  python-vte: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 is installed and it is kept back.
  libvte4: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 is installed and it is kept back.

```

But as long all apps work I'll ignore this.

---

### Post by latebeat on 2006-08-17
I know it's been mentioned [here]("http://www.ubuntuforums.org/showpost.php?p=1389608&postcount=119") already. Everything works now but how are u gonna upgrade something else if the need comes up. Synaptic will complain and won't let u do anything

---

### Post by Ramses de Norre on 2006-08-17
Hmm seems you're right.. I can't remove/install anything with this dependency issue.. this sucks big time..
Isn't there any way to get proper packages then?

---

### Post by latebeat on 2006-08-17
I had to downgrade some packages with aptitute to resolve dependences:

```
Downgrade the following packages:
libvte-common [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.2-0ubuntu1
(dapper-updates)]
libvte4 [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.2-0ubuntu1
(dapper-updates)]
python-vte [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.2-0ubuntu1
(dapper-updates)]
```


I know it sucks, hopefully someone will make new freetype and cairo packages. I wish I knew how to do it myself. Till then all we can do is wait :) Fortunatelly nothing broke by downgrading.

---

### Post by latebeat on 2006-08-17
> **latebeat said:**
> Fortunatelly nothing broke by downgrading.

I was wrong!! Gnome-terminal doesn't work now: 
```
gnome-terminal
gnome-terminal: symbol lookup error: gnome-terminal: undefined symbol: vte_terminal_set_opacity

```

mmm I'll have to think this through..

---

### Post by Ramses de Norre on 2006-08-17
I get this:
```
ramses@icarus:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  libvte4 python-vte
The following packages are unused and will be REMOVED:
  libgl1-mesa-dev libglitz1-dev mesa-common-dev
The following packages have been kept back:
  libcairo2 libcairo2-dev libfreetype6 libfreetype6-dev
The following packages will be REMOVED:
  grub language-pack-kde-en language-pack-kde-en-base language-pack-kde-nl language-pack-kde-nl-base libdvdcss2
  mozilla-firefox-locale-en-gb mozilla-firefox-locale-nl-nl
0 packages upgraded, 0 newly installed, 11 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 28.5MB will be freed.
The following packages have unmet dependencies:
  python-vte: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 is installed and it is kept back.
  libvte4: Depends: libfreetype6 (>= 2.2.1) but 2.1.10-1ubuntu2-turnerpatch0 is installed and it is kept back.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
grub [0.97-1ubuntu9 (dapper, now)]

Upgrade the following packages:
libfreetype6 [2.1.10-1ubuntu2-turnerpatch0 (now) -> 2.2.1-0ubuntu1 (dapper, dapper)]
libfreetype6-dev [2.1.10-1ubuntu2-turnerpatch0 (now) -> 2.2.1-0ubuntu1 (dapper, dapper)]

Score is -39

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
lilo [1:22.6.1-7ubuntu2 (dapper)]

Upgrade the following packages:
libfreetype6 [2.1.10-1ubuntu2-turnerpatch0 (now) -> 2.2.1-0ubuntu1 (dapper, dapper)]
libfreetype6-dev [2.1.10-1ubuntu2-turnerpatch0 (now) -> 2.2.1-0ubuntu1 (dapper, dapper)]

Score is -59

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
grub [0.97-1ubuntu9 (dapper, now)]

Downgrade the following packages:
libvte-common [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.1-0ubuntu1 (dapper)]
libvte4 [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.1-0ubuntu1 (dapper)]
python-vte [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.2-0ubuntu1 (dapper-updates)]

Score is -269

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  libgl1-mesa-dev libglitz1-dev mesa-common-dev
The following packages will be DOWNGRADED:
  libvte-common libvte4 python-vte
The following packages have been kept back:
  libcairo2 libcairo2-dev libfreetype6 libfreetype6-dev
The following packages will be REMOVED:
  language-pack-kde-en language-pack-kde-en-base language-pack-kde-nl language-pack-kde-nl-base libdvdcss2
  mozilla-firefox-locale-en-gb mozilla-firefox-locale-nl-nl
0 packages upgraded, 0 newly installed, 3 downgraded, 10 to remove and 4 not upgraded.
Need to get 887kB of archives. After unpacking 27.7MB will be freed.
Do you want to continue? [Y/n/?]

```
But obviously I don't want to remove the language packs, mozilla locals or libdvdcss.. I don't get why aptitude wants to remove those.. Anyone who knows how to downgrade those vte packages without removing all the others?

(Synaptic doen't work for this purpose neither, it want's to remove a whole bunch of important apps when trying to downgrade the vte stuff)

---

### Post by givré on 2006-08-17
You'll need to downgrade also gnome-terminal.

---

### Post by Ramses de Norre on 2006-08-17
How do I do this with aptitude? Synaptic wants to remove a whole bunch of apps.. (gdebi, gnome-app-install, language-selector, libvte4, python-vte, synaptic, tilda, ubuntu-desktop, update-manager, update-notifier).

---

### Post by ravenon on 2006-08-17
Same problem with my updates today--it does come from the libfreetype6 stuff that got upgraded.
This post worked for me
[http://www.ubuntuforums.org/showthread.php?t=180647](http://www.ubuntuforums.org/showthread.php?t=180647)

Two packages libvte4 and python-vte end up broken, but I do not see that this has any consequences, at least for what I do.

Hopefully a true fix will come down the pike soon.

---

### Post by Ramses de Norre on 2006-08-17
I did the same, but the problem is you can't install/remove/upgrade any package without fixing the broken ones first.. so aptitude(/synaptic) is down untill we've got a fix..

---

### Post by shoagun on 2006-08-17
n00b question.  what's the difference between transparency before the update and after?  didn't compiz always use true transparency?

---

### Post by peabody on 2006-08-17
I think it means that now when you set transparency in the gnome-terminal settings it's actual transparency rather than just desktop background.  That's stupid though, because, as you said, adjusting the opacity of the window via Alt+Mouse wheel gives you pretty much the exact same effect.

---

### Post by latebeat on 2006-08-17
> **Ramses de Norre said:**
> How do I do this with aptitude? 

try: 
```
sudo aptitute remove gnome-terminal
sudo aptitute remove gnome-terminal-data
```

I then got: 

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  gnome-terminal
The following packages have been kept back:
  libcairo2 libcairo2-dev libfreetype6 libfreetype6-dev libvte-common libvte4 python-vte xserver-xorg-input-evdev
The following packages will be REMOVED:
  gnome-terminal-data
0 packages upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 9306kB will be freed.
The following packages have unmet dependencies:
  gnome-terminal: Depends: gnome-terminal-data (= 2.14.1-0ubuntu1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
gnome-terminal-data [2.14.2-0ubuntu2 (dapper, dapper, now) -> 2.14.1-0ubuntu1 (dapper)]

Score is -39

Accept this solution? [Y/n/q/?] y

```

which was what I wanted

---

### Post by Ramses de Norre on 2006-08-18
I did got it fixed, I asked to remove gnome-terminal but instead aptitude did this: ```
Keep the following packages at their current version:
gnome-terminal [2.14.2-0ubuntu2 (dapper, dapper, now)]

Downgrade the following packages:
libvte-common [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.1-0ubuntu1 (dapper)]
libvte4 [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.1-0ubuntu1 (dapper)]
python-vte [1:0.12.2-0ubuntu2 (dapper, dapper, now) -> 1:0.12.2-0ubuntu1 (dapper-updates)]

```

Then I commented the XGL/Compiz repos and did a dist-upgrade.
Everything is fine now (I hope..) and I'll keep the compiz repo out for a while..

---

