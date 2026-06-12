---
title: "installing beryl or compiz"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by dexjul on 2007-09-17
Hi,

I installed dapper drake, how can install beryl or compiz. And my laptop is dell inspiron 1300, It is compatible to installberyl or compiz.

thank you.

---

### Post by kirios on 2007-09-17
> **dexjul said:**
> Hi,

I installed dapper drake, how can install beryl or compiz. And my laptop is dell inspiron 1300, It is compatible to installberyl or compiz.

thank you. 
[COLOR="DarkRed"]Compiz and Beryl have merged and the project is now called CompizFusion.[/COLOR] 

[https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

[COLOR="DarkRed"]I don't think you can run CompizFusion on Dapper. Any particular reason you chose not to go with Feisty? 

By the way, you'll probably get lots of replies if you add the word 'Windows' to the title of this thread. 
"Windows Vista vs CompizFusion" would probably work best. :lolflag:[/COLOR]

---

### Post by dexjul on 2007-09-17
Thanks for reply. 

I tried too follow this (Beryl on Dapper Drake).

[https://help.ubuntu.com/community/CompositeManager/InstallingBeryl#head-0f4a6aa067d74f36a5fdbd08c5ed14b29bd7652d](https://help.ubuntu.com/community/CompositeManager/InstallingBeryl#head-0f4a6aa067d74f36a5fdbd08c5ed14b29bd7652d)

It says:
but unable to install. It say "E: Couldn't find package beryl"
Beryl wont install.

Any idea about this.

---

### Post by Forlong on 2007-09-17
Dapper is not supported anymore by Beryl (in fact nothing is officially supported by Beryl anymore), therefore the repository is now defunct.

Dapper is really not the best version of Ubuntu to use composite - you'll need to use Xgl in order to get the effects, which is not necessary with most graphics cards in Feisty.

If you don't have a specific reason to use Dapper, I recommend installing Feisty instead (you could upgrade your Dapper install but then you will have to upgrade to Edgy first and in the end this will take a lot of time).

---

### Post by dexjul on 2007-09-17
Thank you. Now I konw it.

Is Compiz-Fusion compatible to install on dapper and how to install it.

The reason I choose dapper is to, I want to install server side application like apache, mysql, php.

Thank you for your time.

---

### Post by Forlong on 2007-09-17
> **dexjul said:**
> Is Compiz-Fusion compatible to install on dapper and how to install it.
There are no packages available so you would have to compile it from the source code - but I wouldn't recommend it.

The only Beryl packages I know of are located in this repository: [http://3v1n0.tuxfamily.org/dists/dapper/beryl-svn/index.html](http://3v1n0.tuxfamily.org/dists/dapper/beryl-svn/index.html)

---

### Post by kirios on 2007-09-17
> **dexjul said:**
> Is Compiz-Fusion compatible to install on dapper and how to install it.

The reason I choose dapper is to, I want to install server side application like apache, mysql, php.
[COLOR="DarkRed"]No, CompizFusion will not run on Dapper. 

Feisty has AIGLX and a limited version of Compiz pre-installed. You can run server applications on Feisty and they will be more recent versions compared to those available for Dapper. 

Having tried (and failed) to get Compiz running on Edgy, I would suggest NOT trying to install CompizFusion on Feisty as it's not likely to be any easier.[/COLOR]

---

### Post by dexjul on 2007-09-17
I tried to install berly, I got this errors.

dexter@dexter-laptop:~$ beryl **************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

and this

dexter@dexter-laptop:~$ beryl-manager

(beryl-manager:7995): Gdk-WARNING **: locale not supported by Xlib

(beryl-manager:7995): Gdk-WARNING **: cannot set locale modifiers
GTK Accessibility Module initialized


Thank you

---

### Post by joshuachad on 2007-09-17
First let me say i know nothing of AIGLX and very little on dapper but try this.

sudo gedit /etc/X11/xorg.conf

paste the this section below at the end of the file and save it. then log out and back in and try starting beryl. Again I doubt it will completely solve your issue.

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by Forlong on 2007-09-18
> **dexjul said:**
> Detected xserver                                : AIGLX
So you installed AIGLX on Dapper? How did you do that?

---

### Post by dexjul on 2007-09-18
I follow the link that you gave me 

[http://3v1n0.tuxfamily.org/dists/dapper/beryl-svn/index.html](http://3v1n0.tuxfamily.org/dists/dapper/beryl-svn/index.html)

then 

sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes

then, add this on you /etc/X11/xorg.conf

Section "Extensions"
Option "Composite" "Enable"
EndSection

Almost there, now I having a prolem again starting beryl

dexter@dexter-laptop:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.2)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: symbol lookup error: beryl: undefined symbol: XCompositeGetOverlayWindow

Any Idea of this...

---

### Post by Forlong on 2007-09-18
Like I said, you need to set up [Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl).

But I'm still baffled why you have AIGLX on Dapper.
btw: who told to install those packages?

---

### Post by dexjul on 2007-09-18
> **Forlong said:**
> So you installed AIGLX on Dapper? How did you do that?

No one told me to install the package, I just I installed it and it work. 

About AIGLX

I know now about this, When I run beryl, It appaered
Detected xserver : AIGLX

I use dell laptop, inspiron 1300.

Thank you for reply, I gonna try it to setup xgl.

---

### Post by dexjul on 2007-09-18
1.I already setup xlg but, when I logon in xlg session then type beryl on termial, my system is hanging only white screen on my desktop.

2.When I logon in gnome session then type beryl on teminal, My system is hanging. I dont see the taskbar, I see only the desktop.

Any idea about this.

---

### Post by Forlong on 2007-09-18
Sorry it's just way too long ago when I used Dapper.
There could be a lot of reasons: troubles with the Beryl packages (they were built from SVN, that's never a good thing), with Xgl, with the driver ...
And I guess there are very few people around that could help you with this, because Dapper isn't really around anymore, especially with people that want desktop effects.

Once again, I can only recommend you install Feisty instead. I'm really not an expert when it comes to servers but you might want to check out if whatever you want to do, will work with feisty as well.
You are obviously not trying to use Ubuntu solely for server purpose, so give it a thought.

---

### Post by dexjul on 2007-09-18
Thank you very much,

I follow you advice.

---

