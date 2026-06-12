---
title: "kubuntu &amp; kde apps"
date: 2005-09-01
forum: Desktop Environments
---

### Post by duffman25 on 2005-09-01
Hi

I have a friend which likes kde, so I thought he could try kubuntu. He's been using mandriva, but he doesn't like it too much. He has used debian & he want's to continue that path. Reading reviews about kubuntu he thought he could give it a try.

His main problem is that he likes to have a consistent desktop & doesn't like having qt/gtk apps mixed, so I'm asking for kubuntu users experience. He doesn't like gtk/gnome. He asked me about kubuntu the other day, and since I'm currently using ubuntu I couldn't answer all his questions, so maybe some kubuntu user could help me. He asked me this things:

 - How does kubuntu support kde apps? He meant if there are little kde apps, or more... is there some great kde app not included (I've seen k3b, koffice & k3b in kubuntu, so I think he won't miss any mayor app)

 - AFAIK wxWidgets in linux uses gtk to draw it's widgets, so If he installed for example amule, how would it look? Also, gtk apps seem to work slower in kde than in gnome, and viceversa because when using kde you have loaded kde libraries and when using gnome, it's gnome libraries... Are there alternatives to apps such as amule which uses kde libraries?

As you can see his main concern is if he could use kubuntu with kde/qt consistently, without the need for a gtk app.

My friend wouldn't mind using breezy, so if breezy has better kde support I think he would go for it. 

Thanxs for your help.

---

### Post by gnutux on 2005-09-01
Most programs now are written for GTK, and not much w/ QT. You can find them in the repository.

gnutux

---

### Post by incinerator on 2005-09-01
1.) What's wrong with gtk? Most of the Linux distros I have used have had good interaction between gtk and qt apps. I regulary use gaim and firefox on my kde desktop, and it is all very consistent.

2.) As for gtk apps being slower when started in a kde, that's a stupid false rumour. Do you really think kde/qt don't have to load any libraries when they start up? Believe the FUD, go back to windows-land. A person I don't know, iirc his name is Bill, keeps telling the press it's really fast now.

3.) Dunnow about amule, but I once had a setup running mldonkey on one of my servers and remote-controlling it with kmldonkey and web browser. Worked nice enough for me.

4.) If you want to find out how a gtk app looks on kubuntu, run the livecd and sudo apt-get some gtk apps. With enough RAM and swap that should work no probs.

5.) You could simply check out screenshots. Doesn't madpenguin have screenshot tours of kubuntu?

6.) You will certainly be able to run kde without ever running a single gtk app.

7.) Kubuntu certainly has k3b, koffice. I am not sure if it has & k3b, though ;-)

---

### Post by incinerator on 2005-09-01
[QUOTE=gnutux]Most programs now are written for GTK, and not much w/ QT. You can find them in the repository.

gnutux[/QUOTE]

Eh? kubuntu-cd? no qt/kde apps on it?

---

### Post by gnutux on 2005-09-01
I meant after the installation, using the repos.

As for GTK loading slowly, that is true actually, it's because KDE loads the QT libraries permanently until next reboot, while when you load a GTK app, it loads temp. and the libraries are removed after the program has been terminated.

gnutux

---

### Post by duffman25 on 2005-09-01
[QUOTE=incinerator]1.) What's wrong with gtk? Most of the Linux distros I have used have had good interaction between gtk and qt apps. I regulary use gaim and firefox on my kde desktop, and it is all very consistent.

2.) As for gtk apps being slower when started in a kde, that's a stupid false rumour. Do you really think kde/qt don't have to load any libraries when they start up? Believe the FUD, go back to windows-land. A person I don't know, iirc his name is Bill, keeps telling the press it's really fast now.

3.) Dunnow about amule, but I once had a setup running mldonkey on one of my servers and remote-controlling it with kmldonkey and web browser. Worked nice enough for me.

4.) If you want to find out how a gtk app looks on kubuntu, run the livecd and sudo apt-get some gtk apps. With enough RAM and swap that should work no probs.

5.) You could simply check out screenshots. Doesn't madpenguin have screenshot tours of kubuntu?

6.) You will certainly be able to run kde without ever running a single gtk app.

7.) Kubuntu certainly has k3b, koffice. I am not sure if it has & k3b, though ;-)[/QUOTE]


Thanxs for your answers. But, since I use ubuntu and all aps I've ever needed are gtk apps, I don't know about this things, so that the reason for my post. I didn't want to star a flamewar about gtk/qt.

The lastest kubuntu's live cd's doesn't work correctly (nor the daily breezy one, nor the kde 5.4.2 one, and yes, I've asked for help about that, but it seems that there's no fix for that right now. Also, I could install kde myself, but I don't want to mess my box.

