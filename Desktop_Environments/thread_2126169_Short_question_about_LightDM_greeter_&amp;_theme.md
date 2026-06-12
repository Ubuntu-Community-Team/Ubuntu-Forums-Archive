---
title: "Short question about LightDM greeter &amp; theme"
date: 2013-03-16
forum: Desktop Environments
---

### Post by kennethwrede on 2013-03-16
Hi, I have for some time played with a customized installation from Precise server iso. When I was trying to understand how lightdm should be activated (I hade overseen some X11 packages) I also started to wonder about how to manipulate it. That confronted me with another question.

If I look in synaptic, there is both lightdm-themes and lightdm-greeters, but as far as I can se not from the same desktop. Are they different names for the same thing, or is there any difference? Google could not answer, or maybe, I could not ask it god enaugh. :)

Kenneth

---

### Post by kennethwrede on 2013-03-22
No one have en answer? Well, than I don't need to feel stupid by asking. ;)

Kenneth

---

### Post by Krytarik on 2013-03-22
The LightDM greeter and its theme are basically analogous to a desktop environment/session and its theme.

Simple enough? :P

Regards.

---

### Post by diesch on 2013-03-22
The LightDM greeters are responsible for drawing the login screen and asking for a user name and password while LightDM itself is doing the authentication, starting the session, ...

*mythbuntu-lightdm-theme* and *ubuntustudio-lightdm-theme* are themes for *lightdm-gtk-greeter*

If you want to create your own login screen have a look at *lightdm-webkit-greeter*. It's a greeter that uses WebKit to render a HTML file with some JavaScript as login screen.

---

### Post by kennethwrede on 2013-03-23
"The LightDM greeters are responsible for drawing the login screen and asking for a user name and password"

So the greeter is DRAWING and ASKING, but WHAT it is drawing is decided by the theme?
(Eg. The greeter is drawing the windows/popups/menus/background... But what they contain is mentioned in the theme that usually have the same look&feel as the DE?)

Kennth

---

