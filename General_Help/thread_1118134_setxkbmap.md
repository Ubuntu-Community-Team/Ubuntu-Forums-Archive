---
title: "setxkbmap"
date: 2009-04-06
forum: General Help
---

### Post by VCoolio on 2009-04-06
I use setxkbmap to set my keyboard to write classical Greek. Problem is I can' t get back to my default setting. I can do setxkbmap us or us_intl, but that doesn't give me my default setup. So, how do I find out the setxkbmap code for my default setup? Or what is the command to forget about the setxkbmap and get back to default?
EDIT: I used KKBSwitch to find things out. That toggles fine between US and Greek, both set as possible keymaps in my keyboard preferences. When I do setxkbmap, that screws things up. When I open my keyboard preferences and tick and untick some setting, my keyboard indicator switches back to default. Question remains; with what command do I get my default layout?
EDIT2: ok, when I do setxkbmap en_US it creates a file ~ /.xinput.d/en_US with this content:
```
XIM=SCIM
if [ -e /usr/bin/skim ]; then
    XIM_PROGRAM=" "
else
    XIM_PROGRAM=/usr/bin/scim
fi
XIM_ARGS="-d"
if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
else
    QT_IM_MODULE=xim
fi

DEPENDS="scim | skim, scim-bridge-agent, scim-bridge-client-gtk | scim-bridge-client-qt"
```
Maybe the problem is the input settings instead of keymap. Still: what command to get default?

---

### Post by andrew.46 on 2009-04-17
Hi VCoolio,

I am afraid that I cannot help you with your setxkbmap problem but can I suggest another approach to writing ancient greek? My apologies if you have already heard of [the thessalonica utility]("http://www.thessalonica.org.ru/en/") that works beautifully with OpenOffice.

I attach a screenshot of Thessalonica at work in OpenOffice 3 and also wish you all the best in resolving your issue with setxkbmap :-).

Andrew

---

### Post by VCoolio on 2009-04-30
I didn't know about that Thessalonica app. But
1. I don't like Java and
2. It is OpenOffice-only.

I used to follow [this]("http://www.frame-poythress.org/poythress_articles/2007KeyboardGreekHebrew.htm") howto, but it is a bit difficult and (from the point where you change input to xim I think) screws up the normal input of complex characters and unicode input.

Now I found out what to do. If you're interested, here is howto on Jaunty and completely harmless :) :
0. The howto requires your system to be in locale en_US.UTF-8. Don't know how necessary that is, but if you have it different you might have to change the location you use in step 2 to your locale.
1. From the link I gave, download evdev.xml, Compose.new and gr.hal (not gr.new). 
2. put Compose.new in 
/usr/share/X11/locale/en_US.UTF-8/
Backup the existing Compose and rename new one to Compose
3. after backup of existing evdev.xml put downloaded evdev.xml in:
/usr/share/X11/xkb/rules/
4. after backup of existing gr put downloaded gr.hal in
/usr/share/X11/xkb/symbols
and rename to gr
5. Logout, login, go to system > preferences > keyboard > layouts and add greek polytonic. I did not choose the Poythress one as it refused to compose complex characters with spiritus in it. With the button layout options > layout switching you can add a keybinding to switching layout easily. Also you can add a layout switcher to your panel.
6. I recommend font Palatino, but check for yourself.

---

### Post by simosx on 2009-05-05
In Ubuntu 9.04 (and 8.10) you can have Greek Polytonic out of the box, without additional changes.

In Ubuntu 8.10 you need to add the Greek Polytonic keyboard layout.
Then, press, for example, [ + &#945; = &#8118;

In Ubuntu 9.04 you can just add the Greek (default) keyboard layout.
Then, press, for example AltGr + [ + &#945; = &#8118;
You can also have &#993;&#1016;&#1013;&#951;&#991;&#981;&#1010;&#955;&#991;&#892;&#945;&#945;&#1010;&#948;&#981;&#982;&#976;&#1019;&#1018; (archaic symbols) when you press AltGr + alphabet letters.

---