For the screenshots, I've seen osdir ones, but they are only showing a bare kubuntu install, so there's not much to look at. :(
(I've just search madpenguin but didn't find shots of kubuntu...)

Thanxs

---

### Post by shakin on 2005-09-01
Kubuntu is excellent... far better than Mandriva. I'm sure your friend will love it.

I manage to get by with very few GTK apps. When I use Gnome I use a few QT apps like K3B, so it balances out.

You can install gtk2-engines-gtk-qt, which makes GTK apps call the QT libraries to do the actual drawing. It still loads GTK, but unifies the look of the windows and widgets somewhat. IMO, the overhead in loading the GTK apps is negligible. I still use Firefox and it loads very quickly. Synaptic is the other GTK app I can't live without because Kynaptic isn't quite as good yet.

---

### Post by incinerator on 2005-09-01
no sweat, bro. I don't see the need to start a qt/gtk flamewar, either ;-)

Yeah, unfortunately the ubuntu livecds seem to be a wee bit selective regarding what computers they like to run on. There's many boot options you can play around with, but I just tried that on a friend's laptop last week and it did not help. You could try another livecd, like knoppix, but of course there might be differences in gfx output. I guess new knoppix versions, the new 4.0.1 dvd in particular, have lots of gtk software installed.

gnutux: Yeah, sure, but if you use the kubuntu-cd lots of kde/qt packages get installed already. That's not just a few like you were saying.

---

### Post by Lord Illidan on 2005-09-01
IMHO, there is no real difference. I use GAIM and Synaptic on Kubuntu, and I use K3B on Gnome, so there shouldn't be any real difference...

---

### Post by incinerator on 2005-09-01
[QUOTE=shakin]Synaptic is the other GTK app I can't live without because Kynaptic isn't quite as good yet.[/QUOTE]

Bah, apt-cache, apt-get, dpkg, dselect and aptitude are the tools of the truly enlightened. The [noodly master](http://en.wikipedia.org/wiki/Flying_Spaghetti_Monster)  would never approve of GUI tools for package management.

Ramen!

---

### Post by DarkT on 2005-09-01
On something related, when running a gtk app with kdesu or gksudo under kde I find that the gtk apps resort back to a very ugly skin (default I suppose) & I'm using the gtk style that draws gtk widgets ala qt. Is there any way to fix this?

Also, I'm surprised that gnutux is getting away with this trolling, there seems to be a fair bit of it against kde users on these ubuntu forums :(

---

### Post by siebzehn on 2005-09-01
[QUOTE=incinerator]Bah, apt-cache, apt-get, dpkg, dselect and aptitude are the tools of the truly enlightened. The [noodly master](http://en.wikipedia.org/wiki/Flying_Spaghetti_Monster)  would never approve of GUI tools for package management.

Ramen![/QUOTE]
 Couldn't agree more!

---

### Post by Pitou on 2005-09-01
[QUOTE=siebzehn]Couldn't agree more![/QUOTE]
 Almost all KDE apps are in the repositories.

If you absolutely need an app that has been written using gtk, you can use qt-engine and/or geramik that will transform the buttons and gui to make it looks like a KDE app.

Just do a search with kynaptic/synaptic

Pitou!

---

### Post by duffman25 on 2005-09-01
[QUOTE=DarkT]On something related, when running a gtk app with kdesu or gksudo under kde I find that the gtk apps resort back to a very ugly skin (default I suppose) & I'm using the gtk style that draws gtk widgets ala qt. Is there any way to fix this?

Also, I'm surprised that gnutux is getting away with this trolling, there seems to be a fair bit of it against kde users on these ubuntu forums :([/QUOTE]

This happens in gnome when you have a theme installed localy (in your home). If you have set a theme which is installed globaly (/usr/share/themes/ ) everything looks good. I don't know if this happens in kde, but I think it would be for the same reason. I think it has to be with the fact of enviroment settings when running sudo & it's gui variants.

---

### Post by DarkT on 2005-09-01
The theme is installed globally so unfortunatly that's the not the problem, however after a bit of messing about I've found a way of getting it to work correctly so I'll post some newbie friendly instructions... 
 
Basically you get to a main console (so ctrl+alt+f1 or similar) and log on as root, which means you need to have set a strong root password before hand with *sudo passwd root* and you then kill the x server with either */etc/init.d/kdm stop* or replace kdm with gdm if you're using that as the login manager.
Now you'll have to run *startx* and this will run the xserver as root - and yes I know, many consider this a stupid thing to do but I know no other way of doing this correctly, sudoing kcontrol just doesn't work - so don't do anything stupid ;) 

*alt+f2* to bring up run and type *kcontrol* and click run, then select your theme prefs under **gtk styles and fonts**, if this is not there seach synaptic for *gtk qt* and install the gtk-qt engine. Also while in kcontrol you can change other look settings for root to make kde apps that you run as sudo also fit in with the general feel of your desktop.
Now log out which will drop you back to the console and enter the command (replacing kdm with gdm if needed) */etc/init.d/kdm start;exit*.
 
And that *should* sort it out, just don't hurt me for logging in to x with the root account :P

---

### Post by Josef K. on 2005-10-07
[QUOTE=incinerator]Bah, apt-cache, apt-get, dpkg, dselect and aptitude are the tools of the truly enlightened.[/QUOTE]

BTW
can anybody explain me why sometimes I found **more** packages in (k)synaptic than in aptitude?!:confused: 

just an example: in aptitude I can see kmldonkey but not mldonkey, but from kynaptic I can see both?! :confused:

---

### Post by Segovia on 2005-10-10
[QUOTE=shakin]You can install gtk2-engines-gtk-qt, which makes GTK apps call the QT libraries to do the actual drawing. It still loads GTK, but unifies the look of the windows and widgets somewhat.[/QUOTE]
...and it is installed with Breezy by default now. :)

---

