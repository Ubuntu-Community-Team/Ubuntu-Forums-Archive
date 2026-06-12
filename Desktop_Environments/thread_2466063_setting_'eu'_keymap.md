---
title: "setting 'eu' keymap?"
date: 2021-08-18
forum: Desktop Environments
---

### Post by Johannes33 on 2021-08-18
Hi,
I would like to set eu keymap i.e. [Eurkey keymap ]("https://eurkey.steffen.bruentjen.eu/download.html").
That can be done after reboot with the commando 
>setxkbmap eu

So I know I have it installed.
Now I wonder how to make it permanent. It is a us keyboard layout with AltGr+<key> to make special characters.
Since it is a us keyboard I would like to select it among the us keyboards. but could not, it does not exist.
I have looked att other languages but nothing seems to fit eurkey. 
Perhaps there is a way to search for the eurkey keyboard layout?
Suggestions would be much appreciated.
So workarounds.
where can I put the command setxkbmap eu to not be overridden by gnome and run everey time I login?
Or perhaps there is a way of setting the keyboard map in dconf editor that make it persistant?
The easiest way would be to edit som text file where the settings are stored so I can just bypass all the cumbersome gui settings tools.
Well suggestions would be much appreciated.
I have tried 'localectl set-x11-keymap *eu*' but it does not work.

---

### Post by bcschmerker on 2021-08-18
**The EurKey software is off-site for Canonical Limited.**  &#1043;teffen Brüntjen (EurKey.Steffen.Bruentjen.eu) has the following command sequence for Terminal (as Root) to add the off-site Repository and install EurKey:

```

wget -nv -O - https://eurkey.steffen.bruentjen.eu/download/debian/repo/conf/eurkey.gpg.key | apt-key add -
echo deb https://eurkey.steffen.bruentjen.eu/download/debian/repo stable main | sh -c 'cat > /etc/apt/sources.list.d/eurkey.steffen.bruentjen.de.sources.list'
apt-get update
apt-get install eurkey

```

---

### Post by Johannes33 on 2021-08-19
Did all that.

After doing the apt-get install eurokey apt responded with that it was already installed.

I do not have the output of the terminal since I loged out and in to try to see if it made any changes to my settings.

so far the only way to activate eurkey is with [B]'setxkbmap eu' 
[/B]
I'm starting to think I should put "setxkbmap eu" in some file that gets executed on startup since no setting in gnome seems to work. 
I have also tried:  dconf write /org/gnome/desktop/input-sources/sources "[('ibus', 'eu')]" but it does not work as well. I have dconf editor installed.

The only problem is I do not know where to put the "setxkbmap eu".
 
Anybody have any clue?

---

### Post by Holger_Gehrke on 2021-08-19
You might want to take a look at the [FAQ]("https://eurkey.steffen.bruentjen.eu/faq.html") page, more specifically the fifth question.

Holger

---

### Post by GhX6GZMB on 2021-08-19
I'm a bit lost about what you are trying to do here.
Keyboards are extremely country/language specific and the idea of an "EU"-keyboard is somewhat... challenging?
The keyboard layout picture on the link to Eurkey made my eyes hurt and almost turned me schizophrenic. (Joke).

If it's just a question of getting the right "Alt" key to operate as an "Alt Gr" key, remapping that key is much easier.

The active keyboard layout is as default defined in /etc/X11/xorg.conf.d/00-keyboard.conf

---

### Post by GhX6GZMB on 2021-08-20
OK, tried it myself just for fun.

The procedure is as follows:
First check if your "eu" keyboard layout is installed by issuing:
```
localectl list-x11-keymap-layouts
```
Then change (sudo edit):
```
/etc/X11/xorg.conf.d/00-keyboard.conf
```
from:
```
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" **"us"**
        Option "XkbModel" "pc104"
EndSection

```to:
```
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" **"us,eu"**
        Option "XkbModel" "pc104"
EndSection

```Don't change anything else.
Now you should be able to switch between US and EU layout. You'll need to at least logout/login, but a reboot might be necessary to make it work.

---

### Post by Johannes33 on 2021-09-22
Thanks a lot for your help!!
I have not tried it yet but I will and report back. 
The thing is that I can find Eurkey in KDE but not in Gnome. It must be a bug since it is selectable through setxkbmap.
As a woraround I installed the .deb file from the Eurkey site.
Then the keyboard layout can be selected among the UK keyboard settings but it should be a US keyboard setting since it is based on the US keyboard layout and not the UK.
Well at least it is selectable in gnome after the work around. If your suggestion work it would be a much nicer way to solve the problem.

About the options. I really like the notion of having one keyboard layout for almost the whole of europe. Then you could easily buy computers from other nations, you can work on different sites all over europe and US, since Eurkey is US based, and still touch type. For me that is a real benefit. 
Also since programming has it's origin in using a US keyobard the ease of programming using a US keyobard compaired using a Swedish is significant imo.
I miss some matematical notation capabilities though, like arrows and greek letters. It would be good if they were accessable through using some sort of AltGr key combination as well.
Just my 5 cents of thought...

Thanks a lot for your help!

/Johannes

---

