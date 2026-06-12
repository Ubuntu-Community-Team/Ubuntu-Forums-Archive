---
title: "Keyboard layout incorrect for some characters"
date: 2008-12-27
forum: General Help
---

### Post by dishbert on 2008-12-27
I just installed 8.04 LTS and set my keyboard layout as "Canada" during the install.  

When I type Shift + 2, instead of the At Symbol I get a quotation mark!  

I imagine this is going to make emailing difficult.

Other characters are wonky as well:

Shift + 3 = /
Shift + 6 = ?

I`ve tried adding the USA keyboard layout under keyboard preferences, layout, with the same result.

dishbert

---

### Post by Ivo Moelans on 2008-12-28
I'm not from Canada but I was intrigued because in Belgium we also have a strange keyboard.

Try this:

Launch *System&#8594;Preferences&#8594;Keyboard*. Click the *Layouts* tab.
Under *Selected layouts...* click on the 'add' icon. Click on "Country" and select Canada. Click on "Variants" and try out all possibilities.

Let me know if this helps.

---

### Post by dishbert on 2008-12-28
Thanks for the suggestion Ivo.  The variants on the Canada keyboard layout are for other languages:  French, some native languages etc.

I added the USA keyboard layout and then installed a keyboard toggle on the panel to switch between them.  The USA layout handles the @*sign*correctly, but then screws up many of the other keys.  As an example, the USA layout prints ¶*when*I*¶ress*the*P key.  (I had to switch back to the Canada layout to get the P to appear).

I think I have standard keyboard hardware, although there is no label on it.  It has worked fine with other versions of Ubuntu, Mint and XP.  

I could move over my keyboard layout file from the Mint 4.0 partition, if I knew the file name and location.

Alternatively, there must be a way to remap the offending keys.

---

### Post by Ivo Moelans on 2008-12-28
The location of the keyboard files is */usr/share/xmodmap/*. With Text Editor (superuser mode) you can open them - or make a new one. I think (have never tried this) that if you read them carefully it is not to difficult to understand them: the format of the document is fairly simple.

---

### Post by dishbert on 2008-12-28
Solved! @#^ !

I think I found the problem:  my generic keyboard is a Multimedia model, and when I changed the hardware selection to an HP Multimedia model it works OK with the USA layout (though not with the Canada layout).

Allow me to demonstrate with the top row using:

USA:     !@#$%^&*()_+|  
Canada:  !"/$%?&*()_+>

My guess is that Ubuntu failed to identify the correct keyboard hardware on installation, but that still doesn't explain the USA - Canada difference.

Thanks for the help Ivo

---

### Post by Ivo Moelans on 2008-12-28
As I understand it you have several keyboards in Canada: French, International and so on. Perhaps the proper xmodmap file is missing. (I'm fairly certain that Shift+2=" is from the Canadian French keyboard.)
BTW: have you tried making a copy of the Canadian xmodmap and editing it?

---

### Post by dishbert on 2008-12-28
I couldn't figure out which of these layouts was the Canadian one:

chris@Linux-Downstairs:/usr/share/xmodmap$ ls
base.xml          xmodmap.gb-102       xmodmap.lt_b        xmodmap.si
xmodmap.am        xmodmap.gb-105       xmodmap.lt_p        xmodmap.sk
xmodmap.ar        xmodmap.ge_la        xmodmap.mk          xmodmap.th
xmodmap.be        xmodmap.ge_ru        xmodmap.mn          xmodmap.tr_f
xmodmap.bg        xmodmap.gr           xmodmap.mn-phonet   xmodmap.tr_q
xmodmap.br        xmodmap.hu           xmodmap.mn-rev      xmodmap.uk
xmodmap.ch        xmodmap.hu-101-lat1  xmodmap.mn-uni      xmodmap.uk_x86
xmodmap.ch_de     xmodmap.hu-101-lat2  xmodmap.nl          xmodmap.us
xmodmap.ch_fr     xmodmap.hu-ibm       xmodmap.no          xmodmap.us-101
xmodmap.cz        xmodmap.hu-lat1      xmodmap.pl          xmodmap.us101A_x86
xmodmap.de        xmodmap.hu_latin1    xmodmap.pl2         xmodmap.us-84
xmodmap.de-apple  xmodmap.hu.old       xmodmap.pt          xmodmap.us-dec
xmodmap.dk        xmodmap.hu-sun-lat2  xmodmap.pt-dead     xmodmap.us-ibm
xmodmap.dvorak    xmodmap.hu_x86       xmodmap.qc          xmodmap.us-int
xmodmap.ee        xmodmap.il           xmodmap.qc-2        xmodmap.us_intl
xmodmap.es        xmodmap.il_phonetic  xmodmap.ro          xmodmap.us-mac
xmodmap.es_x86    xmodmap.is           xmodmap.ru          xmodmap.us.old
xmodmap.fi        xmodmap.it           xmodmap.ru-rev      xmodmap.us-sgi-101
xmodmap.fr        xmodmap.jp           xmodmap.ru_yawerty  xmodmap.us-sun
xmodmap.fr-2      xmodmap.kr           xmodmap.se          xmodmap.yu
xmodmap.fr_x86    xmodmap.la           xmodmap.sf
xmodmap.gb        xmodmap.lt           xmodmap.sg


When I open up the USA layouts, they look fine:

keycode   8 =
keycode   9 = grave asciitilde
keycode  10 = 1 exclam
keycode  11 = 2 at
keycode  12 = 3 numbersign
keycode  13 = 4 dollar
keycode  14 = 5 percent
keycode  15 = 6 asciicircum
keycode  16 = 7 ampersand
keycode  17 = 8 asterisk
keycode  18 = 9 parenleft
keycode  19 = 0 parenright
keycode  20 = minus underscore
keycode  21 = equal plus
keycode  22 =
keycode  23 = BackSpace
keycode  24 = Tab
keycode  25 = q Q
keycode  26 = w W
keycode  27 = e E EuroSign
keycode  28 = r R
keycode  29 = t T
keycode  30 = y Y
keycode  31 = u U
keycode  32 = i I
keycode  33 = o O
keycode  34 = p P
keycode  35 = bracketleft braceleft
keycode  36 = bracketright braceright
keycode  37 = backslash bar
keycode  38 = Caps_Lock
keycode  39 = a A
keycode  40 = s S
keycode  41 = d D
keycode  42 = f F
keycode  43 = g G
keycode  44 = h H
keycode  45 = j J

And my success was short-lived, the USA plus HP Multimedia combo did not survive a reboot.  Switching to an alternative Multimedia board worked, but again, only till the next reboot.

Yikes!

---

### Post by Ivo Moelans on 2008-12-28
I'm beginning to suspect there is something wrong with your locale settings.
Try to run *locale* in a terminal. The output for an English Canadian system should be something like

```

