---
title: "Numpad Idle problem ubuntu 16.04"
date: 2016-08-28
forum: Desktop Environments
---

### Post by amr-gaballa777 on 2016-08-28
Hello I have a problem with Numpad whenever I don't use it for over a minute it doesn't work the next button press and I have to swtich it off and on again (with numlock) to get back to rework 
I even tried to use ubuntu tweaky tool to control miscellaneous and searched for many solutions concerning my problem on **ask-ubuntu** but not any of them worked here are some links for the problems I found [http://goo.gl/ZFQbZF](http://goo.gl/ZFQbZF) and [http://goo.gl/3rc1Sm](http://goo.gl/3rc1Sm)
my distro is ubuntu 16.04 [64] and I use samsung ativbook 270 any help please ?

---

### Post by mook765 on 2016-08-28
Welcome to Ubuntu forums.
I don' think, that this is a real Ubuntu problem.
Maybe a running process is going to toggle NumLock off. Could depend on some software you have installed.
Now idea how to trace which process is doing so.
I found some pretty old related threads, time do do something new...
I am on Kubuntu 16.04, and a few things are different, so on my system i can really adjust a lot in the keyboard-settings, everything works just fine.
If you can not solve the issue with the settings, here is an idea.
This are  the very first lines of the file /usr/share/X11/xkb/symbols/keypad
```

default  hidden partial keypad_keys
xkb_symbols "x11" {

    include "keypad(operators)"

    key  <KP7> {    [  KP_Home,    KP_7    ]    };
    key  <KP8> {    [  KP_Up,    KP_8    ]    };
    key  <KP9> {    [  KP_Prior,    KP_9    ]    };

    key  <KP4> {    [  KP_Left,    KP_4    ]    };
    key  <KP5> {    [  KP_Begin,    KP_5    ]    };
    key  <KP6> {    [  KP_Right,    KP_6    ]    };

    key  <KP1> {    [  KP_End,    KP_1    ]    };
    key  <KP2> {    [  KP_Down,    KP_2    ]    };
    key  <KP3> {    [  KP_Next,    KP_3    ]    };
    key <KPEN> {    [    KP_Enter    ]    };
    key <KPEQ> {    [    KP_Equal    ]    };

    key  <KP0> {    [  KP_Insert,    KP_0    ]    };
    key <KPDL> {    [  KP_Delete,    KP_Decimal ]    };
    key <KPPT> {    [  KP_Decimal,    KP_Decimal ]    };
};
```
I changed this lines to
```

default  hidden partial keypad_keys
xkb_symbols "x11" {

    include "keypad(operators)"

    key  <KP7> {    [  KP_7,    KP_7    ]    };
    key  <KP8> {    [  KP_8,    KP_8    ]    };
    key  <KP9> {    [  KP_9,    KP_9    ]    };

    key  <KP4> {    [  KP_4,    KP_4    ]    };
    key  <KP5> {    [  KP_5,    KP_5    ]    };
    key  <KP6> {    [  KP_6,    KP_6    ]    };

    key  <KP1> {    [  KP_1,    KP_1    ]    };
    key  <KP2> {    [  KP_2,    KP_2    ]    };
    key  <KP3> {    [  KP_3,    KP_3    ]    };
    key <KPEN> {    [    KP_Enter    ]    };
    key <KPEQ> {    [    KP_Equal    ]    };

    key  <KP0> {    [  KP_0,    KP_0    ]    };
    key <KPDL> {    [  KP_Decimal,    KP_Decimal ]    };
    key <KPPT> {    [  KP_Decimal,    KP_Decimal ]    };
};
```
After this change toggling NumLock has no effect, it will be always numerical.
Before you edit the file, backup the original one.
After editing the file you should reboot.
This will work only with a real NumPad like you have in most desktop-PCs, I think you have one like this, I see some pics of
samsung activbook 270.
To create a backup of the file run in terminal
```
sudo mv /usr/share/X11/xkb/symbols/keypad /usr/share/X11/xkb/symbols/keypad.bak
```
Open the file in your text-editor and do the changes.
Save the changes to your Documents-folder as keypad
Run in Terminal:
```
sudo cp ~/Documents/keypad /usr/share/X11/xkb/symbols/
```
Reboot...
Now you should have an always numerical NumPad.
You can try out and check if this works for you...
You are always able to reverse the changes we made, you have a backup of the original file, so nothing to worry about.
See also:
[https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions](https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions)
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)
Edit:
I was writing this post with these changes applied to the system.
Now I will revert changes as I don't have problem with Numlock.
See you later...

---

### Post by amr-gaballa777 on 2016-08-28
I have followed your steps sir but I still have the same problem even after reboot . Do you need me to provide screen shots of anything so it may help ?

---

