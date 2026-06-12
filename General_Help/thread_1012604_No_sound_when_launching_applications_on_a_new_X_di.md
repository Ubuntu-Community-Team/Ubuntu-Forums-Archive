---
title: "No sound when launching applications on a new X display"
date: 2008-12-16
forum: General Help
---

### Post by SBFC on 2008-12-16
Hello everybody.

Let me preface this by saying up until very recently I was still using Gutsy and have just now upgraded to Intrepid.

I like to play my games on a separate X display so I can switch back and forth between displays if I need to. When using Gutsy this worked fine, but after upgrading to Intrepid (via format/reinstall so as to move to x64) my newly launched applications have no sound.

Just curious of anyone else has experienced this. Has something changed with the way sound works? I know pulse audio is in now but if I remember correctly this is just a replacement to esound which means I'm probably not even using it since I didn't call it explicitly. 

Any tips appreciated.

---

### Post by SBFC on 2008-12-16
Ok, I see more is going on here than I first thought. It seems I have fewer privileges on the new X display.

For example, I launched XFCE on display :1 and was unable to mount anything via sshfs. I was also unable to choose any sound devices. The panel applet for network connections said I was unable to connect to anything. And running apps such as user-admin which allow you to 'Unlock' them to make root changes had the 'Unlock' button greyed out which prevented me from unlocking them.

Does anyone know what would cause this? My user still belongs to all the same groups as my primary display. But clearly my rights have been revoked on the new display for some reason.

I have no idea what would cause this. As I mentioned in my first post I didn't run into this issue while using Gutsy.

---

### Post by SBFC on 2008-12-16
Well, I figured out what it was. Or at least I partially solved it.

When I used Gutsy I had GDM disabled and launched Fluxbox via startx. Did that here and I now have sound and what not on any additional X displays launched. 

Why GDM affects this I have no idea.

---

### Post by akraievoy on 2009-01-20
Well, I am struggling with google for a second hour (for now) just to see whether it's possible to mix sound of both X sessions.

You scenario is working fine, but mine is not, at least not out of the box for Hardy.
[INDENT][I]So, I am used to launch a session with a audio player and IM client (using an account for some general browsing), and then spawn another one for some development or document management activities.

This worked fine for openSuse and KDE, but for Ubuntu Hardy and Gnome only active X session is audible, background one is muted.[/I][/INDENT]

Please let me know your ideas regarding the scenario, or at least tell me whether you have sound from BOTH X sessions or not...

Thanks in advance,
Anton

---

