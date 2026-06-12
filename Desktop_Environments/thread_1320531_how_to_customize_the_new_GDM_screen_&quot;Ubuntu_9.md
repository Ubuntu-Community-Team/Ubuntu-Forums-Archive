---
title: "how to customize the new GDM screen &quot;Ubuntu 9.10&quot;"
date: 2009-11-09
forum: Desktop Environments
---

### Post by lionlix on 2009-11-09
in my blog i post 2 posts how to customize your GDM screen in ubuntu 9.10, there might be more in future :)

here are the links

hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen
[http://lionlix.wordpress.com/2009/11/07/hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen/](http://lionlix.wordpress.com/2009/11/07/hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen/)

and this 

hack-ubuntu-9-10-karmic-koala-gdm-login-screen
[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)

Hope you like it all guys :)

-lionlix

---

### Post by JayD2 on 2009-11-09
I tried to follow the steps to customize the gdm login screen but I cannot seem to open gnome control center. I get to the command line and login just fine but when I go to enter the lines I get the following responses.

```
export DISPLAY:0.0
-bash: export: 'DISPLAY:0.0' : not a valid identifier

sudo -u gdm gnome-control-center
cannot open display:
```If I switch back, alt-f7, anyway it is just the normal login screen.

Any suggestions?

---

### Post by hictio on 2009-11-10
Do you know where are the options to customize the GDM now? They used to be on the System > Administration > Login menu, but now there is actually only the option to login w/o password, and not any other option to choose a different GDM theme.
 
I really don't like the new GDM theme, it is way too dark for me taste, the flat brown from 8.10 was rather nice IMHO.

---

### Post by lionlix on 2009-11-10
> **JayD2 said:**
> I tried to follow the steps to customize the gdm login screen but I cannot seem to open gnome control center. I get to the command line and login just fine but when I go to enter the lines I get the following responses.

```
export DISPLAY:0.0
-bash: export: 'DISPLAY:0.0' : not a valid identifier

sudo -u gdm gnome-control-center
cannot open display:
```If I switch back, alt-f7, anyway it is just the normal login screen.

Any suggestions?

when you switch to the tty command line prompt and you login then write 

```

[COLOR=blue]export DISPLAY=:0.0[/COLOR]

```

what you wrote was "export DISPLAY:0.0" and you have missed "="

then write 

```

[COLOR=blue][/COLOR][COLOR=blue]sudo -u gdm gnome-control-center[/COLOR]

```

regards,
-lionlix

---

### Post by JayD2 on 2009-11-10
That was stupid of me. It is working for me now. I had tried it a couple times too...guess I kept misspelling it.

---

### Post by lswb on 2009-11-10
Thanks for the tips on changing the login screen. My question, though: Is there a reason for using the procedure of logging into a vt, exporting DISPLAY, etc, instead of just using "gksudo gnome-control-center" or "gksudo gconf-editor" from a terminal in your regular session?

---

### Post by Faolan84 on 2009-11-10
Who was the idiot that decided that overriding custom themes on an upgrade or install a depression, flat, "corporate" looking default log-in screen was a good idea. The default artwork in Ubuntu 9.10 is just ******* awful. Yes, it is that bad. I know that you can't expect much out of Canoncial in terms of good, artistic themes. But the default themes shipping with 9.10 feel less "Human" and more "corporate khaki" (not to deride khaki, it is a nice color).

They really dropped the ball on this release, and I certainly hope they do much better on 10.04 LTS. I'll give them the benefit of the doubt because all great distros have a bad release every now and then, and Ubuntu is no exception to the rule... but 9.10 was just awful.

Perhaps the development team should switch from a six month release schedule to a "when it's ready" schedule. I'd like to see a bit more effort and stability put into the releases.

---

### Post by JugglinPhil on 2009-11-12
> **hictio said:**
> Do you know where are the options to customize the GDM now? They used to be on the System > Administration > Login menu, but now there is actually only the option to login w/o password, and not any other option to choose a different GDM theme.
 
I really don't like the new GDM theme, it is way too dark for me taste, the flat brown from 8.10 was rather nice IMHO.
Yeah that's what most people think, it's not the nicest thing they've designed. But no there is no way to customize the GDM the easy way by intalling custom themes. 
There are  a few hacks that for example change the background picture, but that's nothing compared to the good old themes.
I'm afraid to say that it reminds me of Vista, I had to do just as much hacking there to customize the login screen..

---

### Post by clicker4721 on 2010-02-16
> **lionlix said:**
> in my blog i post 2 posts how to customize your GDM screen in ubuntu 9.10, there might be more in future :)

here are the links

hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen
[http://lionlix.wordpress.com/2009/11/07/hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen/](http://lionlix.wordpress.com/2009/11/07/hack-ubuntu-9-10-disabling-userlist-in-gdm-login-screen/)

and this 

hack-ubuntu-9-10-karmic-koala-gdm-login-screen
[http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/](http://lionlix.wordpress.com/2009/10/23/hack-ubuntu-9-10-karmic-koala-gdm-login-screen/)

Hope you like it all guys :)

-lionlix
What if neither Ctrl+ALT+F1 nor Ctrl+ALT+F7 do anything?

---

