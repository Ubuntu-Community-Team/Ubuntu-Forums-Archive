---
title: "How to type in Japanese, Chinese, Korean?"
date: 2006-01-27
forum: Desktop Environments
---

### Post by kinseikun on 2006-01-27
Hello.
I discovered the Keyboard Indicator, which finally has Japanese, but when I try to use Korean it says: 

"Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>"

Also, there is no option for Chinese even though I know I installed it.
The Japanese font works, but only if you know the Japanese keyboard (which I don't). I am use to the Mac / Windows Japanese and Korean IME where you can type "ko" in English and it automatically changes to "ko" in Japanese or Korean. I don't know the Korean keyboard either. Is there a way I can use Asian Input like the Mac input? Please! Thanks.

---

### Post by FarEast on 2006-01-27
Hi kinseikun,

> Is there a way I can use Asian Input like the Mac input?
Please visit the web below.
[http://www.scim-im.org/](http://www.scim-im.org/)

---

### Post by heart_reaver on 2006-01-27
you  can install scim
for chinnes INPUT

for more information how to install is at 

[http://www.makuchaku.info/amnesty/#scim](http://www.makuchaku.info/amnesty/#scim)

---

### Post by Marc Higgins on 2006-02-11
not sure what your experiance has been with scim but i could never get it working properly so we use nabi instead & that seems to work perfectly

not saying that this is perfect but this is how i got Korean input working with nabi on brezzy

Firstly full kudos need to go to these guys; [http://rx78gd.egloos.com/m2005-11-01](http://rx78gd.egloos.com/m2005-11-01) if you can read Korean this site is a really good source of brezzy howtos; here it is verbatim from the above site;

1.&#45208;&#48708;&#47484; &#49444;&#52824;&#54620;&#45796;.

$ sudo apt-get install nabi

2. &#46356;&#47113;&#53664;&#47532;&#50640; sudo vi .gnomerc &#54616;&#50668; &#50500;&#47000;&#50752; &#44057;&#51060; &#51077;&#47141;&#54664;&#45796;.

export LANG=ko_KR.UTF-8
export LC_ALL=ko_KR.UTF-8
export XMODIFIERS="@im=nabi"
export GTK_IM_MODULE=hangul3f
export GDK_USE_XFT=1
nabi &

3. $ sudo dpkg-reconfigure locales

4. &#51060;&#44275;&#50640;&#49436; &#50689;&#47928;&#47700;&#45684;&#50640;&#49436; &#51077;&#47141;&#47564; &#54620;&#44544;&#47196; &#49324;&#50857;&#54624;&#47140;&#47732; en_US.UTF-8 UTF-8 &#47484; &#49440;&#53469;&#54616;&#44256;, &#47784;&#46304; &#47700;&#45684;&#47484; &#54620;&#44544;&#47196; &#54624;&#47140;&#47732; ko_KR.EUC-KR EUC-KR, ko_KR.UTF-8 UTF-8 &#47484; &#49440;&#53469;&#54620;&#45796;.

5. &#51116;&#48512;&#54021;...^^

&#51116;&#48512;&#54021;&#54616;&#44256;&#45208;&#47732; &#45208;&#48708;&#44032; &#46896;&#44163;&#51060;&#45796;. &#51060;&#54980; &#44036;&#45800;&#54620; &#49444;&#51221;&#47564; &#54644;&#51452;&#47732; &#51096; &#45208;&#50728;&#45796;.

&#51088;&#49464;&#54620; &#44163;&#51008; [https://wiki.ubuntu.com/KoreanSetupH...=%28korean%29/](https://wiki.ubuntu.com/KoreanSetupH...=%28korean%29/) &#47484; &#52280;&#44256;&#54664;&#45796;.


If you can’t read Korean this is how i have done it;

1) You don’t really need all of these but it will give you all of the Korean goodies

sudo apt-get install language-pack-gnome-ko language-pack-gnome-ko-base language-pack-ko language-pack-ko-base language-support-ko mozilla-firefox-locale-ko nabi openoffice.org2-help-ko openoffice.org2-l10n-ko ttf-alee ttf-unfonts xfonts-baekmuk

2) Sort out your locals

sudo nano /etc/locale.gen edit it to look like this & save it

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

then run

sudo locale-gen

3) in the home directory of each user you want to be able to input Korean you need to create a .gnomerc file

sudo nano .gnomerc

export LANG=ko_KR.UTF-8
export LC_ALL=ko_KR.UTF-8
export XMODIFIERS="@im=nabi"
export GTK_IM_MODULE=hangul3f
export GDK_USE_XFT=1
nabi &

Save the file “ctrl o” then “ctrl x”

4) & then reboot login & select Korean for your language & you should have an all Korean desktop. Nabi will start automatically & you just need to press “shift + space bar” to swap between Korean & English input

The only unresolved issue i have is even if you select English for your language some stuff is still in Korean, date & time, firefox menus etc

---

