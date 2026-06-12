---
title: "Keyboard layout doesn't switch languages"
date: 2017-05-01
forum: Desktop Environments
---

### Post by timomak on 2017-05-01
Hi,
I have succesffuly installed Lubuntu 16.04.2 LTS on a Dell Latitude D630 and works fine.
The only thing i face for the moment is that keyboard layout doesn’t switch between languages.
English is the first language and Greek should be the second. Although Greek is installed (seen 
in the language support) i can’t switch keyboard and only english is enabled.

 Searching a lot about this issue i wasn’t able to find a solution that works.
The only input tool existing in Lubuntu is fcitx. I tried some changes over there but with no luck.
Is any method to work on for solve this problem?
Thank you in advance

---

### Post by Rex Bouwense on 2017-05-02
The keyboard layout switcher can be changed by right clicking the flag icon (or 2 letter country code) in the LXPanel.  Then chose "Keyboard Layout Handler" settings.  In the pop-up window uncheck Keep system layouts (in the right hand column).  Select add (in the left hand column) and then scroll down to Greek and select it.  Arrange the languages like you want them using the up and/or down arrows and then re-check Keep system layouts. Close the window and I believe that you should be go.

---

### Post by timomak on 2017-05-03
Hi Rex,
Thank you for answering.
I think i miss something.
1. I can’t find keyboard handler settings in my system. The only icon that appears is a small
keyboard on the right bottom side, close to computer icon (see photo) and this when i open >system tools>fcitx. If right click on it there are some keyboard settings but not as you described.
2. Saying switch between languages i mean changing input from
english to greek and vis versa, instantly, pressing “alt shift”. This option
is not working with my keyboard.
I"m new to Linux, if i miss things please let me know.

---

### Post by sudodus on 2017-05-03
Which version of Lubuntu are you running? From the attached picture's wallpaper I guess 16.04 LTS. Is that correct? When I know I can check if it works according to @ Rex Bouwense's reply and maybe suggest some modification.

-o-

There is a simple fix, if it is enough to change the keyboard (and not texts in program windows etc), to use aliases and the command setxkbmap. You do that in a terminal window.

Create aliases:
```

alias 2gr='setxkbmap gr'   # to Greek
alias 2&#947;&#946;='setxkbmap gb'   # to British English (gb)
alias 2&#952;&#963;='setxkbmap us'   # to US English (us)

```

Use aliases:
```

2gr  # run in a Latin keyboard (e.g. English ...)
2&#947;&#946;  # run in a Greek keyboard
2&#952;&#963;  # run in a Greek keyboard

```

Store aliases:

You can paste the command lines to create aliases into your **~/.bashrc** file (e.g. near the other aliases). Then they will be activated in all new terminal windows that you open.

Find the aliases (that start with 2) with the following command line

```

alias|grep 'alias 2'

```

You can use the program ***onboard*** to display the current mapping of the keyboard.

---

### Post by timomak on 2017-05-03
Thank you for answering,
You're right. The version is Lubuntu 16.04.2 LTS 64bit

---

### Post by sudodus on 2017-05-03
0. This guide for Lubuntu 16.04 LTS assumes that you start in English

1. To make things work, run

```
sudo apt-get update
```

and in an installed system, run

```
sudo apt-get dist-upgrade
```

2. **Menu: Preferences -- Language Support**

2.1 Let it install complete language support

2.2 Install/Remove Languages ...

and install Greek (tick and apply)

2.2.1 Drag Ellanika to the top in the box with English versions

