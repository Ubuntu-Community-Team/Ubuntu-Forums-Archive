---
title: "Multimedia keyboard"
date: 2006-01-01
forum: General Help
---

### Post by Tosa on 2006-01-01
Hi all, and Happy New Year :KS

This may be a trivial problem, but with Gnome my keyboard - multimedia keys (sound, e-mail, web browser) worked fine from the start. I've switched to KDE 2 days ago and noticed that those keys don't work any more. I tried to find somthing to reactivate them but no luck...

I'll appreciate some help on this.

---

### Post by aysiu on 2006-01-01
No help here, but I just wanted to say I've found this to be the case for my keyboard as well--multimedia keys in Gnome, yes; multimedia keys in KDE, no.

---

### Post by sharke on 2006-01-01
[QUOTE=aysiu]No help here, but I just wanted to say I've found this to be the case for my keyboard as well--multimedia keys in Gnome, yes; multimedia keys in KDE, no.[/QUOTE]
Yes Kubuntu can set your keyboard goto Systemsettings>regional&acessabilty and you should find keyboard setup
Regards
Sharke

---

### Post by limit223 on 2006-01-01
I've got my Logitech Media Keyboard Elite full keys' functions in KDE.
Here is my post related:
[http://ubuntuforums.org/showpost.php?p=563129&postcount=18](http://ubuntuforums.org/showpost.php?p=563129&postcount=18)

---

### Post by aysiu on 2006-01-01
[QUOTE=sharke]Yes Kubuntu can set your keyboard goto Systemsettings>regional&acessabilty and you should find keyboard setup
Regards
Sharke[/QUOTE] I've done that before. Believe me--I've explored all those options in System Settings. My keyboard isn't in the list.

---

### Post by Tosa on 2006-01-01
Thanks sharke and limit223, but,

I ran xev and keysym for all my multimedia keys was 0x0.
I've allready tried to bind the keys through System Settings... but when pressed my multimedia keys are not detected...

Any other ideas ?

---

### Post by Luke on 2006-01-01
limit223, thanks for that post. i used it with success a few days ago on my compaq laptop.

tosa,
when you run xev, you're looking for the number that follows "keycode" not "keysym". then you open your "xmodmap.conf" file that you've created according to limit223's post and assign a keysym to the appropriate keycode. does that make sense?

i didn't check "/usr/share/X11/XKeysymDB" before assigning keysyms but you probably should. you can't just assign whatever text (keysym) you want to a keycode. however, for some of my keys i used "F13" and "F14" as my keysyms. i just checked my "/usr/share/X11/XKeysymDB" and they're not in there but they do work.

after you're done setting up your "xmodmap.conf" file and you've run
> xmodmap xmodmap.conf
you can go into the kde keyboard settings and set the shortcuts. kde should now recognize the keys that you have assined keysyms to.

---

### Post by Tosa on 2006-01-01
Thanks Luke,

I didn't read limit's post carefuly and I've got it all mixed up.
Since I'm an absolute begginer, I still got problems. I have no idea what

xmodmap -pke > xmodmap.conf

did and where is the file created. I have no idea how to asign keysym to a keycode. Should it be something like

keycode 160 (keysym 1008ff12, XF86AudioMute)

?

---

### Post by Tosa on 2006-01-01
OK,

I found the file and got it.

Asigned one key and it works !!!

EDIT:

It did work once. Then it stoped...

---

### Post by limit223 on 2006-01-01
Sorry for the delay,

xmodmap -pke > xmodmap.conf creats a map file of your keyboard named: xmodmap.conf in the directory where you issue the command line.(usually by default you open up your terminal in /home/username directory.
Open that file and edit it like this:
keycode 160 = XF86AudioMute

and follow the rest of the guide..

---

### Post by limit223 on 2006-01-01
The hard part of the this guide is when you don't have any responsive codes for keys in console...that was my case ..and I had to define the whole layout keyboard...

---

### Post by Brando569 on 2006-01-02
only the mute button works on my logitech elite KB :( heres my setup (im using amarok idk if that matters):

keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 160 = XF86AudioMute
keycode 162 = XF86AudioPlay XF86AudioPause
keycode 164 = XF86AudioStop

also is there a way to get rid of the OSD when the key is pressed?

---

### Post by Tosa on 2006-01-02
Nope it doesn't work.

I've got key codes, asigned to keysyms, went to System Settings... Input Actions and it did detect a key! I've tried it imediately and it worked. Then I did

sudo cp xmodmap.conf /etc/xmodmap.conf
echo 'xmodmap /etc/xmodmap.conf' > ~/.kde/Autostart/shortcutkeyset

restarted, after restart a Kate window opend with line

modmap /etc/xmodmap.conf

I closed it and went to System Settings... Input Actions to continue, but nada! MM keys aren't detected any more. Xmodmap files are where they're supposed to be, they contain what they should...

Feel a bit frustrated ](*,)

---

### Post by Luke on 2006-01-02
i think the fact that it opened in kate means that it's not executable. that's what happened to me.

> chmod +x ~/.kde/Autostart/shortcutkeyset

you're almost there!

---

### Post by Tosa on 2006-01-02
I'm afraid it didn't help. Kate shows up again, and keys are not detected...

---

### Post by limit223 on 2006-01-02
In order to have all functions on my Logitech Media keyboard I had to define anothery layout in /etc/X11/xkb/symbols/inet and I did the following:

1. Open that file and edit it with a new Keyboard Name: Logitech Media Kayboard and iserted Logitech section between Logitech Internet Keyboard and Logitech iTouch:
```
//Logitech Media Keyboard
partial alphanumeric_keys
xkb_symbols "logimedia" {   
    // Media keys (Center top)
    key <I20>   {       [ XF86AudioMute         ]       };
    key <I6D>   {       [ XF86AudioMedia        ]       };
    key <I2E>   {       [ XF86AudioLowerVolume  ]       };
    key <I30>   {       [ XF86AudioRaiseVolume  ]       };
    key <I22>   {       [ XF86AudioPlay, XF86AudioPause ] };
    key <I24>   {       [ XF86AudioStop         ]       };
    key <I10>   {       [ XF86AudioPrev         ]       };
    key <I19>   {       [ XF86AudioNext         ]       };

    // Left side
    key <I65>   {       [ XF86Search            ]       };      //100%Zoom
    key <I69>   {       [ XF86Forward           ]       };      //Zoom-
    key <I6A>   {       [ XF86Back               ]       };     //Zoom+

    // Top left side
    key <I66>   {       [ XF86Favorites            ]       };
    key <I32>   {       [ XF86HomePage          ]       };

    // Right side
    key <I6C>   {       [ XF86Mail                    ]       };
    key <I11>   {       [ XF86Messenger           ]       };
    key <I13>   {       [ XF86VendorHome        ]       };
    key <I5F>   {       [ XF86Standby              ]       };

    // Extended function keys
    key <I3B>	{	[ XF86New		]	};	// F1
    key <I3C>	{	[ XF86Reply		]	};	// F2
    key <FK13>	{	[ XF86MailForward	]	};	// F3
    key <FK14>	{	[ XF86Send		]	};	// F4
    key <FK15>	{	[ Undo			]	};	// F5
    key <FK16>	{	[ Redo			]	};	// F6
    key <FK17>	{	[ Print			]	};	// F7
    key <I42>	{	[ XF86Save		]	};	// F8
    key <I43>	{	[ XF86MyComputer	]	};	// F9
    key <I44>	{	[ XF86Documents		]	};	// F10
    key <I57>	{	[ XF86Pictures		]	};	// F11
    key <I58>	{	[ XF86Music		]	};	// F12
};
```
2.Edit /etc/X11/xkb/rules/xorg file in the " ! $inetkbds = .." section inserting the name of the new keyboard:
```
......................................
! $inetkbds = a4techKB21 a4techKBS8 acer_tm_800 acpi airkey azonaRF2300 \
              brother \
              btc5113rf btc5126t btc9000 btc9000a btc9001ah btc5090\
              cherryblue cherrybluea cherryblueb \
              chicony chicony9885 \
              compaqeak8 compaqik7 compaqik13 compaqik18 cymotionlinux \
              armada presario ipaq \
              dell inspiron dtk2000 \
              dexxa diamond genius geniuscomfy2 \
              ennyah_dkb1008 gyration \
              hpi6 hp2501 hp2505 hp5181 hpxe3gc hpxe3gf hpxe4xxx hpzt11xx \
              hp500fa hp5xx hp5185 \
              honeywell_euroboard \
              rapidaccess rapidaccess2 rapidaccess2a \
              ltcd logiaccess logicdp logicdpa logicdit logicink logiciink \
              logiinkse logiinkseusb logiitc logiik **logimedia** itouch logiultrax \
              mx1998 mx2500 mx2750 \
              microsoftinet microsoftpro microsoftprousb microsoftprooem microsoftprose \
              microsoftoffice microsoftmult \
              oretec \
              propeller scorpius \
              qtronix \
              samsung4500 samsung4510 \
              sk1300 sk2500 sk6200 sk7100 sp_inet \
              sven symplon toshiba_s3000 trust trustda yahoo
..............................................................................................

```
3. Edit /etc/X11/xkb/rules/xorg.lst in the Logitech section in this order:
```
..............................................................
  logiitc         Logitech iTouch Cordless Keyboard (model Y-RB6)
  logiik          Logitech Internet Keyboard
**logimedia       Logitech Media Keyboard** 
  itouch          Logitech iTouch
  logiitc         Logitech iTouch Cordless Keyboard (model Y-RB6)
.................................................................

```

and /etc/X11/xkb/rules/xorg.xml

```
.............................................................
 <model>
      <configItem>
        <name>logimedia</name>
        <description>Logitech Media Keyboard</description>
      </configItem>
    </model>
......................................................................
```

4.My "InputDevice section in  /etc/X11/xorg.conf looks like this:
```
...................................................................
Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "XkbModel"	"logimedia"
    Option "XkbLayout"	"us"
EndSection
.......................................................................
```
5. Reboot (restart X)

6.For some keys I didn't have any xev respond and for that I had to setup some scancodes. So following the original guide I had to insert some scankeycodes lines for them in /etc/init.d/bootmisc.sh like that:

```
...............................................................
setkeycodes e011 145
setkeycodes 6a 234
setkeycodes e004 233
...............................................................
```


Here is a table with corresponding keycodes in the /etc/xmodmap.conf, ModeKeys Name, RealName on the keyboard, scancodes, and the lines in the /etc/init.d/bootmisc.sh :

keycode 131 = XF86New                F1mode   e03b    setkeycodes e03b 187
keycode 247 = XF86Reply               F2mode   e03c    setkeycodes e03b 188
keycode 123 = XF86MailForward      F3mode   e03d    setkeycodes e03d 118
keycode undefined...respond as the same keycode of PrintSreen in xev
keycode 139 = Undu                       F5mode    e03f    setkeycodes e03f 120
keycode 134 = Redu	                 F6mode    e040   setkeycodes e040 121
keycode 209 = Print	                 F7mode    e040   setkeycodes e040 122
keycode 207 = XF86Save               F8mode    e042   setkeycodes e042 194 
keycode 149 = XF86MyComputer     F9mode    e043   setkeycodes e043 195
keycode 150 = XF86Documents       F10mode   e044  setkeycodes e044 196 
keycode 120 = XF86Pictures           F11mode   e057  setkeycodes e057 215
keycode 121 = XF86Music              F12mode   e058  setkeycodes e058 216

keycode 216 = XF86Search            100%Zoom 6b    setkeycodes 6b 229
keycode 213 = XF86Forward           Zoom+      6a    setkeycodes 6a 234
keycode 142 = XF86Back               Zoom-      e004  setkeycodes e004 233

keycode 199 = XF86Messenger       Messenger  e011  setkeycodes e011 145 

7.For those who is not clear what to introduce in /etc/xmodmap.conf, here is mine attached.
8.Setting your new layout in KDE:
Control Center - Keyboard Layout - Layout tab - Enable Keyboards layouts check - Keyboard model: select: Logitech Media Keyboard- Apply

 After all beeing done you should be able to see any pressing keys in KDE Input Action.

For different type of keyboard a good refference may find [here]("http://www.win.tue.nl/~aeb/linux/kbd/scancodes-5.html") .

Now for using Volumeup, VolumeDown, VolumeMute properly I use this script which is written special for ALSA driver alsamixer tool:
```
#!/bin/bash
volsetting=`amixer sget 'Front' | grep off`
    case "$1" in
    mute)
        amixer sset 'Front' mute
    ;;
    unmute)
        amixer sset 'Front' unmute
    ;;
    toggle)
        if [[ x"$volsetting" = x"" ]]; then
            amixer sset 'Front' mute
        else
            amixer sset 'Front' unmute
        fi
    ;;
    increase)
        amixer sset 'PCM' 5%+
    ;;
    decrease)
        amixer sset 'PCM' 5%-
    ;;
    *)
        echo "This is not an acceptable command!";
        echo -e "Use \033[01;33mmute\033[01;00;0m, \033[01;33mincrease\033[01;00;0m or \033[01;33mdecrease\033[01;00;0m as options!";
        echo;
    esac
```

Place it in a file, make it executable, be aware by its path and in Control Center at Input Action define new keys:
VolumeDown - XF86AudioLowerVolume - Command: /path/to/your/sript/above decrease
VolumeUp - XF86AudioRaiseVolume - Command: /path/to/your/sript/above increase
VolumeMute - XF86AudioMute - Command: /path/to/your/sript/above toggle

Wasn't suppose to be a book but I couldn't make it any shorter.

Good Luck!

Edit: Made a correction instead of xfree86 and xfree86.lst use xorg and xorg.lst.

---

### Post by limit223 on 2006-01-02
And the attached xmodmap.conf:

---

### Post by poekie on 2006-07-24
I tried your howto, but I came up with keysyms similar to this:

KeyRelease event, serial 31, synthetic NO, window 0x2c00001,
    root 0x119, subw 0x0, time 2699261277, (-296,498), root:(802,524),
    state 0x10, keycode 164 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:

KeyRelease event, serial 31, synthetic NO, window 0x2c00001,
    root 0x119, subw 0x0, time 2699260693, (-296,498), root:(802,524),
    state 0x10, keycode 144 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:


All th emultimediakeys have 'NoSymbol' is it still possible to make a keyboard layout from things like this? for instance giving keycode 164 the keysym XF86AudioPlay, XF86AudioPause or something? Like you did in the last post?
[edit] ok, found out that it really is that 'simple' (quite some work though :) )
only problem that remains: three keys are not 'found' by xev but switching to console (ctrl+alt+F1) does nothing either, dmesg just blabbers something about which apparatus I have installed and the latest network activity, nothing about keys.. Can someone help?

[edit2]Ah well, it didn't work, so I gave up. My keyboard is too weird: a Chicony Ku-0108. If anybody out there has the same one and their keys working, can I get your driver? :D prettyplease :)

---

