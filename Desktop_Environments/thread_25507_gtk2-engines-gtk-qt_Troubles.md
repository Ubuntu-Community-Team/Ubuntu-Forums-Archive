---
title: "gtk2-engines-gtk-qt Troubles"
date: 2005-04-10
forum: Desktop Environments
---

### Post by !nkubus on 2005-04-10
I have installed this package
```

gtk2-engines-gtk-qt - Makes your GTK 2 apps look like Qt ones

```

 from Universe and when i go under the kde control center and change the style to QT or tu use my KDE settings, all my GTK applications are plain ugly all the widgets are screwed up and the color of the widgets are like windows 98  :-? 

[IMG]http://img171.exs.cx/img171/807/snapshot13zw.png[/IMG]


i'm shure that this is a kde 3.4 problem because i heard that the theme engine have changel a lot.


Thanks for your help :)

-----------

SORRY for taking your time my fault Synapic run as root ;) so i have no theme set as root ;

anyway thanks for your help

lol

---

### Post by ubuntu-geek on 2005-04-10
Probably related to to the engine and kde3.4. I haven't used KDE in about a year but ran into some of the same issues with that engine. What I ended up doing was installing gnome along side KDE, set my settings in Gnome and then made a sym link in my ~/.kde/AutoStart folder to the "gnome-settings-daemon" program so it would load my Gnome settings on load up of KDE.

Hope that help some.

---

### Post by bushsux on 2005-04-10
Your screen shot is of synaptic which I assume is running as root. You might try copying your .gtkrc-2.0 file to /root . Anyways, gtk2-engines-gtk-qt is working for me under 3.4.

---

### Post by Jonathan2007 on 2005-04-10
It is also working just fine for me under Kubuntu 5.04 final.

---

### Post by André on 2005-04-10
Hi,

i am having a same problem.

For me the gtk-qt engine works in Tagedit for example. But it doesn't work with synatpic.

I already have copied the gtkrc file over to root but no go. Any other ideas??

I also tried gtk-theme-switch. There i can see that the theme is set for gtk-theme-switch2 but not for gtk-theme-switch.

I think the difference is that the second one sets the theme for gtk1 apps.

Since i tried these programs i also have the problem that my fonts in my firefox menus are pretty small (that didn't happen before :-/).

Any suggestions on how to use gtk-qt with synaptic and firefox?? Like i already said: it works fine with TagEdit :-/

Greetings and thanks for any help
André

//edit:
P.S.: After setting the fonts again for two times it works... But don't ask me why ;-)

Still having the synaptic problem...

---

### Post by bushsux on 2005-04-10
[QUOTE=André]Hi,
Still having the synaptic problem...[/QUOTE]

Try copying the .gtk_qt_engine_rc file over to /root also.

---

### Post by Jonathan2007 on 2005-04-10
[QUOTE=André]Hi,

i am having a same problem.

For me the gtk-qt engine works in Tagedit for example. But it doesn't work with synatpic.

I already have copied the gtkrc file over to root but no go. Any other ideas??

I also tried gtk-theme-switch. There i can see that the theme is set for gtk-theme-switch2 but not for gtk-theme-switch.

I think the difference is that the second one sets the theme for gtk1 apps.

Since i tried these programs i also have the problem that my fonts in my firefox menus are pretty small (that didn't happen before :-/).

Any suggestions on how to use gtk-qt with synaptic and firefox?? Like i already said: it works fine with TagEdit :-/

Greetings and thanks for any help
André

//edit:
P.S.: After setting the fonts again for two times it works... But don't ask me why ;-)

Still having the synaptic problem...[/QUOTE]
Hmm now that you mention it I have noticed the font size in Firefox. It was really small. I though it was due to Neowin or something because they had a notice about increasing their font size and such and I thought maybe it was just that site but xbox-scene.com's font was very small also. I went into Edit and preferences on Firefox and then fonts and colors and I upped the font size to 16. Now I can see the font but it screws up the design badly on Xbox-Scene and it looks weird on Neowin. I didn't really notice the font size before I installed gtk2-engines-gtk-qt so it must have been ok. Can anyone help? Thanks.

---

### Post by André on 2005-04-11
Helllo,

@bushsux: Tried it, but still no-go :-(

@Jonathan2007: Try to tinker around with the settings in Control Centrum -> Appearance -> Gtk Styles and fonts.

That worked for me after a while.

Greetings
André

---

### Post by lao_V on 2005-04-11
Ok, try this:

Install the gtk2-clearlooks theme from synaptic and then goto gtk2 themes in kcontrol and chose the clearlooks theme instead of QT or default and your gtk apps will look fab!

---

### Post by André on 2005-04-11
Hi there,

the apps do not feel like absolute kde apps anymore... but it's even hard for me to notice the difference ;-)

Thank you very much!! Finally i can use the better synaptic over kynaptic without ruining my eyes :-)

Greetings
André

---

### Post by !nkubus on 2005-04-11
[QUOTE=bushsux]Your screen shot is of synaptic which I assume is running as root. You might try copying your .gtkrc-2.0 file to /root . Anyways, gtk2-engines-gtk-qt is working for me under 3.4.[/QUOTE]

that's exactly what i did and it worked like a charm :)

---

### Post by André on 2005-04-11
Now you see me jealous ;-)

But i can live with the clearlook style. As i said before: My untrained eye doesn't notice a difference :-)

Greetings and a big "good job" for the Kubuntu devs
André

---

### Post by !nkubus on 2005-04-11
Well André, you can also try:

```

kdesu kcontrol 

```


and change the look under  **Aperence & Settings -> gtk styles and fonts**    there if you have the package install and it will take care of doing all that stuff for you :)

hope this helps :)

---

### Post by André on 2005-04-11
Already tried that one... No go :-(

---

### Post by vanaedium on 2005-04-11
hi I have the same problem but I think the real problem is that dcopserver doesn't work properly.
Infacts kcontrol in root doesn't work
It needs to cancel the 2 dcop flise under /home and /root and restart dcopserver from root and normal-user
The problem is a conflict between sudo and kdesu I think I
 received an error with kcontrol:
Error: "/var/tmp/kdecache-myaccount" is owned by uid 1000 instead of uid 0.
I have installed gtk-theme-switch by synaptic and thrue consolle type switch2 to set the gtk 1.0 and 2.0 themes.
To see synaptic with baghira style it will take a lot of time I think!!! :roll:

---

### Post by dhanish on 2005-05-08
Seems like root and kubuntu just don't go together well.

I solved this by keeping defaults but instead of executing "synaptic".  I modified the KMenu entry for synaptic to "sudo synaptic" which works just as expected (and no need for clearlooks though I wish there is a qt version of it.)

---

### Post by Samout on 2005-09-13
I had the exactly same problem. What i did was that i ran kdesu kcontrol, then Appearance & Themes -> Colors and selected the colors/color scheme i wanted. It worked perfectly. And now whenever i change colors, i do the same as root in kcontrol, and then my root apps look the same.

---

### Post by wally83 on 2007-01-22
> **lao_V said:**
> Ok, try this:

Install the gtk2-clearlooks theme from synaptic and then goto gtk2 themes in kcontrol and chose the clearlooks theme instead of QT or default and your gtk apps will look fab!

Thx very much. My every single gtk-app really _sucked_ (buttons and toolbars were like blocks) in Fluxbox&KDE, now they look great. Now I can switch back to Firefox.

That was so obvious solution so I didn't even try this before.

---

