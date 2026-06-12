---
title: "korean input"
date: 2006-01-08
forum: Desktop Environments
---

### Post by konrad on 2006-01-08
How does one set up korean input (hangul) for GTK/Gnome apps?

---

### Post by FarEast on 2006-01-08
It will be worth visiting the website of SICM.
[http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu](http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu)

apt-cache shows that the package is available:) .
scim-hangul - Hangul Input Method Engine for SCIM

---

### Post by konrad on 2006-01-08
thanks!

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

### Post by GordSellar on 2006-03-24
Well, I got all the way to the end of that, found myself with the unresolved issues, and then found nabi still wasn't working. So I undid all the changes I could, which was too many, and then redid some of what I'd undone. 

I have a question: does nabi need to be active in the "main" user profile for it to work in any "other" user profile? I'm trying to make it available when my girlfriend logs in, but not when I do. I would *LIKE* to be able to log into my own account and type Korean, but without having half of Mozilla and other things in Korean, and I'm seriously thinking of trying this solution instead:

[https://wiki.ubuntu.com/JapaneseInputHowToInBreezy](https://wiki.ubuntu.com/JapaneseInputHowToInBreezy)

... as the guy says he thinks it would work with Korean too...

---

### Post by Sef on 2006-03-24
I have had the same problem.  But happy that Dapper has been delayed to improve their language capabilities for Korean, Chinese, and Japanese at least.

---

### Post by GordSellar on 2006-03-24
And even worse, now I've redone those changes, and everytime I try to login with Korean as the language -- even though it's displayed as an option in the login Languages menu -- I'm told that Korean does not exist.... the message is basically "language ko-KR_UTF-8 does not exist. using default language."

And when nabi loads in the corner of the screen I see....

&#50500;&#51060;&#44256;! &#51060;&#44060; &#47952;&#50696;&#50836;?

I guess it is working, but the change from English to Korean is via the "hangeul key", not via pressing Control-shift. (My left ALT key was just remapped to be a Hangeul key, it seems.) Now the only problem is that the system won't let me login with Korea localization. I'll try again, maybe it'll work this time. Hmmm.

---

### Post by GordSellar on 2006-03-24
Marc, 

Thanks for your wonderful instructios, they did sort out everything except that issue with localization. Reinstalling Korean fonts helped with fixing the "language does not exist" problem. However, I really can't deal with having both OpenOffice and Mozilla localized in Korean when I select English. 

Did you ever work out how to keep the localization in reserve only for when someone signs in using a language other than system default? Do you know whether that's even possible? Otherwise, I suppose I shall just create another user profile for when I need access to Hangeul, and apply the localizations and all there. Wait... would Nabi still work without my localizing hangeul at all? I think my girlfriend could deal with Mozilla in English, and OO.o in English, if the system were in Korean when she logged on. Or does the localization also equip those apps to handle Hangeul? (I don't think that's the case.)

---

### Post by GordSellar on 2006-03-25
By the way, I was able to switch Open Office over from a Korean interface to and English one by experimentation. If you can read Korean, you'd go under "Tools::Options::Language Settings::Languages::User Interface" -- it's the first select menu on that tab. You can switch the user interface back to English, no problem. But as for Mozilla Firefox, I have yet to find anything in the program that allows you to do this... as well, I have yet to find a post o the forums about this problem. I assume it's not a very common problem, as anyone who wants Korean localization probably can read the menus in Korea, to begin with. But I'll keep fiddling. If anyone else who sees this post finds a way to switch it over for one user, but *not* globally, please do post here. 

I'm beginning to have a feeling it's going to have to be some kind of manual tweaking, but I know so very little about Linux at this point I'm scared to undertake it. Maybe I should visit an IRC channel or something. Hmmmmmmmm.

---

