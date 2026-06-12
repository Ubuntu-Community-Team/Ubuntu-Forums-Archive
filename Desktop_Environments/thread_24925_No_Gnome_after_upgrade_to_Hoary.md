---
title: "No Gnome after upgrade to Hoary"
date: 2005-04-08
forum: Desktop Environments
---

### Post by nicolas on 2005-04-08
System: Acer Travelmate 4100 wLMI laptop
Screen: ATI 9700
Upgrade from Warty to Hoary

I have used Warty on my laptop for months without trouble. Now I wanted to upgrade to Hoary.

After my upgrade to hoary I have a big problem getting the Gnome desktop to start. When I start my laptop I get the Gnome screen to login. After logging in I get the brown screen with my cursor. That' s it. The screen just sits there.

I tried to do a xserver-xorg reconfigure but that did not help either.

Anyone know what can be the issue here. I don't want to do a clean install because I have a lot of stuff on my laptop harddrive that I won't want to lose.

I did a clean install of Hoary on my desktop. No problems there. I have used that to search for solutions, but sofar no luck.

Nico

---

### Post by blueplazma on 2005-04-08
I had exactly the same problem when I was trying to upgrade from Warty.  My problem was that my firewall did not allow connections from localhost to localhost.  If you are using any kind of firewalling, try turning it off then try logging in.  If you do your own firewall with a script execute this command at a terminal before logging in: ```
sudo iptables -A INPUT --src 127.0.0.1 --dest 127.0.0.1 -j ACCEPT
``` 

This will tell the firewall to accept any connections coming from localhost going to localhost.  It fixed my problem.

---

### Post by Django on 2005-04-09
I have exactly the same problem with an IBM Thinkpad 600X after a fresh install of Hoary.

I tried the iptables command suggested by blueplazma, but it makes no difference.  ](*,)

---

### Post by nicolas on 2005-04-09
OK, I finally gave up on upgrading from Warty on my laptop. I made a full backup of all relevant data and did a fresh install from the Hoary CD. I had a fully working Ubuntu Linux instance on my laptop in about half an hour.

Now I know what I am going to do when the next release comes around.  :-x

---

### Post by moopere on 2005-04-10
[QUOTE=Django]I have exactly the same problem with an IBM Thinkpad 600X after a fresh install of Hoary.

I tried the iptables command suggested by blueplazma, but it makes no difference.  ](*,)[/QUOTE]
 Hmm, I've just hit this with a fresh Hoary install on a generic desktop (AMD K6-2-300).

What do you get coming up?

I get GDM, GDM 'ready' sound effect.  I can login, gdm goes away, brown wallpaper comes up, I get the hoary startup sound effect which plays for maybe a few seconds, then the sound effect cuts out (note - not the end of the sound effect, it just cuts off short) and nothing....I am still looking at brown wallpaper, mouse moving around but no Gnome.

Its something gnome related because I installed xfce (4.2.xx) and it starts up just fine from GDM.

Sigh.

Craig

---

### Post by Django on 2005-04-10
[QUOTE=moopere]What do you get coming up?

I get GDM, GDM 'ready' sound effect.  I can login, gdm goes away, brown wallpaper comes up, I get the hoary startup sound effect which plays for maybe a few seconds, then the sound effect cuts out (note - not the end of the sound effect, it just cuts off short) and nothing....I am still looking at brown wallpaper, mouse moving around but no Gnome.
[/QUOTE]

Exactly it. I tried replacing the NeoMagic <spits on floor> driver with the generic Vesa, but that made no change.

[QUOTE=moopere]Its something gnome related because I installed xfce (4.2.xx) and it starts up just fine from GDM.
[/QUOTE]

I tried a Failsafe Gnome session... it failed :?

---

### Post by crim on 2005-04-10
I just made a new thread about this because I missed this one. I did a fresh install also of Hoary on a dual athlon (so amd is something we have in common) and I get the brown wallpaper and nothing else. My problem is a bit more severe in that menus in GDM only work sometimes also, i.e session and language. 

 ](*,)

---

### Post by crim on 2005-04-10
The plot thickens, I've found the same behavior in kubuntu, it doesn't even get to the loaded kde greeter. So something is fubar, maybe xorg on amd?

---

