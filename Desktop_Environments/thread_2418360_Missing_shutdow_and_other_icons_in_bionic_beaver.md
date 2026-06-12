---
title: "Missing shutdow and other icons in bionic beaver"
date: 2019-05-06
forum: Desktop Environments
---

### Post by knight69 on 2019-05-06
I am missing the shutdown/logout, clock, network and volume control  icons in the top panel of the gnome flashback desktop in Ubuntu 18.04.  These icons were present until a few hours ago. I have no idea what  happened to make them disappear. 

All these icons are present at  the login screen and they are present in the gnome 3 desktop  but as soon as I log into the flashback desktop shell, they disappear.   I have tried right clicking the panel, but there is no response when I  do that.  I have searched the gnome tweaks tool for any clues but found  none.

Any help in restoring these icons will be greatly appreciated as I now have to use commands to log out or shut down which is a real nuisance.

---

### Post by CatKiller on 2019-05-06
> **knight69 said:**
>  I have tried right clicking the panel, but there is no response when I  do that.

You need to press some combination of modifier keys before right-click brings up the gnome panel menu. I can't remember which combination it is, since I don't use Gnome any more.

---

### Post by Rubi1200 on 2019-05-06
ALT+right-click the panel might work, try please and let us know.

---

### Post by Claus7 on 2019-05-06
Hello,

> **Rubi1200 said:**
> ALT+right-click the panel might work, try please and let us know.

...and choose the option Add to Panel... and from there choose indicator applet complete. It should restore the icons in question unless something else happened.

Also verify that from synaptic package manager the: indicator-applet-complete is there with its dependencies installed and not removed by any mistake.

Regards!

---

### Post by knight69 on 2019-05-06
alt-right click on the panel worked to bring up the "Add to Panel" menu and indicator applet complete brought up all the necessary icons except the shutdown button icon.  There are separate logout and shutdown icons but the shutdown icon doesn't provide the logout and restart options that come with the default shutdown icon that was present before and is present in the other desktops. The missing restart control is still a problem for me.

The only dependency identified by the command *apt rdepends indicator-applet-complete* was gnome-panel which is present.

---

### Post by Claus7 on 2019-05-07
Hello,

> **knight69 said:**
> alt-right click on the panel worked to bring up the "Add to Panel" menu and indicator applet complete brought up all the necessary icons 
so far so good

> **knight69 said:**
> 
except the shutdown button icon.  
You could check dconf editor and the option /apps/indicator-session/suppress-shutdown-menuitem
which should use the default value, which means that should not be enabled, in order for you to have it available.

> **knight69 said:**
> 
There are separate logout and shutdown icons but the shutdown icon doesn't provide the logout and restart options that come with the default shutdown icon that was present before and is present in the other desktops. The missing restart control is still a problem for me.
...

under the indicator-session from dconf editor there are many options you could check in order to re-enable the options you mention. If I recall correctly, just one button both to logout and shutdown is not available anymore. Yet, from indicator applet complete, clicking on the session part of it, you will be able to find these options as long as they are enabled from dconf editor as mentioned before.

If you have installed plank by the way, have in mind that it conflicts with the menu under question, at least in some versions that I had checked. It is advised to remove if, or to enable the suppress-logout-restart-shutdown menu, which will dismiss the confirmation dialog, yet it will have all options available.

Regards!

---