$ locale
LANG=en_CA.UTF-8
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME=en_Ca.UTF-8
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_Ca.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=
$

```

LC_CTYPE & LANG seem to be the most important for this problem.
Could you post the output of the command *locale*?

---

### Post by dishbert on 2008-12-28
Thanks again for your help on this Ivo.

It looks to be the same output as your post:

chris@Linux-Downstairs:~$ locale
LANG=en_CA.UTF-8
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=
chris@Linux-Downstairs:~$

---

### Post by Ivo Moelans on 2008-12-28
Stranger and stranger. *LC_CTYPE="en_CA.UTF-8"* should give you an English Canadian keyboard layout, but apparently something overrides this. The only thing I can think of is that some configuration file in your home directory is responsible for switching the system back to French Canadian because those override global settings.

---

### Post by dishbert on 2008-12-28
It's a new install so there isn't much in the home directory:

chris@Linux-Downstairs:/home$ ls
chris
chris@Linux-Downstairs:/home$ cd chris
chris@Linux-Downstairs:~$ ls
Desktop    Downloads  Examples     google-earth  Pictures  Templates
Documents  dwhelper   googleearth  Music         Public    Videos

I may have to delete the partition and reinstall, but I hate to lose all the work that went into the updates and package installations.  

Are they all stored somewhere?  It thought they were in /etc/apt/ but I don't see them there.

I'm also installing the KDE desktop at the moment, but I don't imagine that will help.

---

### Post by little image on 2008-12-28
Problem with new USB keyboard on Ubuntu 8.04 - wrong characters on part of the keyboard - layout problem.

all characters OK except for right hand side

For example -  é character written instead of /     - want standard english !

Go to System > Preferences > Keyboard >layouts

You will be using the "Type to test settings" bullet in this window

When I type in here I still get the (é) acute e's instead of the /

I entered the correct keyboard information - no change in problem.

For Layout I entered both the USA and the Canada Layout for possible use. Why ? - French Canadiens use a lot of acute e's.  I thought for a short while that the problem might be related - but no !

Then chose USA as default. PS - I'm Canadian.

Further in this window, choose Layout Options > Layout Switching > and I checked to see what was chosen for this option.   I made sure that initially NO choices were selected !   THEN I chose the very first setting

    "R-Alt switches layout while pressed"

( NOTE while PRESSED will then cycle through keyboard layout(s) you may have active in the computer !)

I then pressed down the right alternate key only and then tried the 
/ key again.  I got the / finally and all the key characters on the right side and also the whole keyboard responded in the correct way - but only with the R-Alt key pushed down.

Now to make the change to the correct layout "permanently" for normal operations !

I then choose Layout Options > Layout Switching > and unchecked

  "R-Alt switches layout while pressed"

 THEN I chose a new setting

    "Alt + Ctrl change layout" and checked this box.

NOTE - some choices offered to make "change layout" did not work.  I found the above did.

I closed the Layout Options window and then hit the Alt + Control
keys together and found that I could change the keyboard character layout.  I did so until I found that I could get normal operation of the character keys as desired -   / |  }  etc.  I was pleased.

This was all done using the "Type to test settings" bullet in this window.

I closed off the windows.

I then launched the Text Editor app on the desk-top and found that I STILL got the old acute e  (é) when typing rather than the / as expected.

I was frustrated !

I went back to the Layout window.  PROBLEM SOLVED - how ?

DO NOT check "separate layout for each window" - if checked, desktop app you launch will most likely default back to a layout you don't want when you open any new app/window on the desktop.

Leave this box unchecked and your chosen "normal" keyboard character layout will rule through all apps and windows.

---

### Post by Ivo Moelans on 2008-12-28
No, there is a lot more. Look with nautilus and press Ctrl+H to make the hidden files visible.
There are a lot of configuration files in the directory *.gconf*, but there are also other possibilities like the file *.profile* less likely: *.bash_profile* or *.bash_login*. Probably an application that starts automatically or that you use often changes the keyboard/language settings and writes it in a local settings file. When you override that by selecting another keyboard, that change is applied but doesn't stick because the settings file gets implemented on the next boot. Anyway, that's my working theory for the moment.
It's rather late in Belgium, but I will keep following this post and who knows, after a night's sleep...

Check *.xsession-errors* (if it is there at all) in your home directory (open with Text Editor)

Edit:

> DO NOT check "separate layout for each window" - if checked, desktop app you launch will most likely default back to a layout you don't want when you open any new app/window on the desktop.

That could be it.

---

### Post by dishbert on 2008-12-29
I've never had "separate layout for each window" checked, so that's not the problem.

.xsession-errors has a bunch of these:

last scanned symbol is: XF86KbdBrightnessUp
expected keysym, got XF86Info: line 914 of inet
last scanned symbol is: XF86Info
Warning:          Type "PC_RALT_LEVEL2" has 2 levels, but <LALT> has 3 symbols
                  Ignoring extra symbols
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
Warning:          No symbols defined for <BRK> (keycode 114)
Warning:          No symbols defined for <FK13> (keycode 118)
Warning:          No symbols defined for <FK14> (keycode 119)
Warning:          No symbols defined for <FK15> (keycode 120)
Warning:          No symbols defined for <FK16> (keycode 121)
Warning:          No symbols defined for <FK17> (keycode 122)
Warning:          No symbols defined for <KPDC> (keycode 123)
Warning:          No symbols defined for <XFER> (keycode 129)

But nothing that I can see about the keys that are giving me grief.

Where would the config file for the output of the keyboard layout GUI be located?  I'm thinking there may be a permissions problem or something there.

---

### Post by Ivo Moelans on 2008-12-29
Something new:
Have you checked *System&#8594;Administration&#8594;Language Support*? You can define supported languages there (click open the *Details*), the *Default Language*, which in your case should read *English (Canada)* I suppose, and you can enable support for complex characters.
Are all these settings as they should be?

---

### Post by dishbert on 2008-12-29
Yes, language support is set correctly.

I think I will give up now and reinstall.  This time I will choose the USA keyboard and test the character keys during the install.  I will post the results back to this thread.

Thanks for all your help Ivo, I always learn a lot in these befuddlements.  Now I know how to view the hidden files with Nautilus.

By the way I found a neat little app to back up all the apt-get and install work for those of us who have to reinstall.  It is called ApTONCD.

---

### Post by Ivo Moelans on 2008-12-29
I understand your frustration.
Maybe just one more thing to try before you reinstall. Make a new user. At the very least you will learn if the problem is global or related to something in your home directory.
If the new user hasn't the same problem you don't have to reinstall but 'only' adjust your application settings.
(see *System&#8594;Administration&#8594;Users and Groups*)

Anyway, the best of luck and please report back: I'm very intrigued by now.

---

### Post by dishbert on 2008-12-29
OK Ivo, I set up a new user and still the same problem.  

I installed 8.04 from a DVD included with Linux Identity magazine.  I now see the article about installing specifically mentions the keyboard check during installation, leading me to think there may by a problem specific to this installation disc.  A quick Google search did not turn up any relevant posts however.

I used this disc because it includes the KDE and Mythbuntu distros as well.

I will report back when I reinstall.  Probably tomorrow morning.

---

### Post by Ivo Moelans on 2008-12-29
Well, now you know for sure that it is a system wide problem and not some borked personal setting. Probably something with the disc. Anyhow... good luck with the new installation.

---

### Post by dishbert on 2008-12-29
The reinstall went fine, I chose the USA keyboard this time, and the problem is solved.

Take home message for anyone stumbling across this thread with a similar issue:  DO NOT USE THE KEYBOARD LABELED "CANADA", and ALWAYS try the special characters in the supplied test box during installation.

I can also recommend the APTonCD package to back up and restore your updates and installations if you do have to reinstall.

Thanks again for all the help Ivo, this kind of help from across the planet is one of the things that keeps me going.

---

### Post by Ivo Moelans on 2008-12-30
You're very welcome and I'm glad to hear everything went fine. I know all to well how utterly exasperating and frustrating such 'little' problems can be. I'm afraid I was more of moral support than practical help though, but on the other hand, we learned a thing or two.
Have a nice New Year.

---

### Post by d$_linux on 2009-07-07
After installing Ubuntu on my wifes machine (wubi is simply awesome) I ran into this same issue. There is an Apple keyboard on the machine, the one with clear plastic housing with white keys inside (very common here in Vancouver, likely elsewhere too).

Anyways, I too got the 'en_CA' locale setting when the machine installed. I cannot remember if I specified Canadian in the Wubi installer steps or not. However, that's what I was given after the machine was first up and running.

I did these steps to fix the problem:

1) In a terminal window:
```
> sudo update-locale en_US
```

2) Logged out. In the login screen there is a 'settings' button on the bottom-left of the screen. There, I set the language to 'en_US' and in the dialog that appeared I chose 'Make Default'.

3) After having logged back in, I ran the System->Preferences->Keyboard
3a) Selected the [Layouts] tabbed page
3b) Changed the "Keyboard Model" to "Apple"
3c) Added the USA Layout in the "Layouts" pane
3d) Removed all other layouts from the "Layouts" pane
3e) Ensured the "Separate Layout for each Window" was **unchecked**.
3f) Clicked on the "Apply System-wide..." button

Seemed to have done the trick. See: @ !! (Was " there previously :) )

-D

---

### Post by ross9885 on 2010-02-22
d$_linux, that worked for me on an eee-pc with a Canadian keyboard. I just have to map that extra < on the left to be the second half of the puny left shift key.

~!@#$%^&*()_+
QWERTYUIOP{}
ASDFGHJKL:"|
>ZXCVBNM<>?

`1234567890-=
qwertyuiop[]
asdfghjkl;'\
<zxcvbnm,./

---

