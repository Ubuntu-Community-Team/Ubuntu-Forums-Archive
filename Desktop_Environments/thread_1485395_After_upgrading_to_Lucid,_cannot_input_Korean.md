---
title: "After upgrading to Lucid, cannot input Korean"
date: 2010-05-16
forum: Desktop Environments
---

### Post by ycp1 on 2010-05-16
I upgraded from 9.10 to 10.04. I installed Korean in System > Administration > Language Support > Language. But I couldn't input Korean. Hangul key or Shift + space key do not switch to Korean input mode.
I changed "Display numbers, dates and currency...." to Korean under System > Administration > Language Support > Text. After restart, Hangul key works and I could input Korean. However, the environment variable LANG changed to ko_KR.utf8. So, some application work in Korean environment. Compiz setting manager has many Korean words. Emacs tutorial comes in Korean. Firefox menus became in Korean. So, this cannot be my solution.

Anyone can help me?

---

### Post by Zorael on 2010-05-17
Could you paste the output of the following entered in a terminal?
```
echo -e "\nGTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n"; im-switch -l
```

---

### Post by ycp1 on 2010-05-17
"Display numbers, dates and currency...." is set to Korean under System > Administration > Language Support > Text. And login again.


GTK:	ibus
Qt:	ibus
XMOD:	@im=ibus

Your input method setup under ko_KR locale as below.
=======================================================
The configuration "/home/young/.xinput.d/ko_KR" is defined as a link pointing to
none
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-ko_KR" .
xinput-ko_KR - auto mode
 link currently points to ibus
ibus - priority 60
nabi - priority 50
scim - priority 50
scim-bridge - priority 60
scim-immodule - priority 0
Current `best' version is ibus.
=======================================================
The available input method configuration files are:
default default-xim ibus lo-gtk nabi none scim scim-bridge scim-immodule th-gtk th-xim 
=======================================================





"Display numbers, dates and currency...." is set to United States under System > Administration > Language Support > Text. And login again.


GTK:	ibus
Qt:	ibus
XMOD:	@im=ibus

Your input method setup under en_US locale as below.
=======================================================
The configuration "/home/young/.xinput.d/en_US" is defined as a link pointing to
none
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim ibus lo-gtk nabi none scim scim-bridge scim-immodule th-gtk th-xim 
=======================================================


Thank you.

---

### Post by Zorael on 2010-05-18
I think this is due to [bug #522814](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/522814), which I reported back during lucid development. It's still not fixed, I see. I'm still unsure why your environment variables point to ibus even though you have set it to **none**. Hm.

Try entering this in a terminal and then log out and back in with an en_US locale.
```
$ im-switch -s ibus
```
If it doesn't work, we'll have to go and modify some files.

---

### Post by ycp1 on 2010-05-18
```
$ im-switch -s ibus
```

After I login again. it still didn't work.

I found a file ~/.gnomerc. I deleted all lines that I wrote to use Korean input system, Nabi. I restart system. and it works now.

Thank you so much

PS> this is my old .gnomerc
```
export XMODIFIERS="@im=nabi"
export XIM_PROGRAM=/usr/bin/nabi
export GTK_IM_MODULE=xim
export QT_IM_MODULE=xim
#export LANG=ko_KR.EUC-KR
nabi &

```

---

