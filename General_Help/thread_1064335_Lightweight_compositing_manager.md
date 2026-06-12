---
title: "Lightweight compositing manager"
date: 2009-02-08
forum: General Help
---

### Post by Trzone on 2009-02-08
I need a lightweight compositing manager to run avant-window-navigator, i have a 7 yr old computer with 8mb of video ram.  Any help would be great :)

---

### Post by demosthenese on 2009-02-08
You can run awn with xfce and on an old system xubuntu may well be a better all round choice.

---

### Post by Trzone on 2009-02-08
But what compositing manager does xfce use? Oh and with firefox 3.1 i am all set :)

---

### Post by Trzone on 2009-02-08
Here's what i get for an error message

theo@Ubuntu:~$ xfwm4

** (xfwm4:25827): WARNING **: Another Window Manager is already running

I know metacity is a window manager hmm...

---

### Post by demosthenese on 2009-02-08
You can use synaptic to install xubuntu-desktop. Then log out.

To log in with xfce select 'session' in the log in screen. Choose xfce.

After logging in, from the Applications panel button, go to Settings->Settings Manager->Desktop. Select 'Allow xfce to manage the desktop'.

---

### Post by Trzone on 2009-02-08
Thank you, however i am wondering if it is possible to use xfwm4 with gnome?

---

### Post by loell on 2009-02-08
> **Trzone said:**
> Thank you, however i am wondering if it is possible to use xfwm4 with gnome?

yes its possible, but that would loose the entire point, metacity and xfwm4 more or less uses the same resources. generally window management doesn't do heavy lifting, they just manage windows that is.


there is also the old **xcompmgr** compositor, if you like. :)

---

### Post by demosthenese on 2009-02-08
There is a how-to at:

[http://www.cafecomputer.com/page6faq.htm]("http://www.cafecomputer.com/page6faq.htm")

However, it is not something I have done, so I don't know how well it works and you will need to add in the window manager of you choice inside the case statement in the script.

Something like:

xfm)
WINDOWMANAGER=xfwm4
;;

---

### Post by Trzone on 2009-02-08
I will have to try xcompmgr

---

### Post by Trzone on 2009-02-08
Are there any settings that i may change (familiar with terminal!!!) that will maximize performance yet be able to have awn?

---

### Post by snowpine on 2009-02-09
> **Trzone said:**
> Are there any settings that i may change (familiar with terminal!!!) that will maximize performance yet be able to have awn?

If you are looking to "maximize performance," don't use compositing--it's just "eye candy" that slows down your system, in my opinion. I have hotkeys set up for my most commonly used applications, so I can access everything instantly without using extra computer resources. Just my opinion. :)

---

### Post by Trzone on 2009-02-09
Here's the output I am talking about.  
theo@Ubuntu:~$ xcompmgr --help
xcompmgr: invalid option -- -
xcompmgr v1.1.3
usage: xcompmgr [options]
Options
   -d display
      Specifies which display should be managed.
   -r radius
      Specifies the blur radius for client-side shadows. (default 12)
   -o opacity
      Specifies the translucency for client-side shadows. (default .75)
   -l left-offset
      Specifies the left offset for client-side shadows. (default -15)
   -t top-offset
      Specifies the top offset for clinet-side shadows. (default -15)
   -I fade-in-step
      Specifies the opacity change between steps while fading in. (default 0.028)
   -O fade-out-step
      Specifies the opacity change between steps while fading out. (default 0.03)
   -D fade-delta-time
      Specifies the time between steps in a fade in milliseconds. (default 10)
   -a
      Use automatic server-side compositing. Faster, but no special effects.
   -c
      Draw client-side shadows with fuzzy edges.
   -C
      Avoid drawing shadows on dock/panel windows.
   -f
      Fade windows in/out when opening/closing.
   -F
      Fade windows during opacity changes.
   -n
      Normal client-side compositing with transparency support
   -s
      Draw server-side shadows with sharp edges.
   -S
      Enable synchronous operation (for debugging).


For each program there are a variety of options
now i have -C right now, however i am unsure of any other options that may impact performance hehe.

---

### Post by dje on 2009-02-09
You can use metacity as a compositing manager. Open gconf-editor:
```
gconf-editor
```
then navigate to apps >> metacity >> general and tick compositing_manager

hope that helps,
dje

---

### Post by cb951303 on 2009-02-09
> **dje said:**
> you can use metacity as a compositing manager. Open gconf-editor:
```
gconf-editor
```
then navigate to apps >> metacity >> general and tick compositing_manager

hope that helps,
dje

+1

---

### Post by loell on 2009-02-09
> **Trzone said:**
> 

For each program there are a variety of options
now i have -C right now, however i am unsure of any other options that may impact performance hehe.

you might wanna try following this,  [http://crunchbang.org/archives/2008/03/02/openbox-xcompmgr-transset-and-conky/]("http://crunchbang.org/archives/2008/03/02/openbox-xcompmgr-transset-and-conky/")

---

### Post by Trzone on 2009-02-09
Thank you for your insight. However it seems that the xcompmgr -C uses up too many resources with avant-window-navigator to the point that i cannot play videos but i can watch youtube videos hehe...
I am guessing that there is nothing lighter than xcompmgr and that there are no others capable of running awn...
There's a tradeoff between new computer with amazing graphics and 7.5 year old computer that still works hehe.
Thanks.

---

### Post by loell on 2009-02-09
> **Trzone said:**
> 
There's a tradeoff between new computer with amazing graphics and 7.5 year old computer that still works hehe.
Thanks.

yeah, weather you choose compositing with metacity or xfwm4 or xcompmgr. they all need some graphics processing power (not much bu to some degree), though, if its just for the purpose of using AWN, why not you use a lighter icon dock, one that doesn't use compositing for transparency.

---

### Post by Trzone on 2009-02-10
Any suggestions for a dock?

---

### Post by loell on 2009-02-10
probably one of  these..

wbar,ksmoothdock, kooldock and  docky(not sure).

---

