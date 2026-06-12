---
title: "compiz removes titlebars"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by thebrandon on 2007-10-31
I have searched and searched the forum and found that a lot of people have had this problem but none of their fixes seem to have worked for me.  Whenever I enable any level of visual effects under the appearance preferences > visual effects tab when the settings take effect the titlebar disappears and all windows are locked in place.  All the effects are operational however.  So far here is what I have tried, in no particular order :

Uninstalling / Reinstalling Compiz & Emerald via  sudo apt-get remove compiz* libcompiz* emerald libemerald*  then  sudo aptitude install compizconfig-settings-manager and the same for compiz and emeral (I didnt know the code for how to do them all at once)

emerald --replace
metacity --replace
compiz --replace

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

nohup metacity --replace &

and I have added these lines to my xorg.conf :
Section "Screen"
	Option "AllowGLXWithComposite" "True"
	Option "RenderAccel" "True"
	Option "AddARGBGLXVisuals" "True"
	Option "AddARGBGLXRootClipping" "True"

I have attached (hopefully correctly) my xorg.conf.  Thanks for any and all help!

---

### Post by Jose Catre-Vandis on 2007-10-31
Go into compiz settings, select windows decoration, enter "emerald" in the "command" box, and save out. This should give you back your window borders

---

### Post by thebrandon on 2007-10-31
Thanks, that worked perfectly!  Do you perhaps know how to get rid of the black box that fills the top portion of say Firefox when ever I bring it up from the tray?

---

### Post by Jose Catre-Vandis on 2007-10-31
I don't get that on my machine, sorry

---

### Post by thebrandon on 2007-11-01
Well now it has gone away!  Thanks again for all your help!

---

