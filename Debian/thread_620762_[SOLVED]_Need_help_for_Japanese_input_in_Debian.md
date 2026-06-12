---
title: "[SOLVED] Need help for Japanese input in Debian"
date: 2007-11-23
forum: Debian
---

### Post by ubuntu27 on 2007-11-23
OK. I've used Ubuntu for two years. I tried out Debian since there are some people claiming that Debian is harder to install than Ubuntu. I can attest that is not true. Debian is quite easy to install. Unfortunately, it seems to be harder to configure (or at least not as easy as in Ubuntu) as you wish. 

Anyway, straight to my point.  I NEED YOUR HELP.

Debian works differnet than Ubuntu. In Ubuntu I can just install Language-support packages and I will have a working input method.

in Debian, I have no idea what to do. I been searching with google for two months and haven't found anything. **I want to be able to input Japanese.**

The only thing I was able to accomplish was to add Japanese support in my applications (for reading i.e. Japanese fonts, etc)

****

I use Debian Sid
I use KDE
I have installed Skim but it is not working yet.
I've installed the  i18 packages

---

### Post by seshomaru samma on 2007-11-23
I have scim running on Sid. On both Gnome and XFCE. 
I used Ubuntu's wiki top set it up : [https://wiki.ubuntu.com/InputMethods/SCIM/Setup](https://wiki.ubuntu.com/InputMethods/SCIM/Setup)
Don't know about KDE, sorry.
Is it working in a text editor (the KDE equivalent of gedit/mousepad)?
Open a text editor and right click anywhere . look for Skim in the 'input methods' tab. Is it there?
Do apt-cache search japanese
and download all the fonts apt comes up with
you probably need to download scim-anthy and im-switch 

try the im-switch method described in the wiki
restart x and it should work

---

### Post by ubuntu27 on 2007-11-23
> **seshomaru samma said:**
> 
Is it working in a text editor (the KDE equivalent of gedit/mousepad)?
Open a text editor and right click anywhere . look for Skim in the 'input methods' tab. Is it there?

The input method editor is not working in any editors. 
When I right click I only encounter 

Select Input Method/Simple Composing Input Method
Select Input Method/XIM

whichever I choose I cannot do anything. It just types with roman letters as usual. 

> **seshomaru samma said:**
> 
Do apt-cache search Japanese
and download all the fonts apt comes up with
you probably need to download scim-anthy and im-switch 

I have installed all the Japanese Fonts for X and the following packages:

anthy
scim-anthy
im-switch
kde-i18n-ja
edict
enamdict
gsfonts-wadalab-common
gsfonts-wadalab-gothic
gsfonts-wadalab-mincho
xfonts-intl-japanese
xfonts-intl-japanese-big
ttf-kochi-mincho
kakasi
kakasi-dic
libtext-wrapi18n-perl


***************************************************************************

EDIT:

Problem solved thanks to Seshou Maru Sama ^^

> **seshomaru samma said:**
> I have scim running on Sid. On both Gnome and XFCE. 
I used Ubuntu's wiki top set it up : [https://wiki.ubuntu.com/InputMethods/SCIM/Setup](https://wiki.ubuntu.com/InputMethods/SCIM/Setup)
Don't know about KDE, sorry.


That dis the trick. I was reading this part 

scim/skim is default Input Method for Ubuntu/Kubuntu CJK users. 
 scim and scim-gtk2-immodule are installed by ubuntu-desktop. 
** skim and scim-qtimm are installed by kubuntu-desktop. **
 Defaulted IM engine module(s)(ie, scim-chewing, scim-pinyin, scim-anthy, or scim-hangul) is installed by language-support-??(ie, language-support-zh, language-support-ja, or language-support-ko) for CJK languages. 
 im-switch is installed by language-support-??.


That's all what I needed. scim-qtimm wasn't installed. Now that it is installed I can type in Japanes yeah!! &#26085;&#26412;&#35486;&#12391;&#12452;&#12531;&#12503;&#12483;&#12488;&#12391;&#12365;&#12427;&#12382;&#12290;&#12288;&#12420;&#12387;&#12383;&#65281;

Thank you seshomaru samma.

---