2.2.2 Drag English (UK) to the top or the second position (unless you prefer
English (US), which is there now.

2.3 Keyboard input method system: Select fcitx

2.4 Apply System-Wide if you wish

2.5 Close the window

3. **Menu: Preferences -- Fcitx Configuration**

Maybe you want to configure something.

4. **Menu: System tools -- Fcitx**

4.1 ***You get a keyboard icon near the right end of the panel. Click on it.***

4.2 Select 'Configure Current Input Method'

4.2.1 Untick 'Only show Current Language'

4.2.2 Select Greek and expand it (click on the triangle in front of the text)

4.2.3 Mark the Greek keyboard that works best and click on the right arrow to
move it to the 'Current Input Method' box

4.2.4 Mark and move the 'languages' up or down in the 'Current Input Method' box

4.2.5 Close the window

5. **Now you should be able to switch language of the keyboard**

5.1 ***Click on the keyboard icon near the right end of the panel.***

5.2 ***Select 'Input Method'*** and in the sub-menu Greek or English, and you should
be able to switch easily what is typed, when you use the keyboard.

After logout and login the text in the desktop and in application programs will be in Greek, if that is the default language (at the top of the box with selected languages). See the attached picture.

---

### Post by timomak on 2017-05-03
Thank you.
I will go through this guide and come back again.
However, Greek is already installed, i want to keep English as main system language.(i guess i will skip this step)
Only issue is while typing, to be able switch between the 2 languages.

---

### Post by timomak on 2017-05-05
Hi,
Cont/d..
According to your suggestions this worked in a way. 
I explain: I can switch keyboard using the icon right down corner> input method> sub-menu and switch languages. Then keyboard works.
I would suggest in this case, for having this work, check ‘fcitx’ in the keyboard input method system (down bottom) in the box of language support. Leaving ‘none’ which is default setting, may not work at all. I haven’t try ‘XIM’ option (i don’t know what stands for)

But the problem is that i still can’t switch languages directly from keyboard using ‘alt shift’ keys or other combination. Something more is needed for keyboard mapping.

Another ‘strange’ thing here is with the Lenovo (friend’s notebook), on which i have installed the same system 16,04.2 LTS (32 bit) on a usb drive and US English language. 
In this case, while installation was correctly done with Athens area in the map, Greek language doesn’t seem installed in the support languages, and keyboard input method system is checked ‘none’ by default. However,*** keyboard  switches  languages using ‘alt shift’ with no problem!!!***
I tried reproduce the above on Dell but didn’t work.

When searching about this issue, i found the follow related articles.
1. The command,&#65279;
sudo dpkg-reconfigure keyboard-configuration
from this post [https://askubuntu.com/questions/765015/how-do-i-change-default-keyboard-layout-not-input-method-in-ubuntu-16-04](https://askubuntu.com/questions/765015/how-do-i-change-default-keyboard-layout-not-input-method-in-ubuntu-16-04)
Entering this command in terminal, reading is, ‘Generic 105-key (intl) pc.
But there are choises among keyboards by computer brand names(i.e lenovo, hp etc) and there i found dell latitude keyboard. I didn’t proceed further for not making things worse.
Q: should i go for it and reconfigure my keyboard or will cause another problem?

2. The following is an official guide for keyboard mapping.
[https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)
Q: May this be helpful ?

3. During the procedure you proposed, the volume of ‘accumulative’ updates an upgrades was big enough. After that i noticed an "instability", i.e system didn’t reboot as normal.  I had to reboot again.
Q: Would this be too much for a newly installed system?

Thank you.

---

### Post by sudodus on 2017-05-05
I think you have reached beyond my experiences of keymap switching now. So I have no good answers. Let us hope people with more experience in this area will see your thread and share their methods.

What I can suggest is that you create a separate test system, either in an external drive or as a dual or multi boot alternative in the internal drive, and do the experiments there (without risking your 'production system').

---

### Post by timomak on 2017-05-05
I'll do set as separate system as you suggested,
Thank you - &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974;! (mean the same)

---

### Post by sudodus on 2017-05-05
Good luck :-)

---

### Post by timomak on 2017-05-10
Cont/ed...
Finally, the reason i couldn&#8217;t switch keyboard between languages is because during installation i missed to configure the correct keyboard layout. 

1. **System and keyboard**
In Lubuntu 16.04. and beyond, configuring a second keyboard and system language is obtained through &#8216;fcitx&#8217; input method under >system tools and of course &#8216;language support&#8217; under >preferences, for installing and setting a second language. The method  @sudodus as above (last post), describes the steps to follow for obtaining it.

2. **Change keyboard layout after installation**
If we need to change the keyboard layout after installation, so that being able to switch one or more languages, either momentary or for the current session  using &#8216;alt shift&#8217; or other keys,  we have to type the following command in terminal and follow the guided setup.

&#8220;&#65279;sudo dpkg-reconfigure keyboard-configuration&#8221;

Perhaps there is another method on this issue but the above is tested and works fine.

---

### Post by sudodus on 2017-05-11
Congratulations and thanks for sharing your solution :KS

---

