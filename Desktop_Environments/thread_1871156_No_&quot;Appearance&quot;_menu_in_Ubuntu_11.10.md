---
title: "No &quot;Appearance&quot; menu in Ubuntu 11.10"
date: 2011-10-28
forum: Desktop Environments
---

### Post by iosuna86 on 2011-10-28
I know that the appearance menu does not come with the new release and that there are some alternatives like Gnome Tweak Tools, but I truly miss the simplicity of the old System->Preferences->Appearance menu that allowed you to change anything within the selected theme. 

Now you can only choose between themes, but you cannot select "Ambiance" and change the window top bar appearance or whether you want the Maximize, Minimize and Close buttons to the left/right of a window, and many other minor tweaks.

Is there a COMPLETE app as the old Appearance? Or better, is there a way to install that old app in Ubuntu 11.10?

Thanks!

---

### Post by Frogs Hair on 2011-10-28
Right click desktop and select change background or use   system settings > appearance , it only offers the default themes and wallpaper selection . Themes and other settings handled by the Gnome Teak Tool. 

There is no replacement for the old application and being that it is a gnome 2 application would be difficult to make it work .

---

### Post by iosuna86 on 2011-10-29
> **Frogs Hair said:**
> Right click desktop and select change background or use   system settings > appearance , it only offers the default themes and wallpaper selection . Themes and other settings handled by the Gnome Teak Tool. 

There is no replacement for the old application and being that it is a gnome 2 application would be difficult to make it work .

Yeah, that's what we got under Ubuntu 11.10. And I do not understand why would they replace a great app like the old Appearance with a ****** new Appearance app. And the Gnome Tweak Tool does not do the work either. You can change between themes, you can select the pointer, and so on, but you cannot change things within a selected theme as you could with the old Appearance menu.

This is something weird. Ubuntu tends to make things better with each release. But in regards with the Appearance menu, that's just the opposite.

Thanks for the reply, though! ;)

---

### Post by mcduck on 2011-10-29
> **iosuna86 said:**
> Yeah, that's what we got under Ubuntu 11.10. And I do not understand why would they replace a great app like the old Appearance with a ****** new Appearance app. And the Gnome Tweak Tool does not do the work either. You can change between themes, you can select the pointer, and so on, but you cannot change things within a selected theme as you could with the old Appearance menu.

This is something weird. Ubuntu tends to make things better with each release. But in regards with the Appearance menu, that's just the opposite.

Thanks for the reply, though! ;)

Simple. The features you sued to have were features of Gnome 2 and GTK2, which is now out of support as Gnmome has moved to Gnome 3 and GTK3.

Ubuntu 11.10 uses Gnome 3 so you'll have to live with the features and tools built for it. So no, you can't use the old tool, even if you installed it, it would only change the appearance of any old application that's still using GTK2.

GTK3 is quite new, nobody has yet written a tool for configuring theme colors and such things with it. Not a surprise, it took about 8 years for somebody to figure out how to do that for a limited amount of themes with GTK2. I would expect it to take less than that with GTK3, but you'll definitely have to wait a bit before you get all the same features.

Currently the configuration options you get with Gnome-tweak-tool are the best you can get (apart from learning how to make and edit GTK3 themes yourself).

(And no, keeping Gnome2 and GTK2 would not have been an acceptable option for Ubuntu, it would have left us with an outdated and unsupported desktop environment, unable to run any new versions of programs. There are far more important things behind such choices than just the configuration options, even though such options might be the thing the end user most likely notices. This time making things better with GTK an Gnome required a fresh start.)

---

### Post by iosuna86 on 2011-10-29
Thanks mcduck.

I did not know GTK3 had so much work behind it and that it is so new that there is not much progress made on it.

I guess we will have to wait some time...

---

### Post by mdhollis on 2011-10-29
Are we talking about unity or gnome-shell? There are extensions for gnome-shell to change shell themes. I find CCSM the best way to customize unity.

---

### Post by iosuna86 on 2011-10-31
> **mdhollis said:**
> Are we talking about unity or gnome-shell? There are extensions for gnome-shell to change shell themes. I find CCSM the best way to customize unity.

Good point. I am currently using Unity and I was questioning about it. I use CompizConfig and it is pretty good but it still fails to do what the old Appearance menu did. 

Also, I had some issues "setting Keys" after enabling the Unity plugin in Compiz. I do not know what was that all about though.

I'll check those extensions for gnome-shell because I might change to gnome after all.

---

### Post by mcduck on 2011-10-31
> **mdhollis said:**
> Are we talking about unity or gnome-shell? There are extensions for gnome-shell to change shell themes. I find CCSM the best way to customize unity.

Window borders and both GTK and icon themes are configured using the Gnome-tweak-tool, regardless of if you use Unity or Gnome-Shell. These settings are related to Gnome 3 itself, not the shell you run on top of it.

Of course the Gnome-Shell's shell theme and Unity's settings are then configured using the specific tool the shell in question. But Gnome-teak-tool is the closest equivalent to the Appearance dialog that was available n Gnome 2.

---

