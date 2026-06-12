---
title: "Chinese/Korean input in Breezy?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by yangsanggunja on 2005-11-08
Hi.  I'm really new to Linux and Ubuntu.  I had installed Hoary a couple of months ago, including SCIM for Chinese/Korean input and it worked beautifully.  Then I upgraded to Breezy and SCIM doesn't work (I searced and see that this is a common problem).

I updated the language selections to include Korean and Chinese from inside the X system settings, and it downloaded them both (I know because now there is a check mark in those boxes).  From my reading of the help files, this should allow input of these languages, but I can't figure out *how* to do that inputting.  I searched the Wiki and forums.  Somebody posted a way to do it for Japanese, but I don't see anything for Korean or Chinese.

How do I get my Breezy system to switch input so I can type Korean or Chinese?

Thanks!

---

### Post by hunteramor on 2005-11-08
assuming you have all of the packages installed correctly, you should next make scim run on startup.  

go to 'sessions' in the system/preferences menu and add scim -d as a startup program.  the default order should be fine.

when you restart (actually killall gnome-panel *might* do it, i'm not sure) you should then see a keyboard in the notification area.  that's scim.  you can click on that to select your input method (smart pinyin for simplified chinese and UIM-romaja for korean would be my recommendations) or you can hit ctrl+space to switch between methods.

i'm using chinese and korean too, so feel free to post a follow up if you can't get it working with that.

---

### Post by Marc Higgins on 2005-11-15
Hi Guys

We are having some issues getting Korean working here; we live & work in Seoul so Korean is fairly important to us.

2 issues, 1) many korean sights don't work properly (in my view) maybe because they are made with only MS java in mind & it's a bastardised java. To be fair I have come across a number of US sights that are the same. Are you guys experiancing the same thing?

In terms of input methods the alternatives we have tried of are scim & nabi.

Have got scim running but Hoary doesn't seem to do korean properly, some 3 charicter letters can't be typed.

Have nabi working on a FC4 machine with gnome & it works a treat (apart from being a redhat machine). The only reason it's not an ubuntu machine is I haven't worked out Nabi on Breezy

Have had a few shots at getting nabi runing but i just end up with the input box & no thing to select for korean inut. My challenge is want to be able to do this not only in gnome but also xfce4 (xubuntu) & KDE

This is what i have installed.

Installed the following packages:Hi Adam,

We are having some of the same issues here; we live & work in Seoul so Korean is fairly important to us & many korean sights don't work properly (in my view) because they are made with only MS java in mind & it's a bastardised java.

To be fair I have come across a number of US sights that are the same.

In terms of input methods the alternatives I know of are scim & nabi.

Have got scim running but Hoary doesn't seem to do korean properly, some 3 charicter letters can't be typed.

Have nabi working on a FC4 machine with gnome & it works a treat (apart from being a redhat machine). The only reason it's not an ubuntu machine is I haven't worked out Nabi on Breezy

Have had a few shots at getting nabi runing but i just end up with the input box & no thing to select for korean inut. My challenge is want to be able to do this not only in gnome but also xfce4 (xubuntu) & KDE

This is what i have installed.
imhangul (0.9.11-1)
language-pack-gnome-ko (20051011)
language-pack-gnome-ko-base (20051011)
language-pack-ko (20051011)
language-pack-ko-base (20051011)
language-support-ko (20051010)
libnspr4 (2:1.7.12-1ubuntu1)
mozilla-browser (2:1.7.12-1ubuntu1)
mozilla-firefox-locale-ko (1.0-1ubuntu1)
mozilla-locale-ko (1.7-1)
nabi (0.15-1)
openoffice.org2-help-ko (1.9.129-0.1ubuntu5)
openoffice.org2-l10n-ko (1.9.129-0.1ubuntu3)
ttf-alee (4.7ubuntu1)
ttf-unfonts (1.0.1-2ubuntu1)
xfonts-baekmuk (2.2-1ubuntu1)


Then I have  

#sudo dpkg-reconfigure locales

decided i didn't really need 50 differnet kinds of english but i did need Korean, so  i selected the following; 

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

the quick way to achivev the same this is sudo nano /etc/locale.gen  edit it to look like this & save it

en_US.UTF-8 UTF-8
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR

then run 

 sudo locale-gen

But when i run nabi for the term i see;

Nabi: Can't load config file
Nabi: xim server started

It starts but there are no fonts

If you can help me find what i am doing wrong I would appreciate it

---

### Post by yangsanggunja on 2005-11-15
Marc,

I also live and work in Seoul, so Korean is very important to me, too.  Your post makes it clear that you know TONS more than I do, so I doubt I will be of any help.

Many Korean sites do appear to be tailored to MS Explorer.  If there is anything fancy on a site at all, it won't work in Firefox (same is true of Windows Firefox).

I have gotten SCIM up and running many under Hoary several times on different machines.  I just use the unofficial add-on CD and the Korean instructions on this page:

[www.mrbass.org/linux/ubuntu/scim/](www.mrbass.org/linux/ubuntu/scim/) 

I set it for 2-bul input (the standard Korean keyboard layout) and it works beautifully.  I have used it quite a bit for a lot of typing.  I've never seen a character that didn't come out right.

But recently I upgraded to Breezy and SCIM won't even start on any of my machines.  I am still hoping to get something going, but I don't have much time to tinker with it.  I was hoping to get Nabi (or any kind of input method) going today, but it doesn't look good :(

---

### Post by Marc Higgins on 2005-11-27
hi yangsanggunja,

Seeing you live & work in Seoul too, we should get some soju, our laptops & sort some of this stuff out together!

Anyway not saying that this is perfect but this is how i got Korean input working with nabi on brezzy

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

&#51088;&#49464;&#54620; &#44163;&#51008; [https://wiki.ubuntu.com/KoreanSetupHowto?highlight=%28korean%29/](https://wiki.ubuntu.com/KoreanSetupHowto?highlight=%28korean%29/) &#47484; &#52280;&#44256;&#54664;&#45796;.


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

### Post by Chen_Zhen on 2005-11-27
Hi, I basically have the same problem as yangsanggunja. I added scim -d in the session menu as a startup program but still doesn't work. The little keyboard icon appears but it won't allow me to write in most programs (such as openoffice, firefox and others). Any ideas how to solve the situation?

---