### Post by mook765 on 2016-08-28
Unbelievable, the change we made is pretty deep in the system.
On my machine i was not able to toggle NumLock on and off anymore.
Screenshots are not necessary, but you could attach the current configuration-file (which is /usr/share/X11/xkb/symbols/keypad)  to your next post, so I can take a look at it.
I would like to see if the changes are correctly applied...
To attach the file, click "go advanced",click the paperclip-icon, this will start the upload-manager.browse to the file, when the file is uploaded, drag it to the lower pane,done.
You may have to type a few words, otherwise the forum-software will complain that the message is too short...
I will be back here in about ten hours, need a few hours of sleep now, some job to do as well...

---

### Post by mook765 on 2016-08-29
Please run in terminal
```
setxkbmap -print -verbose 10
```
and paste the output in your next post.

Pretty detailed information about Keyboard-configuration you can find here:
[URL]http://pascal.tsu.ru/en/xkb/[/URK]

---

### Post by amr-gaballa777 on 2016-08-29
Actually there is an error with uploading the attachment , it says " invalid file" but however I uploaded to dropbox and here is the link [https://goo.gl/3KtTpN](https://goo.gl/3KtTpN) I also had to turn it into keypad.txt so you can view it on dropbox . thanks for your efforts

---

### Post by amr-gaballa777 on 2016-08-29
Here is the output ```
Setting verbose level to 10locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     us
options:    numpad:pc
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete+numpad(pc)
compat:     complete
symbols:    pc+us+inet(evdev)
geometry:   pc(pc105)
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete+numpad(pc)"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us+inet(evdev)"	};
	xkb_geometry  { include "pc(pc105)"	};
};



```

---

### Post by mook765 on 2016-08-30
Thanks, I will check out more will take some time, please be patient, I will reply as soon as possible.

---

### Post by mook765 on 2016-08-30
I think we should take a look for the scancodes which are generated by your keyboard.
To do this, please run in terminal
```
sudo showkey -s
```
then hit key"4" on NumPad once,
then hit key "NumLock" once,
then hit key "4" once again,
wait ten seconds to come back to command prompt.
If your output in the terminal is differnt from mine, please post it.
Here is my terminal-output (added a few comments)
```

mook@MookPC:~$ sudo showkey -s
kb mode was ?UNKNOWN?
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]

press any key (program terminates 10s after last keypress)...
0x9c             <---this is left from hitting enter, 0x9c is generated when enter key is released
^[[D0x4b 0xcb    <---here I hit the key"4" on the NumPad quickly
0x45 0xc5        <---here I hit the NumLock-Key quickly
40x4b 0xcb       <---and I hit the key "4" on the NumPad again, after that wait 10 seconds to come back to command prompt.
mook@MookPC:~$ 

```
If your output is the same,let me know...

---

### Post by amr-gaballa777 on 2016-08-31
The output is not identical but I think they are the same .. ah wait if that is going to help I think I read something about connecting external mouse to the laptop ( which I always use for its ease ) which may cause some problems with the keypad is it a true thing ? 
here is my terminal output ....... 
```
 sudo showkey -s[sudo] password for ryuk: 
kb mode was ?UNKNOWN?
[ if you are trying this under X, it might not work
since the X server is also reading /dev/console ]


press any key (program terminates 10s after last keypress)...
0x9c 
40x4b 
0xcb 
0x45 
0xc5 
^[[D0xe0 0x4b 
0xe0 0xcb 



```

---

### Post by mook765 on 2016-08-31
```
^[[D0xe0 0x4b
0xe0 0xcb
```
This is the reason for the headache and the reason why my first idea didn't work.
It is a Samsung thing, we don't have influence upon that on the operating system level.
The scancode is what is sent from the keyboard to the computer. In your case we get different scancodes for the same key just depending on NumLock-state.
Samsung goes an unusual way with this.
Some users tried to solve this with numlockx, a small programm to change the NumLock-state. They where using numlockx in small scripts, checking the NumLock-state every five seconds,if state=off
switch it to state=on. In my opinion not a really good solution, as you have a script running in the background all the time and the NumLock-state is in undefined state for a maximum off 5 seconds, maybe just the moment when you want to use the numpad, NumLock might be toggled off.
So what to do for the moment? 
Leave NumLock toggled off and use shift-key instead, as long as you press shift you have numerical pad, with shift released you have navigation-pad. (This is the case when Numlock is toggled off, when Numlock is toggled on, this reverts)
Do you use an external numpad as well? Your configuration settings show something that let me think that. Please let me know...
You should revert the changes we made in the first step, this changes will affect external numpad too, we reduce functionality when we leave it changed.
I will try to find out something about this strange scancode, seems hard to find.
That NumLock is toggled off after a minute is an other point. I can't believe that this is done by Ubuntu, this is not the Ubuntu way of life.
Maybe Samsung think that this is a good idea, and it might be a good idea when we think about smaller laptops which have the numpad integrated in the literal keys.
You may check your Bios-settings. Many Bios provide a setting for the NumLock-state, maybe yours provides a setting for NumLock-time-out too, I don't know that...
The external mouse shouldn't be a problem... I've never seen an internal mouse...
Can you run```
sudo getkeycodes
```
in terminal and post the output, maybe we can get get some information about that strange scancode.

---

### Post by mook765 on 2016-08-31
So, I found it out what the strange scancode means.
"0xe0 0x4b" is the same scancode as the scancode of the arrow-left key in the  small group of four navigation keys between the numpad and the touchpad.
You can try it out,toggle Numlock off and run```
sudo showkey -s
```
again.Then hit key"4" on numpad and then arrow-left-navigation-key and you will see, that both keys give the same scancode.
That means, that the numpad-keys will not be handled as first-level-keypad when NumLock is toggled off. That is why my first idea didn't work. The numpad-keys will be handled as second-level-keypad when NumLock is toggled on.
Playing with configuration-settings will not change anything, it is the way Samsung handle the scancodes which are generated keyboard-intern and sent to the operating-system, and we don't have any influence upon that. Really no way.
In my last post i suggested to check Bios-settings. If it is not to difficult, try to update your Bios as well.Check out  if newer version is available.
Would be nice to hear from you how things are going...
I move to my bed now...

---

### Post by amr-gaballa777 on 2016-09-03
Sorry for the delay sir but I'm totally new to ubuntu forms and didn't get any notification about the reply .. first of all if you mean I use an external numpad a device with w external cable to use nums then no I'm not using any only the normal number and the normal numpad which is internal in the keyboard second of all about the BIOS thing no it doesn't provide anything about the numpad or even the keyboard it only supports few options for my laptop and third of all after running the code ```
[COLOR=#000000][FONT=&quot]sudo getkeycodes
[/FONT][/COLOR][COLOR=#000000][/COLOR]
```
the result is as follows : ```
Plain scancodes xx (hex) versus keycodes (dec)for 1-83 (0x01-0x53) scancode equals keycode


 0x50:   80  81  82  83  99   0  86  87
 0x58:   88 117   0   0  95 183 184 185
 0x60:    0   0   0   0   0   0   0   0
 0x68:    0   0   0   0   0   0   0   0
 0x70:   93   0   0  89 148 150  85  91
 0x78:  155  92   0  94   0 124 121   0


Escaped scancodes e0 xx (hex)


e0 00:    0   0 227 236 148   0 238   0
e0 08:  225 224   0   0   0   0   0   0
e0 10:  165   0   0   0   0   0   0   0
e0 18:    0 163   0   0  96  97   0   0
e0 20:  113 140 164   0 166   0   0   0
e0 28:    0   0 255   0   0   0 114   0
e0 30:  115 149 172 202 238  98 255  99
e0 38:  100   0   0   0   0   0   0   0
e0 40:    0   0   0   0   0 202 119 102
e0 48:  103 104   0 105 112 106 118 107
e0 50:  108 109 110 111   0 238   0   0
e0 58:    0   0   0 125 126 127 116 142
e0 60:    0   0   0 143   0 217 156 173
e0 68:  128 159 158 157 155 226   0 112
e0 70:    0   0   0   0   0   0   0 192
e0 78:    0 193   0   0   0   0   0   0
```

---

### Post by amr-gaballa777 on 2016-09-03
wow that seems a bit disappointing but anyways I didn't know how to update my BIOS I don't even know it's update-able I ever thought it's a solid thing which comes with the laptop/PC and never changes I already appreciate your efforts sir but would be very grateful if you show me some path to walk through ... by the by I ran the code when numpad toggled off and you were absolutely right the output for "4" and the left arrow are identical .. anyways I feel a little depressed from ubuntu 16.04 and seriously thinking of getting back to 14.04 although I have the same trouble there with numpad thing .. thanks

---

### Post by mook765 on 2016-09-04
For me 16.04 is running just smoothly, the main problems which might exist in a brand new release are almost solved, now it is 16.04.1 already.
If you want to go back to 14.04 it means to do a fresh install of 14.04, there is no other way to downgrade. 
If you upgraded from 14.04 using the software-updater I would suggest do try a fresh install of 16.04.1.
A fresh install is different from a do-release-upgrade. I read a lot here in the forums, you can find many threads with problems after a do-release-upgrade.
Many experienced users recommend a fresh install.
About updating the firmware (Bios) you have to refer to your user-manual which came with your laptop. You may got a CD with all the Windows-drivers, you may find a manual on the CD.
If you don't have any manual you have to check out at [www.samsung.com]("http://www.samsung.com"). You need the exact name of your computer ("samsung ativbook 270" might be not exact enough, I get very different models
when I google for this). You can download manual and firmware from samsung. Every machine is a bit different, so I am unable to tell you exactly how to update your Bios, you have to refer to the manual.
If you feel not sure or it seems to difficult, then don't perform the update.Old wisdom tells:"never change a running system"...
If you need more help with new problems it is better to open a new thread. You will get more attention for your specific topic in a new thread.
Just right now we are off-topic already and when we continue that a forum-moderator might close the thread...
So you don't need to type an answer in this thread, new topic --> new thread.
When I have an answer for your questions in a new thread, you will get it...

---

