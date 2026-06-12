---
title: "scim in beryl"
date: 2006-10-29
forum: Desktop Environments
---

### Post by depp on 2006-10-29
anyone is using scim under beryl. I got bad rendered scim-panel. anyone else?

---

### Post by precinto on 2006-11-15
Hi. I'm trying to set SCIM up with Beryl. It works just fine under Gnome (I followed the HOWTO: Enable Chinese Input), but  when I start it under Xgl they icon just sits on the system tray, but I when I click it it doesn't drop down the input methods menu and the toolbar doesn't even appear.

Did you do anything special to get it to work?

Thanks.

---

### Post by zhang2006chn on 2006-11-15
> **depp said:**
> anyone is using scim under beryl. I got bad rendered scim-panel. anyone else?

What you're showing is definitely NOT the MOST FRUSTRATING part of it with beryl. A really annoying thing about SCIM(Smart Pinyin) is that when you input the first syllable as the only one, you will find what is wrong.

See the screenshot here:
[http://zhcn.blogspot.com/2006/10/ubuntuberylscim.html](http://zhcn.blogspot.com/2006/10/ubuntuberylscim.html)

---

### Post by Jiawen on 2007-05-14
I'm having the same problem, or a related one. When I try to input something while in Firefox using SCIM and Beryl, SCIM only allows me to input the first few letters (it's a random amount) before dropping me back into English. The SCIM menu becomes non-responsive and I have to ctrl+space then ctrl+space again to get back. Gedit, however, works fine. 

Before, when I used Mandriva/Mandrake, I had to append this to the beginning of every Firefox startup script:```
scim -f x11 -c simple -ns socket -d
export LC_CTYPE=en_US.UTF-8
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=xim
```
That allowed Firefox to start (otherwise it would just sit there), but it dumped core every time I did it. That was one of the reasons that I moved to Ubuntu. I hope that Beryl doesn't bring me back to the days of Mandriva.

---

### Post by Jiawen on 2007-05-14
Aha, tried a part of that and it seems to work.

First, quit out of Beryl. (Change from Beryl as window manager and window decorator to Gnome/Metacity/GTK/whatever).
Then, enter in a terminal:
```
export GTK_IM_MODULE=scim
```Then start Firefox normally, then restart Beryl. (Switch back to Beryl as window manager and window decorator.)

It made Firefox forget all my tabs -- not even a "Would you like to restore your earlier session?" message -- but now SCIM works fine in Firefox. &#20320;&#30475;&#65292;&#29694;&#22312;&#33021;&#36664;&#20837;&#20013;&#25991;&#20102;&#65281; I just hope it's not putting a core dump somewhere on my system. I tried running it from a terminal and I don't *see* any sign of a core dump, so let's hope it's working.

---

### Post by Jhongy on 2007-05-14
I wonder if I can add this to .gnomerc or my .profile to solve this annoying problem of SCIM dropping back to English at random intervals in FireFox....? That would be a MJOR headache solved.


Then, the only problem left will be figuring out why SCIM doesn't work under FreeNX!

---

### Post by Jiawen on 2007-05-15
Well, when I used Mandrake/Mandriva, I added that four-line thing to my Firefox scripts. It might work to just add the one-line version (export GTK_IM_MODULE=scim). 

Maybe .bashrc is the place to add it? I don't know that stuff well enough to say.

---

