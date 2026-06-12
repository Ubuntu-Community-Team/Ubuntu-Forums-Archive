---
title: "How to repair Unity 2D?"
date: 2013-03-08
forum: Desktop Environments
---

### Post by amanchesterman on 2013-03-08
I know there are many threads about installing Unity and repairing Unity installations and I have looked at several of them, but I haven't yet found an answer that clearly meets my situation so I'm hoping someone here can provide one.

I have an elderly Toshiba laptop on which I have (single boot) Ubuntu 12.04 LTS. When I first installed it I found that the computer's graphics capability is not up to running Unity 3D and Compiz, so I abandoned Unity and installed the Gnome desktop instead. That runs fine and I have no problems with it (I currently have Gnome 3.2).

Recently I thought I should give Unity 2D a try (in appearance it's very similar to Gnome of course). When I select 'Unity 2D' at login, I get the desktop and the top panel OK, but there is no Dash and I can only start programs from the terminal; moreover there is no top bar and no border to the windows that open with programs in them.

I worked out that that's due to Metacity not functioning as the window manager -- and sure enough, if I log in to Unity 2D and then start Metacity in the terminal, everything is fine: Dash appears and the program windows behave normally.

So the problem seems to be that when I login to Unity 2D, Metacity isn't starting as it should. Can someone tell me how to cure it? (Incidentally I want to retain Gnome as a working desktop environment: it would just be nice to have Unity 2D as an alternative.)

Thanks in advance
John

---

### Post by black veils on 2013-03-08
maybe as a workaround you could set that command as a startup application? i would think on that hardware though you would be better using a light desktop environment like lxde, you can change the window manager to xfwm4 and the notifications to xfce4-notifyd if preferred.

---

### Post by grahammechanical on 2013-03-08
I do not know if this will help but as you are on 12.04 you should have the Synaptic Package Manager installed. Open it and search for Unity 2D and metacity and mark all the libraries to be re-installed. You select a line and right click and then you get options. By reinstalling you may just reconfigure something that makes the connection between logging in to Ubuntu 2D and running metacity.

Regards.

---

### Post by amanchesterman on 2013-03-08
Hi and thanks to you both for your replies.

To Black Veils: I take the point of your suggestion, of course, but I have tried lighter desktop environments (and currently have Xubuntu running on another laptop) and I'm not greatly enamoured of them. I like the functionality of the Gnome desktop and wanted to explore if Unity 2D would do something similar.

To GrahamMechanical: Thanks for the suggestion, I have done what you said and have re-installed all the libraries -- but that hasn't solved the problem, which remains as I originally described.

Thanks for trying to help!
John

---

